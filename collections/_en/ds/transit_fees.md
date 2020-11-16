---
title: Transit Fees
chapter: 4
order: 7
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Transit Fees

## Overview

IOU transit fees allow accounts to set a fee for utilizing their IOUs.

Account holders would be paid for providing liquidity and trust relationships.

This encourages a robust ripple network. This allow anyone to function as a liquidity provider (similar to BitInstant).

## Rationale

Transit fees are primarily intended to cover four cases:

Gateway: A gateway will have to make money even in a zero interest rate situation. By charging a very small 'tax' on transfers of their IOUs, a gateway can accumulate an income. Inter-Gateway: An inter-gateway allows people to easily move money from one gateway to another. They need to charge fees for this service and they need to maintain balances at the other gateways they move currency between. Debt Quality: You will generally prefer to hold gateway debt to other types of debt. You may consider some people poor credit risks. Debt Overhead: If somebody holds your IOUs and you have settlement terms with them, they can enforce those terms. If you incur a debt for someone else's convenience, you should share some of the benefit in exchange for the obligations you take on. (In theory, if Jack owes you $100 and you owe Joe $100, your balance is still zero. But now Joe might come to collect the $100 and you might have to collect from Jack.)

## Concept

The basic idea is that each hop in a ripple path will have an associated fee. The fee will determine how much currency must be pushed into the hop to get the same amount out.

Fees apply to three types of operations:

1) Transfer: Transfer occurs when an IOU changes hands without the identity of the paying party changing. For example, if user B holds gateway A IOUs and user C accepts gateway A IOUs, a payment from B to C will *transfer* the gateway IOUs. (You can tell it is transfer if the account can never run out. There is nothing the gateway can run out of when its IOUs change hands. It is not issuing or consuming IOUs.)

2) Credit: Credit occurs when an operation causes a user to owe another user money. So, for example, if user A wants to pay user C money through user B, and this winds up with user B holding newly-created user A IOUs, *credit* has been used by user A.

User A → User B → User C

If user B has no user C IOUs, user C must accept them for this path to work. If User a has no user B IOUs, user B must accept them for this path to work. If user A has user B IOUs, then no credit applies, the IOUs are just settled. Credit applies when you accept someone else's IOUs.

3) Downgrade: Downgrade occurs when an operation causes a user to hold IOUs that he values less than the IOUs he previously held. For example, say user A wants to pay user B some money. But user B only accepts Gateway C IOUs and user A has none. User A can give his IOUs to user D in exchange for gateway C IOUs he pays to user B. In this case, used D has downgraded his gateway C IOUs to user A IOUs. The link through user D is a downgrade, the link through gateway C is a transfer.

User A → User D → Gateway C → User B

## Implementation

1) Transfer: A transfer fee can be set per account. This will be stored in the account's root node. It will be in units of billionths of the amount being transferred.

2) Downgrade: Each ripple node can contain, for each user, an “input” quality and an “output” quality for IOUs between these two users. The fee charged will be based on the difference between the output quality and the input quality of the two ripple nodes. If there is a negative difference, no fee is charged. The units will be in billionths of the amount downgraded.

3) Credit: A use of credit occurs when you accept another person's IOUs and in exchange either offer your own or lose someone else's that you previous held. A fee can be charged for this. Credit fees are implemented by always valuating one's own IOUs at face value while valuing other people's IOUs at a discounted rate. (If the credit balance in a ripple node goes up and that node is not an endpoint of the payment path, credit has been used.)

Transfer fees always apply alone. No hop can both be a transfer and require any credit use or grade changes. A downgrade fee and a credit fee can apply to the same hop. In that case, the fee rate is the sum of the two fees. For example:

Joe (holds no IOUs) → Jack (holds Jeff IOUs, accepts Joe IOUs) → Jeff

Joe wishes to pay Jeff through Jack. Joe gives his IOUs to Jack, causing him to use the credit Jack has extended to him. Jack then gives his Jeff IOUs to Jeff, settling them, so Joe has paid Jeff. This causes Jack to downgrade from Jeff IOUs to Joe IOUs. If Joe held sufficient Jack IOUs, no credit fee would apply. (Annoyingly, this means a credit fee can apply to only part of a payment.)

Generally, you would set the input and output qualities the same for each ripple node. If you value gaining a particular IOU at 95% of the face value, you would typically value losing that same IOU also at 95% of the face value. But for the inter-gateway case, the input quality would be set lower than the output quality for each ripple node. Thus every path through the inter-gateway would entail a reduction in quality and thus a downgrade fee.

Redeem → Redeem : 1.0 : quality out Redeem → Issue : 1.0 : 1.0 + Transfer Fee Issue → Redeem : quality in : quality out Issue → Issue : quality in : 1.0

## Detailed Example

Alice → Bob → Carol

Say Bob owes Alice $50. Alice wants to pay Carol $100. If no fees apply, the payments would change this:

Alice: Holds $50 in Bob IOUs. (+$50 for Alice, -$50 for Bob) Total: Alice:+$50, Bob:-$50, Carol:$0

To:

Bob: Holds $50 in Alice IOUs. (+50 for Bob, -$50 for Alice) Carol: Holds $100 in Bob IOUs. (+100 for Carol, -100 for Bob) Total: Alice:-$50, Bob:-$50, Carol:+$100

Notice that Alice's payment to Carol leaves Bob with the same balance, -$50. Alice's balance has gone down by $100 and Carol's has gone up by $100. So it's a $100 payment from Alice to Carol, though Bob.

Bob must accept his own IOUs at face value. He cannot charge a fee for that. But he can charge a fee for accepting the $50 in Alice IOUs. And he can charge a fee for issuing IOUs to Carol. (Because Carol can impose costs on him by demanding he settle them. He may need to arrange such terms to get Carol to accept his IOUs – the very thing that made this convenience to Alice possible.)

Suppose Bob places a 0.95 input quality on Alice IOUs and 1.02 output quality on Carol IOUs. This means the first $50 rippled into the path buy $49.02 out ($50 / 1.02). To get the remaining $50.98 out to make the $100 payment costs $53.06 ($50.98 * 1.02 / .98). The end result is this:

Bob: Holds $53.06 in Alice IOUs. (+$53.06 for Bob, -$53.06 for Alice) Carol: Holds $100 in Bob IOUs. (+$100 for Carol, -$100 for Bob) Total: Alice:-$53.06, Bob:-$46.94, Carol:+$100

The net effect is that Alice owes an extra $3.06 to Bob in exchange for possibly making him settle with Carol and Bob. If Bob paid through a gateway, he could avoid this fee (and instead pay a transfer fee that would likely be much, much less).

## Client-side Logic

We'll probably support three tiers, for gateways (good as fiat), good credit risks (happy to hold IOUs), and poor credit risks (prefer not to hold).

## Goal

The goal is to ensure everyone who provides a service can make money and to ensure that people wind up getting what they actually want just by the system finding the lowest-cost paths.

# Links
 
  * [Master_Key](./master_key)
  * [Transaction Fees](../../introduction/transaction_fee)
