---
title: ThunderLoan Audit Report
author: Lulox
date: June 16, 2024
header-includes:
  - \usepackage{titling}
  - \usepackage{graphicx}
---

\begin{titlepage}
\centering
\begin{figure}[h]
\centering
\includegraphics[width=0.5\textwidth]{logo.pdf}
\end{figure}
\vspace{2cm}
{\Huge\bfseries ThunderLoan Audit Report\par}
\vspace{1cm}
{\Large Version 1.0\par}
\vspace{2cm}
{\Large\itshape Lulox\par}
\vfill
{\large \today\par}
\end{titlepage}

\maketitle

<!-- Your report starts here! -->

Prepared by: [Lulox](https://x.com/LuloxEth)
Lead Auditors:

- Lulox

# Table of Contents

- [Table of Contents](#table-of-contents)
- [Protocol Summary](#protocol-summary)
- [Disclaimer](#disclaimer)
- [Risk Classification](#risk-classification)
- [Audit Details](#audit-details)
  - [Scope](#scope)
  - [Roles](#roles)
- [Executive Summary](#executive-summary)
  - [Issues found](#issues-found)
- [Findings](#findings)
- [High](#high)
- [Medium](#medium)
- [Low](#low)
- [Informational](#informational)
- [Gas](#gas)

# Protocol Summary

This project is a lending market (similar to [AAVE, one of the biggest lending and borrowing protocol](https://www.youtube.com/watch?v=dTCwssZ116A)) to provide liquidity to flashloan users, in exchange for fees that are accrued by the shareholders of the lending pool. [A flash loan is a loan that exists for exactly 1 transaction](https://www.youtube.com/watch?v=Aw7yvGFtOvI). A user can borrow any amount of assets from the protocol as long as they pay it back in the same transaction. If they don't pay it back, the transaction reverts and the loan is cancelled.

It uses [TSwap Protocol](https://github.com/Cyfrin/5-t-swap-audit) as an oracle to maintain stability in the exchange rate.

# Disclaimer

The Lulox team makes all effort to find as many vulnerabilities in the code in the given time period, but holds no responsibilities for the findings provided in this document. A security audit by the team is not an endorsement of the underlying business or product. The audit was time-boxed and the review of the code was solely on the security aspects of the Solidity implementation of the contracts.

# Risk Classification

|            |        | Impact |        |     |
| ---------- | ------ | ------ | ------ | --- |
|            |        | High   | Medium | Low |
|            | High   | H      | H/M    | M   |
| Likelihood | Medium | H/M    | M      | M/L |
|            | Low    | M      | M/L    | L   |

We use the [CodeHawks](https://docs.codehawks.com/hawks-auditors/how-to-evaluate-a-finding-severity) severity matrix to determine severity. See the documentation for more details.

# Audit Details

**The findings described in this document correspond the following commit hash:**
`8803f851f6b37e99eab2e94b4690c8b70e26b3f6`

## Scope

```
./src
#-- /interfaces
|   #-- IFlashLoanReceiver.sol
|   #-- IPoolFactory.sol
|   #-- ITSwapPool.sol
|   #-- IThunderLoan.sol
#-- /protocol
|   #-- AssetToken.sol
|   #-- OracleUpgradeable.sol
|   #-- ThunderLoan.sol
#-- /upgradedProtocol
    #-- ThunderLoanUpgraded.sol
```

Solc Version: 0.8.20
Chain(s) to deploy contract to: Ethereum
ERC20s:
USDC
DAI
LINK
WETH

## Roles

- Owner: The owner of the protocol who has the power to upgrade the implementation.
- Liquidity Provider: A user who deposits assets into the protocol to earn interest.
- User: A user who takes out flash loans from the protocol.

# Executive Summary

## Issues found

| Severity | Number of issues found |
| -------- | ---------------------- |
| High     | 4                      |
| Medium   | 2                      |
| Low      | 2                      |
| Info     | 8                      |
| Gas      | 2                      |
| Total    | 18                     |

# Findings

## High

## Medium

## Low

## Informational

## Gas
