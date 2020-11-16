---
title: Binary Format
chapter: 4
order: 4
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Binary Format

## Introduction

The binary format will consist of a set of fields, each of which has a type and a name. The list of names will be specific for each type.

## Encoding

The first byte is split in half. The four high-order bits are the type and the four low-order bits are the field. If the type or field is 1 through 15 inclusive, that is the type or field value. If the type or field value is zero, then a subsequent byte encodes the type or field value.

The next byte will encode the type if the type in the first byte was 0. In that case, it's an uncommon type and the next byte encodes which uncommon type it is.

The next byte will encode the value if the value in the first byte was 0. In that case, it's an uncommon value for that type, and the next byte encodes which uncommon value it is.

If the type is common and the field is common, then only a single byte is needed to encode the type and field. Code changes will be needed to support new types. Supporting new fields of a known type will only require adding a new name/number mapping.

Unless we ever add uncommon fields for uncommon types, the worst case encoding will be two bytes. It seems we'd never need this because it would have to be an uncommon field that nevertheless had so many types that they couldn't all be represented as common. In that unlikely case, three bytes would be used.

## Sorting

For signing or hashing, transactions and ledgers must be sorted into canonical order. Canonical order consists of sorting numerically first by type and then by name. Multiple entries of the same name and type are only permitted inside an array which preserves order internally.

## Type Encoding

Note: The most current type table is found in the SField.h file.

### Common Types:

  * 1: 16-bit unsigned integer
  * 2: 32-bit unsigned integer
  * 3: 64-bit unsigned integer
  * 4: 128-bit hash
  * 5: 256-bit hash
  * 6: Currency Amount
  * 7: Variable length data
  * 8: Account
  * 9-13: Reserved
  * 14: Inner object (An object consisting of multiple fields)
  * 15: Array of objects (An ordered array of objects)

### Uncommon Types:

  * 16: 8-bit unsigned integer
  * 17: 160-bit unsigned integer
  * 18: Path set
  * 19: Vector of 256-bit values

## Field Name Encodings

Note: The most current encodings are found in the SField.cpp file.

### 8-bit unsigned common:

  * 1: Ledger Close Time Resolution
  * 2: Template Entry Type
  * 3: Transaction Result (for metadata)

### 16-bit unsigned common:

  * 1: Ledger Entry Type
  * 2: Transaction Type

### 32-bit unsigned common:

  * 1: Flags
  * 2: Source tag
  * 3: Sequence Number
  * 4: Previous Transaction Ledger Sequence
  * 5: Ledger Sequence
  * 6: Ledger Close Time
  * 7: Parent Ledger Close Time
  * 8: Signing Time
  * 9: Expiration Time
  * 10: Transfer Rate
  * 11: Wallet Size
  * 12: Owner Count
  * 13: Destination Tag

### Variable Length common:

  * 1: Public Key
  * 2: Message Key
  * 3: Signing Public Key
  * 4: Transaction Signature
  * 5: Generator
  * 6: Signature
  * 7: Domain
  * 8: Fund Script
  * 9: Remove Script
  * 10: Expire Script
  * 11: Create Script
  * 12: Memo Type
  * 13: Memo Data

### Account common:

  * 1: Account
  * 2: Owner
  * 3: Destination
  * 4: Issuer
  * 7: Target
  * 8: Authorized/Regular Key

### Amount common:

  * 1: Amount
  * 2: Balance
  * 3: Limit
  * 4: Taker Pays
  * 5: Taker Gets
  * 6: Low Limit
  * 7: High Limit
  * 8: Fee
  * 9: Send Maximum

### 128-bit common:

  * 1: Email Hash

### 256-bit common:

  * 1: Ledger Hash
  * 2: Parent Ledger Hash
  * 3: Transaction Tree Hash
  * 4: State Tree Hash
  * 5: Previous Transaction ID
  * 6: Ledger Index (for metadata)
  * 7: Wallet Locator
  * 8: Root Index
  * 9: Account Transaction ID


To be continued...

(@see: 🌐  <https://wiki.ripple.com/Binary_Format>)

