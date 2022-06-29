
<!--
Guiding Principles:

Changelogs are for humans, not machines.
There should be an entry for every single version.
The same types of changes should be grouped.
Versions and sections should be linkable.
The latest version comes first.
The release date of each version is displayed.
Mention whether you follow Semantic Versioning.

Usage:

Change log entries are to be added to the Unreleased section under the
appropriate stanza (see below). Each entry should ideally include a tag and
the Github issue reference in the following format:

* (<tag>) \#<issue-number> message

The issue numbers will later be link-ified during the release process so you do
not have to worry about including a link manually, but you can if you wish.

Types of changes (Stanzas):

"Features" for new features.
"Improvements" for changes in existing functionality.
"Deprecated" for soon-to-be removed features.
"Bug Fixes" for any bug fixes.
"Client Breaking" for breaking CLI commands and REST routes used by end-users.
"API Breaking" for breaking exported APIs used by developers building on SDK.
"State Machine Breaking" for any changes that result in a different AppState given same genesisState and txList.

Ref: https://keepachangelog.com/en/1.0.0/
-->

# Changelog

## [v0.1.1] - 2022-06-27

### State Machine Breaking

* (evm) [\#1128](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1128) Clear tx logs if tx failed in post processing hooks
* (evm) [\#1124](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1124) Reject non-replay-protected tx in `AnteHandler` to prevent replay attack

### API Breaking

* (rpc) [\#1126](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1126) Make some JSON-RPC APIS work for pruned nodes.
* (rpc) [\#1143](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1143) Restrict unprotected txs on the node JSON-RPC configuration.
* (all) [\#1137](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1137) Rename go module to `Ambiplatforms-TORQUE/ethermint`

### Improvements

* (deps) [\#1147](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1147) Bump Go version to `1.18`.
* (feemarket) [\#1135](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1135) Set lower bound of base fee to min gas price param
* (evm) [\#1142](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1142) Rename `RejectUnprotectedTx` to `AllowUnprotectedTxs` for consistency with go-ethereum.

### Bug Fixes

* (rpc) [\#1138](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1138) Fix GasPrice calculation with relation to `MinGasPrice`

## [v0.16.1] - 2022-06-09

### Improvements

* (feemarket) [\#1120](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1120) Make `min-gas-multiplier` parameter accept zero value

### Bug Fixes

* (evm) [\#1118](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1118) Fix `Type()` `Account` method `EmptyCodeHash` comparison

## [v0.16.0] - 2022-06-06

### State Machine Breaking

* (feemarket) [Ambiplatforms-TORQUE#1105](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1105) Update `BaseFee` calculation based on `GasWanted` instead of `GasUsed`.

### API Breaking

* (feemarket) [Ambiplatforms-TORQUE#1104](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1104) Enforce a minimum gas price for Cosmos and EVM transactions through the `MinGasPrice` parameter.
* (rpc) [Ambiplatforms-TORQUE#1081](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1081) Deduplicate some json-rpc logic codes, cleanup several dead functions.
* (ante) [Ambiplatforms-TORQUE#1062](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1062) Emit event of eth tx hash in ante handler to support query failed transactions.
* (analytics) [Ambiplatforms-TORQUE#1106](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1106) Update telemetry to Ethermint modules.
* (rpc) [Ambiplatforms-TORQUE#1108](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1108) Update GetGasPrice RPC endpoint with global `MinGasPrice`

### Improvements

* (cli) [Ambiplatforms-TORQUE#1086](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1086) Add rollback command.
* (specs) [Ambiplatforms-TORQUE#1095](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1095) Add more evm specs concepts.
* (evm) [Ambiplatforms-TORQUE#1101](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1101) Add tx_type, gas and counter telemetry for ethereum txs.

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#1082](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1082) fix gas price returned in getTransaction api.
* (evm) [Ambiplatforms-TORQUE#1088](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1088) Fix ability to append log in tx post processing.
* (rpc) [Ambiplatforms-TORQUE#1081](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1081) fix `debug_getBlockRlp`/`debug_printBlock` don't filter failed transactions.
* (ante) [Ambiplatforms-TORQUE#1111](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1111) Move CanTransfer decorator before GasConsume decorator
* (types) [Ambiplatforms-TORQUE#1112](https://github.com/cosmos/ethermint/pull/1112) Add `GetBaseAccount` to avoid invalid account error when create vesting account.

## [v0.15.0] - 2022-05-09

### State Machine Breaking

* (ante) [Ambiplatforms-TORQUE#1060](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1060) Check `EnableCreate`/`EnableCall` in `AnteHandler` to short-circuit EVM transactions.
* (evm) [Ambiplatforms-TORQUE#1087](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1087) Minimum GasUsed proportional to GasLimit and `MinGasDenominator` EVM module param.

### API Breaking

* (rpc) [Ambiplatforms-TORQUE#1070](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1070) Refactor `rpc/` package:
  * `Backend` interface is now `BackendI`, which implements `EVMBackend` (for Ethereum namespaces) and `CosmosBackend` (for Cosmos namespaces)
  * Previous `EVMBackend` type is now `Backend`, which is the concrete implementation of `BackendI`
  * Move `rpc/ethereum/types` -> `rpc/types`
  * Move `rpc/ethereum/backend` -> `rpc/backend`
  * Move `rpc/ethereum/namespaces` -> `rpc/namespaces/ethereum`
* (rpc) [Ambiplatforms-TORQUE#1068](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1068) Fix London hard-fork check logic in JSON-RPC APIs.

### Improvements

* (ci, evm) [Ambiplatforms-TORQUE#1063](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1063) Run simulations on CI.

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#1059](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1059) Remove unnecessary event filtering logic on the `eth_baseFee` JSON-RPC endpoint.

## [v0.14.0] - 2022-04-19

### API Breaking

* (evm) [Ambiplatforms-TORQUE#1051](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1051) Context block height fix on TraceTx. Removes `tx_index` on `QueryTraceTxRequest` proto type.
* (evm) [Ambiplatforms-TORQUE#1091](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1091) Add query params command on EVM Module

### Improvements

* (deps) [Ambiplatforms-TORQUE#1046](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1046) Bump Cosmos SDK version to [`v0.45.3`](https://github.com/cosmos/cosmos-sdk/releases/tag/v0.45.3)
* (rpc) [Ambiplatforms-TORQUE#1056](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1056) Make json-rpc namespaces extensible

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#1050](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1050) `eth_getBlockByNumber` fix on batch transactions
* (app) [Ambiplatforms-TORQUE#658](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/658) Support simulations for the EVM.

## [v0.13.0] - 2022-04-05

### API Breaking

* (evm) [Ambiplatforms-TORQUE#1027](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1027) Change the `PostTxProcessing` hook interface to include the full message data.
* (feemarket) [Ambiplatforms-TORQUE#1026](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1026) Fix REST endpoints to use `/ethermint/feemarket/*` instead of `/feemarket/evm/*`.

### Improvements

* (deps) [Ambiplatforms-TORQUE#1029](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1029) Bump Cosmos SDK version to [`v0.45.2`](https://github.com/cosmos/cosmos-sdk/releases/tag/v0.45.2)
* (evm) [Ambiplatforms-TORQUE#1025](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1025) Allow to append logs after a post processing hook.

## [v0.12.2] - 2022-03-30

### Bug Fixes

* (feemarket) [Ambiplatforms-TORQUE#1021](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1021) Fix fee market migration.

## [v0.12.1] - 2022-03-29

### Bug Fixes

* (evm) [Ambiplatforms-TORQUE#1016](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1016) Update validate basic check for storage state.

## [v0.12.0] - 2022-03-24

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#1012](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1012) fix the tx hash in filter entries created by `eth_newPendingTransactionFilter`.
* (rpc) [Ambiplatforms-TORQUE#1006](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1006) Use `string` as the parameters type to correct ambiguous results.
* (ante) [Ambiplatforms-TORQUE#1004](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/1004) Make `MaxTxGasWanted` configurable.
* (ante) [Ambiplatforms-TORQUE#991](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/991) Set an upper bound to gasWanted to prevent DoS attack.
* (rpc) [Ambiplatforms-TORQUE#990](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/990) Calculate reward values from all `MsgEthereumTx` from a block in `eth_feeHistory`.

## [v0.11.0] - 2022-03-06

### State Machine Breaking

* (ante) [Ambiplatforms-TORQUE#964](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/964) add NewInfiniteGasMeterWithLimit for storing the user provided gas limit. Fixes block's consumed gas calculation in the block creation phase.

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#975](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/975) Fix unexpected `nil` values for `reward`, returned by `EffectiveGasTipValue(blockBaseFee)` in the `eth_feeHistory` RPC method.

### Improvements

* (rpc) [Ambiplatforms-TORQUE#979](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/979) Add configurable timeouts to http server
* (rpc) [Ambiplatforms-TORQUE#988](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/988) json-rpc server always use local rpc client

## [v0.10.1] - 2022-03-04

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#970](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/970) Fix unexpected nil reward values on `eth_feeHistory` response
* (evm) [Ambiplatforms-TORQUE#529](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/529) Add support return value on trace tx response.

### Improvements

* (rpc) [Ambiplatforms-TORQUE#968](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/968) Add some buffer to returned gas price to provide better default UX for client.

## [v0.10.0] - 2022-02-26

### API Breaking

* (ante) [Ambiplatforms-TORQUE#866](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/866) `NewAnteHandler` constructor now receives a `HandlerOptions` field.
* (evm) [Ambiplatforms-TORQUE#849](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/849) `PostTxProcessing` hook now takes an Ethereum tx `Receipt` and a `from` `Address` as arguments.
* (ante) [Ambiplatforms-TORQUE#916](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/916) Don't check min-gas-price for eth tx if london hardfork enabled and feemarket enabled.

### State Machine Breaking

* (deps) [Ambiplatforms-TORQUE#912](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/912) Bump Cosmos SDK version to [`v0.45.1`](https://github.com/cosmos/cosmos-sdk/releases/tag/v0.45.1)
* (evm) [Ambiplatforms-TORQUE#840](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/840) Store empty topics as empty array rather than nil.
* (feemarket) [Ambiplatforms-TORQUE#822](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/822) Update EIP1559 base fee in `BeginBlock`.
* (evm) [Ambiplatforms-TORQUE#817](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/817) Use `effectiveGasPrice` in ante handler, add `effectiveGasPrice` to tx receipt.
* (evm) [Ambiplatforms-TORQUE#808](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/808) increase nonce in ante handler for contract creation transaction.
* (evm) [Ambiplatforms-TORQUE#851](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/851) fix contract address used in EVM, this issue is caused by [Ambiplatforms-TORQUE#808](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/808).
* (evm)  Reject invalid `MsgEthereumTx` wrapping tx
* (evm)  Fix `SelfDestruct` opcode by deleting account code and state.
* (feemarket) [Ambiplatforms-TORQUE#855](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/855) Consistent `BaseFee` check logic.
* (evm) [Ambiplatforms-TORQUE#729](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/729) Refactor EVM `StateDB` implementation.
* (evm) [Ambiplatforms-TORQUE#945](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/945) Bumb Go-ethereum version to [`v1.10.16`](https://github.com/ethereum/go-ethereum/releases/tag/v1.10.16)

### Features

* (ante) [Ambiplatforms-TORQUE#950](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/950) Add support for EIP712 signed Cosmos transactions

### Improvements

* (types) [Ambiplatforms-TORQUE#884](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/884) Introduce a new `EthAccountI` interface for EVM-compatible account types.
* (types) [Ambiplatforms-TORQUE#849](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/849) Add `Type` function to distinguish EOAs from Contract accounts.
* (evm) [Ambiplatforms-TORQUE#826](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/826) Improve allocation of bytes of `tx.To` address.
* (evm) [Ambiplatforms-TORQUE#827](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/827) Speed up creation of event logs by using the slice insertion idiom with indices.
* (ante) [Ambiplatforms-TORQUE#819](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/819) Remove redundant ante handlers
* (app) [Ambiplatforms-TORQUE#873](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/873) Validate code hash in GenesisAccount
* (evm) [Ambiplatforms-TORQUE#901](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/901) Support multiple `MsgEthereumTx` in single tx.
* (config) [Ambiplatforms-TORQUE#908](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/908) Add `api.enable` flag for Cosmos SDK Rest server
* (feemarket) [Ambiplatforms-TORQUE#919](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/919) Initialize baseFee in default genesis state.
* (feemarket) [Ambiplatforms-TORQUE#943](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/943) Store the base fee as a module param instead of using state storage.

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#955](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/955) Fix websocket server push duplicated messages to subscriber.
* (rpc) [Ambiplatforms-TORQUE#953](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/953) Add `eth_signTypedData` api support.
* (log) [Ambiplatforms-TORQUE#948](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/948) Redirect go-ethereum's logs to cosmos-sdk logger.
* (evm) [Ambiplatforms-TORQUE#884](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/884) Support multiple account types on the EVM `StateDB`.
* (rpc) [Ambiplatforms-TORQUE#831](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/831) Fix BaseFee value when height is specified.
* (evm) [Ambiplatforms-TORQUE#838](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/838) Fix splitting of trace.Memory into 32 chunks.
* (rpc) [Ambiplatforms-TORQUE#860](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/860) Fix `eth_getLogs` when specify blockHash without address/topics, and limit the response size.
* (rpc) [Ambiplatforms-TORQUE#865](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/865) Fix RPC Filter parameters being ignored
* (evm) [Ambiplatforms-TORQUE#871](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/871) Set correct nonce in `EthCall` and `EstimateGas` grpc query.
* (rpc) [Ambiplatforms-TORQUE#878](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/878) Workaround to make GetBlock RPC api report correct block gas used.
* (rpc) [Ambiplatforms-TORQUE#900](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/900) `newPendingTransactions` filter return ethereum tx hash.
* (rpc) [Ambiplatforms-TORQUE#933](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/933) Fix `newPendingTransactions` subscription deadlock when a Websocket client exits without unsubscribing and the node errors.
* (evm) [Ambiplatforms-TORQUE#932](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/932) Fix base fee check logic in state transition.

## [v0.9.0] - 2021-12-01

### State Machine Breaking

* (evm) [Ambiplatforms-TORQUE#802](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/802) Clear access list for each transaction

### Improvements

* (app) [Ambiplatforms-TORQUE#794](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/794) Setup in-place store migrators.
* (ci) [Ambiplatforms-TORQUE#784](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/784) Enable automatic backport of PRs.
* (rpc) [Ambiplatforms-TORQUE#786](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/786) Improve error message of `SendTransaction`/`SendRawTransaction` JSON-RPC APIs.
* (rpc) [Ambiplatforms-TORQUE#810](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/810) Optimize tx index lookup in web3 rpc

### Bug Fixes

* (license) [Ambiplatforms-TORQUE#800](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/800) Re-license project to [LGPLv3](https://choosealicense.com/licenses/lgpl-3.0/#) to comply with go-ethereum.
* (evm) [Ambiplatforms-TORQUE#794](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/794) Register EVM gRPC `Msg` server.
* (rpc) [Ambiplatforms-TORQUE#781](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/781) Fix get block invalid transactions filter.
* (rpc) [Ambiplatforms-TORQUE#782](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/782) Fix wrong block gas limit returned by JSON-RPC.
* (evm) [Ambiplatforms-TORQUE#798](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/798) Fix the semantic of `ForEachStorage` callback's return value

## [v0.8.1] - 2021-11-23

### Bug Fixes

* (feemarket) [Ambiplatforms-TORQUE#770](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/770) Enable fee market (EIP1559) by default.
* (rpc) [Ambiplatforms-TORQUE#769](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/769) Fix default Ethereum signer for JSON-RPC.

## [v0.8.0] - 2021-11-17

### State Machine Breaking

* (evm, ante) [Ambiplatforms-TORQUE#620](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/620) Add fee market field to EVM `Keeper` and `AnteHandler`.
* (all) [Ambiplatforms-TORQUE#231](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/231) Bump go-ethereum version to [`v1.10.9`](https://github.com/ethereum/go-ethereum/releases/tag/v1.10.9)
* (ante) [Ambiplatforms-TORQUE#703](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/703) Fix some fields in transaction are not authenticated by signature.
* (evm) [Ambiplatforms-TORQUE#751](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/751) don't revert gas refund logic when transaction reverted

### Features

* (rpc, evm) [Ambiplatforms-TORQUE#673](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/673) Use tendermint events to store fee market basefee.
* (rpc) [Ambiplatforms-TORQUE#624](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/624) Implement new JSON-RPC endpoints from latest geth version
* (evm) [Ambiplatforms-TORQUE#662](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/662) Disable basefee for non london blocks
* (cmd) [Ambiplatforms-TORQUE#712](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/712) add tx cli to build evm transaction
* (rpc) [Ambiplatforms-TORQUE#733](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/733) add JSON_RPC endpoint `personal_unpair`
* (rpc) [Ambiplatforms-TORQUE#734](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/734) add JSON_RPC endpoint `eth_feeHistory`
* (rpc) [Ambiplatforms-TORQUE#740](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/740) add JSON_RPC endpoint `personal_initializeWallet`
* (rpc) [Ambiplatforms-TORQUE#743](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/743) add JSON_RPC endpoint `debug_traceBlockByHash`
* (rpc) [Ambiplatforms-TORQUE#748](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/748) add JSON_RPC endpoint `personal_listWallets`
* (rpc) [Ambiplatforms-TORQUE#754](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/754) add JSON_RPC endpoint `debug_intermediateRoots`

### Bug Fixes

* (evm) [Ambiplatforms-TORQUE#746](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/746) Set EVM debugging based on tracer configuration.
* (app,cli) [Ambiplatforms-TORQUE#725](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/725) Fix cli-config for  `keys` command.
* (rpc) [Ambiplatforms-TORQUE#727](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/727) Decode raw transaction using RLP.
* (rpc) [Ambiplatforms-TORQUE#661](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/661) Fix OOM bug when creating too many filters using JSON-RPC.
* (evm) [Ambiplatforms-TORQUE#660](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/660) Fix `nil` pointer panic in `ApplyNativeMessage`.
* (evm, test) [Ambiplatforms-TORQUE#649](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/649) Test DynamicFeeTx.
* (evm) [Ambiplatforms-TORQUE#702](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/702) Fix panic in web3 RPC handlers
* (rpc) [Ambiplatforms-TORQUE#720](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/720) Fix `debug_traceTransaction` failure
* (rpc) [Ambiplatforms-TORQUE#741](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/741) Fix `eth_getBlockByNumberAndHash` return with non eth txs
* (rpc) [Ambiplatforms-TORQUE#743](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/743) Fix debug JSON RPC handler crash on non-existing block

### Improvements

* (tests) [Ambiplatforms-TORQUE#704](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/704) Introduce E2E testing framework for clients
* (deps) [Ambiplatforms-TORQUE#737](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/737) Bump ibc-go to [`v2.0.0`](https://github.com/cosmos/ibc-go/releases/tag/v2.0.0)
* (rpc) [Ambiplatforms-TORQUE#671](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/671) Don't pass base fee externally for `EthCall`/`EthEstimateGas` apis.
* (evm) [Ambiplatforms-TORQUE#674](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/674) Refactor `ApplyMessage`, remove
  `ApplyNativeMessage`.
* (rpc) [Ambiplatforms-TORQUE#714](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/714) remove `MsgEthereumTx` support in `TxConfig`

## [v0.7.2] - 2021-10-24

### Improvements

* (deps) [Ambiplatforms-TORQUE#692](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/692) Bump Cosmos SDK version to [`v0.44.3`](https://github.com/cosmos/cosmos-sdk/releases/tag/v0.44.3).
* (rpc) [Ambiplatforms-TORQUE#679](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/679) Fix file close handle.
* (deps) [Ambiplatforms-TORQUE#668](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/668) Bump Tendermint version to [`v0.34.14`](https://github.com/tendermint/tendermint/releases/tag/v0.34.14).

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#667](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/667) Fix `ExpandHome` restrictions bypass

## [v0.7.1] - 2021-10-08

### Bug Fixes

* (evm) [Ambiplatforms-TORQUE#650](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/650) Fix panic when flattening the cache context in case transaction is reverted.
* (rpc, test) [Ambiplatforms-TORQUE#608](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/608) Fix rpc test.

## [v0.7.0] - 2021-10-07

### API Breaking

* (rpc) [Ambiplatforms-TORQUE#400](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/400) Restructure JSON-RPC directory and rename server config

### Improvements

* (deps) [Ambiplatforms-TORQUE#621](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/621) Bump IBC-go to [`v1.2.1`](https://github.com/cosmos/ibc-go/releases/tag/v1.2.1)
* (evm) [Ambiplatforms-TORQUE#613](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/613) Refactor `traceTx`
* (deps) [Ambiplatforms-TORQUE#610](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/610) Bump Cosmos SDK to [v0.44.1](https://github.com/cosmos/cosmos-sdk/releases/tag/v0.44.1).

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#642](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/642) Fix `eth_getLogs` when string is specified in filter's from or to fields
* (evm) [Ambiplatforms-TORQUE#616](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/616) Fix halt on deeply nested stack of cache context. Stack is now flattened before iterating over the tx logs.
* (rpc, evm) [Ambiplatforms-TORQUE#614](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/614) Use JSON for (un)marshaling tx `Log`s from events.
* (rpc) [Ambiplatforms-TORQUE#611](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/611) Fix panic on JSON-RPC when querying for an invalid block height.
* (cmd) [Ambiplatforms-TORQUE#483](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/483) Use config values on genesis accounts.

## [v0.6.0] - 2021-09-29

### State Machine Breaking

* (app) [Ambiplatforms-TORQUE#476](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/476) Update Bech32 HRP to `ethm`.
* (evm) [Ambiplatforms-TORQUE#556](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/556) Remove tx logs and block bloom from chain state
* (evm) [Ambiplatforms-TORQUE#590](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/590) Contract storage key is not hashed anymore

### API Breaking

* (evm) [Ambiplatforms-TORQUE#469](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/469) Deprecate `YoloV3Block` and `EWASMBlock` from `ChainConfig`

### Features

* (evm) [Ambiplatforms-TORQUE#469](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/469) Support [EIP-1559](https://eips.ethereum.org/EIPS/eip-1559)
* (evm) [Ambiplatforms-TORQUE#417](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/417) Add `EvmHooks` for tx post-processing
* (rpc) [Ambiplatforms-TORQUE#506](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/506) Support for `debug_traceTransaction` RPC endpoint
* (rpc) [Ambiplatforms-TORQUE#555](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/555) Support for `debug_traceBlockByNumber` RPC endpoint

### Bug Fixes

* (rpc, server) [Ambiplatforms-TORQUE#600](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/600) Add TLS configuration for websocket API
* (rpc) [Ambiplatforms-TORQUE#598](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/598) Check truncation when creating a `BlockNumber` from `big.Int`
* (evm) [Ambiplatforms-TORQUE#597](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/597) Check for `uint64` -> `int64` block height overflow on `GetHashFn`
* (evm) [Ambiplatforms-TORQUE#579](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/579) Update `DeriveChainID` function to handle `v` signature values `< 35`.
* (encoding) [Ambiplatforms-TORQUE#478](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/478) Register `Evidence` to amino codec.
* (rpc) [Ambiplatforms-TORQUE#478](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/481) Getting the node configuration when calling the `miner` rpc methods.
* (cli) [Ambiplatforms-TORQUE#561](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/561) `Export` and `Start` commands now use the same home directory.

### Improvements

* (evm) [Ambiplatforms-TORQUE#461](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/461) Increase performance of `StateDB` transaction log storage (r/w).
* (evm) [Ambiplatforms-TORQUE#566](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/566) Introduce `stateErr` store in `StateDB` to avoid meaningless operations if any error happened before
* (rpc, evm) [Ambiplatforms-TORQUE#587](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/587) Apply bloom filter when query ethlogs with range of blocks
* (evm) [Ambiplatforms-TORQUE#586](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/586) Benchmark evm keeper

## [v0.5.0] - 2021-08-20

### State Machine Breaking

* (app, rpc) [Ambiplatforms-TORQUE#447](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/447) Chain ID format has been changed from `<identifier>-<epoch>` to `<identifier>_<EIP155_number>-<epoch>`
in order to clearly distinguish permanent vs impermanent components.
* (app, evm) [Ambiplatforms-TORQUE#434](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/434) EVM `Keeper` struct and `NewEVM` function now have a new `trace` field to define
the Tracer type used to collect execution traces from the EVM transaction execution.
* (evm) [Ambiplatforms-TORQUE#175](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/175) The msg `TxData` field is now represented as a `*proto.Any`.
* (evm) [Ambiplatforms-TORQUE#84](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/84) Remove `journal`, `CommitStateDB` and `stateObjects`.
* (rpc, evm) [Ambiplatforms-TORQUE#81](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/81) Remove tx `Receipt` from store and replace it with fields obtained from the Tendermint RPC client.
* (evm) [Ambiplatforms-TORQUE#72](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/72) Update `AccessList` to use `TransientStore` instead of map.
* (evm) [Ambiplatforms-TORQUE#68](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/68) Replace block hash storage map to use staking `HistoricalInfo`.
* (evm) [Ambiplatforms-TORQUE#276](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/276) Vm errors don't result in cosmos tx failure, just
  different tx state and events.
* (evm) [Ambiplatforms-TORQUE#342](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/342) Don't clear balance when resetting the account.
* (evm) [Ambiplatforms-TORQUE#334](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/334) Log index changed to the index in block rather than
  tx.
* (evm) [Ambiplatforms-TORQUE#399](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/399) Exception in sub-message call reverts the call if it's not propagated.

### API Breaking

* (proto) [Ambiplatforms-TORQUE#448](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/448) Bump version for all Ethermint messages to `v1`
* (server) [Ambiplatforms-TORQUE#434](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/434) `evm-rpc` flags and app config have been renamed to `json-rpc`.
* (proto, evm) [Ambiplatforms-TORQUE#207](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/207) Replace `big.Int` in favor of `sdk.Int` for `TxData` fields
* (proto, evm) [Ambiplatforms-TORQUE#81](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/81) gRPC Query and Tx service changes:
  * The `TxReceipt`, `TxReceiptsByBlockHeight` endpoints have been removed from the Query service.
  * The `ContractAddress`, `Bloom` have been removed from the `MsgEthereumTxResponse` and the
    response now contains the ethereum-formatted `Hash` in hex format.
* (eth) [Ambiplatforms-TORQUE#845](https://github.com/cosmos/ethermint/pull/845) The `eth` namespace must be included in the list of API's as default to run the rpc server without error.
* (evm) [Ambiplatforms-TORQUE#202](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/202) Web3 api `SendTransaction`/`SendRawTransaction` returns ethereum compatible transaction hash, and query api `GetTransaction*` also accept that.
* (rpc) [Ambiplatforms-TORQUE#258](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/258) Return empty `BloomFilter` instead of throwing an error when it cannot be found (`nil` or empty).
* (rpc) [Ambiplatforms-TORQUE#277](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/321) Fix `BloomFilter` response.

### Improvements

* (client) [Ambiplatforms-TORQUE#450](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/450) Add EIP55 hex address support on `debug addr` command.
* (server) [Ambiplatforms-TORQUE#343](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/343) Define a wrap tendermint logger `Handler` go-ethereum's `root` logger.
* (rpc) [Ambiplatforms-TORQUE#457](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/457) Configure RPC gas cap through app config.
* (evm) [Ambiplatforms-TORQUE#434](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/434) Support different `Tracer` types for the EVM.
* (deps) [Ambiplatforms-TORQUE#427](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/427) Bump ibc-go to [`v1.0.0`](https://github.com/cosmos/ibc-go/releases/tag/v1.0.0)
* (gRPC) [Ambiplatforms-TORQUE#239](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/239) Query `ChainConfig` via gRPC.
* (rpc) [Ambiplatforms-TORQUE#181](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/181) Use evm denomination for params on tx fee.
* (deps) [Ambiplatforms-TORQUE#423](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/423) Bump Cosmos SDK and Tendermint versions to [v0.43.0](https://github.com/cosmos/cosmos-sdk/releases/tag/v0.43.0) and [v0.34.11](https://github.com/tendermint/tendermint/releases/tag/v0.34.11), respectively.
* (evm) [Ambiplatforms-TORQUE#66](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/66) Support legacy transaction types for signing.
* (evm) [Ambiplatforms-TORQUE#24](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/24) Implement metrics for `MsgEthereumTx`, state transitions, `BeginBlock` and `EndBlock`.
* (rpc)  [Ambiplatforms-TORQUE#124](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/124) Implement `txpool_content`, `txpool_inspect` and `txpool_status` RPC methods
* (rpc) [Ambiplatforms-TORQUE#112](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/153) Fix `eth_coinbase` to return the ethereum address of the validator
* (rpc) [Ambiplatforms-TORQUE#176](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/176) Support fetching pending nonce
* (rpc) [Ambiplatforms-TORQUE#272](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/272) do binary search to estimate gas accurately
* (rpc) [Ambiplatforms-TORQUE#313](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/313) Implement internal debug namespace (Not including logger functions nor traces).
* (rpc) [Ambiplatforms-TORQUE#349](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/349) Implement configurable JSON-RPC APIs to manage enabled namespaces.
* (rpc) [Ambiplatforms-TORQUE#377](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/377) Implement `miner_` namespace. `miner_setEtherbase` and `miner_setGasPrice` are working as intended. All the other calls are not applicable and return `unsupported`.
* (eth) [Ambiplatforms-TORQUE#460](https://github.com/Ambiplatforms-TORQUE/ethermint/issues/460) Add support for EIP-1898.

### Bug Fixes

* (keys) [Ambiplatforms-TORQUE#346](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/346) Fix `keys add` command with `--ledger` flag for the `secp256k1` signing algorithm.
* (evm) [Ambiplatforms-TORQUE#291](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/291) Use block proposer address (validator operator) for `COINBASE` opcode.
* (rpc) [Ambiplatforms-TORQUE#81](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/81) Fix transaction hashing and decoding on `eth_sendTransaction`.
* (rpc) [Ambiplatforms-TORQUE#45](https://github.com/Ambiplatforms-TORQUE/ethermint/pull/45) Use `EmptyUncleHash` and `EmptyRootHash` for empty ethereum `Header` fields.

## [v0.4.1] - 2021-03-01

### API Breaking

* (faucet) [Ambiplatforms-TORQUE#678](https://github.com/cosmos/ethermint/pull/678) Faucet module has been removed in favor of client libraries such as [`@cosmjs/faucet`](https://github.com/cosmos/cosmjs/tree/master/packages/faucet).
* (evm) [Ambiplatforms-TORQUE#670](https://github.com/cosmos/ethermint/pull/670) Migrate types to the ones defined by the protobuf messages, which are required for the stargate release.

### Bug Fixes

* (evm) [Ambiplatforms-TORQUE#799](https://github.com/cosmos/ethermint/issues/799) Fix wrong precision in calculation of gas fee.
* (evm) [Ambiplatforms-TORQUE#760](https://github.com/cosmos/ethermint/issues/760) Fix Failed to call function EstimateGas.
* (evm) [Ambiplatforms-TORQUE#767](https://github.com/cosmos/ethermint/issues/767) Fix error of timeout when using Truffle to deploy contract.
* (evm) [Ambiplatforms-TORQUE#751](https://github.com/cosmos/ethermint/issues/751) Fix misused method to calculate block hash in evm related function.
* (evm) [Ambiplatforms-TORQUE#721](https://github.com/cosmos/ethermint/issues/721) Fix mismatch block hash in rpc response when use eht.getBlock.
* (evm) [Ambiplatforms-TORQUE#730](https://github.com/cosmos/ethermint/issues/730) Fix 'EIP2028' not open when Istanbul version has been enabled.
* (evm) [Ambiplatforms-TORQUE#749](https://github.com/cosmos/ethermint/issues/749) Fix panic in `AnteHandler` when gas price larger than 100000
* (evm) [Ambiplatforms-TORQUE#747](https://github.com/cosmos/ethermint/issues/747) Fix format errors in String() of QueryETHLogs
* (evm) [Ambiplatforms-TORQUE#742](https://github.com/cosmos/ethermint/issues/742) Add parameter check for evm query func.
* (evm) [Ambiplatforms-TORQUE#687](https://github.com/cosmos/ethermint/issues/687) Fix nonce check to explicitly check for the correct nonce, rather than a simple 'greater than' comparison.
* (api) [Ambiplatforms-TORQUE#687](https://github.com/cosmos/ethermint/issues/687) Returns error for a transaction with an incorrect nonce.
* (evm) [Ambiplatforms-TORQUE#674](https://github.com/cosmos/ethermint/issues/674) Reset all cache after account data has been committed in `EndBlock` to make sure every node state consistent.
* (evm) [Ambiplatforms-TORQUE#672](https://github.com/cosmos/ethermint/issues/672) Fix panic of `wrong Block.Header.AppHash` when restart a node with snapshot.
* (evm) [Ambiplatforms-TORQUE#775](https://github.com/cosmos/ethermint/issues/775) MisUse of headHash as blockHash when create EVM context.

### Features

* (api) [Ambiplatforms-TORQUE#821](https://github.com/cosmos/ethermint/pull/821) Individually enable the api modules. Will be implemented in the latest version of ethermint with the upcoming stargate upgrade.

### Features

* (api) [Ambiplatforms-TORQUE#825](https://github.com/cosmos/ethermint/pull/825) Individually enable the api modules. Will be implemented in the latest version of ethermint with the upcoming stargate upgrade.

## [v0.4.0] - 2020-12-15

### API Breaking

* (evm) [Ambiplatforms-TORQUE#661](https://github.com/cosmos/ethermint/pull/661) `Balance` field has been removed from the evm module's `GenesisState`.

### Features

* (rpc) [Ambiplatforms-TORQUE#571](https://github.com/cosmos/ethermint/pull/571) Add pending queries to JSON-RPC calls. This allows for the querying of pending transactions and other relevant information that pertains to the pending state:
  * `eth_getBalance`
  * `eth_getTransactionCount`
  * `eth_getBlockTransactionCountByNumber`
  * `eth_getBlockByNumber`
  * `eth_getTransactionByHash`
  * `eth_getTransactionByBlockNumberAndIndex`
  * `eth_sendTransaction` - the nonce will automatically update to its pending nonce (when none is explicitly provided)

### Improvements

* (evm) [Ambiplatforms-TORQUE#661](https://github.com/cosmos/ethermint/pull/661) Add invariant check for account balance and account nonce.
* (deps) [Ambiplatforms-TORQUE#654](https://github.com/cosmos/ethermint/pull/654) Bump go-ethereum version to [v1.9.25](https://github.com/ethereum/go-ethereum/releases/tag/v1.9.25)
* (evm) [Ambiplatforms-TORQUE#627](https://github.com/cosmos/ethermint/issues/627) Add extra EIPs parameter to apply custom EVM jump tables.

### Bug Fixes

* (evm) [Ambiplatforms-TORQUE#661](https://github.com/cosmos/ethermint/pull/661) Set nonce to the EVM account on genesis initialization.
* (rpc) [Ambiplatforms-TORQUE#648](https://github.com/cosmos/ethermint/issues/648) Fix block cumulative gas used value.
* (evm) [Ambiplatforms-TORQUE#621](https://github.com/cosmos/ethermint/issues/621) EVM `GenesisAccount` fields now share the same format as the auth module `Account`.
* (evm) [Ambiplatforms-TORQUE#618](https://github.com/cosmos/ethermint/issues/618) Add missing EVM `Context` `GetHash` field that retrieves a the header hash from a given block height.
* (app) [Ambiplatforms-TORQUE#617](https://github.com/cosmos/ethermint/issues/617) Fix genesis export functionality.
* (rpc) [Ambiplatforms-TORQUE#574](https://github.com/cosmos/ethermint/issues/574) Fix outdated version from `eth_protocolVersion`.

## [v0.3.1] - 2020-11-24

### Improvements

* (deps) [Ambiplatforms-TORQUE#615](https://github.com/cosmos/ethermint/pull/615) Bump Cosmos SDK version to [v0.39.2](https://github.com/cosmos/cosmos-sdk/tag/v0.39.2)
* (deps) [Ambiplatforms-TORQUE#610](https://github.com/cosmos/ethermint/pull/610) Update Go dependency to 1.15+.
* (evm) [Ambiplatforms-TORQUE#603](https://github.com/cosmos/ethermint/pull/603) Add state transition params that enable or disable the EVM `Call` and `Create` operations.
* (deps) [Ambiplatforms-TORQUE#602](https://github.com/cosmos/ethermint/pull/602) Bump tendermint version to [v0.33.9](https://github.com/tendermint/tendermint/releases/tag/v0.33.9)

### Bug Fixes

* (rpc) [Ambiplatforms-TORQUE#613](https://github.com/cosmos/ethermint/issues/613) Fix potential deadlock caused if the keyring `List` returned an error.

## [v0.3.0] - 2020-11-16

### API Breaking

* (crypto) [Ambiplatforms-TORQUE#559](https://github.com/cosmos/ethermint/pull/559) Refactored crypto package in preparation for the SDK's Stargate release:
  * `crypto.PubKeySecp256k1` and `crypto.PrivKeySecp256k1` are now `ethsecp256k1.PubKey` and `ethsecp256k1.PrivKey`, respectively
  * Moved SDK `SigningAlgo` implementation for Ethermint's Secp256k1 key to `crypto/hd` package.
* (rpc) [Ambiplatforms-TORQUE#588](https://github.com/cosmos/ethermint/pull/588) The `rpc` package has been refactored to account for the separation of each
corresponding Ethereum API namespace:
  * `rpc/namespaces/eth`: `eth` namespace. Exposes the `PublicEthereumAPI` and the `PublicFilterAPI`.
  * `rpc/namespaces/personal`: `personal` namespace. Exposes the `PrivateAccountAPI`.
  * `rpc/namespaces/net`: `net` namespace. Exposes the `PublicNetAPI`.
  * `rpc/namespaces/web3`: `web3` namespace. Exposes the `PublicWeb3API`.
* (evm) [Ambiplatforms-TORQUE#588](https://github.com/cosmos/ethermint/pull/588) The EVM transaction CLI has been removed in favor of the JSON-RPC.

### Improvements

* (deps) [Ambiplatforms-TORQUE#594](https://github.com/cosmos/ethermint/pull/594) Bump go-ethereum version to [v1.9.24](https://github.com/ethereum/go-ethereum/releases/tag/v1.9.24)

### Bug Fixes

* (ante) [Ambiplatforms-TORQUE#597](https://github.com/cosmos/ethermint/pull/597) Fix incorrect fee check on `AnteHandler`.
* (evm) [Ambiplatforms-TORQUE#583](https://github.com/cosmos/ethermint/pull/583) Fixes incorrect resetting of tx count and block bloom during `BeginBlock`, as well as gas consumption.
* (crypto) [Ambiplatforms-TORQUE#577](https://github.com/cosmos/ethermint/pull/577) Fix `BIP44HDPath` that did not prepend `m/` to the path. This now uses the `DefaultBaseDerivationPath` variable from go-ethereum to ensure addresses are consistent.

## [v0.2.1] - 2020-09-30

### Features

* (rpc) [Ambiplatforms-TORQUE#552](https://github.com/cosmos/ethermint/pull/552) Implement Eth Personal namespace `personal_importRawKey`.

### Bug fixes

* (keys) [Ambiplatforms-TORQUE#554](https://github.com/cosmos/ethermint/pull/554) Fix private key derivation.
* (app/ante) [Ambiplatforms-TORQUE#550](https://github.com/cosmos/ethermint/pull/550) Update ante handler nonce verification to accept any nonce greater than or equal to the expected nonce to allow to successive transactions.

## [v0.2.0] - 2020-09-24

### State Machine Breaking

* (app) [Ambiplatforms-TORQUE#540](https://github.com/cosmos/ethermint/issues/540) Chain identifier's format has been changed to match the Cosmos `chainID` [standard](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-5.md), which is required for IBC. The epoch number of the ID is used as the EVM `chainID`.

### API Breaking

* (types) [Ambiplatforms-TORQUE#503](https://github.com/cosmos/ethermint/pull/503) The `types.DenomDefault` constant for `"aphoton"` has been renamed to `types.AttoPhoton`.

### Improvements

* (types) [Ambiplatforms-TORQUE#504](https://github.com/cosmos/ethermint/pull/504) Unmarshal a JSON `EthAccount` using an Ethereum hex address in addition to Bech32.
* (types) [Ambiplatforms-TORQUE#503](https://github.com/cosmos/ethermint/pull/503) Add `--coin-denom` flag to testnet command that sets the given coin denomination to SDK and Ethermint parameters.
* (types) [Ambiplatforms-TORQUE#502](https://github.com/cosmos/ethermint/pull/502) `EthAccount` now also exposes the Ethereum hex address in `string` format to clients.
* (types) [Ambiplatforms-TORQUE#494](https://github.com/cosmos/ethermint/pull/494) Update `EthAccount` public key JSON type to `string`.
* (app) [Ambiplatforms-TORQUE#471](https://github.com/cosmos/ethermint/pull/471) Add `x/upgrade` module for managing software updates.
* (evm) [Ambiplatforms-TORQUE#458](https://github.com/cosmos/ethermint/pull/458) Define parameter for token denomination used for the EVM module.
* (evm) [Ambiplatforms-TORQUE#443](https://github.com/cosmos/ethermint/issues/443) Support custom Ethereum `ChainConfig` params.
* (types) [Ambiplatforms-TORQUE#434](https://github.com/cosmos/ethermint/issues/434) Update default denomination to Atto Photon (`aphoton`).
* (types) [Ambiplatforms-TORQUE#515](https://github.com/cosmos/ethermint/pull/515) Update minimum gas price to be 1.

### Bug Fixes

* (ante) [Ambiplatforms-TORQUE#525](https://github.com/cosmos/ethermint/pull/525) Add message validation decorator to `AnteHandler` for `MsgEthereumTx`.
* (types) [Ambiplatforms-TORQUE#507](https://github.com/cosmos/ethermint/pull/507) Fix hardcoded `aphoton` on `EthAccount` balance getter and setter.
* (types) [Ambiplatforms-TORQUE#501](https://github.com/cosmos/ethermint/pull/501) Fix bech32 encoding error by using the compressed ethereum secp256k1 public key.
* (evm) [Ambiplatforms-TORQUE#496](https://github.com/cosmos/ethermint/pull/496) Fix bugs on `journal.revert` and `CommitStateDB.Copy`.
* (types) [Ambiplatforms-TORQUE#480](https://github.com/cosmos/ethermint/pull/480) Update [BIP44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki) coin type to `60` to satisfy [EIP84](https://github.com/ethereum/EIPs/issues/84).
* (types) [Ambiplatforms-TORQUE#513](https://github.com/cosmos/ethermint/pull/513) Fix simulated transaction bug that was causing a consensus error by unintentionally affecting the state.

## [v0.1.0] - 2020-08-23

### Improvements

* (sdk) [Ambiplatforms-TORQUE#386](https://github.com/cosmos/ethermint/pull/386) Bump Cosmos SDK version to [v0.39.1](https://github.com/cosmos/cosmos-sdk/releases/tag/v0.39.1)
* (evm) [Ambiplatforms-TORQUE#181](https://github.com/cosmos/ethermint/issues/181) Updated EVM module to the recommended module structure.
* (app) [Ambiplatforms-TORQUE#188](https://github.com/cosmos/ethermint/issues/186)  Misc cleanup:
  * (evm) Rename `EthereumTxMsg` --> `MsgEthereumTx` and `EmintMsg` --> `MsgEthermint` for consistency with SDK standards
  * Updated integration and unit tests to use `EthermintApp` as testing suite
  * Use expected `Keeper` interface for `AccountKeeper`
  * Replaced `count` type in keeper with `int`
  * Add SDK events for transactions
* [Ambiplatforms-TORQUE#236](https://github.com/cosmos/ethermint/pull/236) Changes from upgrade:
  * (`app/ante`) Moved `AnteHandler` implementation to `app/ante`
  * (keys) Marked `ExportEthKeyCommand` as **UNSAFE**
  * (evm) Moved `BeginBlock` and `EndBlock` to `x/evm/abci.go`
* (evm) [Ambiplatforms-TORQUE#255](https://github.com/cosmos/ethermint/pull/255) Add missing `GenesisState` fields and support `ExportGenesis` functionality.
* [Ambiplatforms-TORQUE#272](https://github.com/cosmos/ethermint/pull/272) Add `Logger` for evm module.
* [Ambiplatforms-TORQUE#317](https://github.com/cosmos/ethermint/pull/317) `GenesisAccount` validation.
* (evm) [Ambiplatforms-TORQUE#319](https://github.com/cosmos/ethermint/pull/319) Various evm improvements:
  * Add transaction `[]*ethtypes.Logs` to evm's `GenesisState` to persist logs after an upgrade.
  * Remove evm `CodeKey` and `BlockKey`in favor of a prefix `Store`.
  * Set `BlockBloom` during `EndBlock` instead of `BeginBlock`.
  * `Commit` state object and `Finalize` storage after `InitGenesis` setup.
* (rpc) [Ambiplatforms-TORQUE#325](https://github.com/cosmos/ethermint/pull/325) `eth_coinbase` JSON-RPC query now returns the node's validator address.

### Features

* (build) [Ambiplatforms-TORQUE#378](https://github.com/cosmos/ethermint/pull/378) Create multi-node, local, automated testnet setup with `make localnet-start`.
* (rpc) [Ambiplatforms-TORQUE#330](https://github.com/cosmos/ethermint/issues/330) Implement `PublicFilterAPI`'s `EventSystem` which subscribes to Tendermint events upon `Filter` creation.
* (rpc) [Ambiplatforms-TORQUE#231](https://github.com/cosmos/ethermint/issues/231) Implement `NewBlockFilter` in rpc/filters.go which instantiates a polling block filter
  * Polls for new blocks via `BlockNumber` rpc call; if block number changes, it requests the new block via `GetBlockByNumber` rpc call and adds it to its internal list of blocks
  * Update `uninstallFilter` and `getFilterChanges` accordingly
  * `uninstallFilter` stops the polling goroutine
  * `getFilterChanges` returns the filter's internal list of block hashes and resets it
* (rpc) [Ambiplatforms-TORQUE#54](https://github.com/cosmos/ethermint/issues/54), [Ambiplatforms-TORQUE#55](https://github.com/cosmos/ethermint/issues/55)
  Implement `eth_getFilterLogs` and `eth_getLogs`:
  * For a given filter, look through each block for transactions. If there are transactions in the block, get the logs from it, and filter using the filterLogs method
  * `eth_getLogs` and `eth_getFilterChanges` for log filters use the same underlying method as `eth_getFilterLogs`
  * update `HandleMsgEthereumTx` to store logs using the ethereum hash
* (app) [Ambiplatforms-TORQUE#187](https://github.com/cosmos/ethermint/issues/187) Add support for simulations.

### Bug Fixes

* (evm) [Ambiplatforms-TORQUE#767](https://github.com/cosmos/ethermint/issues/767) Fix error of timeout when using Truffle to deploy contract.
* (evm) [Ambiplatforms-TORQUE#751](https://github.com/cosmos/ethermint/issues/751) Fix misused method to calculate block hash in evm related function.
* (evm) [Ambiplatforms-TORQUE#721](https://github.com/cosmos/ethermint/issues/721) Fix mismatch block hash in rpc response when use eth.getBlock.
* (evm) [Ambiplatforms-TORQUE#730](https://github.com/cosmos/ethermint/issues/730) Fix 'EIP2028' not open when Istanbul version has been enabled.
* (app) [Ambiplatforms-TORQUE#749](https://github.com/cosmos/ethermint/issues/749) Fix panic in `AnteHandler` when gas price larger than 100000
* (rpc) [Ambiplatforms-TORQUE#305](https://github.com/cosmos/ethermint/issues/305) Update `eth_getTransactionCount` to check for account existence before getting sequence and return 0 as the nonce if it doesn't exist.
* (evm) [Ambiplatforms-TORQUE#319](https://github.com/cosmos/ethermint/pull/319) Fix `SetBlockHash` that was setting the incorrect height during `BeginBlock`.
* (evm) [Ambiplatforms-TORQUE#176](https://github.com/cosmos/ethermint/issues/176) Updated Web3 transaction hash from using RLP hash. Now all transaction hashes exposed are amino hashes:
  * Removes `Hash()` (RLP) function from `MsgEthereumTx` to avoid confusion or misuse in future.
