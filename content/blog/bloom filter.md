---
title: "Understanding Bloom Filters in Ethereum"
date: "2024-09-17T15:00:00-05:00"
tags: ["Bloom Filter", "Advanced Data Management", "Blockchain"]
draft: false
---

**Note**: This article assumes that the reader already understands what a Bloom Filter is. If you are not familiar, reference [1](#references) provides a very clear explanation along with code implementations that you can review.

### Bloom Filter Recap
A Bloom Filter is a data structure composed of an array of `n` bits. If we want to check whether a piece of data exists in a dataset, we can use a Bloom Filter to reduce search time.

To query whether a piece of data (x) exists in a dataset, we use `m` different hash functions (`h1(x), h2(x), … hm(x)`), each of which generates a value. After taking the modulo of each value by `n`, we get `m` integers (0 ≤ integer < n, which serve as indices).

Once we get the values at these `m` positions in the Bloom Filter, if all the results are 1, the data *might* exist in the dataset, and further searching is worthwhile. However, if any of the `m` positions is 0, it means the data definitely does not exist in the dataset, saving the need for further searching.

### Bloom Filter in Ethereum
In the case of Ethereum, each block header contains a Bloom Filter that is 2048 bits in size. Each transaction's log records (up to 4 topics) and the addresses involved in the transaction are recorded in the Filter [3](#references).

When a user searches for all transactions related to a specific address on the blockchain, the program first checks the Bloom Filter in each block. If all `m` positions are 1, the block might contain data related to that address, and the program will inspect the block further. If any position is 0, the block does not contain relevant data, and the program can skip it, saving search time.

Let's dive into how much search time can be saved using a specific example of searching for addresses.

### False Positive Rate Estimation (2022 / 12 / 20)
**Note**: I did not run experiments; the following estimates may be incorrect. Feel free to leave comments for corrections.

#### Worst Case Scenario
In the worst case, the block contains a large amount of data, making it more likely to mistakenly believe that some data exists in the block. How much data can a block hold?

According to Etherscan, the gas used per block is approximately 10,000,000 gas, and a simple transfer transaction consumes around 21,000 gas. This means each block contains about 476 transactions (10,000,000 gas / 21,000 gas). Each transaction involves 3 addresses (sender, receiver, contract). Thus, each Bloom Filter would contain data for about 1428 addresses.

However, the Bloom Filter contains not only address data but also other information, such as transaction logs [3](#references). When searching for addresses, the actual False Positive Rate would likely be higher than the following scenario.

**False Positive Rate**: ≈ 67% (this seems a bit unrealistic...)

#### Average Scenario
- **Bloom Filter Size**: 2048 bits

Based on data from Etherscan, each block contains an average of 150 transactions, with each transaction involving 3 addresses. Therefore, each Bloom Filter contains approximately 450 pieces of data (150 * 3).

**False Positive Rate**: ≈ 10% (still somewhat high)

### References:
1. [Data Structure Overview: Bloom Filter](https://medium.com/@Kadai/%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B%E5%A4%A7%E4%BE%BF%E7%95%B6-bloom-filter-58b0320a346d)
2. [Ethereum's Bloom Filters Explained](https://medium.com/@naterush1997/eth-goes-bloom-filling-up-ethereums-bloom-filters-68d4ce237009)
3. [What Exactly Is Included in the Bloom Filters?](https://ethereum.stackexchange.com/questions/17256/what-exactly-is-included-in-the-bloom-filters)
