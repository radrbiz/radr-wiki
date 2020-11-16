---
title: Returning Payments
chapter: 3
order: 5
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Returning Payments

## Introduction

From time to time payments may need to be returned. This page suggests a standard policy for returning payments.

## Reasons for Returning Funds
  
  * A payment was sent in error
  * Incomplete payment was made
  * To return of an overpayment amount
  * To return a payment made to an expired offer
  * When a merchant agrees to perform a refund

## Complications in Returning Funds

The nature of Radar networking is such that a sender may incur costs when delivering funds to a receiver, and additional fees may be required to return these funds.

Due to currency risk, delays in returning funds may cause the amount returned to be different than the original amount sent.

## Standard Policies

  * Returns may be processed automatically.
  * The original sender agrees returns are to be made to the original sender's address with the destination tag set to the original payment transaction's source tag (if a source tag was provided).
  * For unsolicited payments, the returner may deduct a reasonable amount to cover the return payment's transaction fee.
    * Rationale: Most merchants and reasonable persons will waive this trivial cost. However, no one should be obligated to pay for returning spam payments.
  * Unless disclaimed, the receiver should not be responsible for any costs incurred by the sender in delivering payments. This is regardless of whether or not the transaction is completed.
    * Rationale: The sender has little to no control over the costs involved in delivering payment.
  * Unless disclaimed, the returner of funds will select the delivery path providing the best rate.
    * Rationale: The sender can directly or indirectly incur additional costs in delivering payment.
  * Unless disclaimed, the returner of funds will not be responsible for delivery costs, and the delivered sum will be reduced by these costs.
    * Rationale: Waiting for advantageous conversion rates places a needless burden on the the returner. The amount of liquidity generally available is the choice of the original sender in choosing their credit relationships.
  * Unless disclaimed, the returner of funds need only make responsible efforts to return the funds.
    * Rationale: The original sender may not have sufficient liquidity to receive the funds.

## Implementation

### Sending funds

When originating payments, to allow correct bouncing set the source_tag to identify where return payments should be bounced to.

When returning payments, set the destination_tag to the original payment's source_tag to identify return payments.

### Returning funds

When constructing the return payment:
  * Set the tfPartialPayment flag to shift the sending costs, other than the transaction fee, to the receiver.
  * Set the DestinationTag to the SourceTag of the original payment.
  * Set Amount to the currency and issuer of the receiver's SendMax.
