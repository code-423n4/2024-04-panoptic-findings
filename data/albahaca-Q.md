# Quality Assurance Report for Panoptic Contest


Total Low Risk Issues : 22
Total Non-critical Issues : 68

# Summary

# Low Risk Issues

| |Issue|Instances|
|-|:-|:-:|
| [[L001](#l001---abiencodepacked-should-not-be-used-with-dynamic-types-when-passing-the-result-to-a-hash-function-such-as-keccak256)] | `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()` | 7 |
| [[L002](#l002---large-approvals-may-not-work-with-some-tokens)] | Large approvals may not work with some tokens | 4 |
| [[L003](#l003---array-lengths-not-checked)] | Array lengths not checked | 7 |
| [[L004](#l004---nft-minting-can-allow-json-injection)] | NFT minting can allow JSON Injection | 2 |
| [[L005](#l005---large-transfers-may-not-work-with-some-erc20-tokens)] | Large transfers may not work with some ERC20 tokens | 1 |
| [[L006](#l006---unsafe-downcast)] | Unsafe downcast | 60 |
| [[L007](#l007---approve-typeuint256max-may-not-work-with-some-tokens)] | Approve `type(uint256).max` may not work with some tokens | 4 |
| [[L008](#l008---return-values-of-approve-not-checked)] | Return values of `approve()` not checked | 4 |
| [[L009](#l009---no-limits-when-setting-state-variable-amounts)] | No limits when setting state variable amounts | 27 |
| [[L010](#l010---double-type-casts-create-complexity-within-the-code)] | Double type casts create complexity within the code | 55 |
| [[L011](#l011---constructor-contains-no-validation)] | Constructor contains no validation | 4 |
| [[L012](#l012---for-loops-in-public-or-external-functions-should-be-avoided-due-to-high-gas-costs-and-possible-dos)] | For loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS | 4 |
| [[L013](#l013---function-calls-within-for-loops)] | Function calls within for loops | 12 |
| [[L014](#l014----subtraction-may-underflow-if-multiplication-is-too-large)] |  Subtraction may underflow if multiplication is too large | 10 |
| [[L015](#l015---contracts-are-not-using-their-oz-upgradeable-counterparts)] | Contracts are not using their OZ Upgradeable counterparts | 5 |
| [[L016](#l016---multiplication-on-the-result-of-a-division)] | Multiplication on the result of a division | 3 |
| [[L017](#l017---unbounded-state-array-which-is-iterated-upon)] | Unbounded state array which is iterated upon | 38 |
| [[L018](#l018---prefer-continue-over-revert-model-in-iteration)] | Prefer continue over revert model in iteration | 4 |
| [[L019](#l019---missing-checks-for-address0x0-in-the-constructor)] | Missing checks for address(0x0) in the constructor | 3 |
| [[L020](#l020---missing-checks-for-address0x0-in-the-initializer)] | Missing checks for address(0x0) in the initializer | 1 |
| [[L021](#l021---code-does-not-follow-the-best-practice-of-check-effects-interaction)] | Code does not follow the best practice of check-effects-interaction | 2 |
| [[L022](#l022---the-additionsmultiplications-may-silently-overflow-because-theyre-in-unchecked-blocks-with-no-preceding-value-checks-which-may-lead-to-unexpected-results)] | The additions/multiplications may silently overflow because they're in unchecked blocks with no preceding value checks, which may lead to unexpected results. | 237 |



## L001 - `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()`:

Use `abi.encode()` instead which will pad items to 32 bytes, which will [prevent hash collisions](https://docs.soliditylang.org/en/v0.8.13/abi-spec.html#non-standard-packed-mode) (e.g. `abi.encodePacked(0x123,0x456)` => `0x123456` => `abi.encodePacked(0x1,0x23456)`, but `abi.encode(0x123,0x456)` => `0x0...1230...456`). Unless there is a compelling reason, `abi.encode` should be preferred. If there is only one argument to `abi.encodePacked()` it can often be cast to `bytes()` or `bytes32()` [instead](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739). If all arguments are strings and or bytes, `bytes.concat()` should be used instead.


<details>
<summary>Click to show 2 findings</summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol
keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))

keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))
```
https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1544:1544

</details>

## L002 - Large approvals may not work with some tokens:

Not all IERC20 implementations are totally compliant, and some (e.g UNI, COMP) may fail if the valued passed is larger than uint96. [Source](https://github.com/d-xo/weird-erc20#revert-on-large-approvals--transfers)


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/libraries/InteractionHelper.sol


32              IERC20Partial(token0).approve(address(sfpm), type(uint256).max);


33              IERC20Partial(token1).approve(address(sfpm), type(uint256).max);


36              IERC20Partial(token0).approve(address(ct0), type(uint256).max);


37              IERC20Partial(token1).approve(address(ct1), type(uint256).max);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L37:37

</details>

## L003 - Array lengths not checked:

If the length of the arrays are not required to be of the same length, user operations may not be fully executed due to a mismatch in the number of items iterated over, versus the number of items provided in the second array.


<details>
<summary>Click to show 7 findings</summary>

```solidity
File: contracts/PanopticPool.sol


586         function burnOptions(
587             TokenId[] calldata positionIdList,
588             TokenId[] calldata newPositionIdList,
589             int24 tickLimitLow,
590             int24 tickLimitHigh
591         ) external {
592             _burnAllOptionsFrom(
593                 msg.sender,
594                 tickLimitLow,
595                 tickLimitHigh,
596                 COMMIT_LONG_SETTLED,
597                 positionIdList
598             );
599     
600             _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);
601         }


1017        function liquidate(
1018            TokenId[] calldata positionIdListLiquidator,
1019            address liquidatee,
1020            LeftRightUnsigned delegations,
1021            TokenId[] calldata positionIdList
1022        ) external {
1023            _validatePositionList(liquidatee, positionIdList, 0);
1024    
1025            // Assert the account we are liquidating is actually insolvent
1026            int24 twapTick = getUniV3TWAP();
1027    
1028            LeftRightUnsigned tokenData0;
1029            LeftRightUnsigned tokenData1;
1030            LeftRightSigned premia;
1031            {
1032                (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
1033    
1034                // Enforce maximum delta between TWAP and currentTick to prevent extreme price manipulation
1035                if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)
1036                    revert Errors.StaleTWAP();
1037    
1038                uint256[2][] memory positionBalanceArray = new uint256[2][](positionIdList.length);
1039                (premia, positionBalanceArray) = _calculateAccumulatedPremia(
1040                    liquidatee,
1041                    positionIdList,
1042                    COMPUTE_ALL_PREMIA,
1043                    ONLY_AVAILABLE_PREMIUM,
1044                    currentTick
1045                );
1046                tokenData0 = s_collateralToken0.getAccountMarginDetails(
1047                    liquidatee,
1048                    twapTick,
1049                    positionBalanceArray,
1050                    premia.rightSlot()
1051                );
1052    
1053                tokenData1 = s_collateralToken1.getAccountMarginDetails(
1054                    liquidatee,
1055                    twapTick,
1056                    positionBalanceArray,
1057                    premia.leftSlot()
1058                );
1059    
1060                (uint256 balanceCross, uint256 thresholdCross) = _getSolvencyBalances(
1061                    tokenData0,
1062                    tokenData1,
1063                    Math.getSqrtRatioAtTick(twapTick)
1064                );
1065    
1066                if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();
1067            }
1068    
1069            // Perform the specified delegation from `msg.sender` to `liquidatee`
1070            // Works like a transfer, so the liquidator must possess all the tokens they are delegating, resulting in no net supply change
1071            // If not enough tokens are delegated for the positions of `liquidatee` to be closed, the liquidation will fail
1072            s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());
1073            s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());
1074    
1075            int256 liquidationBonus0;
1076            int256 liquidationBonus1;
1077            int24 finalTick;
1078            {
1079                LeftRightSigned netExchanged;
1080                LeftRightSigned[4][] memory premiasByLeg;
1081                // burn all options from the liquidatee
1082    
1083                // Do not commit any settled long premium to storage - we will do this after we determine if any long premium must be revoked
1084                // This is to prevent any short positions the liquidatee has being settled with tokens that will later be revoked
1085                // Note: tick limits are not applied here since it is not the liquidator's position being liquidated
1086                (netExchanged, premiasByLeg) = _burnAllOptionsFrom(
1087                    liquidatee,
1088                    Constants.MIN_V3POOL_TICK,
1089                    Constants.MAX_V3POOL_TICK,
1090                    DONOT_COMMIT_LONG_SETTLED,
1091                    positionIdList
1092                );
1093    
1094                (, finalTick, , , , , ) = s_univ3pool.slot0();
1095    
1096                LeftRightSigned collateralRemaining;
1097                // compute bonus amounts using latest tick data
1098                (liquidationBonus0, liquidationBonus1, collateralRemaining) = PanopticMath
1099                    .getLiquidationBonus(
1100                        tokenData0,
1101                        tokenData1,
1102                        Math.getSqrtRatioAtTick(twapTick),
1103                        Math.getSqrtRatioAtTick(finalTick),
1104                        netExchanged,
1105                        premia
1106                    );
1107    
1108                // premia cannot be paid if there is protocol loss associated with the liquidatee
1109                // otherwise, an economic exploit could occur if the liquidator and liquidatee collude to
1110                // manipulate the fees in a liquidity area they control past the protocol loss threshold
1111                // such that the PLPs are forced to pay out premia to the liquidator
1112                // thus, we haircut any premium paid by the liquidatee (converting tokens as necessary) until the protocol loss is covered or the premium is exhausted
1113                // note that the haircutPremia function also commits the settled amounts (adjusted for the haircut) to storage, so it will be called even if there is no haircut
1114    
1115                // if premium is haircut from a token that is not in protocol loss, some of the liquidation bonus will be converted into that token
1116                // reusing variables to save stack space; netExchanged = deltaBonus0, premia = deltaBonus1
1117                address _liquidatee = liquidatee;
1118                TokenId[] memory _positionIdList = positionIdList;
1119                int24 _finalTick = finalTick;
1120                int256 deltaBonus0;
1121                int256 deltaBonus1;
1122                (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(
1123                    _liquidatee,
1124                    _positionIdList,
1125                    premiasByLeg,
1126                    collateralRemaining,
1127                    s_collateralToken0,
1128                    s_collateralToken1,
1129                    Math.getSqrtRatioAtTick(_finalTick),
1130                    s_settledTokens
1131                );
1132    
1133                unchecked {
1134                    liquidationBonus0 += deltaBonus0;
1135                    liquidationBonus1 += deltaBonus1;
1136                }
1137            }
1138    
1139            LeftRightUnsigned _delegations = delegations;
1140            // revoke the delegated amount plus the bonus amount.
1141            s_collateralToken0.revoke(
1142                msg.sender,
1143                liquidatee,
1144                uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)
1145            );
1146            s_collateralToken1.revoke(
1147                msg.sender,
1148                liquidatee,
1149                uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)
1150            );
1151    
1152            // check that the provided positionIdList matches the positions in memory
1153            _validatePositionList(msg.sender, positionIdListLiquidator, 0);
1154    
1155            if (
1156                !_checkSolvencyAtTick(
1157                    msg.sender,
1158                    positionIdListLiquidator,
1159                    finalTick,
1160                    finalTick,
1161                    BP_DECREASE_BUFFER
1162                )
1163            ) revert Errors.NotEnoughCollateral();
1164    
1165            LeftRightSigned bonusAmounts = LeftRightSigned
1166                .wrap(0)
1167                .toRightSlot(int128(liquidationBonus0))
1168                .toLeftSlot(int128(liquidationBonus1));
1169    
1170            emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);
1171        }


1179        function forceExercise(
1180            address account,
1181            TokenId[] calldata touchedId,
1182            TokenId[] calldata positionIdListExercisee,
1183            TokenId[] calldata positionIdListExercisor
1184        ) external {
1185            // revert if multiple positions are specified
1186            // the reason why the singular touchedId is an array is so it composes well with the rest of the system
1187            // '_calculateAccumulatedPremia' expects a list of positions to be touched, and this is the only way to pass a single position
1188            if (touchedId.length != 1) revert Errors.InputListFail();
1189    
1190            // validate the exercisor's position list (the exercisee's list will be evaluated after their position is force exercised)
1191            _validatePositionList(msg.sender, positionIdListExercisor, 0);
1192    
1193            uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();
1194    
1195            // compute the notional value of the short legs (the maximum amount of tokens required to exercise - premia)
1196            // and the long legs (from which the exercise cost is computed)
1197            (LeftRightSigned longAmounts, LeftRightSigned delegatedAmounts) = PanopticMath
1198                .computeExercisedAmounts(touchedId[0], positionBalance);
1199    
1200            int24 twapTick = getUniV3TWAP();
1201    
1202            (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
1203    
1204            {
1205                // add the premia to the delegated amounts to ensure the user has enough collateral to exercise
1206                (LeftRightSigned positionPremia, ) = _calculateAccumulatedPremia(
1207                    account,
1208                    touchedId,
1209                    COMPUTE_LONG_PREMIA,
1210                    ONLY_AVAILABLE_PREMIUM,
1211                    currentTick
1212                );
1213    
1214                // long premia is represented as negative so subtract it to increase it for the delegated amounts
1215                delegatedAmounts = delegatedAmounts.sub(positionPremia);
1216            }
1217    
1218            // on forced exercise, the price *must* be outside the position's range for at least 1 leg
1219            touchedId[0].validateIsExercisable(twapTick);
1220    
1221            // The protocol delegates some virtual shares to ensure the burn can be settled.
1222            s_collateralToken0.delegate(account, uint128(delegatedAmounts.rightSlot()));
1223            s_collateralToken1.delegate(account, uint128(delegatedAmounts.leftSlot()));
1224    
1225            // Exercise the option
1226            // Note: tick limits are not applied here since it is not the exercisor's position being closed
1227            _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);
1228    
1229            // Compute the exerciseFee, this will decrease the further away the price is from the forcedExercised position
1230            /// @dev use the medianTick to prevent price manipulations based on swaps.
1231            LeftRightSigned exerciseFees = s_collateralToken0.exerciseCost(
1232                currentTick,
1233                twapTick,
1234                touchedId[0],
1235                positionBalance,
1236                longAmounts
1237            );
1238    
1239            LeftRightSigned refundAmounts = delegatedAmounts.add(exerciseFees);
1240    
1241            // redistribute token composition of refund amounts if user doesn't have enough of one token to pay
1242            refundAmounts = PanopticMath.getRefundAmounts(
1243                account,
1244                refundAmounts,
1245                twapTick,
1246                s_collateralToken0,
1247                s_collateralToken1
1248            );
1249    
1250            unchecked {
1251                // settle difference between delegated amounts (from the protocol) and exercise fees/substituted tokens
1252                s_collateralToken0.refund(
1253                    account,
1254                    msg.sender,
1255                    refundAmounts.rightSlot() - delegatedAmounts.rightSlot()
1256                );
1257                s_collateralToken1.refund(
1258                    account,
1259                    msg.sender,
1260                    refundAmounts.leftSlot() - delegatedAmounts.leftSlot()
1261                );
1262            }
1263    
1264            // refund the protocol any virtual shares after settling the difference with the exercisor
1265            s_collateralToken0.refund(account, uint128(delegatedAmounts.rightSlot()));
1266            s_collateralToken1.refund(account, uint128(delegatedAmounts.leftSlot()));
1267    
1268            _validateSolvency(account, positionIdListExercisee, NO_BUFFER);
1269    
1270            // the exercisor's position list is validated above
1271            // we need to assert their solvency against their collateral requirement plus a buffer
1272            // force exercises involve a collateral decrease with open positions, so there is a higher standard for solvency
1273            // a similar buffer is also invoked when minting options, which also decreases the available collateral
1274            if (positionIdListExercisor.length > 0)
1275                _validateSolvency(msg.sender, positionIdListExercisor, BP_DECREASE_BUFFER);
1276    
1277            emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);
1278        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1179:1278

```solidity
File: contracts/SemiFungiblePositionManager.sol


566         function safeBatchTransferFrom(
567             address from,
568             address to,
569             uint256[] calldata ids,
570             uint256[] calldata amounts,
571             bytes calldata data
572         ) public override {
573             // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
574             // so just check if there is an active reentrancy lock for the relevant pool on each token
575             for (uint256 i = 0; i < ids.length; ) {
576                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
577                 registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
578                 unchecked {
579                     ++i;
580                 }
581             }
582     
583             // transfer the token (note that all state updates are completed before reentrancy is possible)
584             super.safeBatchTransferFrom(from, to, ids, amounts, data);
585         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566:585

```solidity
File: contracts/libraries/PanopticMath.sol


768         function haircutPremia(
769             address liquidatee,
770             TokenId[] memory positionIdList,
771             LeftRightSigned[4][] memory premiasByLeg,
772             LeftRightSigned collateralRemaining,
773             CollateralTracker collateral0,
774             CollateralTracker collateral1,
775             uint160 sqrtPriceX96Final,
776             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777         ) external returns (int256, int256) {
778             unchecked {
779                 // get the amount of premium paid by the liquidatee
780                 LeftRightSigned longPremium;
781                 for (uint256 i = 0; i < positionIdList.length; ++i) {
782                     TokenId tokenId = positionIdList[i];
783                     uint256 numLegs = tokenId.countLegs();
784                     for (uint256 leg = 0; leg < numLegs; ++leg) {
785                         if (tokenId.isLong(leg) == 1) {
786                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
787                         }
788                     }
789                 }
790                 // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token
791                 int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);
792                 int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);
793                 int256 haircut0;
794                 int256 haircut1;
795                 // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,
796                 // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token
797                 if (
798                     longPremium.rightSlot() < collateralDelta0 &&
799                     longPremium.leftSlot() > collateralDelta1
800                 ) {
801                     int256 protocolLoss1 = collateralDelta1;
802                     (collateralDelta0, collateralDelta1) = (
803                         -Math.min(
804                             collateralDelta0 - longPremium.rightSlot(),
805                             PanopticMath.convert1to0(
806                                 longPremium.leftSlot() - collateralDelta1,
807                                 sqrtPriceX96Final
808                             )
809                         ),
810                         Math.min(
811                             longPremium.leftSlot() - collateralDelta1,
812                             PanopticMath.convert0to1(
813                                 collateralDelta0 - longPremium.rightSlot(),
814                                 sqrtPriceX96Final
815                             )
816                         )
817                     );
818     
819                     haircut0 = longPremium.rightSlot();
820                     haircut1 = protocolLoss1 + collateralDelta1;
821                 } else if (
822                     longPremium.leftSlot() < collateralDelta1 &&
823                     longPremium.rightSlot() > collateralDelta0
824                 ) {
825                     int256 protocolLoss0 = collateralDelta0;
826                     (collateralDelta0, collateralDelta1) = (
827                         Math.min(
828                             longPremium.rightSlot() - collateralDelta0,
829                             PanopticMath.convert1to0(
830                                 collateralDelta1 - longPremium.leftSlot(),
831                                 sqrtPriceX96Final
832                             )
833                         ),
834                         -Math.min(
835                             collateralDelta1 - longPremium.leftSlot(),
836                             PanopticMath.convert0to1(
837                                 longPremium.rightSlot() - collateralDelta0,
838                                 sqrtPriceX96Final
839                             )
840                         )
841                     );
842     
843                     haircut0 = collateralDelta0 + protocolLoss0;
844                     haircut1 = longPremium.leftSlot();
845                 } else {
846                     // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
847                     haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
848                     haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
849     
850                     collateralDelta0 = 0;
851                     collateralDelta1 = 0;
852                 }
853     
854                 {
855                     address _liquidatee = liquidatee;
856                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
857                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
858                 }
859     
860                 for (uint256 i = 0; i < positionIdList.length; i++) {
861                     TokenId tokenId = positionIdList[i];
862                     LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
863                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864                         if (tokenId.isLong(leg) == 1) {
865                             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
866                                 storage _settledTokens = settledTokens;
867     
868                             // calculate amounts to revoke from settled and subtract from haircut req
869                             uint256 settled0 = Math.unsafeDivRoundingUp(
870                                 uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871                                 uint128(longPremium.rightSlot())
872                             );
873                             uint256 settled1 = Math.unsafeDivRoundingUp(
874                                 uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875                                 uint128(longPremium.leftSlot())
876                             );
877     
878                             bytes32 chunkKey = keccak256(
879                                 abi.encodePacked(
880                                     tokenId.strike(0),
881                                     tokenId.width(0),
882                                     tokenId.tokenType(0)
883                                 )
884                             );
885     
886                             // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
887                             // for the haircut directly to the accumulator
888                             settled0 = Math.max(
889                                 0,
890                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891                             );
892                             settled1 = Math.max(
893                                 0,
894                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895                             );
896     
897                             _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
898                                 LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
899                                     uint128(settled1)
900                                 )
901                             );
902                         }
903                     }
904                 }
905     
906                 return (collateralDelta0, collateralDelta1);
907             }
908         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768:908

```solidity
File: contracts/tokens/ERC1155Minimal.sol


130         function safeBatchTransferFrom(
131             address from,
132             address to,
133             uint256[] calldata ids,
134             uint256[] calldata amounts,
135             bytes calldata data
136         ) public virtual {
137             if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
138     
139             // Storing these outside the loop saves ~15 gas per iteration.
140             uint256 id;
141             uint256 amount;
142     
143             for (uint256 i = 0; i < ids.length; ) {
144                 id = ids[i];
145                 amount = amounts[i];
146     
147                 balanceOf[from][id] -= amount;
148     
149                 // balance will never overflow
150                 unchecked {
151                     balanceOf[to][id] += amount;
152                 }
153     
154                 // An array can't have a total length
155                 // larger than the max uint256 value.
156                 unchecked {
157                     ++i;
158                 }
159             }
160     
161             emit TransferBatch(msg.sender, from, to, ids, amounts);
162     
163             if (to.code.length != 0) {
164                 if (
165                     ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
166                     ERC1155Holder.onERC1155BatchReceived.selector
167                 ) {
168                     revert UnsafeRecipient();
169                 }
170             }
171         }


178         function balanceOfBatch(
179             address[] calldata owners,
180             uint256[] calldata ids
181         ) public view returns (uint256[] memory balances) {
182             balances = new uint256[](owners.length);
183     
184             // Unchecked because the only math done is incrementing
185             // the array index counter which cannot possibly overflow.
186             unchecked {
187                 for (uint256 i = 0; i < owners.length; ++i) {
188                     balances[i] = balanceOf[owners[i]][ids[i]];
189                 }
190             }
191         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L178:191

</details>


## L004 - NFT minting can allow JSON Injection:

Reason: JSON injection in NFT metadata can create various vulnerabilities and manipulation tactics in the NFT ecosystem. The metadata of NFTs, often stored off-chain and referenced by URI, could be manipulated through JSON injection if unsanitized inputs are allowed. This could alter the visual representation of an NFT on platforms and mislead buyers or impact the perceived value of the asset.

Resolution: To protect against JSON injection, the metadata processing system should properly sanitize and validate all inputs. Smart contracts should not handle this task due to their limitations. Instead, robust off-chain server code should manage the processing, using tools designed to prevent JSON injection such as input validation, escaping special characters, and utilizing secure JSON parsing libraries. In addition, implementing strict access control to the metadata storage can further safeguard against unauthorized changes.


```solidity
File: contracts/PanopticPool.sol


27      contract PanopticPool is ERC1155Holder, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L27:27

```solidity
File: contracts/SemiFungiblePositionManager.sol


72      contract SemiFungiblePositionManager is ERC1155, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L72:72

## L005 - Large transfers may not work with some ERC20 tokens:

Some  IERC20 implementations (e.g UNI, COMP) may fail if the valued transferred is larger than uint96. [Source](https://github.com/d-xo/weird-erc20#revert-on-large-approvals--transfers)


```solidity
File: contracts/CollateralTracker.sol


333             return ERC20Minimal.transfer(recipient, amount);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L333:333



## L006 - Unsafe downcast:

When a type is downcast to a smaller type, the higher order bits are truncated, effectively applying a modulo to the original value. Without any other checks, this wrapping will lead to unexpected behavior and bugs.


<details>
<summary>Click to show 60 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


1585                        ? int64(uint64(poolUtilization))


1632                uint64 poolUtilization1 = uint64(poolUtilization >> 64);


1637                    uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +


1029                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));


262                 s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);


1586                        : int64(uint64(poolUtilization >> 64))


731                     .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))


1638                    (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);


1028                s_poolAssets = uint128(uint256(updatedAssets));


732                     .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));


1631                uint64 poolUtilization0 = uint64(poolUtilization);


1085                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));


436                 s_poolAssets += uint128(assets);


1330                : int64(uint64(poolUtilization >> 64));


552                 s_poolAssets -= uint128(assets);


1329                ? int64(uint64(poolUtilization))


1084                s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1084:1084

```solidity
File: contracts/PanopticFactory.sol


356                     fullRangeLiquidity = uint128(
357                         Math.mulDivRoundingUp(
358                             FULL_RANGE_LIQUIDITY_AMOUNT_WETH,
359                             Constants.FP96,
360                             currentSqrtPriceX96
361                         )
362                     );


365                     uint128 liquidity0 = uint128(
366                         Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN, currentSqrtPriceX96)
367                     );


352                     fullRangeLiquidity = uint128(
353                         Math.mulDiv96RoundingUp(FULL_RANGE_LIQUIDITY_AMOUNT_WETH, currentSqrtPriceX96)
354                     );


368                     uint128 liquidity1 = uint128(
369                         Math.mulDivRoundingUp(
370                             FULL_RANGE_LIQUIDITY_AMOUNT_TOKEN,
371                             Constants.FP96,
372                             currentSqrtPriceX96
373                         )
374                     );


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L368:374

```solidity
File: contracts/PanopticPool.sol


730                 return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));


309                     (uint256(block.timestamp) << 216) +


1635                    .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))


1636                    .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1636:1636

```solidity
File: contracts/SemiFungiblePositionManager.sol


1242                    -int128(int256(amount1))


1215                int128(int256(amount1))


1214            movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(


1169                        int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))


1241                movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(


1172                        int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))


1176                    .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))


1567            poolId = uint64(s_AddrToPoolIdData[univ3pool]);


607                     uint128(amount)


1177                    .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1177:1177

```solidity
File: contracts/libraries/Errors.sol


9           /// @dev e.g. uint128(uint256(a)) fails


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol#L9:9

```solidity
File: contracts/libraries/FeesCalc.sol


118                     .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));


117                     .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L117:117

```solidity
File: contracts/libraries/Math.sol


297             if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();


303             if ((downcastedInt = uint128(toDowncast)) != toDowncast) {


319             if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L319:319

```solidity
File: contracts/libraries/PanopticMath.sol


178                     (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +


257                     twapMeasurement[i] = int24(
258                         (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
259                     );


155                 return int24(Math.sort(ticks)[cardinality / 2]);


62                  return (poolId & TICKSPACING_MASK) + (uint48(poolId) + 1);


585                 amount0 = positionSize * uint128(tokenId.optionRatio(legIndex));


377                 int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))


200                     uint24 orderMap = uint24(medianData >> 192);


179                         int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /


183                 if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {


103                     (uint248(uint256(keccak256(abi.encode(tokenId)))));


217                         entry = int24(uint24(medianData >> (rank * 24)));


591                 amount1 = positionSize * uint128(tokenId.optionRatio(legIndex));


50                  uint64 poolId = uint64(uint160(univ3pool) >> 112);


102                 uint248 updatedHash = uint248(existingHash) ^


229                         uint256(uint192(medianData << 24)) +


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L229:229

```solidity
File: contracts/types/LiquidityChunk.sol


182                 return int24(int256(LiquidityChunk.unwrap(self) >> 208));


173                 return int24(int256(LiquidityChunk.unwrap(self) >> 232));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L173:173

```solidity
File: contracts/types/TokenId.sol


160                 return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));


171                 return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L171:171

</details>

## L007 - Approve `type(uint256).max` may not work with some tokens:

Source: https://github.com/d-xo/weird-erc20#revert-on-large-approvals--transfers


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/libraries/InteractionHelper.sol


37              IERC20Partial(token1).approve(address(ct1), type(uint256).max);


32              IERC20Partial(token0).approve(address(sfpm), type(uint256).max);


36              IERC20Partial(token0).approve(address(ct0), type(uint256).max);


33              IERC20Partial(token1).approve(address(sfpm), type(uint256).max);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L33:33

</details>


## L008 - Return values of `approve()` not checked:

Not all IERC20 implementations `revert()` when there's a failure in `approve()`. The function signature has a boolean return value and they indicate errors that way instead. By not checking the return value, operations that should have marked as failed, may potentially go through without actually approving anything


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/libraries/InteractionHelper.sol


32              IERC20Partial(token0).approve(address(sfpm), type(uint256).max);


33              IERC20Partial(token1).approve(address(sfpm), type(uint256).max);


36              IERC20Partial(token0).approve(address(ct0), type(uint256).max);


37              IERC20Partial(token1).approve(address(ct1), type(uint256).max);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L37:37

</details>



## L009 - No limits when setting state variable amounts:

It is important to ensure state variables numbers are set to a reasonable value.


<details>
<summary>Click to show 27 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


187             COMMISSION_FEE = _commissionFee;


188             SELLER_COLLATERAL_RATIO = _sellerCollateralRatio;


189             BUYER_COLLATERAL_RATIO = _buyerCollateralRatio;


190             FORCE_EXERCISE_COST = _forceExerciseCost;


191             TARGET_POOL_UTIL = _targetPoolUtilization;


192             SATURATED_POOL_UTIL = _saturatedPoolUtilization;


193             ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;


201                 TICK_DEVIATION = uint256(


251             s_poolFee = _poolFee;


262                 s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);


282             poolAssets = s_poolAssets;


283             insideAMM = s_inAMM;


1028                s_poolAssets = uint128(uint256(updatedAssets));


1029                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));


1084                s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));


1085                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1085:1085

```solidity
File: contracts/PanopticPool.sol


366             poolUtilization0 = uint64(balanceData.leftSlot());


370             poolUtilization1 = uint64(balanceData.leftSlot() >> 64);


533             if (medianData != 0) s_miniMedian = medianData;


664             if (medianData != 0) s_miniMedian = medianData;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L664:664

```solidity
File: contracts/SemiFungiblePositionManager.sol


1567            poolId = uint64(s_AddrToPoolIdData[univ3pool]);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1567:1567

```solidity
File: contracts/libraries/Math.sol


297             if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();


303             if ((downcastedInt = uint128(toDowncast)) != toDowncast) {


312             if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();


319             if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L319:319

```solidity
File: contracts/libraries/PanopticMath.sol


681                     bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));


683                     bonus1 = int256(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L683:683

</details>

## L010 - Double type casts create complexity within the code:

Double type casting should be avoided in Solidity contracts to prevent unintended consequences and ensure accurate data representation. Performing multiple type casts in succession can lead to unexpected truncation, rounding errors, or loss of precision, potentially compromising the contract's functionality and reliability. Furthermore, double type casting can make the code less readable and harder to maintain, increasing the likelihood of errors and misunderstandings during development and debugging. To ensure precise and consistent data handling, developers should use appropriate data types and avoid unnecessary or excessive type casting, promoting a more robust and dependable contract execution.


<details>
<summary>Click to show 55 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


int128(uint128(oracleValue0)) - int128(uint128(currentValue0))

int128(uint128(oracleValue1)) - int128(uint128(currentValue1))

int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

s_poolAssets = uint128(uint256(updatedAssets));

s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));

int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;

s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));

s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));

uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,

netBalance += uint256(uint128(premiumAllPositions));

? int64(uint64(poolUtilization))

: int64(uint64(poolUtilization >> 64));

? int64(uint64(poolUtilization))

: int64(uint64(poolUtilization >> 64))

uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +

(uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1638:1638

```solidity
File: contracts/PanopticFactory.sol


if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L220:220

```solidity
File: contracts/PanopticPool.sol


(uint256(uint24(currentTick)) << 24) + // add to slot 4

(uint256(uint24(currentTick))); // add to slot 3

uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)

uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1149:1149

```solidity
File: contracts/SemiFungiblePositionManager.sol


int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))

int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))

.toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))

.toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));

movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(

int128(int256(amount1))

movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(

-int128(int256(amount1))

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1242:1242

```solidity
File: contracts/libraries/Errors.sol


/// @dev e.g. uint128(uint256(a)) fails

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol#L9:9

```solidity
File: contracts/libraries/FeesCalc.sol


.toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))

.toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L118:118

```solidity
File: contracts/libraries/Math.sol


uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));

if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L131:131

```solidity
File: contracts/libraries/PanopticMath.sol


poolId += uint64(uint24(tickSpacing)) << 48;

(uint248(uint256(keccak256(abi.encode(tokenId)))));

(int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +

int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /

if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {

entry = int24(uint24(medianData >> (rank * 24)));

uint256(uint192(medianData << 24)) +

uint256(uint24(lastObservedTick));

(tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))

int256 balance0 = int256(uint256(tokenData0.rightSlot())) -

int256 balance1 = int256(uint256(tokenData1.rightSlot())) -

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L695:695

```solidity
File: contracts/types/LeftRight.sol


int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));

uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)

(int256(int128(LeftRightSigned.unwrap(self)) + right) & RIGHT_HALF_BIT_MASK)

int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();

int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L201:201

```solidity
File: contracts/types/LiquidityChunk.sol


(uint256(uint24(_tickLower)) << 232) +

(uint256(uint24(_tickUpper)) << 208) +

LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)

LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L126:126

```solidity
File: contracts/types/TokenId.sol


return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L195:195

</details>

## L011 - Constructor contains no validation:

In Solidity, when values are being assigned in constructors to unsigned or integer variables, it's crucial to ensure the provided values adhere to the protocol's specific operational boundaries as laid out in the project specifications and documentation. If the constructors lack appropriate validation checks, there's a risk of setting state variables with values that could cause unexpected and potentially detrimental behavior within the contract's operations, violating the intended logic of the protocol. This can compromise the contract's security and impact the maintainability and reliability of the system. In order to avoid such issues, it is recommended to incorporate rigorous validation checks in constructors. These checks should align with the project's defined rules and constraints, making use of Solidity's built-in require function to enforce these conditions. If the validation checks fail, the require function will cause the transaction to revert, ensuring the integrity and adherence to the protocol's expected behavior.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


178         constructor(
179             uint256 _commissionFee,
180             uint256 _sellerCollateralRatio,
181             uint256 _buyerCollateralRatio,
182             int256 _forceExerciseCost,
183             uint256 _targetPoolUtilization,
184             uint256 _saturatedPoolUtilization,
185             uint256 _ITMSpreadMultiplier
186         ) {
187             COMMISSION_FEE = _commissionFee;
188             SELLER_COLLATERAL_RATIO = _sellerCollateralRatio;
189             BUYER_COLLATERAL_RATIO = _buyerCollateralRatio;
190             FORCE_EXERCISE_COST = _forceExerciseCost;
191             TARGET_POOL_UTIL = _targetPoolUtilization;
192             SATURATED_POOL_UTIL = _saturatedPoolUtilization;
193             ITM_SPREAD_MULTIPLIER = _ITMSpreadMultiplier;
194     
195             // calculate amount of ticks required for upwards and downwards moves, used to check if current and mini-median tick
196             // are out of sync (then apply a 100% collateral requirement)
197             unchecked {
198                 // taylor expand log(1-sellCollateralRatio)/log(1.0001) around sellCollateralRatio=2000 up to 3rd order
199                 /// since we're dropping the higher order terms, which are all negative, this will underestimate the number of ticks for a 20% move
200                 int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);
201                 TICK_DEVIATION = uint256(
202                     2230 +
203                         (12500 * ratioTick) /
204                         10_000 +
205                         (7812 * ratioTick ** 2) /
206                         10_000 ** 2 +
207                         (6510 * ratioTick ** 3) /
208                         10_000 ** 3
209                 );
210             }
211         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L178:211

```solidity
File: contracts/PanopticFactory.sol


115         constructor(
116             address _WETH9,
117             SemiFungiblePositionManager _SFPM,
118             IUniswapV3Factory _univ3Factory,
119             IDonorNFT _donorNFT,
120             address _poolReference,
121             address _collateralReference
122         ) {
123             WETH = _WETH9;
124             SFPM = _SFPM;
125             DONOR_NFT = _donorNFT;
126             // We store the Uniswap Factory contract - later we can use this to verify uniswap pools
127             UNIV3_FACTORY = _univ3Factory;
128             POOL_REFERENCE = _poolReference;
129             COLLATERAL_REFERENCE = _collateralReference;
130         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L115:130

```solidity
File: contracts/PanopticPool.sol


280         constructor(SemiFungiblePositionManager _sfpm) {
281             SFPM = _sfpm;
282         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L280:282

```solidity
File: contracts/SemiFungiblePositionManager.sol


341         constructor(IUniswapV3Factory _factory) {
342             FACTORY = _factory;
343         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L341:343

</details>

## L012 - For loops in `public` or `external` functions should be avoided due to high gas costs and possible DOS:

In Solidity, for loops can potentially cause Denial of Service (DoS) attacks if not handled carefully. DoS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. Below are some scenarios where for loops can lead to DoS attacks: Nested for loops can become exceptionally gas expensive and should be used sparingly.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol


566         function safeBatchTransferFrom(
567             address from,
568             address to,
569             uint256[] calldata ids,
570             uint256[] calldata amounts,
571             bytes calldata data
572         ) public override {
573             // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
574             // so just check if there is an active reentrancy lock for the relevant pool on each token
575             for (uint256 i = 0; i < ids.length; ) {
576                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
577                 registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
578                 unchecked {
579                     ++i;
580                 }
581             }
582     
583             // transfer the token (note that all state updates are completed before reentrancy is possible)
584             super.safeBatchTransferFrom(from, to, ids, amounts, data);
585         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566:585

```solidity
File: contracts/libraries/PanopticMath.sol


768         function haircutPremia(
769             address liquidatee,
770             TokenId[] memory positionIdList,
771             LeftRightSigned[4][] memory premiasByLeg,
772             LeftRightSigned collateralRemaining,
773             CollateralTracker collateral0,
774             CollateralTracker collateral1,
775             uint160 sqrtPriceX96Final,
776             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777         ) external returns (int256, int256) {
778             unchecked {
779                 // get the amount of premium paid by the liquidatee
780                 LeftRightSigned longPremium;
781                 for (uint256 i = 0; i < positionIdList.length; ++i) {
782                     TokenId tokenId = positionIdList[i];
783                     uint256 numLegs = tokenId.countLegs();
784                     for (uint256 leg = 0; leg < numLegs; ++leg) {
785                         if (tokenId.isLong(leg) == 1) {
786                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
787                         }
788                     }
789                 }
790                 // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token
791                 int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);
792                 int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);
793                 int256 haircut0;
794                 int256 haircut1;
795                 // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,
796                 // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token
797                 if (
798                     longPremium.rightSlot() < collateralDelta0 &&
799                     longPremium.leftSlot() > collateralDelta1
800                 ) {
801                     int256 protocolLoss1 = collateralDelta1;
802                     (collateralDelta0, collateralDelta1) = (
803                         -Math.min(
804                             collateralDelta0 - longPremium.rightSlot(),
805                             PanopticMath.convert1to0(
806                                 longPremium.leftSlot() - collateralDelta1,
807                                 sqrtPriceX96Final
808                             )
809                         ),
810                         Math.min(
811                             longPremium.leftSlot() - collateralDelta1,
812                             PanopticMath.convert0to1(
813                                 collateralDelta0 - longPremium.rightSlot(),
814                                 sqrtPriceX96Final
815                             )
816                         )
817                     );
818     
819                     haircut0 = longPremium.rightSlot();
820                     haircut1 = protocolLoss1 + collateralDelta1;
821                 } else if (
822                     longPremium.leftSlot() < collateralDelta1 &&
823                     longPremium.rightSlot() > collateralDelta0
824                 ) {
825                     int256 protocolLoss0 = collateralDelta0;
826                     (collateralDelta0, collateralDelta1) = (
827                         Math.min(
828                             longPremium.rightSlot() - collateralDelta0,
829                             PanopticMath.convert1to0(
830                                 collateralDelta1 - longPremium.leftSlot(),
831                                 sqrtPriceX96Final
832                             )
833                         ),
834                         -Math.min(
835                             collateralDelta1 - longPremium.leftSlot(),
836                             PanopticMath.convert0to1(
837                                 longPremium.rightSlot() - collateralDelta0,
838                                 sqrtPriceX96Final
839                             )
840                         )
841                     );
842     
843                     haircut0 = collateralDelta0 + protocolLoss0;
844                     haircut1 = longPremium.leftSlot();
845                 } else {
846                     // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
847                     haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
848                     haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
849     
850                     collateralDelta0 = 0;
851                     collateralDelta1 = 0;
852                 }
853     
854                 {
855                     address _liquidatee = liquidatee;
856                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
857                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
858                 }
859     
860                 for (uint256 i = 0; i < positionIdList.length; i++) {
861                     TokenId tokenId = positionIdList[i];
862                     LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
863                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864                         if (tokenId.isLong(leg) == 1) {
865                             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
866                                 storage _settledTokens = settledTokens;
867     
868                             // calculate amounts to revoke from settled and subtract from haircut req
869                             uint256 settled0 = Math.unsafeDivRoundingUp(
870                                 uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871                                 uint128(longPremium.rightSlot())
872                             );
873                             uint256 settled1 = Math.unsafeDivRoundingUp(
874                                 uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875                                 uint128(longPremium.leftSlot())
876                             );
877     
878                             bytes32 chunkKey = keccak256(
879                                 abi.encodePacked(
880                                     tokenId.strike(0),
881                                     tokenId.width(0),
882                                     tokenId.tokenType(0)
883                                 )
884                             );
885     
886                             // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
887                             // for the haircut directly to the accumulator
888                             settled0 = Math.max(
889                                 0,
890                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891                             );
892                             settled1 = Math.max(
893                                 0,
894                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895                             );
896     
897                             _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
898                                 LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
899                                     uint128(settled1)
900                                 )
901                             );
902                         }
903                     }
904                 }
905     
906                 return (collateralDelta0, collateralDelta1);
907             }
908         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768:908

```solidity
File: contracts/multicall/Multicall.sol


12          function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {
13              results = new bytes[](data.length);
14              for (uint256 i = 0; i < data.length; ) {
15                  (bool success, bytes memory result) = address(this).delegatecall(data[i]);
16      
17                  if (!success) {
18                      // Bubble up the revert reason
19                      // The bytes type is ABI encoded as a length-prefixed byte array
20                      // So we simply need to add 32 to the pointer to get the start of the data
21                      // And then revert with the size loaded from the first 32 bytes
22                      // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
23                      // However, we have chosen to simply replicate the the normal behavior of the call
24                      // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
25                      assembly ("memory-safe") {
26                          revert(add(result, 32), mload(result))
27                      }
28                  }
29      
30                  results[i] = result;
31      
32                  unchecked {
33                      ++i;
34                  }
35              }
36          }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L12:36

```solidity
File: contracts/tokens/ERC1155Minimal.sol


130         function safeBatchTransferFrom(
131             address from,
132             address to,
133             uint256[] calldata ids,
134             uint256[] calldata amounts,
135             bytes calldata data
136         ) public virtual {
137             if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();
138     
139             // Storing these outside the loop saves ~15 gas per iteration.
140             uint256 id;
141             uint256 amount;
142     
143             for (uint256 i = 0; i < ids.length; ) {
144                 id = ids[i];
145                 amount = amounts[i];
146     
147                 balanceOf[from][id] -= amount;
148     
149                 // balance will never overflow
150                 unchecked {
151                     balanceOf[to][id] += amount;
152                 }
153     
154                 // An array can't have a total length
155                 // larger than the max uint256 value.
156                 unchecked {
157                     ++i;
158                 }
159             }
160     
161             emit TransferBatch(msg.sender, from, to, ids, amounts);
162     
163             if (to.code.length != 0) {
164                 if (
165                     ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
166                     ERC1155Holder.onERC1155BatchReceived.selector
167                 ) {
168                     revert UnsafeRecipient();
169                 }
170             }
171         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L130:171

</details>

## L013 - Function calls within for loops:

Making function calls within loops in Solidity can lead to inefficient gas usage, potential bottlenecks, and increased vulnerability to attacks. Each function call or external call consumes gas, and when executed within a loop, the gas cost multiplies, potentially causing the transaction to run out of gas or exceed block gas limits. This can result in transaction failure or unpredictable behavior.


<details>
<summary>Click to show 12 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


1255                for (uint256 index = 0; index < numLegs; ++index) {
1256                    // revert if the tokenType does not match the current collateral token
1257                    if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;
1258                    // Increment the tokenRequired accumulator
1259                    tokenRequired += _getRequiredCollateralSingleLeg(
1260                        tokenId,
1261                        index,
1262                        positionSize,
1263                        atTick,
1264                        poolUtilization
1265                    );
1266                }


1208            for (uint256 i = 0; i < totalIterations; ) {
1209                // read the ith tokenId from the account
1210                TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);
1211    
1212                // read the position size and the pool utilization at mint
1213                uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();
1214    
1215                // read the pool utilization at mint
1216                uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();
1217    
1218                // Get tokens required for the current tokenId (a single active position)
1219                uint256 _tokenRequired = _getRequiredCollateralAtTickSinglePosition(
1220                    tokenId,
1221                    positionSize,
1222                    atTick,
1223                    poolUtilization
1224                );
1225    
1226                // add to the tokenRequired accumulator
1227                unchecked {
1228                    tokenRequired += _tokenRequired;
1229                }
1230                unchecked {
1231                    ++i;
1232                }
1233            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1208:1233

```solidity
File: contracts/PanopticPool.sol


441             for (uint256 k = 0; k < pLength; ) {
442                 TokenId tokenId = positionIdList[k];
443     
444                 balances[k][0] = TokenId.unwrap(tokenId);
445                 balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);
446     
447                 (
448                     LeftRightSigned[4] memory premiaByLeg,
449                     uint256[2][4] memory premiumAccumulatorsByLeg
450                 ) = _getPremia(
451                         tokenId,
452                         LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
453                         c_user,
454                         computeAllPremia,
455                         atTick
456                     );
457     
458                 uint256 numLegs = tokenId.countLegs();
459                 for (uint256 leg = 0; leg < numLegs; ) {
460                     if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
461                         bytes32 chunkKey = keccak256(
462                             abi.encodePacked(
463                                 tokenId.strike(leg),
464                                 tokenId.width(leg),
465                                 tokenId.tokenType(leg)
466                             )
467                         );
468     
469                         LeftRightUnsigned availablePremium = _getAvailablePremium(
470                             _getTotalLiquidity(tokenId, leg),
471                             s_settledTokens[chunkKey],
472                             s_grossPremiumLast[chunkKey],
473                             LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
474                             premiumAccumulatorsByLeg[leg]
475                         );
476                         portfolioPremium = portfolioPremium.add(
477                             LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478                         );
479                     } else {
480                         portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
481                     }
482                     unchecked {
483                         ++leg;
484                     }
485                 }
486     
487                 unchecked {
488                     ++k;
489                 }
490             }


864             for (uint256 leg = 0; leg < numLegs; ) {
865                 if (tokenId.isLong(leg) == 0) {
866                     // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
867                     (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
868                     _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
869                 }
870                 s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
871                 unchecked {
872                     ++leg;
873                 }
874             }


1672            for (uint256 leg = 0; leg < numLegs; ++leg) {
1673                bytes32 chunkKey = keccak256(
1674                    abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1675                );
1676                // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers
1677                s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1678    
1679                if (tokenId.isLong(leg) == 0) {
1680                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1681                        tokenId,
1682                        leg,
1683                        positionSize
1684                    );
1685    
1686                    // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (R + N)
1687                    uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1688    
1689                    // We need to adjust the grossPremiumLast value such that the result of
1690                    // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64
1691                    // G: total gross premium
1692                    // T: totalLiquidityBeforeMint
1693                    // R: positionLiquidity
1694                    // C: current grossPremium value
1695                    // L: current grossPremiumLast value
1696                    // Ln: updated grossPremiumLast value
1697                    // T * (C - L) = G
1698                    // (T + R) * (C - Ln) = G
1699                    //
1700                    // T * (C - L) = (T + R) * (C - Ln)
1701                    // (TC - TL) / (T + R) = C - Ln
1702                    // Ln = C - (TC - TL)/(T + R)
1703                    // Ln = (CT + CR - TC + TL)/(T+R)
1704                    // Ln = (CR + TL)/(T+R)
1705    
1706                    uint256[2] memory grossCurrent;
1707                    (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1708                        address(s_univ3pool),
1709                        address(this),
1710                        tokenId.tokenType(leg),
1711                        liquidityChunk.tickLower(),
1712                        liquidityChunk.tickUpper(),
1713                        type(int24).max,
1714                        0
1715                    );
1716    
1717                    unchecked {
1718                        // L
1719                        LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1720                        // R
1721                        uint256 positionLiquidity = liquidityChunk.liquidity();
1722                        // T (totalLiquidity is (T + R) after minting)
1723                        uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
1724    
1725                        s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1726                            .wrap(0)
1727                            .toRightSlot(
1728                                uint128(
1729                                    (grossCurrent[0] *
1730                                        positionLiquidity +
1731                                        grossPremiumLast.rightSlot() *
1732                                        totalLiquidityBefore) / (totalLiquidity)
1733                                )
1734                            )
1735                            .toLeftSlot(
1736                                uint128(
1737                                    (grossCurrent[1] *
1738                                        positionLiquidity +
1739                                        grossPremiumLast.leftSlot() *
1740                                        totalLiquidityBefore) / (totalLiquidity)
1741                                )
1742                            );
1743                    }
1744                }
1745            }


459                 for (uint256 leg = 0; leg < numLegs; ) {
460                     if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
461                         bytes32 chunkKey = keccak256(
462                             abi.encodePacked(
463                                 tokenId.strike(leg),
464                                 tokenId.width(leg),
465                                 tokenId.tokenType(leg)
466                             )
467                         );
468     
469                         LeftRightUnsigned availablePremium = _getAvailablePremium(
470                             _getTotalLiquidity(tokenId, leg),
471                             s_settledTokens[chunkKey],
472                             s_grossPremiumLast[chunkKey],
473                             LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
474                             premiumAccumulatorsByLeg[leg]
475                         );
476                         portfolioPremium = portfolioPremium.add(
477                             LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478                         );
479                     } else {
480                         portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
481                     }
482                     unchecked {
483                         ++leg;
484                     }
485                 }


802             for (uint256 i = 0; i < positionIdList.length; ) {
803                 LeftRightSigned paidAmounts;
804                 (paidAmounts, premiasByLeg[i]) = _burnOptions(
805                     commitLongSettled,
806                     positionIdList[i],
807                     owner,
808                     tickLimitLow,
809                     tickLimitHigh
810                 );
811                 netPaid = netPaid.add(paidAmounts);
812                 unchecked {
813                     ++i;
814                 }
815             }


1852            for (uint256 leg = 0; leg < numLegs; ) {
1853                LeftRightSigned legPremia = premiaByLeg[leg];
1854    
1855                bytes32 chunkKey = keccak256(
1856                    abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1857                );
1858    
1859                // collected from Uniswap
1860                LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1861    
1862                if (LeftRightSigned.unwrap(legPremia) != 0) {
1863                    // (will be) paid by long legs
1864                    if (tokenId.isLong(leg) == 1) {
1865                        if (commitLongSettled)
1866                            settledTokens = LeftRightUnsigned.wrap(
1867                                uint256(
1868                                    LeftRightSigned.unwrap(
1869                                        LeftRightSigned
1870                                            .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1871                                            .sub(legPremia)
1872                                    )
1873                                )
1874                            );
1875                        realizedPremia = realizedPremia.add(legPremia);
1876                    } else {
1877                        uint256 positionLiquidity = PanopticMath
1878                            .getLiquidityChunk(tokenId, leg, positionSize)
1879                            .liquidity();
1880    
1881                        // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (T - R)
1882                        uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1883                        // T (totalLiquidity is (T - R) after burning)
1884                        uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;
1885    
1886                        LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1887    
1888                        LeftRightUnsigned availablePremium = _getAvailablePremium(
1889                            totalLiquidity + positionLiquidity,
1890                            settledTokens,
1891                            grossPremiumLast,
1892                            LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
1893                            premiumAccumulatorsByLeg[leg]
1894                        );
1895    
1896                        // subtract settled tokens sent to seller
1897                        settledTokens = settledTokens.sub(availablePremium);
1898    
1899                        // add available premium to amount that should be settled
1900                        realizedPremia = realizedPremia.add(
1901                            LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1902                        );
1903    
1904                        // We need to adjust the grossPremiumLast value such that the result of
1905                        // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostBurn/2**64 is equal to
1906                        // (grossPremium - grossPremiumLast)*totalLiquidityBeforeBurn/2**64 - premiumOwedToPosition
1907                        // G: total gross premium (- premiumOwedToPosition)
1908                        // T: totalLiquidityBeforeMint
1909                        // R: positionLiquidity
1910                        // C: current grossPremium value
1911                        // L: current grossPremiumLast value
1912                        // Ln: updated grossPremiumLast value
1913                        // T * (C - L) = G
1914                        // (T - R) * (C - Ln) = G - P
1915                        //
1916                        // T * (C - L) = (T - R) * (C - Ln) + P
1917                        // (TC - TL - P) / (T - R) = C - Ln
1918                        // Ln = C - (TC - TL - P) / (T - R)
1919                        // Ln = (TC - CR - TC + LT + P) / (T-R)
1920                        // Ln = (LT - CR + P) / (T-R)
1921    
1922                        unchecked {
1923                            uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
1924                            uint256 _leg = leg;
1925    
1926                            // if there's still liquidity, compute the new grossPremiumLast
1927                            // otherwise, we just reset grossPremiumLast to the current grossPremium
1928                            s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929                                ? LeftRightUnsigned
1930                                    .wrap(0)
1931                                    .toRightSlot(
1932                                        uint128(
1933                                            uint256(
1934                                                Math.max(
1935                                                    (int256(
1936                                                        grossPremiumLast.rightSlot() *
1937                                                            totalLiquidityBefore
1938                                                    ) -
1939                                                        int256(
1940                                                            _premiumAccumulatorsByLeg[_leg][0] *
1941                                                                positionLiquidity
1942                                                        )) + int256(legPremia.rightSlot() * 2 ** 64),
1943                                                    0
1944                                                )
1945                                            ) / totalLiquidity
1946                                        )
1947                                    )
1948                                    .toLeftSlot(
1949                                        uint128(
1950                                            uint256(
1951                                                Math.max(
1952                                                    (int256(
1953                                                        grossPremiumLast.leftSlot() *
1954                                                            totalLiquidityBefore
1955                                                    ) -
1956                                                        int256(
1957                                                            _premiumAccumulatorsByLeg[_leg][1] *
1958                                                                positionLiquidity
1959                                                        )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960                                                    0
1961                                                )
1962                                            ) / totalLiquidity
1963                                        )
1964                                    )
1965                                : LeftRightUnsigned
1966                                    .wrap(0)
1967                                    .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968                                    .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1969                        }
1970                    }
1971                }
1972    
1973                // update settled tokens in storage with all local deltas
1974                s_settledTokens[chunkKey] = settledTokens;
1975    
1976                unchecked {
1977                    ++leg;
1978                }
1979            }


745             for (uint256 leg = 0; leg < numLegs; ) {
746                 // Extract base fee (AMM swap/trading fees) for the position and add it to s_options
747                 // (ie. the (feeGrowth * liquidity) / 2**128 for each token)
748                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
749                 uint256 isLong = tokenId.isLong(leg);
750                 {
751                     (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
752                         address(s_univ3pool),
753                         address(this),
754                         tokenId.tokenType(leg),
755                         tickLower,
756                         tickUpper,
757                         type(int24).max,
758                         isLong
759                     );
760     
761                     // update the premium accumulators
762                     s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
763                         .wrap(0)
764                         .toRightSlot(premiumAccumulator0)
765                         .toLeftSlot(premiumAccumulator1);
766                 }
767                 // verify base Liquidity limit only if new position is long
768                 if (isLong == 1) {
769                     // Move this into a new function
770                     _checkLiquiditySpread(
771                         tokenId,
772                         leg,
773                         tickLower,
774                         tickUpper,
775                         uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))
776                     );
777                 }
778                 unchecked {
779                     ++leg;
780                 }
781             }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L745:781

```solidity
File: contracts/SemiFungiblePositionManager.sol


882             for (uint256 leg = 0; leg < numLegs; ) {
883                 LeftRightSigned _moved;
884                 LeftRightSigned _itmAmounts;
885                 LeftRightUnsigned _collectedSingleLeg;
886     
887                 {
888                     // cache the univ3pool, tokenId, isBurn, and _positionSize variables to get rid of stack too deep error
889                     IUniswapV3Pool _univ3pool = univ3pool;
890                     TokenId _tokenId = tokenId;
891                     bool _isBurn = isBurn;
892                     uint128 _positionSize = positionSize;
893                     uint256 _leg;
894     
895                     unchecked {
896                         // Reverse the order of the legs if this call is burning a position (LIFO)
897                         // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,
898                         // allowing the corresponding short liquidity to be removed
899                         _leg = _isBurn ? numLegs - leg - 1 : leg;
900                     }
901     
902                     // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
903                     // @dev see `contracts/types/LiquidityChunk.sol`
904                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
905                         _tokenId,
906                         _leg,
907                         _positionSize
908                     );
909     
910                     (_moved, _itmAmounts, _collectedSingleLeg) = _createLegInAMM(
911                         _univ3pool,
912                         _tokenId,
913                         _leg,
914                         liquidityChunk,
915                         _isBurn
916                     );
917     
918                     collectedByLeg[_leg] = _collectedSingleLeg;
919     
920                     unchecked {
921                         // increment accumulators of the upper bound on tokens contained across all legs of the position at any given tick
922                         amount0 += Math.getAmount0ForLiquidity(liquidityChunk);
923     
924                         amount1 += Math.getAmount1ForLiquidity(liquidityChunk);
925                     }
926                 }
927     
928                 totalMoved = totalMoved.add(_moved);
929                 itmAmounts = itmAmounts.add(_itmAmounts);
930     
931                 unchecked {
932                     ++leg;
933                 }
934             }


575             for (uint256 i = 0; i < ids.length; ) {
576                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
577                 registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
578                 unchecked {
579                     ++i;
580                 }
581             }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L575:581

```solidity
File: contracts/libraries/PanopticMath.sol


395             for (uint256 leg = 0; leg < numLegs; ) {
396                 // Compute the amount of funds that have been removed from the Panoptic Pool
397                 (LeftRightSigned longs, LeftRightSigned shorts) = _calculateIOAmounts(
398                     tokenId,
399                     positionSize,
400                     leg
401                 );
402     
403                 longAmounts = longAmounts.add(longs);
404                 shortAmounts = shortAmounts.add(shorts);
405     
406                 unchecked {
407                     ++leg;
408                 }
409             }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L395:409

</details>

## L014 -  Subtraction may underflow if multiplication is too large:




<details>
<summary>Click to show 10 findings</summary>

```solidity
File: contracts/PanopticPool.sol


1940                                                            _premiumAccumulatorsByLeg[_leg][0] *
1941                                                                positionLiquidity


1957                                                            _premiumAccumulatorsByLeg[_leg][1] *
1958                                                                positionLiquidity


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1957:1958

```solidity
File: contracts/SemiFungiblePositionManager.sol


1389                            totalLiquidity *
1390                            removedLiquidity +


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1389:1390

```solidity
File: contracts/libraries/Math.sol


418                 inv *= 2 - denominator * inv; // inverse mod 2**8


419                 inv *= 2 - denominator * inv; // inverse mod 2**16


420                 inv *= 2 - denominator * inv; // inverse mod 2**32


421                 inv *= 2 - denominator * inv; // inverse mod 2**64


422                 inv *= 2 - denominator * inv; // inverse mod 2**128


423                 inv *= 2 - denominator * inv; // inverse mod 2**256


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L423:423

```solidity
File: contracts/libraries/PanopticMath.sol


140                             (int256(observationIndex) - int256(i * period)) +


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L140:140

</details>


## L015 - Contracts are not using their OZ Upgradeable counterparts:

The non-upgradeable standard version of OpenZeppelin’s library is inherited/used by the contracts. It would be safer to use the upgradeable versions of the library contracts to avoid unexpected behavior.

Use the contracts from `@openzeppelin/contracts-upgradeable` instead of `@openzeppelin/contracts` where applicable. See https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/tree/master/contracts for a list of available upgradeable contracts


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: contracts/PanopticFactory.sol


14      import {Clones} from "@openzeppelin/contracts/proxy/Clones.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L14:14

```solidity
File: contracts/PanopticPool.sol


9       import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L9:9

```solidity
File: contracts/libraries/InteractionHelper.sol


6       import {IERC20Metadata} from "@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol";


10      import {Strings} from "@openzeppelin/contracts/utils/Strings.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L10:10

```solidity
File: contracts/tokens/ERC1155Minimal.sol


5       import {ERC1155Holder} from "@openzeppelin/contracts/token/ERC1155/utils/ERC1155Holder.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L5:5

</details>

## L016 - Multiplication on the result of a division:

Dividing an integer by another integer will often result in loss of precision. When the result is multiplied by another number, the loss of precision is magnified, often to material magnitudes. (X / Z) * Y should be re-written as (X * Y) / Z.


```solidity
File: contracts/PanopticFactory.sol


392                 tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L392:392

```solidity
File: contracts/libraries/PanopticMath.sol


346                 int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;


347                 int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L347:347

## L017 - Unbounded state array which is iterated upon:

Iterating over an unbounded state array in Solidity can result in excessive gas consumption, especially if the array size exceeds the block gas limit. This issue commonly arises in tasks like token distribution. To address this, it is recommended to limit array sizes for iteration, consider alternative data structures like linked lists, adopt paginated processing for smaller batches over multiple transactions, or use a 'state array' with a separate index-tracking array to manage large datasets and avoid gas-related problems.


<details>
<summary>Click to show 38 findings</summary>

```solidity
File: contracts/PanopticPool.sol


445                 balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);


445                 balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);


471                             s_settledTokens[chunkKey],


472                             s_grossPremiumLast[chunkKey],


471                             s_settledTokens[chunkKey],


472                             s_grossPremiumLast[chunkKey],


762                     s_options[msg.sender][tokenId][leg] = LeftRightUnsigned


762                     s_options[msg.sender][tokenId][leg] = LeftRightUnsigned


762                     s_options[msg.sender][tokenId][leg] = LeftRightUnsigned


870                 s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);


870                 s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);


870                 s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);


1540                        LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];


1540                        LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];


1540                        LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];


1677                s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);


1677                s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);


1719                        LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];


1725                        s_grossPremiumLast[chunkKey] = LeftRightUnsigned


1860                LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);


1886                        LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];


1928                            s_grossPremiumLast[chunkKey] = totalLiquidity != 0


1974                s_settledTokens[chunkKey] = settledTokens;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1974:1974

```solidity
File: contracts/SemiFungiblePositionManager.sol


576                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();


632                     (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||


633                     (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)


637                 LeftRightUnsigned fromLiq = s_accountLiquidity[positionKey_from];


641                 LeftRightSigned fromBase = s_accountFeesBase[positionKey_from];


644                 s_accountLiquidity[positionKey_to] = fromLiq;


645                 s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);


647                 s_accountFeesBase[positionKey_to] = fromBase;


648                 s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L648:648

```solidity
File: contracts/tokens/ERC1155Minimal.sol


147                 balanceOf[from][id] -= amount;


147                 balanceOf[from][id] -= amount;


151                     balanceOf[to][id] += amount;


151                     balanceOf[to][id] += amount;


188                     balances[i] = balanceOf[owners[i]][ids[i]];


188                     balances[i] = balanceOf[owners[i]][ids[i]];


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L188:188

</details>

## L018 - Prefer continue over revert model in iteration:

Preferably, it's better to skip operations on array indices when a condition is not met instead of reverting the entire transaction. Reverting could be exploited by malicious actors who might intentionally introduce array objects failing conditional checks, disrupting group operations. It's advisable to skip array indices rather than revert, unless there are valid security or logic reasons for doing otherwise


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol


575             for (uint256 i = 0; i < ids.length; ) {
576                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
577                 registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
578                 unchecked {
579                     ++i;
580                 }
581             }


601             for (uint256 leg = 0; leg < numLegs; ) {
602                 // for this leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
603                 // @dev see `contracts/types/LiquidityChunk.sol`
604                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
605                     id,
606                     leg,
607                     uint128(amount)
608                 );
609     
610                 //construct the positionKey for the from and to addresses
611                 bytes32 positionKey_from = keccak256(
612                     abi.encodePacked(
613                         address(univ3pool),
614                         from,
615                         id.tokenType(leg),
616                         liquidityChunk.tickLower(),
617                         liquidityChunk.tickUpper()
618                     )
619                 );
620                 bytes32 positionKey_to = keccak256(
621                     abi.encodePacked(
622                         address(univ3pool),
623                         to,
624                         id.tokenType(leg),
625                         liquidityChunk.tickLower(),
626                         liquidityChunk.tickUpper()
627                     )
628                 );
629     
630                 // Revert if recipient already has that position
631                 if (
632                     (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
633                     (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)
634                 ) revert Errors.TransferFailed();
635     
636                 // Revert if sender has long positions in that chunk or the entire liquidity is not being transferred
637                 LeftRightUnsigned fromLiq = s_accountLiquidity[positionKey_from];
638                 if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity())
639                     revert Errors.TransferFailed();
640     
641                 LeftRightSigned fromBase = s_accountFeesBase[positionKey_from];
642     
643                 //update+store liquidity and fee values between accounts
644                 s_accountLiquidity[positionKey_to] = fromLiq;
645                 s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);
646     
647                 s_accountFeesBase[positionKey_to] = fromBase;
648                 s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);
649                 unchecked {
650                     ++leg;
651                 }
652             }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L601:652

```solidity
File: contracts/types/TokenId.sol


507                 for (uint256 i = 0; i < 4; ++i) {
508                     if (self.optionRatio(i) == 0) {
509                         // final leg in this position identified;
510                         // make sure any leg above this are zero as well
511                         // (we don't allow gaps eg having legs 1 and 4 active without 2 and 3 is not allowed)
512                         if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)
513                             revert Errors.InvalidTokenIdParameter(1);
514     
515                         break; // we are done iterating over potential legs
516                     }
517     
518                     // prevent legs touching the same chunks - all chunks in the position must be discrete
519                     uint256 numLegs = self.countLegs();
520                     for (uint256 j = i + 1; j < numLegs; ++j) {
521                         if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {
522                             revert Errors.InvalidTokenIdParameter(6);
523                         }
524                     }
525                     // now validate this ith leg in the position:
526     
527                     // The width cannot be 0; the minimum is 1
528                     if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);
529                     // Strike cannot be MIN_TICK or MAX_TICK
530                     if (
531                         (self.strike(i) == Constants.MIN_V3POOL_TICK) ||
532                         (self.strike(i) == Constants.MAX_V3POOL_TICK)
533                     ) revert Errors.InvalidTokenIdParameter(4);
534     
535                     // In the following, we check whether the risk partner of this leg is itself
536                     // or another leg in this position.
537                     // Handles case where riskPartner(i) != i ==> leg i has a risk partner that is another leg
538                     uint256 riskPartnerIndex = self.riskPartner(i);
539                     if (riskPartnerIndex != i) {
540                         // Ensures that risk partners are mutual
541                         if (self.riskPartner(riskPartnerIndex) != i)
542                             revert Errors.InvalidTokenIdParameter(3);
543     
544                         // Ensures that risk partners have 1) the same asset, and 2) the same ratio
545                         if (
546                             (self.asset(riskPartnerIndex) != self.asset(i)) ||
547                             (self.optionRatio(riskPartnerIndex) != self.optionRatio(i))
548                         ) revert Errors.InvalidTokenIdParameter(3);
549     
550                         // long/short status of associated legs
551                         uint256 _isLong = self.isLong(i);
552                         uint256 isLongP = self.isLong(riskPartnerIndex);
553     
554                         // token type status of associated legs (call/put)
555                         uint256 _tokenType = self.tokenType(i);
556                         uint256 tokenTypeP = self.tokenType(riskPartnerIndex);
557     
558                         // if the position is the same i.e both long calls, short put's etc.
559                         // then this is a regular position, not a defined risk position
560                         if ((_isLong == isLongP) && (_tokenType == tokenTypeP))
561                             revert Errors.InvalidTokenIdParameter(4);
562     
563                         // if the two token long-types and the tokenTypes are both different (one is a short call, the other a long put, e.g.), this is a synthetic position
564                         // A synthetic long or short is more capital efficient than each leg separated because the long+short premia accumulate proportionally
565                         // unlike short stranlges, long strangles also cannot be partnered, because there is no reduction in risk (both legs can earn premia simultaneously)
566                         if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))
567                             revert Errors.InvalidTokenIdParameter(5);
568                     }
569                 } // end for loop over legs


520                     for (uint256 j = i + 1; j < numLegs; ++j) {
521                         if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {
522                             revert Errors.InvalidTokenIdParameter(6);
523                         }
524                     }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L520:524

</details>



## L019 - Missing checks for address(0x0) in the constructor:




```solidity
File: contracts/PanopticFactory.sol


129             COLLATERAL_REFERENCE = _collateralReference;


128             POOL_REFERENCE = _poolReference;


123             WETH = _WETH9;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L123:123

## L020 - Missing checks for address(0x0) in the initializer:




```solidity
File: contracts/PanopticFactory.sol


134         function initialize(address _owner) public {
135             if (!s_initialized) {
136                 s_owner = _owner;
137                 s_initialized = true;
138             }
139         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L134:139

## L021 - Code does not follow the best practice of check-effects-interaction:

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.


```solidity
File: contracts/SemiFungiblePositionManager.sol


/// @audit _createLegInAMM() called prior to this assignment
/// @audit contains nested function call univ3pool.mint() 
/// @audit located in file albahca/contracts/SemiFungiblePositionManager.sol  
1098            s_accountFeesBase[positionKey] = _getFeesBase(
1099                univ3pool,
1100                updatedLiquidity,
1101                liquidityChunk,
1102                true
1103            );


/// @audit _mintLiquidity() called prior to this assignment
/// @audit contains nested function call univ3pool.mint() 
/// @audit located in file albahca/contracts/SemiFungiblePositionManager.sol  
1098            s_accountFeesBase[positionKey] = _getFeesBase(
1099                univ3pool,
1100                updatedLiquidity,
1101                liquidityChunk,
1102                true
1103            );


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1098:1103


## L022 - The additions/multiplications may silently overflow because they're in unchecked blocks with no preceding value checks, which may lead to unexpected results.:

The additions/multiplications may silently overflow because they're in unchecked blocks with no preceding value checks, which may lead to unexpected results.


<details>
<summary>Click to show 237 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


200                 int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);


202                     2230 +
203                         (12500 * ratioTick) /
204                         10_000 +
205                         (7812 * ratioTick ** 2) /
206                         10_000 ** 2 +
207                         (6510 * ratioTick ** 3) /
208                         10_000 ** 3


249                 _poolFee = fee / 100;


262                 s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);


372                 return s_poolAssets + s_inAMM;


403                     assets * (DECIMALS - COMMISSION_FEE),


405                     totalAssets() * DECIMALS


446                 return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);


463                     shares * DECIMALS,


465                     totalSupply * (DECIMALS - COMMISSION_FEE)


670                                     uint24(positionId.width(leg) * positionId.tickSpacing()),


677                             uint256(Math.abs(currentTick - positionId.strike(leg)) / range)


715                                     int128(uint128(oracleValue0)) - int128(uint128(currentValue0))


718                                     int128(uint128(oracleValue1)) - int128(uint128(currentValue1))


727                 int256 fee = (FORCE_EXERCISE_COST >> (maxNumRangesFromStrike - 1)); // exponential decay of fee based on number of half ranges away from the price


731                     .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))


732                     .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));


743                 return int256((s_inAMM * DECIMALS) / totalAssets());


796                     min_sell_ratio +
797                     ((DECIMALS - min_sell_ratio) * (uint256(utilization) - TARGET_POOL_UTIL)) /
798                     (SATURATED_POOL_UTIL - TARGET_POOL_UTIL);


843                     return BUYER_COLLATERAL_RATIO / 2;


849                     (BUYER_COLLATERAL_RATIO +
850                         (BUYER_COLLATERAL_RATIO * (SATURATED_POOL_UTIL - utilization)) /
851                         (SATURATED_POOL_UTIL - TARGET_POOL_UTIL)) / 2; // do the division by 2 at the end after all addition and multiplication; b/c y1 = buyCollateralRatio / 2


1003                int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;


1029                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));


1052                int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;


1058                int256 intrinsicValue = swappedAmount - (longAmount - shortAmount);


1084                s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));


1085                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));


1105                int256 intrinsicValue = swappedAmount - (shortAmount - longAmount);


1110                        s_ITMSpreadFee * uint256(Math.abs(intrinsicValue)),


1115                    exchangedAmount = intrinsicValue + int256(swapCommission);


1121                        uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,


1364                                Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)


1367                                Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)


1397                            uint256 c2 = Constants.FP96 - ratio;


1409                                (tickUpper - strike) + (strike - tickLower)


1413                                scaleFactor - ratio,


1414                                scaleFactor + Constants.FP96


1486                    required = Math.unsafeDivRoundingUp(amount * sellCollateral, DECIMALS);


1496                    required = Math.unsafeDivRoundingUp(amount * buyCollateral, DECIMALS);


1546                            ? movedPartnerRight - movedRight


1547                            : movedRight - movedPartnerRight;


1550                            ? movedPartnerLeft - movedLeft


1551                            : movedLeft - movedPartnerLeft;


1571                        ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)


1572                        : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);


1637                    uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +
1638                    (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1637:1638

```solidity
File: contracts/PanopticFactory.sol


300                 maxSalt = uint256(salt) + loops;


323                     salt = bytes32(uint256(salt) + 1);


392                 tickLower = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L392:392

```solidity
File: contracts/PanopticPool.sol


309                     (uint256(block.timestamp) << 216) +
310                     // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
311                     // see comment on s_miniMedian initialization for format of this magic number
312                     (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
313                     (uint256(uint24(currentTick)) << 24) + // add to slot 4
314                     (uint256(uint24(currentTick))); // add to slot 3


624                 tokenId = positionIdList[positionIdList.length - 1];


730                 return uint128(uint256(utilization0) + uint128(uint256(utilization1) << 64));


1255                    refundAmounts.rightSlot() - delegatedAmounts.rightSlot()


1260                    refundAmounts.leftSlot() - delegatedAmounts.leftSlot()


1329                return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);


1348                    Math.mulDiv(uint256(tokenData1.rightSlot()), 2 ** 96, sqrtPriceX96) +
1349                    Math.mulDiv96(tokenData0.rightSlot(), sqrtPriceX96);


1353                    Math.mulDivRoundingUp(uint256(tokenData1.leftSlot()), 2 ** 96, sqrtPriceX96) +
1354                    Math.mulDiv96RoundingUp(tokenData0.leftSlot(), sqrtPriceX96);


1376                pLength = positionIdList.length - offset;


1487                effectiveLiquidityFactorX32 = (uint256(totalLiquidity) * 2 ** 32) / netLiquidity;


1550                                        ((premiumAccumulatorsByLeg[leg][0] -
1551                                            premiumAccumulatorLast.rightSlot()) *
1552                                            (liquidityChunk.liquidity())) / 2 ** 64


1559                                        ((premiumAccumulatorsByLeg[leg][1] -
1560                                            premiumAccumulatorLast.leftSlot()) *
1561                                            (liquidityChunk.liquidity())) / 2 ** 64


1635                    .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))


1636                    .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));


1723                        uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;


1729                                    (grossCurrent[0] *
1730                                        positionLiquidity +
1731                                        grossPremiumLast.rightSlot() *
1732                                        totalLiquidityBefore) / (totalLiquidity)


1737                                    (grossCurrent[1] *
1738                                        positionLiquidity +
1739                                        grossPremiumLast.leftSlot() *
1740                                        totalLiquidityBefore) / (totalLiquidity)


1768                uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *
1769                    totalLiquidity) / 2 ** 64;


1770                uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *
1771                    totalLiquidity) / 2 ** 64;


1779                                    (uint256(premiumOwed.rightSlot()) * settledTokens.rightSlot()) /
1780                                        (accumulated0 == 0 ? type(uint256).max : accumulated0),


1788                                    (uint256(premiumOwed.leftSlot()) * settledTokens.leftSlot()) /
1789                                        (accumulated1 == 0 ? type(uint256).max : accumulated1),


1820                totalLiquidity = accountLiquidities.rightSlot() + accountLiquidities.leftSlot();


1933                                            uint256(
1934                                                Math.max(
1935                                                    (int256(
1936                                                        grossPremiumLast.rightSlot() *
1937                                                            totalLiquidityBefore
1938                                                    ) -
1939                                                        int256(
1940                                                            _premiumAccumulatorsByLeg[_leg][0] *
1941                                                                positionLiquidity
1942                                                        )) + int256(legPremia.rightSlot() * 2 ** 64),
1943                                                    0
1944                                                )
1945                                            ) / totalLiquidity


1950                                            uint256(
1951                                                Math.max(
1952                                                    (int256(
1953                                                        grossPremiumLast.leftSlot() *
1954                                                            totalLiquidityBefore
1955                                                    ) -
1956                                                        int256(
1957                                                            _premiumAccumulatorsByLeg[_leg][1] *
1958                                                                positionLiquidity
1959                                                        )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960                                                    0
1961                                                )
1962                                            ) / totalLiquidity


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1950:1962

```solidity
File: contracts/SemiFungiblePositionManager.sol


388                 s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;


817                     int256 net0 = itm0 - PanopticMath.convert1to0(itm1, sqrtPriceX96);


842                         ? Constants.MIN_V3POOL_SQRT_RATIO + 1


843                         : Constants.MAX_V3POOL_SQRT_RATIO - 1,


899                         _leg = _isBurn ? numLegs - leg - 1 : leg;


1023                            updatedLiquidity = startingLiquidity - chunkLiquidity;


1297                        ? receivedAmount0 - uint128(-movedInLeg.rightSlot())


1300                        ? receivedAmount1 - uint128(-movedInLeg.leftSlot())


1340                uint256 totalLiquidity = netLiquidity + removedLiquidity;


1352                        totalLiquidity * 2 ** 64,


1357                        totalLiquidity * 2 ** 64,


1367                        uint256 numerator = netLiquidity + (removedLiquidity / 2 ** VEGOID);


1388                        uint256 numerator = totalLiquidity ** 2 -
1389                            totalLiquidity *
1390                            removedLiquidity +
1391                            ((removedLiquidity ** 2) / 2 ** (VEGOID));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1388:1391

```solidity
File: contracts/libraries/FeesCalc.sol


166                     feeGrowthInside0X128 = lowerOut0 - upperOut0; // fee growth inside the chunk


167                     feeGrowthInside1X128 = lowerOut1 - upperOut1;


183                     feeGrowthInside0X128 = upperOut0 - lowerOut0;


184                     feeGrowthInside1X128 = upperOut1 - lowerOut1;


204                     feeGrowthInside0X128 = univ3pool.feeGrowthGlobal0X128() - lowerOut0 - upperOut0;


205                     feeGrowthInside1X128 = univ3pool.feeGrowthGlobal1X128() - lowerOut1 - upperOut1;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L205:205

```solidity
File: contracts/libraries/Math.sol


137                 if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;


139                 if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;


141                 if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;


143                 if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;


145                 if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;


147                 if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;


149                 if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;


151                 if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;


153                 if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;


155                 if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;


157                 if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;


159                 if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;


161                 if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;


163                 if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;


165                 if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;


167                 if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;


169                 if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;


171                 if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;


173                 if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;


176                 if (tick > 0) sqrtR = type(uint256).max / sqrtR;


179                 return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));


196                     mulDiv(
197                         uint256(liquidityChunk.liquidity()) << 96,
198                         highPriceX96 - lowPriceX96,
199                         highPriceX96
200                     ) / lowPriceX96;


212                 return mulDiv96(liquidityChunk.liquidity(), highPriceX96 - lowPriceX96);


258                                 highPriceX96 - lowPriceX96


284                         toUint128(mulDiv(amount1, Constants.FP96, highPriceX96 - lowPriceX96))


391                 uint256 twos = (0 - denominator) & denominator;


407                 prod0 |= prod1 * twos;


414                 uint256 inv = (3 * denominator) ^ 2;


418                 inv *= 2 - denominator * inv; // inverse mod 2**8


419                 inv *= 2 - denominator * inv; // inverse mod 2**16


420                 inv *= 2 - denominator * inv; // inverse mod 2**32


421                 inv *= 2 - denominator * inv; // inverse mod 2**64


422                 inv *= 2 - denominator * inv; // inverse mod 2**128


423                 inv *= 2 - denominator * inv; // inverse mod 2**256


431                 result = prod0 * inv;


511                 prod0 |= prod1 * 2 ** 192;


574                 prod0 |= prod1 * 2 ** 160;


651                 prod0 |= prod1 * 2 ** 128;


728                 prod0 |= prod1 * 2 ** 64;


758                 int256 pivot = arr[uint256(left + (right - left) / 2)];


778                 quickSort(data, int256(0), int256(data.length - 1));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L778:778

```solidity
File: contracts/libraries/PanopticMath.sol


62                  return (poolId & TICKSPACING_MASK) + (uint48(poolId) + 1);


77                  return addr == address(0) ? 40 : 39 - Math.mostSignificantNibble(uint160(addr));


107                         ? uint256(updatedHash) + (((existingHash >> 248) + 1) << 248)


108                         : uint256(updatedHash) + (((existingHash >> 248) - 1) << 248);


133                 int256[] memory tickCumulatives = new int256[](cardinality + 1);


135                 uint256[] memory timestamps = new uint256[](cardinality + 1);


137                 for (uint256 i = 0; i < cardinality + 1; ++i) {


140                             (int256(observationIndex) - int256(i * period)) +
141                                 int256(observationCardinality)


150                         (tickCumulatives[i] - tickCumulatives[i + 1]) /
151                         int256(timestamps[i] - timestamps[i + 1]);


155                 return int24(Math.sort(ticks)[cardinality / 2]);


178                     (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
179                         int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
180                     2;


183                 if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {


188                                 int256(observationIndex) - int256(1) + int256(observationCardinality)


195                             (tickCumulative_last - tickCumulative_old) /
196                                 int256(timestamp_last - timestamp_old)


209                         rank = (orderMap >> (3 * i)) % 8;


217                         entry = int24(uint24(medianData >> (rank * 24)));


223                         newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));


227                         (block.timestamp << 216) +
228                         (uint256(newOrderMap) << 192) +
229                         uint256(uint192(medianData << 24)) +
230                         uint256(uint24(lastObservedTick));


249                     secondsAgos[i] = uint32(((i + 1) * twapWindow) / 20);


258                         (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))


346                 int24 minTick = (Constants.MIN_V3POOL_TICK / tickSpacing) * tickSpacing;


347                 int24 maxTick = (Constants.MAX_V3POOL_TICK / tickSpacing) * tickSpacing;


351                 (tickLower, tickUpper) = (strike - rangeDown, strike + rangeUp);


476                     ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))


477                     : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));


669                     uint256 requiredRatioX128 = (required0 << 128) / (required0 + required1);


678                     uint256 bonusCross = Math.min(balanceCross / 2, thresholdCross - balanceCross);


685                             Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),


693                 int256 balance0 = int256(uint256(tokenData0.rightSlot())) -
694                     Math.max(premia.rightSlot(), 0);


695                 int256 balance1 = int256(uint256(tokenData1.rightSlot())) -
696                     Math.max(premia.leftSlot(), 0);


698                 int256 paid0 = bonus0 + int256(netExchanged.rightSlot());


699                 int256 paid1 = bonus1 + int256(netExchanged.leftSlot());


716                             balance1 - paid1,


717                             PanopticMath.convert0to1(paid0 - balance0, sqrtPriceX96Final)


720                             PanopticMath.convert1to0(balance1 - paid1, sqrtPriceX96Final),


721                             paid0 - balance0


734                             balance0 - paid0,


735                             PanopticMath.convert1to0(paid1 - balance1, sqrtPriceX96Final)


738                             PanopticMath.convert0to1(balance0 - paid0, sqrtPriceX96Final),


739                             paid1 - balance1


744                 paid0 = bonus0 + int256(netExchanged.rightSlot());


745                 paid1 = bonus1 + int256(netExchanged.leftSlot());


749                     LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(


750                         int128(balance1 - paid1)


804                             collateralDelta0 - longPremium.rightSlot(),


806                                 longPremium.leftSlot() - collateralDelta1,


811                             longPremium.leftSlot() - collateralDelta1,


813                                 collateralDelta0 - longPremium.rightSlot(),


820                     haircut1 = protocolLoss1 + collateralDelta1;


828                             longPremium.rightSlot() - collateralDelta0,


830                                 collateralDelta1 - longPremium.leftSlot(),


835                             collateralDelta1 - longPremium.leftSlot(),


837                                 longPremium.rightSlot() - collateralDelta0,


843                     haircut0 = collateralDelta0 + protocolLoss0;


870                                 uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),


874                                 uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),


890                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0


894                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1


928                 int256 balanceShortage = refundValues.rightSlot() -
929                     int256(collateral0.convertToAssets(collateral0.balanceOf(refunder)));


935                             .toRightSlot(int128(refundValues.rightSlot() - balanceShortage))


938                                     int256(
939                                         PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
940                                     ) + refundValues.leftSlot()


946                     refundValues.leftSlot() -
947                     int256(collateral1.convertToAssets(collateral1.balanceOf(refunder)));


953                             .toLeftSlot(int128(refundValues.leftSlot() - balanceShortage))


956                                     int256(
957                                         PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
958                                     ) + refundValues.rightSlot()


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L956:958

```solidity
File: contracts/types/LeftRight.sol


68                          (LeftRightUnsigned.unwrap(self) & LEFT_HALF_BIT_MASK) +
69                              uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)


88                          (LeftRightSigned.unwrap(self) & LEFT_HALF_BIT_MASK_INT) +
89                              (int256(int128(LeftRightSigned.unwrap(self)) + right) & RIGHT_HALF_BIT_MASK)


126                 return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));


136                 return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));


155                 z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));


178                 z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));


196                 int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();


201                 int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();


216                 int256 left256 = int256(x.leftSlot()) + y.leftSlot();


219                 int256 right256 = int256(x.rightSlot()) + y.rightSlot();


234                 int256 left256 = int256(x.leftSlot()) - y.leftSlot();


237                 int256 right256 = int256(x.rightSlot()) - y.rightSlot();


256                 int256 left256 = int256(x.leftSlot()) - y.leftSlot();


259                 int256 right256 = int256(x.rightSlot()) - y.rightSlot();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L259:259

```solidity
File: contracts/types/LiquidityChunk.sol


78                          (uint256(uint24(_tickLower)) << 232) +
79                              (uint256(uint24(_tickUpper)) << 208) +
80                              uint256(amount)


94                  return LiquidityChunk.wrap(LiquidityChunk.unwrap(self) + amount);


109                         LiquidityChunk.unwrap(self) + (uint256(uint24(_tickLower)) << 232)


126                         LiquidityChunk.unwrap(self) + ((uint256(uint24(_tickUpper))) << 208)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L126:126

```solidity
File: contracts/types/TokenId.sol


110                 return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);


120                 return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 1)) % 128);


130                 return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 8)) % 2);


140                 return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 9)) % 2);


150                 return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 10)) % 4);


160                 return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));


171                 return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


195                 return TokenId.wrap(TokenId.unwrap(self) + (uint256(uint24(_tickSpacing)) << 48));


212                     TokenId.wrap(TokenId.unwrap(self) + (uint256(_asset % 2) << (64 + legIndex * 48)));


229                         TokenId.unwrap(self) + (uint256(_optionRatio % 128) << (64 + legIndex * 48 + 1))


246                 return TokenId.wrap(TokenId.unwrap(self) + ((_isLong % 2) << (64 + legIndex * 48 + 8)));


263                         TokenId.unwrap(self) + (uint256(_tokenType % 2) << (64 + legIndex * 48 + 9))


281                         TokenId.unwrap(self) + (uint256(_riskPartner % 4) << (64 + legIndex * 48 + 10))


299                         TokenId.unwrap(self) +
300                             uint256((int256(_strike) & BITMASK_INT24) << (64 + legIndex * 48 + 12))


319                         TokenId.unwrap(self) +
320                             (uint256(uint24(_width) % 4096) << (64 + legIndex * 48 + 36))


395                             ((LONG_MASK >> (48 * (4 - optionRatios))) & CLEAR_POOLID_MASK)


406                 return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);


512                         if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)


520                     for (uint256 j = i + 1; j < numLegs; ++j) {


521                         if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {


589                     if ((currentTick >= _strike + rangeUp) || (currentTick < _strike - rangeDown)) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L589:589

</details>

# Non-critical Issues

| |Issue|Instances|
|-|:-|:-:|
| [[NC001](#nc001---empty-bytes-check-is-missing)] | Empty bytes check is missing | 7 |
| [[NC002](#nc002---defining-all-externalpublic-functions-in-contract-interfaces)] | Defining All External/Public Functions in Contract Interfaces | 16 |
| [[NC003](#nc003---avoid-mutating-function-parameters)] | Avoid mutating function parameters | 4 |
| [[NC004](#nc004---use-a-struct-to-encapsulate-multiple-function-parameters)] | Use a struct to encapsulate multiple function parameters | 42 |
| [[NC005](#nc005---constants-in-comparisons-should-appear-on-the-left-side)] | Constants in comparisons should appear on the left side | 163 |
| [[NC006](#nc006---else-block-not-required)] | else-block not required | 9 |
| [[NC007](#nc007---events-may-be-emitted-out-of-order-due-to-reentrancy)] | Events may be emitted out of order due to reentrancy | 4 |
| [[NC008](#nc008---if-statement-control-structures-do-not-comply-with-best-practices)] | If statement control structures do not comply with best practices | 78 |
| [[NC009](#nc009---unused-file)] | Unused file | 16 |
| [[NC010](#nc010---it-is-best-practice-to-use-linear-inheritance)] | It is best practice to use linear inheritance | 3 |
| [[NC011](#nc011---multiple-addressid-mappings-can-be-combined-into-a-single-mapping-of-an-addressid-to-a-struct-for-readability)] | Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability | 4 |
| [[NC012](#nc012---duplicated-requirerevert-checks-should-be-refactored-to-a-modifier-or-function)] | Duplicated `require()`/`revert()` checks should be refactored to a modifier or function | 1 |
| [[NC013](#nc013---functions-should-have-natspec-param-annotations)] | Functions should have Natspec @param annotations | 19 |
| [[NC014](#nc014---use-a-more-recent-version-of-solidity)] | Use a more recent version of solidity | 2 |
| [[NC015](#nc015---consider-using-delete-rather-than-assigning-falsezero-to-clear-values)] | Consider using delete rather than assigning false/zero to clear values | 1 |
| [[NC016](#nc016---lines-are-too-long)] | Lines are too long | 407 |
| [[NC017](#nc017---function-declarations-should-have-natspec-descriptions)] | Function declarations should have NatSpec descriptions | 1 |
| [[NC018](#nc018---contract-declarations-should-have-notice-tags)] | Contract declarations should have `@notice` tags | 5 |
| [[NC019](#nc019---invalid-natspec-comment-style)] | Invalid NatSpec comment style | 6 |
| [[NC020](#nc020---inconsistent-spacing-in-comments)] | Inconsistent spacing in comments | 4 |
| [[NC021](#nc021---state-variable-declarations-should-have-natspec-dev-annotations)] | State variable declarations should have Natspec @dev annotations | 53 |
| [[NC022](#nc022---functions-should-have-natspec-return-annotations)] | Functions should have Natspec @return annotations | 8 |
| [[NC023](#nc023---not-using-the-named-return-variables-anywhere-in-the-function-is-confusing)] | Not using the named return variables anywhere in the function is confusing | 23 |
| [[NC024](#nc024---non-libraryinterface-files-should-use-fixed-compiler-versions-not-floating-ones)] | Non-library/interface files should use fixed compiler versions, not floating ones | 4 |
| [[NC025](#nc025---contracts-should-have-full-test-coverage)] | Contracts should have full test coverage | 1 |
| [[NC026](#nc026---large-or-complicated-code-bases-should-implement-invariant-tests)] | Large or complicated code bases should implement invariant tests | 1 |
| [[NC027](#nc027---state-variable-declarations-should-have-natspec-notice-annotations)] | State variable declarations should have Natspec @notice annotations | 44 |
| [[NC028](#nc028---consider-using-blocknumber-instead-of-blocktimestamp)] | Consider using `block.number` instead of `block.timestamp` | 3 |
| [[NC029](#nc029---consider-bounding-input-array-length)] | Consider bounding input array length | 15 |
| [[NC030](#nc030---contract-definitions-should-have-natspec-dev-annotations)] | Contract definitions should have Natspec @dev annotations | 2 |
| [[NC031](#nc031---variables-should-be-named-in-mixedcase-style)] | Variables should be named in mixedCase style | 54 |
| [[NC032](#nc032---function-names-should-use-lowercamelcase)] | Function names should use lowerCamelCase | 11 |
| [[NC033](#nc033---consider-adding-a-deny-list)] | Consider adding a deny-list | 4 |
| [[NC034](#nc034---use-a-more-recent-version-of-solidity)] | Use a more recent version of solidity | 1 |
| [[NC035](#nc035---custom-error-has-no-error-details)] | Custom error has no error details | 34 |
| [[NC036](#nc036---modifier-definitions-should-have-natspec-dev-annotations)] | Modifier definitions should have Natspec @dev annotations | 1 |
| [[NC037](#nc037---events-are-missing-sender-information)] | Events are missing sender information | 4 |
| [[NC038](#nc038---enum-values-should-be-used-in-place-of-constant-array-indexes)] | Enum values should be used in place of constant array indexes | 26 |
| [[NC039](#nc039---zero-as-a-function-argument-should-have-a-descriptive-meaning)] | Zero as a function argument should have a descriptive meaning | 88 |
| [[NC040](#nc040---function-names-should-differ-to-make-the-code-more-readable)] | Function names should differ to make the code more readable | 53 |
| [[NC041](#nc041---it-is-standard-for-all-external-and-public-functions-to-be-override-from-an-interface)] | It is standard for all external and public functions to be override from an interface | 67 |
| [[NC042](#nc042---consider-adding-formal-verification-proofs)] | Consider adding formal verification proofs | 1 |
| [[NC043](#nc043---assembly-code-blocks-should-be-thoroughly-commented)] | Assembly code blocks should be thoroughly commented | 30 |
| [[NC044](#nc044---large-multiples-of-ten-should-use-scientific-notation-eg-1e6-rather-than-decimal-literals-eg-1000000-for-readability)] | Large multiples of ten should use scientific notation (e.g. 1e6) rather than decimal literals (e.g. 1000000), for readability | 7 |
| [[NC045](#nc045---polymorphic-functions-make-security-audits-more-time-consuming-and-error-prone)] | Polymorphic functions make security audits more time-consuming and error-prone | 15 |
| [[NC046](#nc046---consider-splitting-long-calculations)] | Consider splitting long calculations | 14 |
| [[NC047](#nc047---high-cyclomatic-complexity)] | High cyclomatic complexity | 7 |
| [[NC048](#nc048---use-of-override-is-unnecessary)] | Use of override is unnecessary | 4 |
| [[NC049](#nc049---non-externalpublic-function-names-should-begin-with-an-underscore)] | Non-`external`/`public` function names should begin with an underscore | 5 |
| [[NC050](#nc050---unused-import)] | Unused import | 1 |
| [[NC051](#nc051---unsafe-conversion-from-unsigned-to-signed-values)] | Unsafe conversion from unsigned to signed values | 72 |
| [[NC052](#nc052---add-inline-comments-for-unnamed-variables)] | Add inline comments for unnamed variables | 2 |
| [[NC053](#nc053---style-guide-state-and-local-variables-should-be-named-using-lowercamelcase)] | Style guide: State and local variables should be named using lowerCamelCase | 715 |
| [[NC054](#nc054---unusual-loop-variable)] | Unusual loop variable | 16 |
| [[NC055](#nc055---use-the-latest-solidity-prior-to-0820-if-on-l2s-for-deployment)] | Use the latest solidity (prior to 0.8.20 if on L2s) for deployment | 20 |
| [[NC056](#nc056---visibility-should-be-set-explicitly-rather-than-defaulting-to-internal)] | Visibility should be set explicitly rather than defaulting to internal | 8 |
| [[NC057](#nc057---use-bit-shifts-in-an-imutable-variable-rather-than-long-bit-masks-of-a-single-bit-for-readability)] | Use bit shifts in an imutable variable rather than long bit masks of a single bit, for readability | 1 |
| [[NC058](#nc058---event-declarations-should-have-natspec-dev-annotations)] | Event declarations should have NatSpec @dev annotations | 11 |
| [[NC059](#nc059---function-definitions-should-have-natspec-dev-annotations)] | Function definitions should have NatSpec @dev annotations | 146 |
| [[NC060](#nc060---function-definitions-should-have-natspec-notice-annotations)] | Function definitions should have NatSpec @notice annotations | 4 |
| [[NC061](#nc061---interface-declarations-should-have-natspec-title-annotations)] | Interface declarations should have NatSpec @title annotations | 1 |
| [[NC062](#nc062---interface-declarations-should-have-natspec-author-annotations)] | Interface declarations should have NatSpec @author annotations | 1 |
| [[NC063](#nc063---interface-declarations-should-have-natspec-notice-annotations)] | Interface declarations should have NatSpec @notice annotations | 2 |
| [[NC064](#nc064---interface-declarations-should-have-natspec-dev-annotations)] | Interface declarations should have NatSpec @dev annotations | 1 |
| [[NC065](#nc065---abstract-contract-declarations-should-have-natspec-notice-annotations)] | Abstract contract declarations should have NatSpec @notice annotations | 2 |
| [[NC066](#nc066---library-declarations-should-have-natspec-title-annotations)] | Library declarations should have Natspec @title annotations | 1 |
| [[NC067](#nc067---library-declarations-should-have-natspec-notice-annotations)] | Library declarations should have Natspec @notice annotations | 1 |
| [[NC068](#nc068---library-declarations-should-have-natspec-dev-annotations)] | Library declarations should have Natspec @dev annotations | 8 |

## NC001 - Empty bytes check is missing:

When developing smart contracts in Solidity, it's crucial to validate the inputs of your functions. This includes ensuring that the bytes parameters are not empty, especially when they represent crucial data such as addresses, identifiers, or raw data that the contract needs to process.Missing empty bytes checks can lead to unexpected behaviour in your contract.For instance, certain operations might fail, produce incorrect results, or consume unnecessary gas when performed with empty bytes.  Moreover, missing input validation can potentially expose your contract to malicious activity, including exploitation of unhandled edge cases.To mitigate these issues, always validate that bytes parameters are not empty when the logic of your contract requires it.


<details>
<summary>Click to show 7 findings</summary>

```solidity
File: contracts/PanopticFactory.sol


172         function uniswapV3MintCallback(
173             uint256 amount0Owed,
174             uint256 amount1Owed,
175             bytes calldata data
176         ) external {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L172:176

```solidity
File: contracts/SemiFungiblePositionManager.sol


402         function uniswapV3MintCallback(
403             uint256 amount0Owed,
404             uint256 amount1Owed,
405             bytes calldata data
406         ) external {


435         function uniswapV3SwapCallback(
436             int256 amount0Delta,
437             int256 amount1Delta,
438             bytes calldata data
439         ) external {


540         function safeTransferFrom(
541             address from,
542             address to,
543             uint256 id,
544             uint256 amount,
545             bytes calldata data
546         ) public override {


566         function safeBatchTransferFrom(
567             address from,
568             address to,
569             uint256[] calldata ids,
570             uint256[] calldata amounts,
571             bytes calldata data
572         ) public override {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566:572

```solidity
File: contracts/tokens/ERC1155Minimal.sol


94          function safeTransferFrom(
95              address from,
96              address to,
97              uint256 id,
98              uint256 amount,
99              bytes calldata data
100         ) public virtual {


130         function safeBatchTransferFrom(
131             address from,
132             address to,
133             uint256[] calldata ids,
134             uint256[] calldata amounts,
135             bytes calldata data
136         ) public virtual {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L130:136

</details>

## NC002 - Defining All External/Public Functions in Contract Interfaces:

It is preferable to have all the external and public function in an interface to make using them easier by developers. This helps ensure the whole API is extracted in a interface.


<details>
<summary>Click to show 16 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


323         function transfer(
324             address recipient,
325             uint256 amount
326         ) public override(ERC20Minimal) returns (bool) {


341         function transferFrom(
342             address from,
343             address to,
344             uint256 amount
345         ) public override(ERC20Minimal) returns (bool) {


370         function totalAssets() public view returns (uint256 totalManagedAssets) {


379         function convertToShares(uint256 assets) public view returns (uint256 shares) {


386         function convertToAssets(uint256 shares) public view returns (uint256 assets) {


399         function previewDeposit(uint256 assets) public view returns (uint256 shares) {


453         function previewMint(uint256 shares) public view returns (uint256 assets) {


507         function maxWithdraw(address owner) public view returns (uint256 maxAssets) {


518         function previewWithdraw(uint256 assets) public view returns (uint256 shares) {


572         function maxRedeem(address owner) public view returns (uint256 maxShares) {


581         function previewRedeem(uint256 shares) public view returns (uint256 assets) {


1141        function getAccountMarginDetails(
1142            address user,
1143            int24 currentTick,
1144            uint256[2][] memory positionBalanceArray,
1145            int128 premiumAllPositions
1146        ) public view returns (LeftRightUnsigned tokenData) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1141:1146

```solidity
File: contracts/PanopticFactory.sol


134         function initialize(address _owner) public {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L134:134

```solidity
File: contracts/PanopticPool.sol


1444        function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1444:1444

```solidity
File: contracts/SemiFungiblePositionManager.sol


540         function safeTransferFrom(
541             address from,
542             address to,
543             uint256 id,
544             uint256 amount,
545             bytes calldata data
546         ) public override {


566         function safeBatchTransferFrom(
567             address from,
568             address to,
569             uint256[] calldata ids,
570             uint256[] calldata amounts,
571             bytes calldata data
572         ) public override {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566:572

</details>

## NC003 - Avoid mutating function parameters:

Function parameters in Solidity are passed by value, meaning they are essentially local copies. Mutating them can lead to confusion and errors because the changes don't persist outside the function. By keeping function parameters immutable, you ensure clarity in code behavior, preventing unintended side-effects. If you need to modify a value based on a parameter, use a local variable inside the function, leaving the original parameter unaltered. By adhering to this practice, you maintain a clear distinction between input data and the internal processing logic, improving code readability and reducing the potential for bugs.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


779                     utilization = -utilization;


1636                poolUtilization =


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1636:1636

```solidity
File: contracts/PanopticFactory.sol


323                     salt = bytes32(uint256(salt) + 1);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L323:323

```solidity
File: contracts/SemiFungiblePositionManager.sol


692                 tokenId = tokenId.flipToBurnToken();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L692:692

</details>


## NC004 - Use a struct to encapsulate multiple function parameters:

Using a struct to encapsulate multiple parameters in Solidity functions can significantly enhance code readability and maintainability. Instead of passing a long list of arguments, which can be error-prone and hard to manage, a struct allows grouping related data into a single, coherent entity. This approach simplifies function signatures and makes the code more organized. It also enhances code clarity, as developers can easily understand the relationship between the parameters. Moreover, it aids in future code modifications and expansions, as adding or modifying a parameter only requires changes in the struct definition, rather than in every function that uses these parameters.


<details>
<summary>Click to show 42 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


178         constructor(
179             uint256 _commissionFee,
180             uint256 _sellerCollateralRatio,
181             uint256 _buyerCollateralRatio,
182             int256 _forceExerciseCost,
183             uint256 _targetPoolUtilization,
184             uint256 _saturatedPoolUtilization,
185             uint256 _ITMSpreadMultiplier
186         ) {


221         function startToken(
222             bool underlyingIsToken0,
223             address token0,
224             address token1,
225             uint24 fee,
226             PanopticPool panopticPool
227         ) external {


650         function exerciseCost(
651             int24 currentTick,
652             int24 oracleTick,
653             TokenId positionId,
654             uint128 positionBalance,
655             LeftRightSigned longAmounts
656         ) external view returns (LeftRightSigned exerciseFees) {


1043        function exercise(
1044            address optionOwner,
1045            int128 longAmount,
1046            int128 shortAmount,
1047            int128 swappedAmount,
1048            int128 realizedPremium
1049        ) external onlyPanopticPool returns (int128) {


1278        function _getRequiredCollateralSingleLeg(
1279            TokenId tokenId,
1280            uint256 index,
1281            uint128 positionSize,
1282            int24 atTick,
1283            uint128 poolUtilization
1284        ) internal view returns (uint256 required) {


1311        function _getRequiredCollateralSingleLegNoPartner(
1312            TokenId tokenId,
1313            uint256 index,
1314            uint128 positionSize,
1315            int24 atTick,
1316            uint128 poolUtilization
1317        ) internal view returns (uint256 required) {


1439        function _getRequiredCollateralSingleLegPartner(
1440            TokenId tokenId,
1441            uint256 index,
1442            uint128 positionSize,
1443            int24 atTick,
1444            uint128 poolUtilization
1445        ) internal view returns (uint256 required) {


1510        function _computeSpread(
1511            TokenId tokenId,
1512            uint128 positionSize,
1513            uint256 index,
1514            uint256 partnerIndex,
1515            uint128 poolUtilization
1516        ) internal view returns (uint256 spreadRequirement) {


1600        function _computeStrangle(
1601            TokenId tokenId,
1602            uint256 index,
1603            uint128 positionSize,
1604            int24 atTick,
1605            uint128 poolUtilization
1606        ) internal view returns (uint256 strangleRequired) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1600:1606

```solidity
File: contracts/PanopticFactory.sol


115         constructor(
116             address _WETH9,
117             SemiFungiblePositionManager _SFPM,
118             IUniswapV3Factory _univ3Factory,
119             IDonorNFT _donorNFT,
120             address _poolReference,
121             address _collateralReference
122         ) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L115:122

```solidity
File: contracts/PanopticPool.sol


291         function startPool(
292             IUniswapV3Pool _univ3pool,
293             address token0,
294             address token1,
295             CollateralTracker collateralTracker0,
296             CollateralTracker collateralTracker1
297         ) external {


429         function _calculateAccumulatedPremia(
430             address user,
431             TokenId[] calldata positionIdList,
432             bool computeAllPremia,
433             bool includePendingPremium,
434             int24 atTick
435         ) internal view returns (LeftRightSigned portfolioPremium, uint256[2][] memory balances) {


547         function mintOptions(
548             TokenId[] calldata positionIdList,
549             uint128 positionSize,
550             uint64 effectiveLiquidityLimitX32,
551             int24 tickLimitLow,
552             int24 tickLimitHigh
553         ) external {


614         function _mintOptions(
615             TokenId[] calldata positionIdList,
616             uint128 positionSize,
617             uint64 effectiveLiquidityLimitX32,
618             int24 tickLimitLow,
619             int24 tickLimitHigh
620         ) internal {


794         function _burnAllOptionsFrom(
795             address owner,
796             int24 tickLimitLow,
797             int24 tickLimitHigh,
798             bool commitLongSettled,
799             TokenId[] calldata positionIdList
800         ) internal returns (LeftRightSigned netPaid, LeftRightSigned[4][] memory premiasByLeg) {


826         function _burnOptions(
827             bool commitLongSettled,
828             TokenId tokenId,
829             address owner,
830             int24 tickLimitLow,
831             int24 tickLimitHigh
832         ) internal returns (LeftRightSigned paidAmounts, LeftRightSigned[4] memory premiaByLeg) {


955         function _burnAndHandleExercise(
956             bool commitLongSettled,
957             int24 tickLimitLow,
958             int24 tickLimitHigh,
959             TokenId tokenId,
960             uint128 positionSize,
961             address owner
962         )
963             internal
964             returns (
965                 LeftRightSigned realizedPremia,
966                 LeftRightSigned[4] memory premiaByLeg,
967                 LeftRightSigned paidAmounts
968             )
969         {


1290        function _checkSolvencyAtTick(
1291            address account,
1292            TokenId[] calldata positionIdList,
1293            int24 currentTick,
1294            int24 atTick,
1295            uint256 buffer
1296        ) internal view returns (bool) {


1465        function _checkLiquiditySpread(
1466            TokenId tokenId,
1467            uint256 leg,
1468            int24 tickLower,
1469            int24 tickUpper,
1470            uint64 effectiveLiquidityLimitX32
1471        ) internal view {


1503        function _getPremia(
1504            TokenId tokenId,
1505            uint128 positionSize,
1506            address owner,
1507            bool computeAllPremia,
1508            int24 atTick
1509        )
1510            internal
1511            view
1512            returns (
1513                LeftRightSigned[4] memory premiaByLeg,
1514                uint256[2][4] memory premiumAccumulatorsByLeg
1515            )
1516        {


1757        function _getAvailablePremium(
1758            uint256 totalLiquidity,
1759            LeftRightUnsigned settledTokens,
1760            LeftRightUnsigned grossPremiumLast,
1761            LeftRightUnsigned premiumOwed,
1762            uint256[2] memory premiumAccumulators
1763        ) internal pure returns (LeftRightUnsigned) {


1833        function _updateSettlementPostBurn(
1834            address owner,
1835            TokenId tokenId,
1836            LeftRightUnsigned[4] memory collectedByLeg,
1837            uint128 positionSize,
1838            bool commitLongSettled
1839        ) internal returns (LeftRightSigned realizedPremia, LeftRightSigned[4] memory premiaByLeg) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1833:1839

```solidity
File: contracts/SemiFungiblePositionManager.sol


540         function safeTransferFrom(
541             address from,
542             address to,
543             uint256 id,
544             uint256 amount,
545             bytes calldata data
546         ) public override {


566         function safeBatchTransferFrom(
567             address from,
568             address to,
569             uint256[] calldata ids,
570             uint256[] calldata amounts,
571             bytes calldata data
572         ) public override {


680         function _validateAndForwardToAMM(
681             TokenId tokenId,
682             uint128 positionSize,
683             int24 tickLimitLow,
684             int24 tickLimitHigh,
685             bool isBurn
686         ) internal returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalMoved) {


958         function _createLegInAMM(
959             IUniswapV3Pool univ3pool,
960             TokenId tokenId,
961             uint256 leg,
962             LiquidityChunk liquidityChunk,
963             bool isBurn
964         )
965             internal
966             returns (
967                 LeftRightSigned moved,
968                 LeftRightSigned itmAmounts,
969                 LeftRightUnsigned collectedSingleLeg
970             )
971         {


1255        function _collectAndWritePositionData(
1256            LiquidityChunk liquidityChunk,
1257            IUniswapV3Pool univ3pool,
1258            LeftRightUnsigned currentLiquidity,
1259            bytes32 positionKey,
1260            LeftRightSigned movedInLeg,
1261            uint256 isLong
1262        ) internal returns (LeftRightUnsigned collectedChunk) {


1421        function getAccountLiquidity(
1422            address univ3pool,
1423            address owner,
1424            uint256 tokenType,
1425            int24 tickLower,
1426            int24 tickUpper
1427        ) external view returns (LeftRightUnsigned accountLiquidities) {


1449        function getAccountPremium(
1450            address univ3pool,
1451            address owner,
1452            uint256 tokenType,
1453            int24 tickLower,
1454            int24 tickUpper,
1455            int24 atTick,
1456            uint256 isLong
1457        ) external view returns (uint128, uint128) {


1535        function getAccountFeesBase(
1536            address univ3pool,
1537            address owner,
1538            uint256 tokenType,
1539            int24 tickLower,
1540            int24 tickUpper
1541        ) external view returns (int128 feesBase0, int128 feesBase1) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1535:1541

```solidity
File: contracts/libraries/FeesCalc.sol


97          function calculateAMMSwapFees(
98              IUniswapV3Pool univ3pool,
99              int24 currentTick,
100             int24 tickLower,
101             int24 tickUpper,
102             uint128 liquidity
103         ) public view returns (LeftRightSigned) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L97:103

```solidity
File: contracts/libraries/InteractionHelper.sol


24          function doApprovals(
25              SemiFungiblePositionManager sfpm,
26              CollateralTracker ct0,
27              CollateralTracker ct1,
28              address token0,
29              address token1
30          ) external {


48          function computeName(
49              address token0,
50              address token1,
51              bool isToken0,
52              uint24 fee,
53              string memory prefix
54          ) external view returns (string memory) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L48:54

```solidity
File: contracts/libraries/PanopticMath.sol


125         function computeMedianObservedPrice(
126             IUniswapV3Pool univ3pool,
127             uint256 observationIndex,
128             uint256 observationCardinality,
129             uint256 cardinality,
130             uint256 period
131         ) external view returns (int24) {


168         function computeInternalMedian(
169             uint256 observationIndex,
170             uint256 observationCardinality,
171             uint256 period,
172             uint256 medianData,
173             IUniswapV3Pool univ3pool
174         ) external view returns (int24 medianTick, uint256 updatedMedianData) {


651         function getLiquidationBonus(
652             LeftRightUnsigned tokenData0,
653             LeftRightUnsigned tokenData1,
654             uint160 sqrtPriceX96Twap,
655             uint160 sqrtPriceX96Final,
656             LeftRightSigned netExchanged,
657             LeftRightSigned premia
658         ) external pure returns (int256 bonus0, int256 bonus1, LeftRightSigned) {


768         function haircutPremia(
769             address liquidatee,
770             TokenId[] memory positionIdList,
771             LeftRightSigned[4][] memory premiasByLeg,
772             LeftRightSigned collateralRemaining,
773             CollateralTracker collateral0,
774             CollateralTracker collateral1,
775             uint160 sqrtPriceX96Final,
776             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777         ) external returns (int256, int256) {


917         function getRefundAmounts(
918             address refunder,
919             LeftRightSigned refundValues,
920             int24 atTick,
921             CollateralTracker collateral0,
922             CollateralTracker collateral1
923         ) external view returns (LeftRightSigned) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L917:923

```solidity
File: contracts/tokens/ERC1155Minimal.sol


94          function safeTransferFrom(
95              address from,
96              address to,
97              uint256 id,
98              uint256 amount,
99              bytes calldata data
100         ) public virtual {


130         function safeBatchTransferFrom(
131             address from,
132             address to,
133             uint256[] calldata ids,
134             uint256[] calldata amounts,
135             bytes calldata data
136         ) public virtual {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L130:136

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


13          function issueNFT(
14              address deployer,
15              PanopticPool newPoolContract,
16              address token0,
17              address token1,
18              uint24 fee


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L13:18

```solidity
File: contracts/types/TokenId.sol


336         function addLeg(
337             TokenId self,
338             uint256 legIndex,
339             uint256 _optionRatio,
340             uint256 _asset,
341             uint256 _isLong,
342             uint256 _tokenType,
343             uint256 _riskPartner,
344             int24 _strike,
345             int24 _width
346         ) internal pure returns (TokenId tokenId) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L336:346

</details>


## NC005 - Constants in comparisons should appear on the left side:

This issue arises when constants in comparisons appear on the right side, which can lead to typo bugs.


<details>
<summary>Click to show 163 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


331             if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();


350             if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();


512             return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;


575             return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;


664                     if (positionId.isLong(leg) == 0) continue;


708                         (tokenType == 0 && currentValue1 < oracleValue1) ||


709                         (tokenType == 1 && currentValue0 < oracleValue0)


776             if (utilization < 0) {


976             if (assets > 0) {


1010                if (tokenToPay > 0) {


1018                } else if (tokenToPay < 0) {


1060                if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {


1067                if (tokenToPay > 0) {


1075                } else if (tokenToPay < 0) {


1107                if (intrinsicValue != 0) {


1168            if (positionBalanceArray.length > 0) {


1173                if (premiumAllPositions < 0) {


1182            if (premiumAllPositions > 0) {


1325            uint128 amountMoved = tokenType == 0 ? amountsMoved.rightSlot() : amountsMoved.leftSlot();


1328            int64 utilization = tokenType == 0


1339                if (isLong == 0) {


1346                        ((atTick >= tickUpper) && (tokenType == 1)) || // strike OTM when price >= upperTick for tokenType=1


1347                        ((atTick < tickLower) && (tokenType == 0)) // strike OTM when price < lowerTick for tokenType=0


1362                        uint160 ratio = tokenType == 1 // tokenType


1374                            ((atTick < tickLower) && (tokenType == 1)) || // strike ITM but out of range price < lowerTick for tokenType=1


1375                            ((atTick >= tickUpper) && (tokenType == 0)) // strike ITM but out of range when price >= upperTick for tokenType=0


1451                if (isLong == 1) {


1479            if (isLong == 0) {


1488            } else if (isLong == 1) {


1544                    if (tokenType == 0) {


1559                    if (tokenType == 1) {


1582                    tokenType == 0 ? movedRight : movedLeft,


1584                    tokenType == 0


1637                    uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +


1638                    (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1638:1638

```solidity
File: contracts/PanopticFactory.sol


181             if (amount0Owed > 0)


188             if (amount1Owed > 0)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L188:188

```solidity
File: contracts/PanopticPool.sol


460                     if (tokenId.isLong(leg) == 0 && !includePendingPremium) {


533             if (medianData != 0) s_miniMedian = medianData;


638             if (LeftRightUnsigned.unwrap(s_positionBalance[msg.sender][tokenId]) != 0)


664             if (medianData != 0) s_miniMedian = medianData;


768                 if (isLong == 1) {


865                 if (tokenId.isLong(leg) == 0) {


1188            if (touchedId.length != 1) revert Errors.InputListFail();


1274            if (positionIdListExercisor.length > 0)


1483            if (netLiquidity == 0) return;


1520                if ((isLong == 1) || computeAllPremia) {


1566                        if (isLong == 1) {


1596            if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();


1679                if (tokenId.isLong(leg) == 0) {


1780                                        (accumulated0 == 0 ? type(uint256).max : accumulated0),


1789                                        (accumulated1 == 0 ? type(uint256).max : accumulated1),


1862                if (LeftRightSigned.unwrap(legPremia) != 0) {


1864                    if (tokenId.isLong(leg) == 1) {


1928                            s_grossPremiumLast[chunkKey] = totalLiquidity != 0


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1928:1928

```solidity
File: contracts/SemiFungiblePositionManager.sol


362             if (s_AddrToPoolIdData[univ3pool] != 0) return;


412             if (amount0Owed > 0)


419             if (amount1Owed > 0)


446             address token = amount0Delta > 0


453             uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);


632                     (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||


633                     (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)


688             if (positionSize == 0) revert Errors.OptionsBalanceZero();


717                 if ((LeftRightSigned.unwrap(itmAmounts) != 0)) {


787                 if ((itm0 != 0) && (itm1 != 0)) {


819                     zeroForOne = net0 < 0;


823                 } else if (itm0 != 0) {


824                     zeroForOne = itm0 < 0;


827                     zeroForOne = itm1 > 0;


833                 if (swapAmount == 0) return LeftRightSigned.wrap(0);


999                 if (isLong == 0) {


1066                moved = isLong == 0


1073                if (tokenType == 1) {


1078                if (tokenType == 0) {


1085            if (currentLiquidity.rightSlot() > 0) {


1275            if (isLong == 1) {


1279            if (LeftRightSigned.unwrap(amountToCollect) != 0) {


1296                    collected0 = movedInLeg.rightSlot() < 0


1299                    collected1 = movedInLeg.leftSlot() < 0


1469                if (netLiquidity != 0) {


1514                    acctPremia = isLong == 1 ? premiumOwed : premiumGross;


1518                acctPremia = isLong == 1


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1518:1518

```solidity
File: contracts/libraries/FeesCalc.sol


67                      if (tokenId.isLong(leg) == 0) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L67:67

```solidity
File: contracts/libraries/Math.sol


74              return x > 0 ? x : -x;


83                  return x > 0 ? uint256(x) : uint256(-x);


93                  if (x >= 0x100000000000000000000000000000000) {


97                  if (x >= 0x10000000000000000) {


101                 if (x >= 0x100000000) {


105                 if (x >= 0x10000) {


109                 if (x >= 0x100) {


113                 if (x >= 0x10) {


130                 uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));


133                 uint256 sqrtR = absTick & 0x1 != 0


137                 if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;


139                 if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;


141                 if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;


143                 if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;


145                 if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;


147                 if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;


149                 if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;


151                 if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;


153                 if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;


155                 if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;


157                 if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;


159                 if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;


161                 if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;


163                 if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;


165                 if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;


167                 if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;


169                 if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;


171                 if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;


173                 if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;


176                 if (tick > 0) sqrtR = type(uint256).max / sqrtR;


179                 return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));


312             if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();


360                 if (prod1 == 0) {


361                     require(denominator > 0);


447                 if (mulmod(a, b, denominator) > 0) {


474                 if (prod1 == 0) {


537                 if (prod1 == 0) {


587                 if (mulmod(a, b, 2 ** 96) > 0) {


614                 if (prod1 == 0) {


664                 if (mulmod(a, b, 2 ** 128) > 0) {


691                 if (prod1 == 0) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L691:691

```solidity
File: contracts/libraries/PanopticMath.sol


207                     for (uint8 i; i < 8; ++i) {


211                         if (rank == 7) {


248                 for (uint256 i = 0; i < 20; ++i) {


256                 for (uint256 i = 0; i < 19; ++i) {


325             if (tokenId.asset(legIndex) == 0) {


357                     tickLower % tickSpacing != 0 ||


358                     tickUpper % tickSpacing != 0 ||


425             if (tokenType == 0) {


475                 uint256 notional = asset == 0


479                 if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();


532                     return amount < 0 ? -absResult : absResult;


537                     return amount < 0 ? -absResult : absResult;


555                     return amount < 0 ? -absResult : absResult;


564                     return amount < 0 ? -absResult : absResult;


584             if (tokenId.asset(legIndex) == 0) {


615             bool isShort = tokenId.isLong(legIndex) == 0;


618             if (tokenId.tokenType(legIndex) == 0) {


785                         if (tokenId.isLong(leg) == 1) {


856                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));


857                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));


864                         if (tokenId.isLong(leg) == 1) {


931                 if (balanceShortage > 0) {


949                 if (balanceShortage > 0) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L949:949

```solidity
File: contracts/tokens/ERC1155Minimal.sol


112             if (to.code.length != 0) {


163             if (to.code.length != 0) {


202                 interfaceId == 0x01ffc9a7 || // ERC165 Interface ID for ERC165


203                 interfaceId == 0xd9b67a26; // ERC165 Interface ID for ERC1155


222             if (to.code.length != 0) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L222:222

```solidity
File: contracts/types/TokenId.sol


465             if (i == 0)


471             if (i == 1)


477             if (i == 2)


483             if (i == 3)


501             if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);


507                 for (uint256 i = 0; i < 4; ++i) {


508                     if (self.optionRatio(i) == 0) {


512                         if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)


528                     if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);


566                         if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))


592                         if (self.isLong(i) == 1) return; // validated


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L592:592

</details>

## NC006 - else-block not required:

One level of nesting can be removed by not having an else block when the if-block returns


<details>
<summary>Click to show 9 findings</summary>

```solidity
File: contracts/libraries/PanopticMath.sol


325             if (tokenId.asset(legIndex) == 0) {
326                 return Math.getLiquidityForAmount0(tickLower, tickUpper, amount);
327             } else {
328                 return Math.getLiquidityForAmount1(tickLower, tickUpper, amount);
329             }


425             if (tokenType == 0) {
426                 return (
427                     tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
428                     tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
429                 );
430             } else {
431                 return (
432                     tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
433                     tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
434                 );
435             }


494                 if (sqrtPriceX96 < type(uint128).max) {
495                     return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
496                 } else {
497                     return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
498                 }


511                 if (sqrtPriceX96 < type(uint128).max) {
512                     return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
513                 } else {
514                     return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
515                 }


528                 if (sqrtPriceX96 < type(uint128).max) {
529                     int256 absResult = Math
530                         .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
531                         .toInt256();
532                     return amount < 0 ? -absResult : absResult;
533                 } else {
534                     int256 absResult = Math
535                         .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
536                         .toInt256();
537                     return amount < 0 ? -absResult : absResult;
538                 }


551                 if (sqrtPriceX96 < type(uint128).max) {
552                     int256 absResult = Math
553                         .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
554                         .toInt256();
555                     return amount < 0 ? -absResult : absResult;
556                 } else {
557                     int256 absResult = Math
558                         .mulDiv(
559                             Math.absUint(amount),
560                             2 ** 128,
561                             Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
562                         )
563                         .toInt256();
564                     return amount < 0 ? -absResult : absResult;
565                 }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L551:565

```solidity
File: contracts/types/TokenId.sol


439             if (optionRatios < 2 ** 64) {
440                 return 0;
441             } else if (optionRatios < 2 ** 112) {
442                 return 1;
443             } else if (optionRatios < 2 ** 160) {
444                 return 2;
445             } else if (optionRatios < 2 ** 208) {
446                 return 3;
447             }


441             } else if (optionRatios < 2 ** 112) {
442                 return 1;
443             } else if (optionRatios < 2 ** 160) {
444                 return 2;
445             } else if (optionRatios < 2 ** 208) {
446                 return 3;
447             }


443             } else if (optionRatios < 2 ** 160) {
444                 return 2;
445             } else if (optionRatios < 2 ** 208) {
446                 return 3;
447             }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L443:447

</details>

## NC007 - Events may be emitted out of order due to reentrancy:

Ensure that events follow the best practice of check-effects-interaction, and are emitted before external calls


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


/// @audit safeTransferFrom() called before event
563             emit Withdraw(msg.sender, receiver, owner, assets, shares);


/// @audit safeTransferFrom() called before event
499             emit Deposit(msg.sender, receiver, assets, shares);


/// @audit safeTransferFrom() called before event
439             emit Deposit(msg.sender, receiver, assets, shares);


/// @audit safeTransferFrom() called before event
623             emit Withdraw(msg.sender, receiver, owner, assets, shares);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L623:623

</details>

## NC008 - If statement control structures do not comply with best practices:

If statements which include a single line do not need to have curly brackets, however according to the Solidiity style guide the line of code executed upon the if statement condition being met should still be on the next line, not on the same line as the if statement declaration.


<details>
<summary>Click to show 78 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


170             if (msg.sender != address(s_panopticPool)) revert Errors.NotPanopticPool();


229             if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();


331             if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();


350             if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();


418             if (assets > type(uint104).max) revert Errors.DepositTooLarge();


480             if (assets > type(uint104).max) revert Errors.DepositTooLarge();


536             if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();


544                 if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;


596             if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();


602                 if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;


664                     if (positionId.isLong(leg) == 0) continue;


1257                    if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1257:1257

```solidity
File: contracts/PanopticFactory.sol


150             if (msg.sender != currentOwner) revert Errors.NotOwner();


220             if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();


224             if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();


227             if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L227:227

```solidity
File: contracts/PanopticPool.sol


299             if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();


533             if (medianData != 0) s_miniMedian = medianData;


664             if (medianData != 0) s_miniMedian = medianData;


940             if (!solventAtFast) revert Errors.NotEnoughCollateral();


1066                if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();


1188            if (touchedId.length != 1) revert Errors.InputListFail();


1394            if (fingerprintIncomingList != currentHash) revert Errors.InputListFail();


1415            if ((newHash >> 248) > MAX_POSITIONS) revert Errors.TooManyPositionsOpen();


1483            if (netLiquidity == 0) return;


1596            if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1596:1596

```solidity
File: contracts/SemiFungiblePositionManager.sol


322             if (s_poolContext[poolId].locked) revert Errors.ReentrantCall();


355             if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();


362             if (s_AddrToPoolIdData[univ3pool] != 0) return;


549             if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();


576                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();


688             if (positionSize == 0) revert Errors.OptionsBalanceZero();


702             if (univ3pool == IUniswapV3Pool(address(0))) revert Errors.UniswapPoolNotInitialized();


833                 if (swapAmount == 0) return LeftRightSigned.wrap(0);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L833:833

```solidity
File: contracts/libraries/Math.sol


131                 if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();


137                 if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;


139                 if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;


141                 if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;


143                 if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;


145                 if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;


147                 if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;


149                 if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;


151                 if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;


153                 if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;


155                 if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;


157                 if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;


159                 if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;


161                 if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;


163                 if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;


165                 if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;


167                 if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;


169                 if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;


171                 if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;


173                 if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;


176                 if (tick > 0) sqrtR = type(uint256).max / sqrtR;


297             if ((downcastedInt = uint128(toDowncast)) != toDowncast) revert Errors.CastingError();


312             if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();


319             if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();


326             if (toCast > uint256(type(int256).max)) revert Errors.CastingError();


757                 if (i == j) return;


768                 if (left < j) quickSort(arr, left, j);


769                 if (i < right) quickSort(arr, i, right);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L769:769

```solidity
File: contracts/libraries/PanopticMath.sol


479                 if (notional == 0 || notional > type(uint128).max) revert Errors.InvalidNotionalValue();


856                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));


857                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L857:857

```solidity
File: contracts/libraries/SafeTransferLib.sol


45              if (!success) revert Errors.TransferFailed();


75              if (!success) revert Errors.TransferFailed();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L75:75

```solidity
File: contracts/tokens/ERC1155Minimal.sol


101             if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();


137             if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L137:137

```solidity
File: contracts/tokens/ERC20Minimal.sol


84              if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L84:84

```solidity
File: contracts/types/LeftRight.sol


199                 if (left128 != left) revert Errors.UnderOverFlow();


204                 if (right128 != right) revert Errors.UnderOverFlow();


222                 if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();


240                 if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();


262                 if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L262:262

```solidity
File: contracts/types/TokenId.sol


501             if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);


528                     if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);


592                         if (self.isLong(i) == 1) return; // validated


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L592:592

</details>

## NC009 - Unused file:

The file is never imported by any other source file. If the file is needed for tests, it should be moved to a test directory


<details>
<summary>Click to show 16 findings</summary>

```solidity
File: contracts/libraries/CallbackLib.sol


/// @auditbase `albahca/contracts/libraries/CallbackLib.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L1:1

```solidity
File: contracts/libraries/Constants.sol


/// @auditbase `albahca/contracts/libraries/Constants.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L1:1

```solidity
File: contracts/libraries/Errors.sol


/// @auditbase `albahca/contracts/libraries/Errors.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol#L1:1

```solidity
File: contracts/libraries/FeesCalc.sol


/// @auditbase `albahca/contracts/libraries/FeesCalc.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L1:1

```solidity
File: contracts/libraries/InteractionHelper.sol


/// @auditbase `albahca/contracts/libraries/InteractionHelper.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L1:1

```solidity
File: contracts/libraries/Math.sol


/// @auditbase `albahca/contracts/libraries/Math.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L1:1

```solidity
File: contracts/libraries/PanopticMath.sol


/// @auditbase `albahca/contracts/libraries/PanopticMath.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L1:1

```solidity
File: contracts/libraries/SafeTransferLib.sol


/// @auditbase `albahca/contracts/libraries/SafeTransferLib.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L1:1

```solidity
File: contracts/multicall/Multicall.sol


/// @auditbase `albahca/contracts/multicall/Multicall.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L1:1

```solidity
File: contracts/tokens/ERC1155Minimal.sol


/// @auditbase `albahca/contracts/tokens/ERC1155Minimal.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L1:1

```solidity
File: contracts/tokens/ERC20Minimal.sol


/// @auditbase `albahca/contracts/tokens/ERC20Minimal.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L1:1

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


/// @auditbase `albahca/contracts/tokens/interfaces/IDonorNFT.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L1:1

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol


/// @auditbase `albahca/contracts/tokens/interfaces/IERC20Partial.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L1:1

```solidity
File: contracts/types/LeftRight.sol


/// @auditbase `albahca/contracts/types/LeftRight.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L1:1

```solidity
File: contracts/types/LiquidityChunk.sol


/// @auditbase `albahca/contracts/types/LiquidityChunk.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L1:1

```solidity
File: contracts/types/TokenId.sol


/// @auditbase `albahca/contracts/types/TokenId.sol` not used in any contracts


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L1:1

</details>

## NC010 - It is best practice to use linear inheritance:

In Solidity, complex inheritance structures can obfuscate code understanding, introducing potential security risks. Multiple inheritance, especially with overlapping function names or state variables, can cause unintentional overrides or ambiguous behavior. Resolution: Strive for linear and simple inheritance chains. Avoid diamond or circular inheritance patterns. Clearly document the purpose and relationships of base contracts, ensuring that overrides are intentional. Tools like Remix or Hardhat can visualize inheritance chains, assisting in verification. Keeping inheritance streamlined aids in better code readability, reduces potential errors, and ensures smoother audits and upgrades.


```solidity
File: contracts/CollateralTracker.sol


36      contract CollateralTracker is ERC20Minimal, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L36:36

```solidity
File: contracts/PanopticPool.sol


27      contract PanopticPool is ERC1155Holder, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L27:27

```solidity
File: contracts/SemiFungiblePositionManager.sol


72      contract SemiFungiblePositionManager is ERC1155, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L72:72




## NC011 - Multiple `address`/ID mappings can be combined into a single `mapping` of an `address`/ID to a `struct`, for readability:

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/PanopticPool.sol


245         mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;
246     
247         /// @dev per-chunk accumulator for tokens owed to sellers that have been settled and are now available
248         /// This number increases when buyers pay long premium and when tokens are collected from Uniswap
249         /// It decreases when sellers close positions and collect the premium they are owed
250         /// LeftRight - right slot is token0, left slot is token1
251         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L245:251

```solidity
File: contracts/SemiFungiblePositionManager.sol


177         mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
178             internal s_accountLiquidity;
179     
180         /**
181             Any liquidity that has been deposited in the AMM using the SFPM will collect fees over 
182             time, we call this the gross premia. If that liquidity has been removed, we also need to
183             keep track of the amount of fees that *would have been collected*, we call this the owed
184             premia. The gross and owed premia are tracked per unit of liquidity by the 
185             s_accountPremiumGross and s_accountPremiumOwed accumulators.
186             
187             Here is how we can use the accumulators to compute the Gross, Net, and Owed fees collected
188             by any position.
189     
190             Let`s say Charlie the smart contract deposited T into the AMM and later removed R from that
191             same tick using a tokenId with a isLong=1 parameter. Because the netLiquidity is only (T-R),
192             the AMM will collect fees equal to:
193     
194                   net_feesCollectedX128 = feeGrowthX128 * (T - R)
195                                         = feeGrowthX128 * N                                     
196             
197             where N = netLiquidity = T-R. Had that liquidity never been removed, we want the gross
198             premia to be given by:
199     
200                   gross_feesCollectedX128 = feeGrowthX128 * T
201     
202             So we must keep track of fees for the removed liquidity R so that the long premia exactly
203             compensates for the fees that would have been collected from the initial liquidity.
204     
205             In addition to tracking, we also want to track those fees plus a small spread. Specifically,
206             we want:
207     
208                   gross_feesCollectedX128 = net_feesCollectedX128 + owed_feesCollectedX128
209     
210            where 
211     
212                   owed_feesCollectedX128 = feeGrowthX128 * R * (1 + spread)                      (Eqn 1)
213     
214             A very opinionated definition for the spread is: 
215                   
216                   spread = ν*(liquidity removed from that strike)/(netLiquidity remaining at that strike)
217                          = ν*R/N
218     
219             For an arbitrary parameter 0 <= ν <= 1 (ν = 1/2^VEGOID). This way, the gross_feesCollectedX128 will be given by: 
220     
221                   gross_feesCollectedX128 = feeGrowthX128 * N + feeGrowthX128*R*(1 + ν*R/N) 
222                                           = feeGrowthX128 * T + feesGrowthX128*ν*R^2/N         
223                                           = feeGrowthX128 * T * (1 + ν*R^2/(N*T))                (Eqn 2)
224             
225             The s_accountPremiumOwed accumulator tracks the feeGrowthX128 * R * (1 + spread) term
226             per unit of removed liquidity R every time the position touched:
227     
228                   s_accountPremiumOwed += feeGrowthX128 * R * (1 + ν*R/N) / R
229                                        += feeGrowthX128 * (T - R + ν*R)/N
230                                        += feeGrowthX128 * T/N * (1 - R/T + ν*R/T)
231              
232             Note that the value of feeGrowthX128 can be extracted from the amount of fees collected by
233             the smart contract since the amount of feesCollected is related to feeGrowthX128 according
234             to:
235     
236                  feesCollected = feesGrowthX128 * (T-R)
237     
238             So that we get:
239                  
240                  feesGrowthX128 = feesCollected/N
241     
242             And the accumulator is computed from the amount of collected fees according to:
243                  
244                  s_accountPremiumOwed += feesCollected * T/N^2 * (1 - R/T + ν*R/T)          (Eqn 3)     
245     
246             So, the amount of owed premia for a position of size r minted at time t1 and burnt at 
247             time t2 is:
248     
249                  owedPremia(t1, t2) = (s_accountPremiumOwed_t2-s_accountPremiumOwed_t1) * r
250                                     = ∆feesGrowthX128 * r * T/N * (1 - R/T + ν*R/T)
251                                     = ∆feesGrowthX128 * r * (T - R + ν*R)/N
252                                     = ∆feesGrowthX128 * r * (N + ν*R)/N
253                                     = ∆feesGrowthX128 * r * (1 + ν*R/N)             (same as Eqn 1)
254     
255             This way, the amount of premia owed for a position will match Eqn 1 exactly.
256     
257             Similarly, the amount of gross fees for the total liquidity is tracked in a similar manner
258             by the s_accountPremiumGross accumulator. 
259     
260             However, since we require that Eqn 2 holds up-- ie. the gross fees collected should be equal
261             to the net fees collected plus the ower fees plus the small spread, the expression for the
262             s_accountPremiumGross accumulator has to be given by (you`ll see why in a minute): 
263     
264                 s_accountPremiumGross += feesCollected * T/N^2 * (1 - R/T + ν*R^2/T^2)       (Eqn 4) 
265     
266             This expression can be used to calculate the fees collected by a position of size t between times
267             t1 and t2 according to:
268                  
269                 grossPremia(t1, t2) = ∆(s_accountPremiumGross) * t
270                                     = ∆feeGrowthX128 * t * T/N * (1 - R/T + ν*R^2/T^2) 
271                                     = ∆feeGrowthX128 * t * (T - R + ν*R^2/T) / N 
272                                     = ∆feeGrowthX128 * t * (N + ν*R^2/T) / N
273                                     = ∆feeGrowthX128 * t * (1  + ν*R^2/(N*T))   (same as Eqn 2)
274                 
275             where the last expression matches Eqn 2 exactly.
276     
277             In summary, the s_accountPremium accumulators allow smart contracts that need to handle 
278             long+short liquidity to guarantee that liquidity deposited always receives the correct
279             premia, whether that liquidity has been removed from the AMM or not.
280     
281             Note that the expression for the spread is extremely opinionated, and may not fit the
282             specific risk management profile of every smart contract. And simply setting the ν parameter
283             to zero would get rid of the "spread logic".
284         */
285     
286         // tracking account premia for the added liquidity (isLong=0 legs) and removed liquidity (isLong=1 legs) separately
287         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;
288     
289         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;
290     
291         /// @dev mapping that stores a LeftRight packing of feesBase of  keccak256(abi.encodePacked(address poolAddress, address owner, int24 tickLower, int24 tickUpper))
292         /// @dev Base fees is stored as int128((feeGrowthInside0LastX128 * liquidity) / 2**128), which allows us to store the accumulated fees as int128 instead of uint256
293         /// @dev Right slot: int128 token0 base fees, Left slot: int128 token1 base fees.
294         /// feesBase represents the baseline fees collected by the position last time it was updated - this is recalculated every time the position is collected from with the new value
295         mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L177:295

```solidity
File: contracts/libraries/PanopticMath.sol


776             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777         ) external returns (int256, int256) {
778             unchecked {
779                 // get the amount of premium paid by the liquidatee
780                 LeftRightSigned longPremium;
781                 for (uint256 i = 0; i < positionIdList.length; ++i) {
782                     TokenId tokenId = positionIdList[i];
783                     uint256 numLegs = tokenId.countLegs();
784                     for (uint256 leg = 0; leg < numLegs; ++leg) {
785                         if (tokenId.isLong(leg) == 1) {
786                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
787                         }
788                     }
789                 }
790                 // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token
791                 int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);
792                 int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);
793                 int256 haircut0;
794                 int256 haircut1;
795                 // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,
796                 // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token
797                 if (
798                     longPremium.rightSlot() < collateralDelta0 &&
799                     longPremium.leftSlot() > collateralDelta1
800                 ) {
801                     int256 protocolLoss1 = collateralDelta1;
802                     (collateralDelta0, collateralDelta1) = (
803                         -Math.min(
804                             collateralDelta0 - longPremium.rightSlot(),
805                             PanopticMath.convert1to0(
806                                 longPremium.leftSlot() - collateralDelta1,
807                                 sqrtPriceX96Final
808                             )
809                         ),
810                         Math.min(
811                             longPremium.leftSlot() - collateralDelta1,
812                             PanopticMath.convert0to1(
813                                 collateralDelta0 - longPremium.rightSlot(),
814                                 sqrtPriceX96Final
815                             )
816                         )
817                     );
818     
819                     haircut0 = longPremium.rightSlot();
820                     haircut1 = protocolLoss1 + collateralDelta1;
821                 } else if (
822                     longPremium.leftSlot() < collateralDelta1 &&
823                     longPremium.rightSlot() > collateralDelta0
824                 ) {
825                     int256 protocolLoss0 = collateralDelta0;
826                     (collateralDelta0, collateralDelta1) = (
827                         Math.min(
828                             longPremium.rightSlot() - collateralDelta0,
829                             PanopticMath.convert1to0(
830                                 collateralDelta1 - longPremium.leftSlot(),
831                                 sqrtPriceX96Final
832                             )
833                         ),
834                         -Math.min(
835                             collateralDelta1 - longPremium.leftSlot(),
836                             PanopticMath.convert0to1(
837                                 longPremium.rightSlot() - collateralDelta0,
838                                 sqrtPriceX96Final
839                             )
840                         )
841                     );
842     
843                     haircut0 = collateralDelta0 + protocolLoss0;
844                     haircut1 = longPremium.leftSlot();
845                 } else {
846                     // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
847                     haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
848                     haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
849     
850                     collateralDelta0 = 0;
851                     collateralDelta1 = 0;
852                 }
853     
854                 {
855                     address _liquidatee = liquidatee;
856                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
857                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
858                 }
859     
860                 for (uint256 i = 0; i < positionIdList.length; i++) {
861                     TokenId tokenId = positionIdList[i];
862                     LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
863                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864                         if (tokenId.isLong(leg) == 1) {
865                             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L776:865

```solidity
File: contracts/tokens/ERC20Minimal.sol


35          mapping(address account => uint256 balance) public balanceOf;
36      
37          /// @notice Stored allowances for each user.
38          /// @dev Indexed by owner, then by spender.
39          mapping(address owner => mapping(address spender => uint256 allowance)) public allowance;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L35:39

</details>

## NC012 - Duplicated `require()`/`revert()` checks should be refactored to a modifier or function:

The compiler will inline the function, which will avoid JUMP instructions usually associated with functions.


```solidity
File: contracts/libraries/Math.sol


448                     require(result < type(uint256).max);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L448:448


## NC013 - Functions should have Natspec @param annotations:

Documents a parameter just like in Doxygen (must be followed by parameter name)

Note: these are instance missed from bots
<details>
<summary>Click to show 19 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


178         constructor(


277         function getPoolData()


289         function name() external view returns (string memory) {


303         function symbol() external view returns (string memory) {


310         function decimals() external view returns (uint8) {


323         function transfer(


341         function transferFrom(


361         function asset() external view returns (address assetTokenAddress) {


370         function totalAssets() public view returns (uint256 totalManagedAssets) {


392         function maxDeposit(address) external pure returns (uint256 maxAssets) {


444         function maxMint(address) external view returns (uint256 maxShares) {


741         function _poolUtilization() internal view returns (int256 poolUtilization) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L741:741

```solidity
File: contracts/PanopticFactory.sol


159         function owner() external view returns (address) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L159:159

```solidity
File: contracts/PanopticPool.sol


522         function pokeMedian() external {


1425        function univ3pool() external view returns (IUniswapV3Pool) {


1431        function collateralToken0() external view returns (CollateralTracker collateralToken) {


1437        function collateralToken1() external view returns (CollateralTracker) {


1450        function getUniV3TWAP() internal view returns (int24 twapTick) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1450:1450

```solidity
File: contracts/libraries/Math.sol


302         function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L302:302

</details>


## NC014 - Use a more recent version of solidity:

Use a solidity version of at least 0.8.13 to get the ability to use `using for` with a list of free functions.


```solidity
File: contracts/libraries/PanopticMath.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L2:2

```solidity
File: contracts/types/LeftRight.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L2:2

## NC015 - Consider using delete rather than assigning false/zero to clear values:

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.


```solidity
File: contracts/SemiFungiblePositionManager.sol


332             s_poolContext[poolId].locked = false;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L332:332


## NC017 - Function declarations should have NatSpec descriptions:

Function declarations should be preceded by a NatSpec comment.


```solidity
File: contracts/CollateralTracker.sol


178         constructor(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L178:178

## NC018 - Contract declarations should have `@notice` tags:

`@notice` is used to explain to end users what the contract does, and the compiler interprets `///` or `/**` comments as this tag if one wasn't explicitly provided.


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: contracts/libraries/PanopticMath.sol


18      library PanopticMath {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L18:18

```solidity
File: contracts/tokens/ERC1155Minimal.sol


11      abstract contract ERC1155 {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L11:11

```solidity
File: contracts/tokens/ERC20Minimal.sol


9       abstract contract ERC20Minimal {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L9:9

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


6       interface IDonorNFT {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L6:6

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol


11      interface IERC20Partial {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L11:11

</details>

## NC019 - Invalid NatSpec comment style:

NatSpec must begin with `///`, or use `/* ... */` syntax. 


<details>
<summary>Click to show 6 findings</summary>

```solidity
File: contracts/SemiFungiblePositionManager.sol


358             // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting


360             // @dev some pools may not be deployable if the poolId has a collision (since we take only 8 bytes)


603                 // @dev see `contracts/types/LiquidityChunk.sol`


836                 // @dev note this triggers our swap callback function


903                     // @dev see `contracts/types/LiquidityChunk.sol`


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L903:903

```solidity
File: contracts/libraries/PanopticMath.sol


98              // @dev 0 ^ x = x


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L98:98

</details>

## NC020 - Inconsistent spacing in comments:

Some lines use // x and some use //x. The instances below point out the usages that don't follow the majority, within each file.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


1118                //compute total commission amount = commission rate + spread fee


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1118:1118

```solidity
File: contracts/SemiFungiblePositionManager.sol


610                 //construct the positionKey for the from and to addresses


643                 //update+store liquidity and fee values between accounts


821                     //compute the swap amount, set as positive (exact input)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L821:821

</details>

## NC021 - State variable declarations should have Natspec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 53 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


70          string internal constant TICKER_PREFIX = "po";


73          string internal constant NAME_PREFIX = "POPT-V1";


96          address internal s_univ3token0;


99          address internal s_univ3token1;


102         bool internal s_underlyingIsToken0;


136         uint256 immutable COMMISSION_FEE;


141         uint256 immutable SELLER_COLLATERAL_RATIO;


145         uint256 immutable BUYER_COLLATERAL_RATIO;


149         int256 immutable FORCE_EXERCISE_COST;


154         uint256 immutable TARGET_POOL_UTIL;


158         uint256 immutable SATURATED_POOL_UTIL;


162         uint256 immutable ITM_SPREAD_MULTIPLIER;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L162:162

```solidity
File: contracts/PanopticFactory.sol


63          IUniswapV3Factory internal immutable UNIV3_FACTORY;


66          SemiFungiblePositionManager internal immutable SFPM;


69          IDonorNFT internal immutable DONOR_NFT;


72          address internal immutable POOL_REFERENCE;


75          address internal immutable COLLATERAL_REFERENCE;


78          address internal immutable WETH;


89          uint16 internal constant CARDINALITY_INCREASE = 100;


96          address internal s_owner;


99          bool internal s_initialized;


102         mapping(IUniswapV3Pool univ3pool => PanopticPool panopticPool) internal s_getPanopticPool;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L102:102

```solidity
File: contracts/PanopticPool.sol


120         bool internal constant DONOT_COMMIT_LONG_SETTLED = false;


133         bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;


136         uint256 internal constant MEDIAN_PERIOD = 60;


156         int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;


160         int256 internal constant MAX_SLOW_FAST_DELTA = 1800;


171         uint256 internal constant BP_DECREASE_BUFFER = 13_333;


174         uint256 internal constant NO_BUFFER = 10_000;


179         SemiFungiblePositionManager internal immutable SFPM;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L179:179

```solidity
File: contracts/SemiFungiblePositionManager.sol


126         bool internal constant BURN = true;


133         uint128 private constant VEGOID = 2;


287         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;


289         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L289:289

```solidity
File: contracts/libraries/Constants.sol


9           uint256 internal constant FP96 = 0x1000000000000000000000000;


12          int24 internal constant MIN_V3POOL_TICK = -887272;


15          int24 internal constant MAX_V3POOL_TICK = 887272;


18          uint160 internal constant MIN_V3POOL_SQRT_RATIO = 4295128739;


21          uint160 internal constant MAX_V3POOL_SQRT_RATIO =


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L21:21

```solidity
File: contracts/libraries/Math.sol


15          uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L15:15

```solidity
File: contracts/libraries/PanopticMath.sol


23          uint256 internal constant MAX_UINT256 = 2 ** 256 - 1;


26          uint64 internal constant TICKSPACING_MASK = 0xFFFF000000000000;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L26:26

```solidity
File: contracts/tokens/ERC20Minimal.sol


35          mapping(address account => uint256 balance) public balanceOf;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L35:35

```solidity
File: contracts/types/LeftRight.sol


22          uint256 internal constant LEFT_HALF_BIT_MASK =


26          int256 internal constant LEFT_HALF_BIT_MASK_INT =


30          int256 internal constant RIGHT_HALF_BIT_MASK = 0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L30:30

```solidity
File: contracts/types/LiquidityChunk.sol


54          uint256 internal constant CLEAR_TL_MASK =


58          uint256 internal constant CLEAR_TU_MASK =


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L58:58

```solidity
File: contracts/types/TokenId.sol


62          uint256 internal constant LONG_MASK =


66          uint256 internal constant CLEAR_POOLID_MASK =


70          uint256 internal constant OPTION_RATIO_MASK =


74          uint256 internal constant CHUNK_MASK =


78          int256 internal constant BITMASK_INT24 = 0xFFFFFF;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L78:78

</details>

## NC022 - Functions should have Natspec @return annotations:

Documents the return variables of a contract’s function

Note: these are instance missed from bots
<details>
<summary>Click to show 8 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


323         function transfer(


341         function transferFrom(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L341:341

```solidity
File: contracts/PanopticPool.sol


794         function _burnAllOptionsFrom(


955         function _burnAndHandleExercise(


1290        function _checkSolvencyAtTick(


1503        function _getPremia(


1802        function _getTotalLiquidity(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1802:1802

```solidity
File: contracts/SemiFungiblePositionManager.sol


1138        function _getFeesBase(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1138:1138

</details>


## NC023 - Not using the named return variables anywhere in the function is confusing:

Consider changing the return variable to be an unnamed one, since the variable is never assigned, nor is it returned by name


<details>
<summary>Click to show 23 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


361         function asset() external view returns (address assetTokenAddress) {


370         function totalAssets() public view returns (uint256 totalManagedAssets) {


379         function convertToShares(uint256 assets) public view returns (uint256 shares) {


386         function convertToAssets(uint256 shares) public view returns (uint256 assets) {


392         function maxDeposit(address) external pure returns (uint256 maxAssets) {


444         function maxMint(address) external view returns (uint256 maxShares) {


507         function maxWithdraw(address owner) public view returns (uint256 maxAssets) {


518         function previewWithdraw(uint256 assets) public view returns (uint256 shares) {


572         function maxRedeem(address owner) public view returns (uint256 maxShares) {


581         function previewRedeem(uint256 shares) public view returns (uint256 assets) {


741         function _poolUtilization() internal view returns (int256 poolUtilization) {


753         ) internal view returns (uint256 sellCollateralRatio) {


808         ) internal view returns (uint256 buyCollateralRatio) {


1284        ) internal view returns (uint256 required) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1284:1284

```solidity
File: contracts/PanopticPool.sol


385         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {


1431        function collateralToken0() external view returns (CollateralTracker collateralToken) {


1512            returns (
1513                LeftRightSigned[4] memory premiaByLeg,
1514                uint256[2][4] memory premiumAccumulatorsByLeg
1515            )


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1512:1515

```solidity
File: contracts/SemiFungiblePositionManager.sol


870             returns (
871                 LeftRightSigned totalMoved,
872                 LeftRightUnsigned[4] memory collectedByLeg,
873                 LeftRightSigned itmAmounts
874             )


1557        ) external view returns (IUniswapV3Pool UniswapV3Pool) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1557:1557

```solidity
File: contracts/types/LeftRight.sol


194         function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {


214         function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {


232         function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {


254         ) internal pure returns (LeftRightSigned z) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L254:254

</details>

## NC024 - Non-library/interface files should use fixed compiler versions, not floating ones:

Using a floating compiler version like ^0.8.16 or >=0.8.16 can lead to unexpected behavior if the compiler version used differs from the one intended. It's recommended to specify a fixed compiler version for non-library/interface files.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L2:2

```solidity
File: contracts/PanopticFactory.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L2:2

```solidity
File: contracts/PanopticPool.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L2:2

```solidity
File: contracts/SemiFungiblePositionManager.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L2:2

</details>

## NC025 - Contracts should have full test coverage:

While 100% code coverage does not guarantee that there are no bugs, it often will catch easy-to-find bugs, and will ensure that there are fewer regressions when the code invariably has to be modified. Furthermore, in order to get full coverage, code authors will often have to re-organize their code so that it is more modular, so that each component can be tested separately, which reduces interdependencies between modules and layers, and makes for code that is easier to reason about and audit.


```solidity
File: Various Files


None

```

## NC026 - Large or complicated code bases should implement invariant tests:

Large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts, should implement invariant fuzzing tests. Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold. Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers, with properly and extensively-written invariants, can close this testing gap significantly.


## NC027 - State variable declarations should have Natspec @notice annotations:

Explain to an end user what this does


<details>
<summary>Click to show 44 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


109         PanopticPool internal s_panopticPool;


112         uint128 internal s_poolAssets;


115         uint128 internal s_inAMM;


124         uint24 internal s_poolFee;


131         uint256 immutable TICK_DEVIATION;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L131:131

```solidity
File: contracts/PanopticPool.sol


103         int24 internal constant MIN_SWAP_TICK = Constants.MIN_V3POOL_TICK + 1;


105         int24 internal constant MAX_SWAP_TICK = Constants.MAX_V3POOL_TICK - 1;


109         bool internal constant COMPUTE_ALL_PREMIA = true;


111         bool internal constant COMPUTE_LONG_PREMIA = false;


114         bool internal constant ONLY_AVAILABLE_PREMIUM = false;


119         bool internal constant COMMIT_LONG_SETTLED = true;


120         bool internal constant DONOT_COMMIT_LONG_SETTLED = false;


123         bool internal constant ADD = true;


128         uint32 internal constant TWAP_WINDOW = 600;


133         bool internal constant SLOW_ORACLE_UNISWAP_MODE = false;


136         uint256 internal constant MEDIAN_PERIOD = 60;


139         uint256 internal constant FAST_ORACLE_CARDINALITY = 3;


145         uint256 internal constant FAST_ORACLE_PERIOD = 1;


148         uint256 internal constant SLOW_ORACLE_CARDINALITY = 7;


152         uint256 internal constant SLOW_ORACLE_PERIOD = 5;


156         int256 internal constant MAX_TWAP_DELTA_LIQUIDATION = 513;


160         int256 internal constant MAX_SLOW_FAST_DELTA = 1800;


165         uint64 internal constant MAX_SPREAD = 9 * (2 ** 32);


168         uint64 internal constant MAX_POSITIONS = 32;


171         uint256 internal constant BP_DECREASE_BUFFER = 13_333;


174         uint256 internal constant NO_BUFFER = 10_000;


186         IUniswapV3Pool internal s_univ3pool;


231         CollateralTracker internal s_collateralToken0;


233         CollateralTracker internal s_collateralToken1;


238         mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))


245         mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;


251         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;


258         mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))


272         mapping(address account => uint256 positionsHash) internal s_positionsHash;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L272:272

```solidity
File: contracts/SemiFungiblePositionManager.sol


125         bool internal constant MINT = false;


126         bool internal constant BURN = true;


133         uint128 private constant VEGOID = 2;


137         IUniswapV3Factory internal immutable FACTORY;


145         mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;


150         mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;


177         mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)


287         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;


289         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;


295         mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L295:295

</details>




## NC028 - Consider using `block.number` instead of `block.timestamp`:

`block.timestamp` is vulnerable to miner manipulation and creates a potential front-running vulnerability. Consider using `block.number` instead.


```solidity
File: contracts/PanopticPool.sol


309                     (uint256(block.timestamp) << 216) +


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L309:309

```solidity
File: contracts/libraries/PanopticMath.sol


183                 if (block.timestamp >= uint256(uint40(medianData >> 216)) + period) {


227                         (block.timestamp << 216) +


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L227:227

## NC029 - Consider bounding input array length:

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to `require()` that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.


<details>
<summary>Click to show 15 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


1208            for (uint256 i = 0; i < totalIterations; ) {
1209                // read the ith tokenId from the account
1210                TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);
1211    
1212                // read the position size and the pool utilization at mint
1213                uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();
1214    
1215                // read the pool utilization at mint
1216                uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();
1217    
1218                // Get tokens required for the current tokenId (a single active position)
1219                uint256 _tokenRequired = _getRequiredCollateralAtTickSinglePosition(
1220                    tokenId,
1221                    positionSize,
1222                    atTick,
1223                    poolUtilization
1224                );
1225    
1226                // add to the tokenRequired accumulator
1227                unchecked {
1228                    tokenRequired += _tokenRequired;
1229                }
1230                unchecked {
1231                    ++i;
1232                }
1233            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1208:1233

```solidity
File: contracts/PanopticPool.sol


441             for (uint256 k = 0; k < pLength; ) {
442                 TokenId tokenId = positionIdList[k];
443     
444                 balances[k][0] = TokenId.unwrap(tokenId);
445                 balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);
446     
447                 (
448                     LeftRightSigned[4] memory premiaByLeg,
449                     uint256[2][4] memory premiumAccumulatorsByLeg
450                 ) = _getPremia(
451                         tokenId,
452                         LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
453                         c_user,
454                         computeAllPremia,
455                         atTick
456                     );
457     
458                 uint256 numLegs = tokenId.countLegs();
459                 for (uint256 leg = 0; leg < numLegs; ) {
460                     if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
461                         bytes32 chunkKey = keccak256(
462                             abi.encodePacked(
463                                 tokenId.strike(leg),
464                                 tokenId.width(leg),
465                                 tokenId.tokenType(leg)
466                             )
467                         );
468     
469                         LeftRightUnsigned availablePremium = _getAvailablePremium(
470                             _getTotalLiquidity(tokenId, leg),
471                             s_settledTokens[chunkKey],
472                             s_grossPremiumLast[chunkKey],
473                             LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
474                             premiumAccumulatorsByLeg[leg]
475                         );
476                         portfolioPremium = portfolioPremium.add(
477                             LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478                         );
479                     } else {
480                         portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
481                     }
482                     unchecked {
483                         ++leg;
484                     }
485                 }
486     
487                 unchecked {
488                     ++k;
489                 }
490             }


459                 for (uint256 leg = 0; leg < numLegs; ) {
460                     if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
461                         bytes32 chunkKey = keccak256(
462                             abi.encodePacked(
463                                 tokenId.strike(leg),
464                                 tokenId.width(leg),
465                                 tokenId.tokenType(leg)
466                             )
467                         );
468     
469                         LeftRightUnsigned availablePremium = _getAvailablePremium(
470                             _getTotalLiquidity(tokenId, leg),
471                             s_settledTokens[chunkKey],
472                             s_grossPremiumLast[chunkKey],
473                             LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
474                             premiumAccumulatorsByLeg[leg]
475                         );
476                         portfolioPremium = portfolioPremium.add(
477                             LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478                         );
479                     } else {
480                         portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
481                     }
482                     unchecked {
483                         ++leg;
484                     }
485                 }


802             for (uint256 i = 0; i < positionIdList.length; ) {
803                 LeftRightSigned paidAmounts;
804                 (paidAmounts, premiasByLeg[i]) = _burnOptions(
805                     commitLongSettled,
806                     positionIdList[i],
807                     owner,
808                     tickLimitLow,
809                     tickLimitHigh
810                 );
811                 netPaid = netPaid.add(paidAmounts);
812                 unchecked {
813                     ++i;
814                 }
815             }


1382            for (uint256 i = 0; i < pLength; ) {
1383                fingerprintIncomingList = PanopticMath.updatePositionsHash(
1384                    fingerprintIncomingList,
1385                    positionIdList[i],
1386                    ADD
1387                );
1388                unchecked {
1389                    ++i;
1390                }
1391            }


1672            for (uint256 leg = 0; leg < numLegs; ++leg) {
1673                bytes32 chunkKey = keccak256(
1674                    abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1675                );
1676                // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers
1677                s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1678    
1679                if (tokenId.isLong(leg) == 0) {
1680                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1681                        tokenId,
1682                        leg,
1683                        positionSize
1684                    );
1685    
1686                    // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (R + N)
1687                    uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1688    
1689                    // We need to adjust the grossPremiumLast value such that the result of
1690                    // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64
1691                    // G: total gross premium
1692                    // T: totalLiquidityBeforeMint
1693                    // R: positionLiquidity
1694                    // C: current grossPremium value
1695                    // L: current grossPremiumLast value
1696                    // Ln: updated grossPremiumLast value
1697                    // T * (C - L) = G
1698                    // (T + R) * (C - Ln) = G
1699                    //
1700                    // T * (C - L) = (T + R) * (C - Ln)
1701                    // (TC - TL) / (T + R) = C - Ln
1702                    // Ln = C - (TC - TL)/(T + R)
1703                    // Ln = (CT + CR - TC + TL)/(T+R)
1704                    // Ln = (CR + TL)/(T+R)
1705    
1706                    uint256[2] memory grossCurrent;
1707                    (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1708                        address(s_univ3pool),
1709                        address(this),
1710                        tokenId.tokenType(leg),
1711                        liquidityChunk.tickLower(),
1712                        liquidityChunk.tickUpper(),
1713                        type(int24).max,
1714                        0
1715                    );
1716    
1717                    unchecked {
1718                        // L
1719                        LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1720                        // R
1721                        uint256 positionLiquidity = liquidityChunk.liquidity();
1722                        // T (totalLiquidity is (T + R) after minting)
1723                        uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
1724    
1725                        s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1726                            .wrap(0)
1727                            .toRightSlot(
1728                                uint128(
1729                                    (grossCurrent[0] *
1730                                        positionLiquidity +
1731                                        grossPremiumLast.rightSlot() *
1732                                        totalLiquidityBefore) / (totalLiquidity)
1733                                )
1734                            )
1735                            .toLeftSlot(
1736                                uint128(
1737                                    (grossCurrent[1] *
1738                                        positionLiquidity +
1739                                        grossPremiumLast.leftSlot() *
1740                                        totalLiquidityBefore) / (totalLiquidity)
1741                                )
1742                            );
1743                    }
1744                }
1745            }


1852            for (uint256 leg = 0; leg < numLegs; ) {
1853                LeftRightSigned legPremia = premiaByLeg[leg];
1854    
1855                bytes32 chunkKey = keccak256(
1856                    abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1857                );
1858    
1859                // collected from Uniswap
1860                LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1861    
1862                if (LeftRightSigned.unwrap(legPremia) != 0) {
1863                    // (will be) paid by long legs
1864                    if (tokenId.isLong(leg) == 1) {
1865                        if (commitLongSettled)
1866                            settledTokens = LeftRightUnsigned.wrap(
1867                                uint256(
1868                                    LeftRightSigned.unwrap(
1869                                        LeftRightSigned
1870                                            .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1871                                            .sub(legPremia)
1872                                    )
1873                                )
1874                            );
1875                        realizedPremia = realizedPremia.add(legPremia);
1876                    } else {
1877                        uint256 positionLiquidity = PanopticMath
1878                            .getLiquidityChunk(tokenId, leg, positionSize)
1879                            .liquidity();
1880    
1881                        // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (T - R)
1882                        uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1883                        // T (totalLiquidity is (T - R) after burning)
1884                        uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;
1885    
1886                        LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1887    
1888                        LeftRightUnsigned availablePremium = _getAvailablePremium(
1889                            totalLiquidity + positionLiquidity,
1890                            settledTokens,
1891                            grossPremiumLast,
1892                            LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
1893                            premiumAccumulatorsByLeg[leg]
1894                        );
1895    
1896                        // subtract settled tokens sent to seller
1897                        settledTokens = settledTokens.sub(availablePremium);
1898    
1899                        // add available premium to amount that should be settled
1900                        realizedPremia = realizedPremia.add(
1901                            LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1902                        );
1903    
1904                        // We need to adjust the grossPremiumLast value such that the result of
1905                        // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostBurn/2**64 is equal to
1906                        // (grossPremium - grossPremiumLast)*totalLiquidityBeforeBurn/2**64 - premiumOwedToPosition
1907                        // G: total gross premium (- premiumOwedToPosition)
1908                        // T: totalLiquidityBeforeMint
1909                        // R: positionLiquidity
1910                        // C: current grossPremium value
1911                        // L: current grossPremiumLast value
1912                        // Ln: updated grossPremiumLast value
1913                        // T * (C - L) = G
1914                        // (T - R) * (C - Ln) = G - P
1915                        //
1916                        // T * (C - L) = (T - R) * (C - Ln) + P
1917                        // (TC - TL - P) / (T - R) = C - Ln
1918                        // Ln = C - (TC - TL - P) / (T - R)
1919                        // Ln = (TC - CR - TC + LT + P) / (T-R)
1920                        // Ln = (LT - CR + P) / (T-R)
1921    
1922                        unchecked {
1923                            uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
1924                            uint256 _leg = leg;
1925    
1926                            // if there's still liquidity, compute the new grossPremiumLast
1927                            // otherwise, we just reset grossPremiumLast to the current grossPremium
1928                            s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929                                ? LeftRightUnsigned
1930                                    .wrap(0)
1931                                    .toRightSlot(
1932                                        uint128(
1933                                            uint256(
1934                                                Math.max(
1935                                                    (int256(
1936                                                        grossPremiumLast.rightSlot() *
1937                                                            totalLiquidityBefore
1938                                                    ) -
1939                                                        int256(
1940                                                            _premiumAccumulatorsByLeg[_leg][0] *
1941                                                                positionLiquidity
1942                                                        )) + int256(legPremia.rightSlot() * 2 ** 64),
1943                                                    0
1944                                                )
1945                                            ) / totalLiquidity
1946                                        )
1947                                    )
1948                                    .toLeftSlot(
1949                                        uint128(
1950                                            uint256(
1951                                                Math.max(
1952                                                    (int256(
1953                                                        grossPremiumLast.leftSlot() *
1954                                                            totalLiquidityBefore
1955                                                    ) -
1956                                                        int256(
1957                                                            _premiumAccumulatorsByLeg[_leg][1] *
1958                                                                positionLiquidity
1959                                                        )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960                                                    0
1961                                                )
1962                                            ) / totalLiquidity
1963                                        )
1964                                    )
1965                                : LeftRightUnsigned
1966                                    .wrap(0)
1967                                    .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968                                    .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1969                        }
1970                    }
1971                }
1972    
1973                // update settled tokens in storage with all local deltas
1974                s_settledTokens[chunkKey] = settledTokens;
1975    
1976                unchecked {
1977                    ++leg;
1978                }
1979            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1852:1979

```solidity
File: contracts/SemiFungiblePositionManager.sol


575             for (uint256 i = 0; i < ids.length; ) {
576                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
577                 registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
578                 unchecked {
579                     ++i;
580                 }
581             }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L575:581

```solidity
File: contracts/libraries/FeesCalc.sol


51              for (uint256 k = 0; k < positionIdList.length; ) {
52                  TokenId tokenId = positionIdList[k];
53                  uint128 positionSize = userBalance[tokenId].rightSlot();
54                  uint256 numLegs = tokenId.countLegs();
55                  for (uint256 leg = 0; leg < numLegs; ) {
56                      LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
57                          tokenId,
58                          leg,
59                          positionSize
60                      );
61      
62                      (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
63                          atTick,
64                          liquidityChunk
65                      );
66      
67                      if (tokenId.isLong(leg) == 0) {
68                          unchecked {
69                              value0 += int256(amount0);
70                              value1 += int256(amount1);
71                          }
72                      } else {
73                          unchecked {
74                              value0 -= int256(amount0);
75                              value1 -= int256(amount1);
76                          }
77                      }
78      
79                      unchecked {
80                          ++leg;
81                      }
82                  }
83                  unchecked {
84                      ++k;
85                  }
86              }


55                  for (uint256 leg = 0; leg < numLegs; ) {
56                      LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
57                          tokenId,
58                          leg,
59                          positionSize
60                      );
61      
62                      (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
63                          atTick,
64                          liquidityChunk
65                      );
66      
67                      if (tokenId.isLong(leg) == 0) {
68                          unchecked {
69                              value0 += int256(amount0);
70                              value1 += int256(amount1);
71                          }
72                      } else {
73                          unchecked {
74                              value0 -= int256(amount0);
75                              value1 -= int256(amount1);
76                          }
77                      }
78      
79                      unchecked {
80                          ++leg;
81                      }
82                  }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L55:82

```solidity
File: contracts/libraries/PanopticMath.sol


781                 for (uint256 i = 0; i < positionIdList.length; ++i) {
782                     TokenId tokenId = positionIdList[i];
783                     uint256 numLegs = tokenId.countLegs();
784                     for (uint256 leg = 0; leg < numLegs; ++leg) {
785                         if (tokenId.isLong(leg) == 1) {
786                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
787                         }
788                     }
789                 }


784                     for (uint256 leg = 0; leg < numLegs; ++leg) {
785                         if (tokenId.isLong(leg) == 1) {
786                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
787                         }
788                     }


860                 for (uint256 i = 0; i < positionIdList.length; i++) {
861                     TokenId tokenId = positionIdList[i];
862                     LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
863                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864                         if (tokenId.isLong(leg) == 1) {
865                             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
866                                 storage _settledTokens = settledTokens;
867     
868                             // calculate amounts to revoke from settled and subtract from haircut req
869                             uint256 settled0 = Math.unsafeDivRoundingUp(
870                                 uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871                                 uint128(longPremium.rightSlot())
872                             );
873                             uint256 settled1 = Math.unsafeDivRoundingUp(
874                                 uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875                                 uint128(longPremium.leftSlot())
876                             );
877     
878                             bytes32 chunkKey = keccak256(
879                                 abi.encodePacked(
880                                     tokenId.strike(0),
881                                     tokenId.width(0),
882                                     tokenId.tokenType(0)
883                                 )
884                             );
885     
886                             // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
887                             // for the haircut directly to the accumulator
888                             settled0 = Math.max(
889                                 0,
890                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891                             );
892                             settled1 = Math.max(
893                                 0,
894                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895                             );
896     
897                             _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
898                                 LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
899                                     uint128(settled1)
900                                 )
901                             );
902                         }
903                     }
904                 }


863                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864                         if (tokenId.isLong(leg) == 1) {
865                             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
866                                 storage _settledTokens = settledTokens;
867     
868                             // calculate amounts to revoke from settled and subtract from haircut req
869                             uint256 settled0 = Math.unsafeDivRoundingUp(
870                                 uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871                                 uint128(longPremium.rightSlot())
872                             );
873                             uint256 settled1 = Math.unsafeDivRoundingUp(
874                                 uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875                                 uint128(longPremium.leftSlot())
876                             );
877     
878                             bytes32 chunkKey = keccak256(
879                                 abi.encodePacked(
880                                     tokenId.strike(0),
881                                     tokenId.width(0),
882                                     tokenId.tokenType(0)
883                                 )
884                             );
885     
886                             // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
887                             // for the haircut directly to the accumulator
888                             settled0 = Math.max(
889                                 0,
890                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891                             );
892                             settled1 = Math.max(
893                                 0,
894                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895                             );
896     
897                             _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
898                                 LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
899                                     uint128(settled1)
900                                 )
901                             );
902                         }
903                     }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L863:903

```solidity
File: contracts/multicall/Multicall.sol


14              for (uint256 i = 0; i < data.length; ) {
15                  (bool success, bytes memory result) = address(this).delegatecall(data[i]);
16      
17                  if (!success) {
18                      // Bubble up the revert reason
19                      // The bytes type is ABI encoded as a length-prefixed byte array
20                      // So we simply need to add 32 to the pointer to get the start of the data
21                      // And then revert with the size loaded from the first 32 bytes
22                      // Other solutions will do work to differentiate the revert reasons and provide paranthetical information
23                      // However, we have chosen to simply replicate the the normal behavior of the call
24                      // NOTE: memory-safe because it reads from memory already allocated by solidity (the bytes memory result)
25                      assembly ("memory-safe") {
26                          revert(add(result, 32), mload(result))
27                      }
28                  }
29      
30                  results[i] = result;
31      
32                  unchecked {
33                      ++i;
34                  }
35              }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L14:35

</details>

## NC030 - Contract definitions should have Natspec @dev annotations:

Explain to a developer any extra details


```solidity
File: contracts/CollateralTracker.sol


36      contract CollateralTracker is ERC20Minimal, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L36:36

```solidity
File: contracts/PanopticFactory.sol


26      contract PanopticFactory is Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L26:26

## NC031 - Variables should be named in mixedCase style:

As the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#naming-styles) suggests: arguments, local variables and mutable state variables should be named in mixedCase style.


<details>
<summary>Click to show 54 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


109         PanopticPool internal s_panopticPool;


115         uint128 internal s_inAMM;


99          address internal s_univ3token1;


112         uint128 internal s_poolAssets;


96          address internal s_univ3token0;


89          address internal s_underlyingToken;


93          bool internal s_initialized;


121         uint128 internal s_ITMSpreadFee;


773             uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;


1557                    uint256 notionalP;


102         bool internal s_underlyingIsToken0;


124         uint24 internal s_poolFee;


185             uint256 _ITMSpreadMultiplier


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L185:185

```solidity
File: contracts/PanopticFactory.sol


116             address _WETH9,


119             IDonorNFT _donorNFT,


99          bool internal s_initialized;


96          address internal s_owner;


102         mapping(IUniswapV3Pool univ3pool => PanopticPool panopticPool) internal s_getPanopticPool;


117             SemiFungiblePositionManager _SFPM,


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L117:117

```solidity
File: contracts/PanopticPool.sol


233         CollateralTracker internal s_collateralToken1;


238         mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))
239             internal s_options;


251         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;


225         uint256 internal s_miniMedian;


245         mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;


272         mapping(address account => uint256 positionsHash) internal s_positionsHash;


439             address c_user = user;


258         mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
259             internal s_positionBalance;


186         IUniswapV3Pool internal s_univ3pool;


231         CollateralTracker internal s_collateralToken0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L231:231

```solidity
File: contracts/SemiFungiblePositionManager.sol


287         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;


145         mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;


1385                    uint128 premium1X64_gross;


1343                uint256 premium1X64_base;


611                 bytes32 positionKey_from = keccak256(


620                 bytes32 positionKey_to = keccak256(


295         mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;


1363                    uint128 premium0X64_owed;


289         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;


1342                uint256 premium0X64_base;


150         mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;


1364                    uint128 premium1X64_owed;


1384                    uint128 premium0X64_gross;


177         mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
178             internal s_accountLiquidity;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L177:178

```solidity
File: contracts/libraries/Math.sol


133                 uint256 sqrtR = absTick & 0x1 != 0


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L133:133

```solidity
File: contracts/libraries/PanopticMath.sol


186                         (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(


192                         (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L192:192

```solidity
File: contracts/types/LeftRight.sol


285             uint128 z_xR = (uint256(x.rightSlot()) + dx.rightSlot()).toUint128Capped();


287             uint128 z_yR = (uint256(y.rightSlot()) + dy.rightSlot()).toUint128Capped();


286             uint128 z_xL = (uint256(x.leftSlot()) + dx.leftSlot()).toUint128Capped();


290             bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);


288             uint128 z_yL = (uint256(y.leftSlot()) + dy.leftSlot()).toUint128Capped();


291             bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L291:291

```solidity
File: contracts/types/TokenId.sol


552                         uint256 isLongP = self.isLong(riskPartnerIndex);


556                         uint256 tokenTypeP = self.tokenType(riskPartnerIndex);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L556:556

</details>


## NC032 - Function names should use lowerCamelCase:

According to the Solidity [style guide](https://docs.soliditylang.org/en/latest/style-guide.html#function-names) function names should be in `mixedCase` (lowerCamelCase).


<details>
<summary>Click to show 11 findings</summary>

```solidity
File: contracts/PanopticPool.sol


677         function _mintInSFPMAndUpdateCollateral(


1450        function getUniV3TWAP() internal view returns (int24 twapTick) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1450:1450

```solidity
File: contracts/SemiFungiblePositionManager.sol


350         function initializeAMMPool(address token0, address token1, uint24 fee) external {


680         function _validateAndForwardToAMM(


756         function swapInAMM(


863         function _createPositionInAMM(


958         function _createLegInAMM(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L958:958

```solidity
File: contracts/libraries/FeesCalc.sol


97          function calculateAMMSwapFees(


130         function _getAMMSwapFeesPerLiquidityCollected(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L130:130

```solidity
File: contracts/libraries/PanopticMath.sol


607         function _calculateIOAmounts(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L607:607

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


13          function issueNFT(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L13:13

</details>

## NC033 - Consider adding a deny-list:

Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


36      contract CollateralTracker is ERC20Minimal, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L36:36

```solidity
File: contracts/PanopticFactory.sol


26      contract PanopticFactory is Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L26:26

```solidity
File: contracts/PanopticPool.sol


27      contract PanopticPool is ERC1155Holder, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L27:27

```solidity
File: contracts/SemiFungiblePositionManager.sol


72      contract SemiFungiblePositionManager is ERC1155, Multicall {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L72:72

</details>

## NC034 - Use a more recent version of solidity:

Use a solidity version of at least 0.8.12 to get string.concat() to be used instead of abi.encodePacked(<str>,<str>)


```solidity
File: contracts/libraries/PanopticMath.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L2:2

## NC035 - Custom error has no error details:

Consider adding parameters to the error to indicate which user or values caused the failure.


<details>
<summary>Click to show 34 findings</summary>

```solidity
File: contracts/libraries/Errors.sol


10          error CastingError();


13          error CollateralTokenAlreadyInitialized();


16          error DepositTooLarge();


20          error EffectiveLiquidityAboveThreshold();


23          error ExceedsMaximumRedemption();


26          error ExerciseeNotSolvent();


29          error InputListFail();


32          error InvalidSalt();


35          error InvalidTick();


38          error InvalidNotionalValue();


45          error InvalidUniswapCallback();


48          error LeftRightInputError();


51          error NoLegsExercisable();


54          error NotEnoughCollateral();


57          error PositionTooLarge();


60          error NotALongLeg();


63          error NotEnoughLiquidity();


66          error NotMarginCalled();


70          error NotOwner();


73          error NotPanopticPool();


76          error OptionsBalanceZero();


79          error PoolAlreadyInitialized();


82          error PositionAlreadyMinted();


85          error PositionCountNotZero();


88          error PriceBoundFail();


91          error ReentrantCall();


95          error StaleTWAP();


98          error TooManyPositionsOpen();


101         error TransferFailed();


105         error TicksNotInitializable();


108         error UnderOverFlow();


111         error UniswapPoolNotInitialized();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol#L111:111

```solidity
File: contracts/tokens/ERC1155Minimal.sol


55          error NotAuthorized();


58          error UnsafeRecipient();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L58:58

</details>

## NC036 - Modifier definitions should have Natspec @dev annotations:

Explain to a developer any extra details


```solidity
File: contracts/CollateralTracker.sol


169         modifier onlyPanopticPool() {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L169:169

## NC037 - Events are missing sender information:

When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the msg.sender the events of these types of action will make events much more useful to end users. Include `msg.sender` in the event output.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/PanopticFactory.sol


154             emit OwnershipTransferred(currentOwner, newOwner);


268             emit PoolDeployed(
269                 newPoolContract,
270                 v3Pool,
271                 collateralTracker0,
272                 collateralTracker1,
273                 amount0,
274                 amount1
275             );


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L268:275

```solidity
File: contracts/PanopticPool.sol


1654                emit PremiumSettled(owner, tokenId, realizedPremia);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1654:1654

```solidity
File: contracts/SemiFungiblePositionManager.sol


390             emit PoolInitialized(univ3pool, poolId);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L390:390

</details>

## NC038 - Enum values should be used in place of constant array indexes:

Create a commented enum value to use in place of constant array indexes, this makes the code far easier to understand.


<details>
<summary>Click to show 26 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


1210                TokenId tokenId = TokenId.wrap(positionBalanceArray[i][0]);


1213                uint128 positionSize = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).rightSlot();


1216                uint128 poolUtilization = LeftRightUnsigned.wrap(positionBalanceArray[i][1]).leftSlot();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1216:1216

```solidity
File: contracts/PanopticPool.sol


444                 balances[k][0] = TokenId.unwrap(tokenId);


445                 balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);


452                         LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),


1193            uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();


1198                .computeExercisedAmounts(touchedId[0], positionBalance);


1219            touchedId[0].validateIsExercisable(twapTick);


1234                touchedId[0],


1277            emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);


1528                    (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM


1528                    (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM


1550                                        ((premiumAccumulatorsByLeg[leg][0] -


1559                                        ((premiumAccumulatorsByLeg[leg][1] -


1707                    (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(


1707                    (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(


1729                                    (grossCurrent[0] *


1737                                    (grossCurrent[1] *


1768                uint256 accumulated0 = ((premiumAccumulators[0] - grossPremiumLast.rightSlot()) *


1770                uint256 accumulated1 = ((premiumAccumulators[1] - grossPremiumLast.leftSlot()) *


1940                                                            _premiumAccumulatorsByLeg[_leg][0] *


1957                                                            _premiumAccumulatorsByLeg[_leg][1] *


1967                                    .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))


1968                                    .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1968:1968

```solidity
File: contracts/libraries/PanopticMath.sol


266                 return int24(sortedTicks[10]);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L266:266

</details>

## NC039 - Zero as a function argument should have a descriptive meaning:

Consider using descriptive constants or an enum instead of passing zero directly on function calls, as that might be error-prone, to fully describe the caller's intention.


<details>
<summary>Click to show 88 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


669                                 Math.unsafeDivRoundingUp(
670                                     uint24(positionId.width(leg) * positionId.tickSpacing()),
671                                     2
672                                 )


712                             LeftRightSigned
713                                 .wrap(0)


959                         uint256(Math.max(1, int256(totalAssets()) - int256(assets)))


1581                _getRequiredCollateralAtUtilization(
1582                    tokenType == 0 ? movedRight : movedLeft,
1583                    1,
1584                    tokenType == 0
1585                        ? int64(uint64(poolUtilization))
1586                        : int64(uint64(poolUtilization >> 64))
1587                )


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1581:1587

```solidity
File: contracts/PanopticPool.sol


312                     (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +


628             _validatePositionList(msg.sender, positionIdList, 1);


634                 revert Errors.InvalidTokenIdParameter(0);


654             s_positionBalance[msg.sender][tokenId] = LeftRightUnsigned
655                 .wrap(0)


762                     s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
763                         .wrap(0)


861             s_positionBalance[owner][tokenId] = LeftRightUnsigned.wrap(0);


870                 s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);


893             _validatePositionList(user, positionIdList, 0);


1023            _validatePositionList(liquidatee, positionIdList, 0);


1153            _validatePositionList(msg.sender, positionIdListLiquidator, 0);


1165            LeftRightSigned bonusAmounts = LeftRightSigned
1166                .wrap(0)


1191            _validatePositionList(msg.sender, positionIdListExercisor, 0);


1227            _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);


1329                return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);


1545                        premiaByLeg[leg] = LeftRightSigned
1546                            .wrap(0)


1567                            premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);


1592            _validatePositionList(owner, positionIdList, 0);


1605                (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
1606                    address(s_univ3pool),
1607                    address(this),
1608                    tokenType,
1609                    tickLower,
1610                    tickUpper,
1611                    currentTick,
1612                    1
1613                );


1614                accumulatedPremium = LeftRightUnsigned
1615                    .wrap(0)


1633                LeftRightSigned realizedPremia = LeftRightSigned
1634                    .wrap(0)


1639                s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());


1640                s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());


1707                    (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1708                        address(s_univ3pool),
1709                        address(this),
1710                        tokenId.tokenType(leg),
1711                        liquidityChunk.tickLower(),
1712                        liquidityChunk.tickUpper(),
1713                        type(int24).max,
1714                        0
1715                    );


1725                        s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1726                            .wrap(0)


1774                    LeftRightUnsigned
1775                        .wrap(0)


1929                                ? LeftRightUnsigned
1930                                    .wrap(0)


1934                                                Math.max(
1935                                                    (int256(
1936                                                        grossPremiumLast.rightSlot() *
1937                                                            totalLiquidityBefore
1938                                                    ) -
1939                                                        int256(
1940                                                            _premiumAccumulatorsByLeg[_leg][0] *
1941                                                                positionLiquidity
1942                                                        )) + int256(legPremia.rightSlot() * 2 ** 64),
1943                                                    0
1944                                                )


1951                                                Math.max(
1952                                                    (int256(
1953                                                        grossPremiumLast.leftSlot() *
1954                                                            totalLiquidityBefore
1955                                                    ) -
1956                                                        int256(
1957                                                            _premiumAccumulatorsByLeg[_leg][1] *
1958                                                                positionLiquidity
1959                                                        )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960                                                    0
1961                                                )


1965                                : LeftRightUnsigned
1966                                    .wrap(0)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1965:1966

```solidity
File: contracts/SemiFungiblePositionManager.sol


645                 s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);


648                 s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);


833                 if (swapAmount == 0) return LeftRightSigned.wrap(0);


848                 totalSwapped = LeftRightSigned.wrap(0).toRightSlot(swap0.toInt128()).toLeftSlot(


1038                s_accountLiquidity[positionKey] = LeftRightUnsigned
1039                    .wrap(0)


1166                ? LeftRightSigned
1167                    .wrap(0)


1174                : LeftRightSigned
1175                    .wrap(0)


1214            movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(


1241                movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(


1306                collectedChunk = LeftRightUnsigned.wrap(0).toRightSlot(collected0).toLeftSlot(


1376                        deltaPremiumOwed = LeftRightUnsigned
1377                            .wrap(0)


1400                        deltaPremiumGross = LeftRightUnsigned
1401                            .wrap(0)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1400:1401

```solidity
File: contracts/libraries/FeesCalc.sol


115                 LeftRightSigned
116                     .wrap(0)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L115:116

```solidity
File: contracts/libraries/Math.sol


778                 quickSort(data, int256(0), int256(data.length - 1));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L778:778

```solidity
File: contracts/libraries/PanopticMath.sol


188                                 int256(observationIndex) - int256(1) + int256(observationCardinality)


242             uint32[] memory secondsAgos = new uint32[](20);


244             int256[] memory twapMeasurement = new int256[](19);


377                 int24(int256(Math.unsafeDivRoundingUp(uint24(width) * uint24(tickSpacing), 2)))


598             return LeftRightUnsigned.wrap(0).toRightSlot(amount0).toLeftSlot(amount1);


671                     (uint256 balanceCross, uint256 thresholdCross) = PanopticMath.convertCollateralData(
672                         tokenData0,
673                         tokenData1,
674                         0,
675                         sqrtPriceX96Twap
676                     );


694                     Math.max(premia.rightSlot(), 0);


696                     Math.max(premia.leftSlot(), 0);


749                     LeftRightSigned.wrap(0).toRightSlot(int128(balance0 - paid0)).toLeftSlot(


791                 int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);


792                 int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);


856                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));


857                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));


880                                     tokenId.strike(0),


881                                     tokenId.width(0),


882                                     tokenId.tokenType(0)


888                             settled0 = Math.max(
889                                 0,
890                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891                             );


892                             settled1 = Math.max(
893                                 0,
894                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895                             );


898                                 LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(


933                         LeftRightSigned
934                             .wrap(0)


951                         LeftRightSigned
952                             .wrap(0)


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L951:952

```solidity
File: contracts/types/LeftRight.sol


27              int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));


27              int256(uint256(0xFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF00000000000000000000000000000000));


265                     z.toRightSlot(int128(Math.max(right128, 0))).toLeftSlot(


266                         int128(Math.max(left128, 0))


294                 LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_xR : x.rightSlot()).toLeftSlot(


297                 LeftRightUnsigned.wrap(0).toRightSlot(r_Enabled ? z_yR : y.rightSlot()).toLeftSlot(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L297:297

```solidity
File: contracts/types/TokenId.sol


406                 return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);


406                 return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);


406                 return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);


406                 return self.isLong(0) + self.isLong(1) + self.isLong(2) + self.isLong(3);


501             if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);


501             if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);


513                             revert Errors.InvalidTokenIdParameter(1);


522                             revert Errors.InvalidTokenIdParameter(6);


528                     if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);


533                     ) revert Errors.InvalidTokenIdParameter(4);


542                             revert Errors.InvalidTokenIdParameter(3);


548                         ) revert Errors.InvalidTokenIdParameter(3);


561                             revert Errors.InvalidTokenIdParameter(4);


567                             revert Errors.InvalidTokenIdParameter(5);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L567:567

</details>

## NC040 - Function names should differ to make the code more readable:

In Solidity, while function overriding allows for functions with the same name to coexist, it is advisable to avoid this practice to enhance code readability and maintainability. Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the likelihood of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function, but also helps prevent unintended function calls or incorrect overriding. By adopting a clear and consistent naming convention, developers can create more comprehensible and maintainable smart contracts.


<details>
<summary>Click to show 53 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


    function transfer(
        address recipient,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool) {
        // make sure the caller does not have any open option positions
        // if they do: we don't want them sending panoptic pool shares to others
        // since that's like reducing collateral

        if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

        return ERC20Minimal.transfer(recipient, amount);
    }

    function transferFrom(
        address from,
        address to,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool) {
        // make sure the caller does not have any open option positions
        // if they do: we don't want them sending panoptic pool shares to others
        // as this would reduce their amount of collateral against the opened positions

        if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

        return ERC20Minimal.transferFrom(from, to, amount);
    }

    function asset() external view returns (address assetTokenAddress) {
        return s_underlyingToken;
    }

    function delegate(
        address delegator,
        address delegatee,
        uint256 assets
    ) external onlyPanopticPool {
        /*
                ┌────────┐
                │Panoptic│
                │Pool    │
                └────┬───┘
                     │(1) convert 'assets' to shares (this ERC20 contract)
        ┌─────────┐  │  ┌─────────┐
        │delegator├──▼──►delegatee│
        └─────────┘(2)  └─────────┘
                move shares
                from delegator
                to delegatee
        */

        uint256 shares = convertToShares(assets);

        // transfer shares from the delegator to the delegatee
        _transferFrom(delegator, delegatee, shares);
    }

    function delegate(address delegatee, uint256 assets) external onlyPanopticPool {
        balanceOf[delegatee] += convertToShares(assets);
    }

    function refund(address delegatee, uint256 assets) external onlyPanopticPool {
        balanceOf[delegatee] -= convertToShares(assets);
    }

    function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {
        if (assets > 0) {
            _transferFrom(refunder, refundee, convertToShares(uint256(assets)));
        } else {
            unchecked {
                _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));
            }
        }
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L975:983

```solidity
File: contracts/tokens/ERC20Minimal.sol


    function transfer(address to, uint256 amount) public virtual returns (bool) {
        balanceOf[msg.sender] -= amount;

        // Cannot overflow because the sum of all user
        // balances can't exceed the max uint256 value.
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(msg.sender, to, amount);

        return true;
    }

    function transferFrom(address from, address to, uint256 amount) public virtual returns (bool) {
        uint256 allowed = allowance[from][msg.sender]; // Saves gas for limited approvals.

        if (allowed != type(uint256).max) allowance[from][msg.sender] = allowed - amount;

        balanceOf[from] -= amount;

        // Cannot overflow because the sum of all user
        // balances can't exceed the max uint256 value.
        unchecked {
            balanceOf[to] += amount;
        }

        emit Transfer(from, to, amount);

        return true;
    }

    function _mint(address to, uint256 amount) internal {
        // Cannot overflow because the sum of all user
        // balances can't exceed the max uint256 value.
        unchecked {
            balanceOf[to] += amount;
        }
        totalSupply += amount;

        emit Transfer(address(0), to, amount);
    }

    function _burn(address from, uint256 amount) internal {
        balanceOf[from] -= amount;

        // Cannot underflow because a user's balance
        // will never be larger than the total supply.
        unchecked {
            totalSupply -= amount;
        }

        emit Transfer(from, address(0), amount);
    }

    function approve(address spender, uint256 amount) public returns (bool) {
        allowance[msg.sender][spender] = amount;

        emit Approval(msg.sender, spender, amount);

        return true;
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L49:55

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol


    function transfer(address to, uint256 amount) external;

    function approve(address spender, uint256 amount) external;

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L22:22

```solidity
File: contracts/types/TokenId.sol


    function asset(TokenId self, uint256 legIndex) internal pure returns (uint256) {
        unchecked {
            return uint256((TokenId.unwrap(self) >> (64 + legIndex * 48)) % 2);
        }
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L108:112

```solidity
File: contracts/PanopticFactory.sol


    function uniswapV3MintCallback(
        uint256 amount0Owed,
        uint256 amount1Owed,
        bytes calldata data
    ) external {
        CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));

        CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);

        if (amount0Owed > 0)
            SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token0,
                decoded.payer,
                msg.sender,
                amount0Owed
            );
        if (amount1Owed > 0)
            SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token1,
                decoded.payer,
                msg.sender,
                amount1Owed
            );
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L172:195

```solidity
File: contracts/SemiFungiblePositionManager.sol


    function uniswapV3MintCallback(
        uint256 amount0Owed,
        uint256 amount1Owed,
        bytes calldata data
    ) external {
        // Decode the mint callback data
        CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));
        // Validate caller to ensure we got called from the AMM pool
        CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);
        // Sends the amount0Owed and amount1Owed quantities provided
        if (amount0Owed > 0)
            SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token0,
                decoded.payer,
                msg.sender,
                amount0Owed
            );
        if (amount1Owed > 0)
            SafeTransferLib.safeTransferFrom(
                decoded.poolFeatures.token1,
                decoded.payer,
                msg.sender,
                amount1Owed
            );
    }

    function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public override {
        // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
        // so just check if there is an active reentrancy lock for the relevant pool on the token we're transferring
        if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

        // update the position data
        registerTokenTransfer(from, to, TokenId.wrap(id), amount);

        // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)
        super.safeTransferFrom(from, to, id, amount, data);
    }

    function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public override {
        // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
        // so just check if there is an active reentrancy lock for the relevant pool on each token
        for (uint256 i = 0; i < ids.length; ) {
            if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
            registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
            unchecked {
                ++i;
            }
        }

        // transfer the token (note that all state updates are completed before reentrancy is possible)
        super.safeBatchTransferFrom(from, to, ids, amounts, data);
    }

    function getPoolId(address univ3pool) external view returns (uint64 poolId) {
        poolId = uint64(s_AddrToPoolIdData[univ3pool]);
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1566:1568

```solidity
File: contracts/PanopticPool.sol


    function burnOptions(
        TokenId tokenId,
        TokenId[] calldata newPositionIdList,
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) external {
        _burnOptions(COMMIT_LONG_SETTLED, tokenId, msg.sender, tickLimitLow, tickLimitHigh);

        _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);
    }

    function burnOptions(
        TokenId[] calldata positionIdList,
        TokenId[] calldata newPositionIdList,
        int24 tickLimitLow,
        int24 tickLimitHigh
    ) external {
        _burnAllOptionsFrom(
            msg.sender,
            tickLimitLow,
            tickLimitHigh,
            COMMIT_LONG_SETTLED,
            positionIdList
        );

        _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L586:601

```solidity
File: contracts/libraries/SafeTransferLib.sol


    function safeTransferFrom(address token, address from, address to, uint256 amount) internal {
        bool success;

        assembly ("memory-safe") {
            // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
            let p := mload(0x40)

            // Write the abi-encoded calldata into memory, beginning with the function selector.
            mstore(p, 0x23b872dd00000000000000000000000000000000000000000000000000000000)
            mstore(add(4, p), from) // Append the "from" argument.
            mstore(add(36, p), to) // Append the "to" argument.
            mstore(add(68, p), amount) // Append the "amount" argument.

            success := and(
                // Set success to whether the call reverted, if not we check it either
                // returned exactly 1 (can't just be non-zero data), or had no return data.
                or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
                // We use 100 because that's the total length of our calldata (4 + 32 * 3)
                // Counterintuitively, this call() must be positioned after the or() in the
                // surrounding and() because and() evaluates its arguments from right to left.
                call(gas(), token, 0, p, 100, 0, 32)
            )
        }

        if (!success) revert Errors.TransferFailed();
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L21:46

```solidity
File: contracts/tokens/ERC1155Minimal.sol


    function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public virtual {
        if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

        balanceOf[from][id] -= amount;

        // balance will never overflow
        unchecked {
            balanceOf[to][id] += amount;
        }

        emit TransferSingle(msg.sender, from, to, id, amount);

        if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155Received(msg.sender, from, id, amount, data) !=
                ERC1155Holder.onERC1155Received.selector
            ) {
                revert UnsafeRecipient();
            }
        }
    }

    function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public virtual {
        if (!(msg.sender == from || isApprovedForAll[from][msg.sender])) revert NotAuthorized();

        // Storing these outside the loop saves ~15 gas per iteration.
        uint256 id;
        uint256 amount;

        for (uint256 i = 0; i < ids.length; ) {
            id = ids[i];
            amount = amounts[i];

            balanceOf[from][id] -= amount;

            // balance will never overflow
            unchecked {
                balanceOf[to][id] += amount;
            }

            // An array can't have a total length
            // larger than the max uint256 value.
            unchecked {
                ++i;
            }
        }

        emit TransferBatch(msg.sender, from, to, ids, amounts);

        if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155BatchReceived(msg.sender, from, ids, amounts, data) !=
                ERC1155Holder.onERC1155BatchReceived.selector
            ) {
                revert UnsafeRecipient();
            }
        }
    }

    function _mint(address to, uint256 id, uint256 amount) internal {
        // balance will never overflow
        unchecked {
            balanceOf[to][id] += amount;
        }

        emit TransferSingle(msg.sender, address(0), to, id, amount);

        if (to.code.length != 0) {
            if (
                ERC1155Holder(to).onERC1155Received(msg.sender, address(0), id, amount, "") !=
                ERC1155Holder.onERC1155Received.selector
            ) {
                revert UnsafeRecipient();
            }
        }
    }

    function _burn(address from, uint256 id, uint256 amount) internal {
        balanceOf[from][id] -= amount;

        emit TransferSingle(msg.sender, from, address(0), id, amount);
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L236:240

```solidity
File: contracts/libraries/PanopticMath.sol


    function getPoolId(address univ3pool) internal view returns (uint64) {
        unchecked {
            int24 tickSpacing = IUniswapV3Pool(univ3pool).tickSpacing();
            uint64 poolId = uint64(uint160(univ3pool) >> 112);
            poolId += uint64(uint24(tickSpacing)) << 48;
            return poolId;
        }
    }

    function convertCollateralData(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint256 tokenType,
        uint160 sqrtPriceX96
    ) internal pure returns (uint256, uint256) {
        if (tokenType == 0) {
            return (
                tokenData0.rightSlot() + convert1to0(tokenData1.rightSlot(), sqrtPriceX96),
                tokenData0.leftSlot() + convert1to0(tokenData1.leftSlot(), sqrtPriceX96)
            );
        } else {
            return (
                tokenData1.rightSlot() + convert0to1(tokenData0.rightSlot(), sqrtPriceX96),
                tokenData1.leftSlot() + convert0to1(tokenData0.leftSlot(), sqrtPriceX96)
            );
        }
    }

    function convertCollateralData(
        LeftRightUnsigned tokenData0,
        LeftRightUnsigned tokenData1,
        uint256 tokenType,
        int24 tick
    ) internal pure returns (uint256, uint256) {
        return
            convertCollateralData(tokenData0, tokenData1, tokenType, Math.getSqrtRatioAtTick(tick));
    }

    function convert0to1(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {
        unchecked {
            // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
            // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
            if (sqrtPriceX96 < type(uint128).max) {
                return Math.mulDiv192(amount, uint256(sqrtPriceX96) ** 2);
            } else {
                return Math.mulDiv128(amount, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
            }
        }
    }

    function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
        unchecked {
            // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
            // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
            if (sqrtPriceX96 < type(uint128).max) {
                int256 absResult = Math
                    .mulDiv192(Math.absUint(amount), uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv128(Math.absUint(amount), Math.mulDiv64(sqrtPriceX96, sqrtPriceX96))
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }
        }
    }

    function convert1to0(uint256 amount, uint160 sqrtPriceX96) internal pure returns (uint256) {
        unchecked {
            // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
            // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
            if (sqrtPriceX96 < type(uint128).max) {
                return Math.mulDiv(amount, 2 ** 192, uint256(sqrtPriceX96) ** 2);
            } else {
                return Math.mulDiv(amount, 2 ** 128, Math.mulDiv64(sqrtPriceX96, sqrtPriceX96));
            }
        }
    }

    function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {
        unchecked {
            // the tick 443636 is the maximum price where (price) * 2**192 fits into a uint256 (< 2**256-1)
            // above that tick, we are forced to reduce the amount of decimals in the final price by 2**64 to 2**128
            if (sqrtPriceX96 < type(uint128).max) {
                int256 absResult = Math
                    .mulDiv(Math.absUint(amount), 2 ** 192, uint256(sqrtPriceX96) ** 2)
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            } else {
                int256 absResult = Math
                    .mulDiv(
                        Math.absUint(amount),
                        2 ** 128,
                        Math.mulDiv64(sqrtPriceX96, sqrtPriceX96)
                    )
                    .toInt256();
                return amount < 0 ? -absResult : absResult;
            }
        }
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L547:567

```solidity
File: contracts/libraries/Math.sol


    function min(uint256 a, uint256 b) internal pure returns (uint256) {
        return a < b ? a : b;
    }

    function min(int256 a, int256 b) internal pure returns (int256) {
        return a < b ? a : b;
    }

    function max(uint256 a, uint256 b) internal pure returns (uint256) {
        return a > b ? a : b;
    }

    function max(int256 a, int256 b) internal pure returns (int256) {
        return a > b ? a : b;
    }

    function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {
        if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();
    }

    function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {
        if (!((downcastedInt = int128(toCast)) == toCast)) revert Errors.CastingError();
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L318:320

```solidity
File: contracts/types/LeftRight.sol


    function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {
        return uint128(LeftRightUnsigned.unwrap(self));
    }

    function rightSlot(LeftRightSigned self) internal pure returns (int128) {
        return int128(LeftRightSigned.unwrap(self));
    }

    function toRightSlot(
        LeftRightUnsigned self,
        uint128 right
    ) internal pure returns (LeftRightUnsigned) {
        unchecked {
            // prevent the right slot from leaking into the left one in the case of an overflow
            // ff + 1 = (1)00, but we want just ff + 1 = 00
            return
                LeftRightUnsigned.wrap(
                    (LeftRightUnsigned.unwrap(self) & LEFT_HALF_BIT_MASK) +
                        uint256(uint128(LeftRightUnsigned.unwrap(self)) + right)
                );
        }
    }

    function toRightSlot(
        LeftRightSigned self,
        int128 right
    ) internal pure returns (LeftRightSigned) {
        // bit mask needed in case rightHalfBitPattern < 0 due to 2's complement
        unchecked {
            // prevent the right slot from leaking into the left one in the case of a positive sign change
            // ff + 1 = (1)00, but we want just ff + 1 = 00
            return
                LeftRightSigned.wrap(
                    (LeftRightSigned.unwrap(self) & LEFT_HALF_BIT_MASK_INT) +
                        (int256(int128(LeftRightSigned.unwrap(self)) + right) & RIGHT_HALF_BIT_MASK)
                );
        }
    }

    function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {
        return uint128(LeftRightUnsigned.unwrap(self) >> 128);
    }

    function leftSlot(LeftRightSigned self) internal pure returns (int128) {
        return int128(LeftRightSigned.unwrap(self) >> 128);
    }

    function toLeftSlot(
        LeftRightUnsigned self,
        uint128 left
    ) internal pure returns (LeftRightUnsigned) {
        unchecked {
            return LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(self) + (uint256(left) << 128));
        }
    }

    function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {
        unchecked {
            return LeftRightSigned.wrap(LeftRightSigned.unwrap(self) + (int256(left) << 128));
        }
    }

    function add(
        LeftRightUnsigned x,
        LeftRightUnsigned y
    ) internal pure returns (LeftRightUnsigned z) {
        unchecked {
            // adding leftRight packed uint128's is same as just adding the values explictily
            // given that we check for overflows of the left and right values
            z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) + LeftRightUnsigned.unwrap(y));

            // on overflow z will be less than either x or y
            // type cast z to uint128 to isolate the right slot and if it's lower than a value it's comprised of (x)
            // then an overflow has occured
            if (
                LeftRightUnsigned.unwrap(z) < LeftRightUnsigned.unwrap(x) ||
                (uint128(LeftRightUnsigned.unwrap(z)) < uint128(LeftRightUnsigned.unwrap(x)))
            ) revert Errors.UnderOverFlow();
        }
    }

    function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
        unchecked {
            int256 left = int256(uint256(x.leftSlot())) + y.leftSlot();
            int128 left128 = int128(left);

            if (left128 != left) revert Errors.UnderOverFlow();

            int256 right = int256(uint256(x.rightSlot())) + y.rightSlot();
            int128 right128 = int128(right);

            if (right128 != right) revert Errors.UnderOverFlow();

            return z.toRightSlot(right128).toLeftSlot(left128);
        }
    }

    function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
        unchecked {
            int256 left256 = int256(x.leftSlot()) + y.leftSlot();
            int128 left128 = int128(left256);

            int256 right256 = int256(x.rightSlot()) + y.rightSlot();
            int128 right128 = int128(right256);

            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

            return z.toRightSlot(right128).toLeftSlot(left128);
        }
    }

    function sub(
        LeftRightUnsigned x,
        LeftRightUnsigned y
    ) internal pure returns (LeftRightUnsigned z) {
        unchecked {
            // subtracting leftRight packed uint128's is same as just subtracting the values explictily
            // given that we check for underflows of the left and right values
            z = LeftRightUnsigned.wrap(LeftRightUnsigned.unwrap(x) - LeftRightUnsigned.unwrap(y));

            // on underflow z will be greater than either x or y
            // type cast z to uint128 to isolate the right slot and if it's higher than a value that was subtracted from (x)
            // then an underflow has occured
            if (
                LeftRightUnsigned.unwrap(z) > LeftRightUnsigned.unwrap(x) ||
                (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))
            ) revert Errors.UnderOverFlow();
        }
    }

    function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {
        unchecked {
            int256 left256 = int256(x.leftSlot()) - y.leftSlot();
            int128 left128 = int128(left256);

            int256 right256 = int256(x.rightSlot()) - y.rightSlot();
            int128 right128 = int128(right256);

            if (left128 != left256 || right128 != right256) revert Errors.UnderOverFlow();

            return z.toRightSlot(right128).toLeftSlot(left128);
        }
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L232:244

</details>

## NC041 - It is standard for all external and public functions to be override from an interface:

This is to ensure the whole API is extracted in an interface


<details>
<summary>Click to show 67 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


221         function startToken(
222             bool underlyingIsToken0,
223             address token0,
224             address token1,
225             uint24 fee,
226             PanopticPool panopticPool
227         ) external {
228             // fails if already initialized
229             if (s_initialized) revert Errors.CollateralTokenAlreadyInitialized();
230             s_initialized = true;
231     
232             // these virtual shares function as a multiplier for the capital requirement to manipulate the pool price
233             // e.g if the virtual shares are 10**6, then the capital requirement to manipulate the price to 10**12 is 10**18
234             totalSupply = 10 ** 6;
235     
236             // set total assets to 1
237             // the initial share price is defined by 1/virtualShares
238             s_poolAssets = 1;
239     
240             // store the address of the underlying ERC20 token
241             s_underlyingToken = underlyingIsToken0 ? token0 : token1;
242     
243             // store the Panoptic pool for this collateral token
244             s_panopticPool = panopticPool;
245     
246             // cache the pool fee in basis points
247             uint24 _poolFee;
248             unchecked {
249                 _poolFee = fee / 100;
250             }
251             s_poolFee = _poolFee;
252     
253             // Stores the addresses of the underlying tracked tokens.
254             s_univ3token0 = token0;
255             s_univ3token1 = token1;
256     
257             // store whether the current collateral token is token0 (true) or token1 (false; since there's always exactly two tokens it could be)
258             s_underlyingIsToken0 = underlyingIsToken0;
259     
260             // Additional risk premium charged on intrinsic value of ITM positions
261             unchecked {
262                 s_ITMSpreadFee = uint128((ITM_SPREAD_MULTIPLIER * _poolFee) / DECIMALS);
263             }
264         }


277         function getPoolData()
278             external
279             view
280             returns (uint256 poolAssets, uint256 insideAMM, int256 currentPoolUtilization)
281         {
282             poolAssets = s_poolAssets;
283             insideAMM = s_inAMM;
284             currentPoolUtilization = _poolUtilization();
285         }


289         function name() external view returns (string memory) {
290             // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size
291             return
292                 InteractionHelper.computeName(
293                     s_univ3token0,
294                     s_univ3token1,
295                     s_underlyingIsToken0,
296                     s_poolFee,
297                     NAME_PREFIX
298                 );
299         }


303         function symbol() external view returns (string memory) {
304             // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size
305             return InteractionHelper.computeSymbol(s_underlyingToken, TICKER_PREFIX);
306         }


310         function decimals() external view returns (uint8) {
311             // this logic requires multiple external calls and error handling, so we do it in a delegatecall to a library to save bytecode size
312             return InteractionHelper.computeDecimals(s_underlyingToken);
313         }


323         function transfer(
324             address recipient,
325             uint256 amount
326         ) public override(ERC20Minimal) returns (bool) {
327             // make sure the caller does not have any open option positions
328             // if they do: we don't want them sending panoptic pool shares to others
329             // since that's like reducing collateral
330     
331             if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();
332     
333             return ERC20Minimal.transfer(recipient, amount);
334         }


341         function transferFrom(
342             address from,
343             address to,
344             uint256 amount
345         ) public override(ERC20Minimal) returns (bool) {
346             // make sure the caller does not have any open option positions
347             // if they do: we don't want them sending panoptic pool shares to others
348             // as this would reduce their amount of collateral against the opened positions
349     
350             if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();
351     
352             return ERC20Minimal.transferFrom(from, to, amount);
353         }


361         function asset() external view returns (address assetTokenAddress) {
362             return s_underlyingToken;
363         }


370         function totalAssets() public view returns (uint256 totalManagedAssets) {
371             unchecked {
372                 return s_poolAssets + s_inAMM;
373             }
374         }


379         function convertToShares(uint256 assets) public view returns (uint256 shares) {
380             return Math.mulDiv(assets, totalSupply, totalAssets());
381         }


386         function convertToAssets(uint256 shares) public view returns (uint256 assets) {
387             return Math.mulDiv(shares, totalAssets(), totalSupply);
388         }


392         function maxDeposit(address) external pure returns (uint256 maxAssets) {
393             return type(uint104).max;
394         }


399         function previewDeposit(uint256 assets) public view returns (uint256 shares) {
400             // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid
401             unchecked {
402                 shares = Math.mulDiv(
403                     assets * (DECIMALS - COMMISSION_FEE),
404                     totalSupply,
405                     totalAssets() * DECIMALS
406                 );
407             }
408         }


417         function deposit(uint256 assets, address receiver) external returns (uint256 shares) {
418             if (assets > type(uint104).max) revert Errors.DepositTooLarge();
419     
420             shares = previewDeposit(assets);
421     
422             // transfer assets (underlying token funds) from the user/the LP to the PanopticPool
423             // in return for the shares to be minted
424             SafeTransferLib.safeTransferFrom(
425                 s_underlyingToken,
426                 msg.sender,
427                 address(s_panopticPool),
428                 assets
429             );
430     
431             // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
432             _mint(receiver, shares);
433     
434             // update tracked asset balance
435             unchecked {
436                 s_poolAssets += uint128(assets);
437             }
438     
439             emit Deposit(msg.sender, receiver, assets, shares);
440         }


444         function maxMint(address) external view returns (uint256 maxShares) {
445             unchecked {
446                 return (convertToShares(type(uint104).max) * DECIMALS) / (DECIMALS + COMMISSION_FEE);
447             }
448         }


453         function previewMint(uint256 shares) public view returns (uint256 assets) {
454             // round up depositing assets to avoid protocol loss
455             // This prevents minting of shares where the assets provided is rounded down to zero
456             // compute the MEV tax, which is equal to a single payment of the commissionRate on the FINAL (post mev-tax) assets paid
457             // finalAssets - convertedAssets = commissionRate * finalAssets
458             // finalAssets - commissionRate * finalAssets = convertedAssets
459             // finalAssets * (1 - commissionRate) = convertedAssets
460             // finalAssets = convertedAssets / (1 - commissionRate)
461             unchecked {
462                 assets = Math.mulDivRoundingUp(
463                     shares * DECIMALS,
464                     totalAssets(),
465                     totalSupply * (DECIMALS - COMMISSION_FEE)
466                 );
467             }
468         }


477         function mint(uint256 shares, address receiver) external returns (uint256 assets) {
478             assets = previewMint(shares);
479     
480             if (assets > type(uint104).max) revert Errors.DepositTooLarge();
481     
482             // transfer assets (underlying token funds) from the user/the LP to the PanopticPool
483             // in return for the shares to be minted
484             SafeTransferLib.safeTransferFrom(
485                 s_underlyingToken,
486                 msg.sender,
487                 address(s_panopticPool),
488                 assets
489             );
490     
491             // mint collateral shares of the Panoptic Pool funds (this ERC20 token)
492             _mint(receiver, shares);
493     
494             // update tracked asset balance
495             unchecked {
496                 s_poolAssets += uint128(assets);
497             }
498     
499             emit Deposit(msg.sender, receiver, assets, shares);
500         }


507         function maxWithdraw(address owner) public view returns (uint256 maxAssets) {
508             // We can only use the standard 4626 withdraw function if the user has no open positions
509             // For the sake of simplicity assets can only be withdrawn through the redeem function
510             uint256 available = s_poolAssets;
511             uint256 balance = convertToAssets(balanceOf[owner]);
512             return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;
513         }


518         function previewWithdraw(uint256 assets) public view returns (uint256 shares) {
519             uint256 supply = totalSupply; // Saves an extra SLOAD if totalSupply is non-zero.
520     
521             return Math.mulDivRoundingUp(assets, supply, totalAssets());
522         }


531         function withdraw(
532             uint256 assets,
533             address receiver,
534             address owner
535         ) external returns (uint256 shares) {
536             if (assets > maxWithdraw(owner)) revert Errors.ExceedsMaximumRedemption();
537     
538             shares = previewWithdraw(assets);
539     
540             // check/update allowance for approved withdraw
541             if (msg.sender != owner) {
542                 uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.
543     
544                 if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
545             }
546     
547             // burn collateral shares of the Panoptic Pool funds (this ERC20 token)
548             _burn(owner, shares);
549     
550             // update tracked asset balance
551             unchecked {
552                 s_poolAssets -= uint128(assets);
553             }
554     
555             // transfer assets (underlying token funds) from the PanopticPool to the LP
556             SafeTransferLib.safeTransferFrom(
557                 s_underlyingToken,
558                 address(s_panopticPool),
559                 receiver,
560                 assets
561             );
562     
563             emit Withdraw(msg.sender, receiver, owner, assets, shares);
564     
565             return shares;
566         }


572         function maxRedeem(address owner) public view returns (uint256 maxShares) {
573             uint256 available = convertToShares(s_poolAssets);
574             uint256 balance = balanceOf[owner];
575             return s_panopticPool.numberOfPositions(owner) == 0 ? Math.min(available, balance) : 0;
576         }


581         function previewRedeem(uint256 shares) public view returns (uint256 assets) {
582             return convertToAssets(shares);
583         }


591         function redeem(
592             uint256 shares,
593             address receiver,
594             address owner
595         ) external returns (uint256 assets) {
596             if (shares > maxRedeem(owner)) revert Errors.ExceedsMaximumRedemption();
597     
598             // check/update allowance for approved redeem
599             if (msg.sender != owner) {
600                 uint256 allowed = allowance[owner][msg.sender]; // Saves gas for limited approvals.
601     
602                 if (allowed != type(uint256).max) allowance[owner][msg.sender] = allowed - shares;
603             }
604     
605             assets = previewRedeem(shares);
606     
607             // burn collateral shares of the Panoptic Pool funds (this ERC20 token)
608             _burn(owner, shares);
609     
610             // update tracked asset balance
611             unchecked {
612                 s_poolAssets -= uint128(assets);
613             }
614     
615             // transfer assets (underlying token funds) from the PanopticPool to the LP
616             SafeTransferLib.safeTransferFrom(
617                 s_underlyingToken,
618                 address(s_panopticPool),
619                 receiver,
620                 assets
621             );
622     
623             emit Withdraw(msg.sender, receiver, owner, assets, shares);
624     
625             return assets;
626         }


650         function exerciseCost(
651             int24 currentTick,
652             int24 oracleTick,
653             TokenId positionId,
654             uint128 positionBalance,
655             LeftRightSigned longAmounts
656         ) external view returns (LeftRightSigned exerciseFees) {
657             // find the leg furthest to the strike price 'currentTick'; this will have the lowest exercise cost
658             // we don't need the leg information itself, really just "the number of half ranges" from the strike price:
659             uint256 maxNumRangesFromStrike = 1; // technically "maxNum(Half)RangesFromStrike" but the name is long
660     
661             unchecked {
662                 for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {
663                     // short legs are not counted - exercise is intended to be based on long legs
664                     if (positionId.isLong(leg) == 0) continue;
665     
666                     {
667                         int24 range = int24(
668                             int256(
669                                 Math.unsafeDivRoundingUp(
670                                     uint24(positionId.width(leg) * positionId.tickSpacing()),
671                                     2
672                                 )
673                             )
674                         );
675                         maxNumRangesFromStrike = Math.max(
676                             maxNumRangesFromStrike,
677                             uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
678                         );
679                     }
680     
681                     uint256 currentValue0;
682                     uint256 currentValue1;
683                     uint256 oracleValue0;
684                     uint256 oracleValue1;
685     
686                     {
687                         LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
688                             positionId,
689                             leg,
690                             positionBalance
691                         );
692     
693                         (currentValue0, currentValue1) = Math.getAmountsForLiquidity(
694                             currentTick,
695                             liquidityChunk
696                         );
697     
698                         (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(
699                             oracleTick,
700                             liquidityChunk
701                         );
702                     }
703     
704                     uint256 tokenType = positionId.tokenType(leg);
705                     // compensate user for loss in value if chunk has lost money between current and median tick
706                     // note: the delta for one token will be positive and the other will be negative. This cancels out any moves in their positions
707                     if (
708                         (tokenType == 0 && currentValue1 < oracleValue1) ||
709                         (tokenType == 1 && currentValue0 < oracleValue0)
710                     )
711                         exerciseFees = exerciseFees.sub(
712                             LeftRightSigned
713                                 .wrap(0)
714                                 .toRightSlot(
715                                     int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
716                                 )
717                                 .toLeftSlot(
718                                     int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
719                                 )
720                         );
721                 }
722     
723                 // note: we HAVE to start with a negative number as the base exercise cost because when shifting a negative number right by n bits,
724                 // the result is rounded DOWN and NOT toward zero
725                 // this divergence is observed when n (the number of half ranges) is > 10 (ensuring the floor is not zero, but -1 = 1bps at that point)
726                 // subtract 1 from max half ranges from strike so fee starts at FORCE_EXERCISE_COST when moving OTM
727                 int256 fee = (FORCE_EXERCISE_COST >> (maxNumRangesFromStrike - 1)); // exponential decay of fee based on number of half ranges away from the price
728     
729                 // store the exercise fees in the exerciseFees variable
730                 exerciseFees = exerciseFees
731                     .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))
732                     .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));
733             }
734         }


864         function delegate(
865             address delegator,
866             address delegatee,
867             uint256 assets
868         ) external onlyPanopticPool {
869             /*
870                     ┌────────┐
871                     │Panoptic│
872                     │Pool    │
873                     └────┬───┘
874                          │(1) convert 'assets' to shares (this ERC20 contract)
875             ┌─────────┐  │  ┌─────────┐
876             │delegator├──▼──►delegatee│
877             └─────────┘(2)  └─────────┘
878                     move shares
879                     from delegator
880                     to delegatee
881             */
882     
883             uint256 shares = convertToShares(assets);
884     
885             // transfer shares from the delegator to the delegatee
886             _transferFrom(delegator, delegatee, shares);
887         }


894         function delegate(address delegatee, uint256 assets) external onlyPanopticPool {
895             balanceOf[delegatee] += convertToShares(assets);
896         }


903         function refund(address delegatee, uint256 assets) external onlyPanopticPool {
904             balanceOf[delegatee] -= convertToShares(assets);
905         }


911         function revoke(
912             address delegator,
913             address delegatee,
914             uint256 assets
915         ) external onlyPanopticPool {
916             /**
917                     ┌────────┐
918                     │Panoptic│
919                     │Pool    │
920                     └────┬───┘
921                          │(1) convert 'assets' to shares (this ERC20 contract)
922             ┌─────────┐  │ ┌─────────┐
923             │delegator◄──▼─┤delegatee│
924             └─────────┘(2) └─────────┘
925                 moves shares
926                 from delegatee
927                 back to delegator
928             */
929     
930             uint256 shares = convertToShares(assets);
931     
932             // get the delegateeBalance and compare later against requestedAmount
933             uint256 delegateeBalance = balanceOf[delegatee];
934     
935             // if requested amount is larger than user balance, transfer shares back,
936             // then issue new shares
937             if (shares > delegateeBalance) {
938                 // transfer delegatee balance to delegator
939                 _transferFrom(delegatee, delegator, delegateeBalance);
940     
941                 // this is paying out protocol loss, so correct for that in the amount of shares to be minted
942                 // X: total assets in vault
943                 // Y: total supply of shares
944                 // Z: desired value (assets) of shares to be minted
945                 // N: total shares corresponding to Z
946                 // T: transferred shares from liquidatee which are a component of N but do not contribute toward protocol loss
947                 // Z = N * X / (Y + N - T)
948                 // Z * (Y + N - T) = N * X
949                 // ZY + ZN - ZT = NX
950                 // ZY - ZT = N(X - Z)
951                 // N = (ZY - ZT) / (X - Z)
952                 // N = Z(Y - T) / (X - Z)
953                 // subtract delegatee balance from N since it was already transferred to the delegator
954                 _mint(
955                     delegator,
956                     Math.mulDiv(
957                         assets,
958                         totalSupply - delegateeBalance,
959                         uint256(Math.max(1, int256(totalAssets()) - int256(assets)))
960                     ) - delegateeBalance
961                 );
962             }
963             // if requested amount < delegatee balance, then just transfer shares back
964             else {
965                 _transferFrom(delegatee, delegator, shares);
966             }
967         }


975         function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {
976             if (assets > 0) {
977                 _transferFrom(refunder, refundee, convertToShares(uint256(assets)));
978             } else {
979                 unchecked {
980                     _transferFrom(refundee, refunder, convertToShares(uint256(-assets)));
981                 }
982             }
983         }


995         function takeCommissionAddData(
996             address optionOwner,
997             int128 longAmount,
998             int128 shortAmount,
999             int128 swappedAmount
1000        ) external onlyPanopticPool returns (int256 utilization) {
1001            unchecked {
1002                // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
1003                int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
1004    
1005                // constrict premium to only assets not belonging to PLPs (i.e premium paid by sellers or collected from the pool earlier)
1006                int256 tokenToPay = _getExchangedAmount(longAmount, shortAmount, swappedAmount);
1007    
1008                // compute tokens to be paid due to swap
1009                // mint or burn tokens due to minting in-the-money
1010                if (tokenToPay > 0) {
1011                    // if user must pay tokens, burn them from user balance
1012                    uint256 sharesToBurn = Math.mulDivRoundingUp(
1013                        uint256(tokenToPay),
1014                        totalSupply,
1015                        totalAssets()
1016                    );
1017                    _burn(optionOwner, sharesToBurn);
1018                } else if (tokenToPay < 0) {
1019                    // if user must receive tokens, mint them
1020                    uint256 sharesToMint = convertToShares(uint256(-tokenToPay));
1021                    _mint(optionOwner, sharesToMint);
1022                }
1023    
1024                // update stored asset balances with net moved amounts
1025                // the inflow or outflow of pool assets is defined by the swappedAmount: it includes both the ITM swap amounts and the short/long amounts used to create the position
1026                // however, any intrinsic value is paid for by the users, so we only add the portion that comes from PLPs: the short/long amounts
1027                // premia is not included in the balance since it is the property of options buyers and sellers, not PLPs
1028                s_poolAssets = uint128(uint256(updatedAssets));
1029                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));
1030    
1031                utilization = _poolUtilization();
1032            }
1033        }


1043        function exercise(
1044            address optionOwner,
1045            int128 longAmount,
1046            int128 shortAmount,
1047            int128 swappedAmount,
1048            int128 realizedPremium
1049        ) external onlyPanopticPool returns (int128) {
1050            unchecked {
1051                // current available assets belonging to PLPs (updated after settlement) excluding any premium paid
1052                int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;
1053    
1054                // add premium to be paid/collected on position close
1055                int256 tokenToPay = -realizedPremium;
1056    
1057                // if burning ITM and swap occurred, compute tokens to be paid through exercise and add swap fees
1058                int256 intrinsicValue = swappedAmount - (longAmount - shortAmount);
1059    
1060                if ((intrinsicValue != 0) && ((shortAmount != 0) || (longAmount != 0))) {
1061                    // intrinsic value is the amount that need to be exchanged due to burning in-the-money
1062    
1063                    // add the intrinsic value to the tokenToPay
1064                    tokenToPay += intrinsicValue;
1065                }
1066    
1067                if (tokenToPay > 0) {
1068                    // if user must pay tokens, burn them from user balance (revert if balance too small)
1069                    uint256 sharesToBurn = Math.mulDivRoundingUp(
1070                        uint256(tokenToPay),
1071                        totalSupply,
1072                        totalAssets()
1073                    );
1074                    _burn(optionOwner, sharesToBurn);
1075                } else if (tokenToPay < 0) {
1076                    // if user must receive tokens, mint them
1077                    uint256 sharesToMint = convertToShares(uint256(-tokenToPay));
1078                    _mint(optionOwner, sharesToMint);
1079                }
1080    
1081                // update stored asset balances with net moved amounts
1082                // any intrinsic value is paid for by the users, so we do not add it to s_inAMM
1083                // premia is not included in the balance since it is the property of options buyers and sellers, not PLPs
1084                s_poolAssets = uint128(uint256(updatedAssets + realizedPremium));
1085                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));
1086    
1087                return (int128(tokenToPay));
1088            }
1089        }


1141        function getAccountMarginDetails(
1142            address user,
1143            int24 currentTick,
1144            uint256[2][] memory positionBalanceArray,
1145            int128 premiumAllPositions
1146        ) public view returns (LeftRightUnsigned tokenData) {
1147            tokenData = _getAccountMargin(user, currentTick, positionBalanceArray, premiumAllPositions);
1148        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1141:1148

```solidity
File: contracts/PanopticFactory.sol


134         function initialize(address _owner) public {
135             if (!s_initialized) {
136                 s_owner = _owner;
137                 s_initialized = true;
138             }
139         }


147         function transferOwnership(address newOwner) external {
148             address currentOwner = s_owner;
149     
150             if (msg.sender != currentOwner) revert Errors.NotOwner();
151     
152             s_owner = newOwner;
153     
154             emit OwnershipTransferred(currentOwner, newOwner);
155         }


159         function owner() external view returns (address) {
160             return s_owner;
161         }


172         function uniswapV3MintCallback(
173             uint256 amount0Owed,
174             uint256 amount1Owed,
175             bytes calldata data
176         ) external {
177             CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));
178     
179             CallbackLib.validateCallback(msg.sender, UNIV3_FACTORY, decoded.poolFeatures);
180     
181             if (amount0Owed > 0)
182                 SafeTransferLib.safeTransferFrom(
183                     decoded.poolFeatures.token0,
184                     decoded.payer,
185                     msg.sender,
186                     amount0Owed
187                 );
188             if (amount1Owed > 0)
189                 SafeTransferLib.safeTransferFrom(
190                     decoded.poolFeatures.token1,
191                     decoded.payer,
192                     msg.sender,
193                     amount1Owed
194                 );
195         }


210         function deployNewPool(
211             address token0,
212             address token1,
213             uint24 fee,
214             bytes32 salt
215         ) external returns (PanopticPool newPoolContract) {
216             // sort the tokens, if necessary:
217             (token0, token1) = token0 < token1 ? (token0, token1) : (token1, token0);
218     
219             // frontrunning protection for mined pool addresses
220             if (address(bytes20(salt)) != msg.sender) revert Errors.InvalidSalt();
221     
222             // restrict pool deployment to owner if contract has not been made permissionless
223             address _owner = s_owner;
224             if (_owner != address(0) && _owner != msg.sender) revert Errors.NotOwner();
225     
226             IUniswapV3Pool v3Pool = IUniswapV3Pool(UNIV3_FACTORY.getPool(token0, token1, fee));
227             if (address(v3Pool) == address(0)) revert Errors.UniswapPoolNotInitialized();
228     
229             if (address(s_getPanopticPool[v3Pool]) != address(0))
230                 revert Errors.PoolAlreadyInitialized();
231     
232             // initialize pool in SFPM if it has not already been initialized
233             SFPM.initializeAMMPool(token0, token1, fee);
234     
235             // This creates a new Panoptic Pool (proxy to the PanopticPool implementation)
236             // Users can specify a salt, the aim is to incentivize the mining of addresses with leading zeros
237             newPoolContract = PanopticPool(POOL_REFERENCE.cloneDeterministic(salt));
238     
239             // Deploy collateral token proxies
240             CollateralTracker collateralTracker0 = CollateralTracker(
241                 Clones.clone(COLLATERAL_REFERENCE)
242             );
243             CollateralTracker collateralTracker1 = CollateralTracker(
244                 Clones.clone(COLLATERAL_REFERENCE)
245             );
246     
247             // Run state initialization sequence for pool and collateral tokens
248             collateralTracker0.startToken(true, token0, token1, fee, newPoolContract);
249             collateralTracker1.startToken(false, token0, token1, fee, newPoolContract);
250     
251             newPoolContract.startPool(v3Pool, token0, token1, collateralTracker0, collateralTracker1);
252     
253             s_getPanopticPool[v3Pool] = newPoolContract;
254     
255             // The Panoptic pool won't be safe to use until the observation cardinality is at least CARDINALITY_INCREASE
256             // If this is not the case, we increase the next cardinality during deployment so the cardinality can catch up over time
257             // When that happens, there will be a period of time where the PanopticPool is deployed, but not (safely) usable
258             v3Pool.increaseObservationCardinalityNext(CARDINALITY_INCREASE);
259     
260             // Mints the full-range initial deposit
261             // which is why the deployer becomes also a "donor" of full-range liquidity
262             // The SFPM will `safeTransferFrom` tokens from the donor during the mint callback
263             (uint256 amount0, uint256 amount1) = _mintFullRange(v3Pool, token0, token1, fee);
264     
265             // Issue reward NFT to donor
266             DONOR_NFT.issueNFT(msg.sender, newPoolContract, token0, token1, fee);
267     
268             emit PoolDeployed(
269                 newPoolContract,
270                 v3Pool,
271                 collateralTracker0,
272                 collateralTracker1,
273                 amount0,
274                 amount1
275             );
276         }


290         function minePoolAddress(
291             bytes32 salt,
292             uint256 loops,
293             uint256 minTargetRarity
294         ) external view returns (bytes32 bestSalt, uint256 highestRarity) {
295             // Start at the given 'salt' value (a checkpoint used to continue mining across multiple calls)
296     
297             // Runs until 'bestSalt' reaches 'minTargetRarity' or for 'loops', whichever comes first
298             uint256 maxSalt;
299             unchecked {
300                 maxSalt = uint256(salt) + loops;
301             }
302     
303             for (; uint256(salt) < maxSalt; ) {
304                 uint256 rarity = PanopticMath.numberOfLeadingHexZeros(
305                     POOL_REFERENCE.predictDeterministicAddress(salt)
306                 );
307     
308                 if (rarity > highestRarity) {
309                     // found a more rare address at this nonce
310                     highestRarity = rarity;
311                     bestSalt = salt;
312                 }
313     
314                 if (rarity >= minTargetRarity) {
315                     // desired target met
316                     highestRarity = rarity;
317                     bestSalt = salt;
318                     break;
319                 }
320     
321                 unchecked {
322                     // increment the nonce of `currentSalt` (lower 96 bits)
323                     salt = bytes32(uint256(salt) + 1);
324                 }
325             }
326         }


420         function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {
421             return s_getPanopticPool[univ3pool];
422         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L420:422

```solidity
File: contracts/PanopticPool.sol


291         function startPool(
292             IUniswapV3Pool _univ3pool,
293             address token0,
294             address token1,
295             CollateralTracker collateralTracker0,
296             CollateralTracker collateralTracker1
297         ) external {
298             // reverts if the Uniswap pool has already been initialized
299             if (address(s_univ3pool) != address(0)) revert Errors.PoolAlreadyInitialized();
300     
301             // Store the univ3Pool variable
302             s_univ3pool = IUniswapV3Pool(_univ3pool);
303     
304             (, int24 currentTick, , , , , ) = IUniswapV3Pool(_univ3pool).slot0();
305     
306             // Store the median data
307             unchecked {
308                 s_miniMedian =
309                     (uint256(block.timestamp) << 216) +
310                     // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
311                     // see comment on s_miniMedian initialization for format of this magic number
312                     (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
313                     (uint256(uint24(currentTick)) << 24) + // add to slot 4
314                     (uint256(uint24(currentTick))); // add to slot 3
315             }
316     
317             // Store the collateral token0
318             s_collateralToken0 = collateralTracker0;
319             s_collateralToken1 = collateralTracker1;
320     
321             // consolidate all 4 approval calls to one library delegatecall in order to reduce bytecode size
322             // approves:
323             // SFPM: token0, token1
324             // CollateralTracker0 - token0
325             // CollateralTracker1 - token1
326             InteractionHelper.doApprovals(SFPM, collateralTracker0, collateralTracker1, token0, token1);
327         }


338         function assertPriceWithinBounds(uint160 sqrtLowerBound, uint160 sqrtUpperBound) external view {
339             (uint160 currentSqrtPriceX96, , , , , , ) = s_univ3pool.slot0();
340     
341             if (currentSqrtPriceX96 <= sqrtLowerBound || currentSqrtPriceX96 >= sqrtUpperBound) {
342                 revert Errors.PriceBoundFail();
343             }
344         }


352         function optionPositionBalance(
353             address user,
354             TokenId tokenId
355         ) external view returns (uint128 balance, uint64 poolUtilization0, uint64 poolUtilization1) {
356             // Extract the data stored in s_positionBalance for the provided user + tokenId
357             LeftRightUnsigned balanceData = s_positionBalance[user][tokenId];
358     
359             // Return the unpacked data: balanceOf(user, tokenId) and packed pool utilizations at the time of minting
360             balance = balanceData.rightSlot();
361     
362             // pool utilizations are packed into a single uint128
363     
364             // the 64 least significant bits are the utilization of token0, so we can simply cast to uint64 to extract it
365             // (cutting off the 64 most significant bits)
366             poolUtilization0 = uint64(balanceData.leftSlot());
367     
368             // the 64 most significant bits are the utilization of token1, so we can shift the number to the right by 64 to extract it
369             // (shifting away the 64 least significant bits)
370             poolUtilization1 = uint64(balanceData.leftSlot() >> 64);
371         }


381         function calculateAccumulatedFeesBatch(
382             address user,
383             bool includePendingPremium,
384             TokenId[] calldata positionIdList
385         ) external view returns (int128 premium0, int128 premium1, uint256[2][] memory) {
386             // Get the current tick of the Uniswap pool
387             (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
388     
389             // Compute the accumulated premia for all tokenId in positionIdList (includes short+long premium)
390             (LeftRightSigned premia, uint256[2][] memory balances) = _calculateAccumulatedPremia(
391                 user,
392                 positionIdList,
393                 COMPUTE_ALL_PREMIA,
394                 includePendingPremium,
395                 currentTick
396             );
397     
398             // Return the premia as (token0, token1)
399             return (premia.rightSlot(), premia.leftSlot(), balances);
400         }


410         function calculatePortfolioValue(
411             address user,
412             int24 atTick,
413             TokenId[] calldata positionIdList
414         ) external view returns (int256 value0, int256 value1) {
415             (value0, value1) = FeesCalc.getPortfolioValue(
416                 atTick,
417                 s_positionBalance[user],
418                 positionIdList
419             );
420         }


522         function pokeMedian() external {
523             (, , uint16 observationIndex, uint16 observationCardinality, , , ) = s_univ3pool.slot0();
524     
525             (, uint256 medianData) = PanopticMath.computeInternalMedian(
526                 observationIndex,
527                 observationCardinality,
528                 MEDIAN_PERIOD,
529                 s_miniMedian,
530                 s_univ3pool
531             );
532     
533             if (medianData != 0) s_miniMedian = medianData;
534         }


547         function mintOptions(
548             TokenId[] calldata positionIdList,
549             uint128 positionSize,
550             uint64 effectiveLiquidityLimitX32,
551             int24 tickLimitLow,
552             int24 tickLimitHigh
553         ) external {
554             _mintOptions(
555                 positionIdList,
556                 positionSize,
557                 effectiveLiquidityLimitX32,
558                 tickLimitLow,
559                 tickLimitHigh
560             );
561         }


569         function burnOptions(
570             TokenId tokenId,
571             TokenId[] calldata newPositionIdList,
572             int24 tickLimitLow,
573             int24 tickLimitHigh
574         ) external {
575             _burnOptions(COMMIT_LONG_SETTLED, tokenId, msg.sender, tickLimitLow, tickLimitHigh);
576     
577             _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);
578         }


586         function burnOptions(
587             TokenId[] calldata positionIdList,
588             TokenId[] calldata newPositionIdList,
589             int24 tickLimitLow,
590             int24 tickLimitHigh
591         ) external {
592             _burnAllOptionsFrom(
593                 msg.sender,
594                 tickLimitLow,
595                 tickLimitHigh,
596                 COMMIT_LONG_SETTLED,
597                 positionIdList
598             );
599     
600             _validateSolvency(msg.sender, newPositionIdList, NO_BUFFER);
601         }


1017        function liquidate(
1018            TokenId[] calldata positionIdListLiquidator,
1019            address liquidatee,
1020            LeftRightUnsigned delegations,
1021            TokenId[] calldata positionIdList
1022        ) external {
1023            _validatePositionList(liquidatee, positionIdList, 0);
1024    
1025            // Assert the account we are liquidating is actually insolvent
1026            int24 twapTick = getUniV3TWAP();
1027    
1028            LeftRightUnsigned tokenData0;
1029            LeftRightUnsigned tokenData1;
1030            LeftRightSigned premia;
1031            {
1032                (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
1033    
1034                // Enforce maximum delta between TWAP and currentTick to prevent extreme price manipulation
1035                if (Math.abs(currentTick - twapTick) > MAX_TWAP_DELTA_LIQUIDATION)
1036                    revert Errors.StaleTWAP();
1037    
1038                uint256[2][] memory positionBalanceArray = new uint256[2][](positionIdList.length);
1039                (premia, positionBalanceArray) = _calculateAccumulatedPremia(
1040                    liquidatee,
1041                    positionIdList,
1042                    COMPUTE_ALL_PREMIA,
1043                    ONLY_AVAILABLE_PREMIUM,
1044                    currentTick
1045                );
1046                tokenData0 = s_collateralToken0.getAccountMarginDetails(
1047                    liquidatee,
1048                    twapTick,
1049                    positionBalanceArray,
1050                    premia.rightSlot()
1051                );
1052    
1053                tokenData1 = s_collateralToken1.getAccountMarginDetails(
1054                    liquidatee,
1055                    twapTick,
1056                    positionBalanceArray,
1057                    premia.leftSlot()
1058                );
1059    
1060                (uint256 balanceCross, uint256 thresholdCross) = _getSolvencyBalances(
1061                    tokenData0,
1062                    tokenData1,
1063                    Math.getSqrtRatioAtTick(twapTick)
1064                );
1065    
1066                if (balanceCross >= thresholdCross) revert Errors.NotMarginCalled();
1067            }
1068    
1069            // Perform the specified delegation from `msg.sender` to `liquidatee`
1070            // Works like a transfer, so the liquidator must possess all the tokens they are delegating, resulting in no net supply change
1071            // If not enough tokens are delegated for the positions of `liquidatee` to be closed, the liquidation will fail
1072            s_collateralToken0.delegate(msg.sender, liquidatee, delegations.rightSlot());
1073            s_collateralToken1.delegate(msg.sender, liquidatee, delegations.leftSlot());
1074    
1075            int256 liquidationBonus0;
1076            int256 liquidationBonus1;
1077            int24 finalTick;
1078            {
1079                LeftRightSigned netExchanged;
1080                LeftRightSigned[4][] memory premiasByLeg;
1081                // burn all options from the liquidatee
1082    
1083                // Do not commit any settled long premium to storage - we will do this after we determine if any long premium must be revoked
1084                // This is to prevent any short positions the liquidatee has being settled with tokens that will later be revoked
1085                // Note: tick limits are not applied here since it is not the liquidator's position being liquidated
1086                (netExchanged, premiasByLeg) = _burnAllOptionsFrom(
1087                    liquidatee,
1088                    Constants.MIN_V3POOL_TICK,
1089                    Constants.MAX_V3POOL_TICK,
1090                    DONOT_COMMIT_LONG_SETTLED,
1091                    positionIdList
1092                );
1093    
1094                (, finalTick, , , , , ) = s_univ3pool.slot0();
1095    
1096                LeftRightSigned collateralRemaining;
1097                // compute bonus amounts using latest tick data
1098                (liquidationBonus0, liquidationBonus1, collateralRemaining) = PanopticMath
1099                    .getLiquidationBonus(
1100                        tokenData0,
1101                        tokenData1,
1102                        Math.getSqrtRatioAtTick(twapTick),
1103                        Math.getSqrtRatioAtTick(finalTick),
1104                        netExchanged,
1105                        premia
1106                    );
1107    
1108                // premia cannot be paid if there is protocol loss associated with the liquidatee
1109                // otherwise, an economic exploit could occur if the liquidator and liquidatee collude to
1110                // manipulate the fees in a liquidity area they control past the protocol loss threshold
1111                // such that the PLPs are forced to pay out premia to the liquidator
1112                // thus, we haircut any premium paid by the liquidatee (converting tokens as necessary) until the protocol loss is covered or the premium is exhausted
1113                // note that the haircutPremia function also commits the settled amounts (adjusted for the haircut) to storage, so it will be called even if there is no haircut
1114    
1115                // if premium is haircut from a token that is not in protocol loss, some of the liquidation bonus will be converted into that token
1116                // reusing variables to save stack space; netExchanged = deltaBonus0, premia = deltaBonus1
1117                address _liquidatee = liquidatee;
1118                TokenId[] memory _positionIdList = positionIdList;
1119                int24 _finalTick = finalTick;
1120                int256 deltaBonus0;
1121                int256 deltaBonus1;
1122                (deltaBonus0, deltaBonus1) = PanopticMath.haircutPremia(
1123                    _liquidatee,
1124                    _positionIdList,
1125                    premiasByLeg,
1126                    collateralRemaining,
1127                    s_collateralToken0,
1128                    s_collateralToken1,
1129                    Math.getSqrtRatioAtTick(_finalTick),
1130                    s_settledTokens
1131                );
1132    
1133                unchecked {
1134                    liquidationBonus0 += deltaBonus0;
1135                    liquidationBonus1 += deltaBonus1;
1136                }
1137            }
1138    
1139            LeftRightUnsigned _delegations = delegations;
1140            // revoke the delegated amount plus the bonus amount.
1141            s_collateralToken0.revoke(
1142                msg.sender,
1143                liquidatee,
1144                uint256(int256(uint256(_delegations.rightSlot())) + liquidationBonus0)
1145            );
1146            s_collateralToken1.revoke(
1147                msg.sender,
1148                liquidatee,
1149                uint256(int256(uint256(_delegations.leftSlot())) + liquidationBonus1)
1150            );
1151    
1152            // check that the provided positionIdList matches the positions in memory
1153            _validatePositionList(msg.sender, positionIdListLiquidator, 0);
1154    
1155            if (
1156                !_checkSolvencyAtTick(
1157                    msg.sender,
1158                    positionIdListLiquidator,
1159                    finalTick,
1160                    finalTick,
1161                    BP_DECREASE_BUFFER
1162                )
1163            ) revert Errors.NotEnoughCollateral();
1164    
1165            LeftRightSigned bonusAmounts = LeftRightSigned
1166                .wrap(0)
1167                .toRightSlot(int128(liquidationBonus0))
1168                .toLeftSlot(int128(liquidationBonus1));
1169    
1170            emit AccountLiquidated(msg.sender, liquidatee, bonusAmounts);
1171        }


1179        function forceExercise(
1180            address account,
1181            TokenId[] calldata touchedId,
1182            TokenId[] calldata positionIdListExercisee,
1183            TokenId[] calldata positionIdListExercisor
1184        ) external {
1185            // revert if multiple positions are specified
1186            // the reason why the singular touchedId is an array is so it composes well with the rest of the system
1187            // '_calculateAccumulatedPremia' expects a list of positions to be touched, and this is the only way to pass a single position
1188            if (touchedId.length != 1) revert Errors.InputListFail();
1189    
1190            // validate the exercisor's position list (the exercisee's list will be evaluated after their position is force exercised)
1191            _validatePositionList(msg.sender, positionIdListExercisor, 0);
1192    
1193            uint128 positionBalance = s_positionBalance[account][touchedId[0]].rightSlot();
1194    
1195            // compute the notional value of the short legs (the maximum amount of tokens required to exercise - premia)
1196            // and the long legs (from which the exercise cost is computed)
1197            (LeftRightSigned longAmounts, LeftRightSigned delegatedAmounts) = PanopticMath
1198                .computeExercisedAmounts(touchedId[0], positionBalance);
1199    
1200            int24 twapTick = getUniV3TWAP();
1201    
1202            (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
1203    
1204            {
1205                // add the premia to the delegated amounts to ensure the user has enough collateral to exercise
1206                (LeftRightSigned positionPremia, ) = _calculateAccumulatedPremia(
1207                    account,
1208                    touchedId,
1209                    COMPUTE_LONG_PREMIA,
1210                    ONLY_AVAILABLE_PREMIUM,
1211                    currentTick
1212                );
1213    
1214                // long premia is represented as negative so subtract it to increase it for the delegated amounts
1215                delegatedAmounts = delegatedAmounts.sub(positionPremia);
1216            }
1217    
1218            // on forced exercise, the price *must* be outside the position's range for at least 1 leg
1219            touchedId[0].validateIsExercisable(twapTick);
1220    
1221            // The protocol delegates some virtual shares to ensure the burn can be settled.
1222            s_collateralToken0.delegate(account, uint128(delegatedAmounts.rightSlot()));
1223            s_collateralToken1.delegate(account, uint128(delegatedAmounts.leftSlot()));
1224    
1225            // Exercise the option
1226            // Note: tick limits are not applied here since it is not the exercisor's position being closed
1227            _burnAllOptionsFrom(account, 0, 0, COMMIT_LONG_SETTLED, touchedId);
1228    
1229            // Compute the exerciseFee, this will decrease the further away the price is from the forcedExercised position
1230            /// @dev use the medianTick to prevent price manipulations based on swaps.
1231            LeftRightSigned exerciseFees = s_collateralToken0.exerciseCost(
1232                currentTick,
1233                twapTick,
1234                touchedId[0],
1235                positionBalance,
1236                longAmounts
1237            );
1238    
1239            LeftRightSigned refundAmounts = delegatedAmounts.add(exerciseFees);
1240    
1241            // redistribute token composition of refund amounts if user doesn't have enough of one token to pay
1242            refundAmounts = PanopticMath.getRefundAmounts(
1243                account,
1244                refundAmounts,
1245                twapTick,
1246                s_collateralToken0,
1247                s_collateralToken1
1248            );
1249    
1250            unchecked {
1251                // settle difference between delegated amounts (from the protocol) and exercise fees/substituted tokens
1252                s_collateralToken0.refund(
1253                    account,
1254                    msg.sender,
1255                    refundAmounts.rightSlot() - delegatedAmounts.rightSlot()
1256                );
1257                s_collateralToken1.refund(
1258                    account,
1259                    msg.sender,
1260                    refundAmounts.leftSlot() - delegatedAmounts.leftSlot()
1261                );
1262            }
1263    
1264            // refund the protocol any virtual shares after settling the difference with the exercisor
1265            s_collateralToken0.refund(account, uint128(delegatedAmounts.rightSlot()));
1266            s_collateralToken1.refund(account, uint128(delegatedAmounts.leftSlot()));
1267    
1268            _validateSolvency(account, positionIdListExercisee, NO_BUFFER);
1269    
1270            // the exercisor's position list is validated above
1271            // we need to assert their solvency against their collateral requirement plus a buffer
1272            // force exercises involve a collateral decrease with open positions, so there is a higher standard for solvency
1273            // a similar buffer is also invoked when minting options, which also decreases the available collateral
1274            if (positionIdListExercisor.length > 0)
1275                _validateSolvency(msg.sender, positionIdListExercisor, BP_DECREASE_BUFFER);
1276    
1277            emit ForcedExercised(msg.sender, account, touchedId[0], exerciseFees);
1278        }


1425        function univ3pool() external view returns (IUniswapV3Pool) {
1426            return s_univ3pool;
1427        }


1431        function collateralToken0() external view returns (CollateralTracker collateralToken) {
1432            return s_collateralToken0;
1433        }


1437        function collateralToken1() external view returns (CollateralTracker) {
1438            return s_collateralToken1;
1439        }


1444        function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {
1445            _numberOfPositions = (s_positionsHash[user] >> 248);
1446        }


1587        function settleLongPremium(
1588            TokenId[] calldata positionIdList,
1589            address owner,
1590            uint256 legIndex
1591        ) external {
1592            _validatePositionList(owner, positionIdList, 0);
1593    
1594            TokenId tokenId = positionIdList[positionIdList.length - 1];
1595    
1596            if (tokenId.isLong(legIndex) == 0 || legIndex > 3) revert Errors.NotALongLeg();
1597    
1598            (, int24 currentTick, , , , , ) = s_univ3pool.slot0();
1599    
1600            LeftRightUnsigned accumulatedPremium;
1601            {
1602                (int24 tickLower, int24 tickUpper) = tokenId.asTicks(legIndex);
1603    
1604                uint256 tokenType = tokenId.tokenType(legIndex);
1605                (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
1606                    address(s_univ3pool),
1607                    address(this),
1608                    tokenType,
1609                    tickLower,
1610                    tickUpper,
1611                    currentTick,
1612                    1
1613                );
1614                accumulatedPremium = LeftRightUnsigned
1615                    .wrap(0)
1616                    .toRightSlot(premiumAccumulator0)
1617                    .toLeftSlot(premiumAccumulator1);
1618    
1619                // update the premium accumulator for the long position to the latest value
1620                // (the entire premia delta will be settled)
1621                LeftRightUnsigned premiumAccumulatorsLast = s_options[owner][tokenId][legIndex];
1622                s_options[owner][tokenId][legIndex] = accumulatedPremium;
1623    
1624                accumulatedPremium = accumulatedPremium.sub(premiumAccumulatorsLast);
1625            }
1626    
1627            uint256 liquidity = PanopticMath
1628                .getLiquidityChunk(tokenId, legIndex, s_positionBalance[owner][tokenId].rightSlot())
1629                .liquidity();
1630    
1631            unchecked {
1632                // update the realized premia
1633                LeftRightSigned realizedPremia = LeftRightSigned
1634                    .wrap(0)
1635                    .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))
1636                    .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));
1637    
1638                // deduct the paid premium tokens from the owner's balance and add them to the cumulative settled token delta
1639                s_collateralToken0.exercise(owner, 0, 0, 0, realizedPremia.rightSlot());
1640                s_collateralToken1.exercise(owner, 0, 0, 0, realizedPremia.leftSlot());
1641    
1642                bytes32 chunkKey = keccak256(
1643                    abi.encodePacked(
1644                        tokenId.strike(legIndex),
1645                        tokenId.width(legIndex),
1646                        tokenId.tokenType(legIndex)
1647                    )
1648                );
1649                // commit the delta in settled tokens (all of the premium paid by long chunks in the tokenIds list) to storage
1650                s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(
1651                    LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(realizedPremia)))
1652                );
1653    
1654                emit PremiumSettled(owner, tokenId, realizedPremia);
1655            }
1656    
1657            // ensure the owner is solvent (insolvent accounts are not permitted to pay premium unless they are being liquidated)
1658            _validateSolvency(owner, positionIdList, NO_BUFFER);
1659        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1587:1659

```solidity
File: contracts/SemiFungiblePositionManager.sol


350         function initializeAMMPool(address token0, address token1, uint24 fee) external {
351             // compute the address of the Uniswap v3 pool for the given token0, token1, and fee tier
352             address univ3pool = FACTORY.getPool(token0, token1, fee);
353     
354             // reverts if the Uni v3 pool has not been initialized
355             if (univ3pool == address(0)) revert Errors.UniswapPoolNotInitialized();
356     
357             // return if the pool has already been initialized in SFPM
358             // @dev pools can be initialized from a Panoptic pool or by calling initializeAMMPool directly, reverting
359             // would prevent any PanopticPool from being deployed
360             // @dev some pools may not be deployable if the poolId has a collision (since we take only 8 bytes)
361             // if poolId == 0, we have a bit on the left set if it was initialized, so this will still return properly
362             if (s_AddrToPoolIdData[univ3pool] != 0) return;
363     
364             // The base poolId is composed as follows:
365             // [tickSpacing][pool pattern]
366             // [16 bit tickSpacing][most significant 48 bits of the pool address]
367             uint64 poolId = PanopticMath.getPoolId(univ3pool);
368     
369             // There are 281,474,976,710,655 possible pool patterns.
370             // A modern GPU can generate a collision such a space relatively quickly,
371             // so if a collision is detected increment the pool pattern until a unique poolId is found
372             while (address(s_poolContext[poolId].pool) != address(0)) {
373                 poolId = PanopticMath.incrementPoolPattern(poolId);
374             }
375     
376             // store the poolId => UniswapV3Pool information in a mapping
377             // `locked` being initialized to false is gas-efficient because the pool address makes the slot nonzero
378             // note: we preserve the state of `locked` to prevent reentering a pool by initializing it during the reentrant call
379             s_poolContext[poolId] = PoolAddressAndLock({
380                 pool: IUniswapV3Pool(univ3pool),
381                 locked: s_poolContext[poolId].locked
382             });
383     
384             // store the UniswapV3Pool => poolId information in a mapping
385             // add a bit on the end to indicate that the pool is initialized
386             // (this is for the case that poolId == 0, so we can make a distinction between zero and uninitialized)
387             unchecked {
388                 s_AddrToPoolIdData[univ3pool] = uint256(poolId) + 2 ** 255;
389             }
390             emit PoolInitialized(univ3pool, poolId);
391         }


402         function uniswapV3MintCallback(
403             uint256 amount0Owed,
404             uint256 amount1Owed,
405             bytes calldata data
406         ) external {
407             // Decode the mint callback data
408             CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));
409             // Validate caller to ensure we got called from the AMM pool
410             CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);
411             // Sends the amount0Owed and amount1Owed quantities provided
412             if (amount0Owed > 0)
413                 SafeTransferLib.safeTransferFrom(
414                     decoded.poolFeatures.token0,
415                     decoded.payer,
416                     msg.sender,
417                     amount0Owed
418                 );
419             if (amount1Owed > 0)
420                 SafeTransferLib.safeTransferFrom(
421                     decoded.poolFeatures.token1,
422                     decoded.payer,
423                     msg.sender,
424                     amount1Owed
425                 );
426         }


435         function uniswapV3SwapCallback(
436             int256 amount0Delta,
437             int256 amount1Delta,
438             bytes calldata data
439         ) external {
440             // Decode the swap callback data, checks that the UniswapV3Pool has the correct address.
441             CallbackLib.CallbackData memory decoded = abi.decode(data, (CallbackLib.CallbackData));
442             // Validate caller to ensure we got called from the AMM pool
443             CallbackLib.validateCallback(msg.sender, FACTORY, decoded.poolFeatures);
444     
445             // Extract the address of the token to be sent (amount0 -> token0, amount1 -> token1)
446             address token = amount0Delta > 0
447                 ? address(decoded.poolFeatures.token0)
448                 : address(decoded.poolFeatures.token1);
449     
450             // Transform the amount to pay to uint256 (take positive one from amount0 and amount1)
451             // the pool will always pass one delta with a positive sign and one with a negative sign or zero,
452             // so this logic always picks the correct delta to pay
453             uint256 amountToPay = amount0Delta > 0 ? uint256(amount0Delta) : uint256(amount1Delta);
454     
455             // Pay the required token from the payer to the caller of this contract
456             SafeTransferLib.safeTransferFrom(token, decoded.payer, msg.sender, amountToPay);
457         }


471         function burnTokenizedPosition(
472             TokenId tokenId,
473             uint128 positionSize,
474             int24 slippageTickLimitLow,
475             int24 slippageTickLimitHigh
476         )
477             external
478             ReentrancyLock(tokenId.poolId())
479             returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
480         {
481             // burn this ERC1155 token id
482             _burn(msg.sender, TokenId.unwrap(tokenId), positionSize);
483     
484             // emit event
485             emit TokenizedPositionBurnt(msg.sender, tokenId, positionSize);
486     
487             // Call a function that contains other functions to mint/burn position, collect amounts, swap if necessary
488             (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
489                 tokenId,
490                 positionSize,
491                 slippageTickLimitLow,
492                 slippageTickLimitHigh,
493                 BURN
494             );
495         }


504         function mintTokenizedPosition(
505             TokenId tokenId,
506             uint128 positionSize,
507             int24 slippageTickLimitLow,
508             int24 slippageTickLimitHigh
509         )
510             external
511             ReentrancyLock(tokenId.poolId())
512             returns (LeftRightUnsigned[4] memory collectedByLeg, LeftRightSigned totalSwapped)
513         {
514             // create the option position via its ID in this erc1155
515             _mint(msg.sender, TokenId.unwrap(tokenId), positionSize);
516     
517             emit TokenizedPositionMinted(msg.sender, tokenId, positionSize);
518     
519             // validate the incoming option position, then forward to the AMM for minting/burning required liquidity chunks
520             (collectedByLeg, totalSwapped) = _validateAndForwardToAMM(
521                 tokenId,
522                 positionSize,
523                 slippageTickLimitLow,
524                 slippageTickLimitHigh,
525                 MINT
526             );
527         }


540         function safeTransferFrom(
541             address from,
542             address to,
543             uint256 id,
544             uint256 amount,
545             bytes calldata data
546         ) public override {
547             // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
548             // so just check if there is an active reentrancy lock for the relevant pool on the token we're transferring
549             if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();
550     
551             // update the position data
552             registerTokenTransfer(from, to, TokenId.wrap(id), amount);
553     
554             // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)
555             super.safeTransferFrom(from, to, id, amount, data);
556         }


566         function safeBatchTransferFrom(
567             address from,
568             address to,
569             uint256[] calldata ids,
570             uint256[] calldata amounts,
571             bytes calldata data
572         ) public override {
573             // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
574             // so just check if there is an active reentrancy lock for the relevant pool on each token
575             for (uint256 i = 0; i < ids.length; ) {
576                 if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
577                 registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
578                 unchecked {
579                     ++i;
580                 }
581             }
582     
583             // transfer the token (note that all state updates are completed before reentrancy is possible)
584             super.safeBatchTransferFrom(from, to, ids, amounts, data);
585         }


1421        function getAccountLiquidity(
1422            address univ3pool,
1423            address owner,
1424            uint256 tokenType,
1425            int24 tickLower,
1426            int24 tickUpper
1427        ) external view returns (LeftRightUnsigned accountLiquidities) {
1428            /// Extract the account liquidity for a given uniswap pool, owner, token type, and ticks
1429            /// @dev tokenType input here is the asset of the positions minted, this avoids put liquidity to be used for call, and vice-versa
1430            accountLiquidities = s_accountLiquidity[
1431                keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))
1432            ];
1433        }


1449        function getAccountPremium(
1450            address univ3pool,
1451            address owner,
1452            uint256 tokenType,
1453            int24 tickLower,
1454            int24 tickUpper,
1455            int24 atTick,
1456            uint256 isLong
1457        ) external view returns (uint128, uint128) {
1458            bytes32 positionKey = keccak256(
1459                abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper)
1460            );
1461    
1462            LeftRightUnsigned acctPremia;
1463    
1464            // Compute the premium up to the current block (ie. after last touch until now). Do not proceed if atTick == type(int24).max = 8388608
1465            if (atTick < type(int24).max) {
1466                // unique key to identify the liquidity chunk in this uniswap pool
1467                LeftRightUnsigned accountLiquidities = s_accountLiquidity[positionKey];
1468                uint128 netLiquidity = accountLiquidities.rightSlot();
1469                if (netLiquidity != 0) {
1470                    LeftRightUnsigned amountToCollect;
1471                    {
1472                        IUniswapV3Pool _univ3pool = IUniswapV3Pool(univ3pool);
1473                        int24 _tickLower = tickLower;
1474                        int24 _tickUpper = tickUpper;
1475    
1476                        // how much fees have been accumulated within the liquidity chunk since last time we updated this chunk?
1477                        // Compute (currentFeesGrowth - oldFeesGrowth), the amount to collect
1478                        // currentFeesGrowth (calculated from FeesCalc.calculateAMMSwapFeesLiquidityChunk) is (ammFeesCollectedPerLiquidity * liquidityChunk.liquidity())
1479                        // oldFeesGrowth is the last stored update of fee growth within the position range in the past (feeGrowthRange*liquidityChunk.liquidity()) (s_accountFeesBase[positionKey])
1480                        LeftRightSigned feesBase = FeesCalc.calculateAMMSwapFees(
1481                            _univ3pool,
1482                            atTick,
1483                            _tickLower,
1484                            _tickUpper,
1485                            netLiquidity
1486                        );
1487    
1488                        // If the current feesBase is close or identical to the stored one, the amountToCollect can be negative.
1489                        // This is because the stored feesBase is rounded up, and the current feesBase is rounded down.
1490                        // When this is the case, we want to behave as if there are 0 fees, so we just rectify the values.
1491                        // Guaranteed to be positive, so swap to unsigned type
1492                        amountToCollect = LeftRightUnsigned.wrap(
1493                            uint256(
1494                                LeftRightSigned.unwrap(feesBase.subRect(s_accountFeesBase[positionKey]))
1495                            )
1496                        );
1497                    }
1498    
1499                    (LeftRightUnsigned premiumOwed, LeftRightUnsigned premiumGross) = _getPremiaDeltas(
1500                        accountLiquidities,
1501                        amountToCollect
1502                    );
1503    
1504                    // add deltas to accumulators and freeze both accumulators (for a token) if one of them overflows
1505                    // (i.e if only token0 (right slot) of the owed premium overflows, then stop accumulating  both token0 owed premium and token0 gross premium for the chunk)
1506                    // this prevents situations where the owed premium gets out of sync with the gross premium due to one of them overflowing
1507                    (premiumOwed, premiumGross) = LeftRightLibrary.addCapped(
1508                        s_accountPremiumOwed[positionKey],
1509                        premiumOwed,
1510                        s_accountPremiumGross[positionKey],
1511                        premiumGross
1512                    );
1513    
1514                    acctPremia = isLong == 1 ? premiumOwed : premiumGross;
1515                }
1516            } else {
1517                // Extract the account liquidity for a given uniswap pool, owner, token type, and ticks
1518                acctPremia = isLong == 1
1519                    ? s_accountPremiumOwed[positionKey]
1520                    : s_accountPremiumGross[positionKey];
1521            }
1522            return (acctPremia.rightSlot(), acctPremia.leftSlot());
1523        }


1535        function getAccountFeesBase(
1536            address univ3pool,
1537            address owner,
1538            uint256 tokenType,
1539            int24 tickLower,
1540            int24 tickUpper
1541        ) external view returns (int128 feesBase0, int128 feesBase1) {
1542            // Get accumulated fees for token0 (rightSlot) and token1 (leftSlot)
1543            LeftRightSigned feesBase = s_accountFeesBase[
1544                keccak256(abi.encodePacked(univ3pool, owner, tokenType, tickLower, tickUpper))
1545            ];
1546            feesBase0 = feesBase.rightSlot();
1547            feesBase1 = feesBase.leftSlot();
1548        }


1555        function getUniswapV3PoolFromId(
1556            uint64 poolId
1557        ) external view returns (IUniswapV3Pool UniswapV3Pool) {
1558            return s_poolContext[poolId].pool;
1559        }


1566        function getPoolId(address univ3pool) external view returns (uint64 poolId) {
1567            poolId = uint64(s_AddrToPoolIdData[univ3pool]);
1568        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1566:1568

</details>

## NC042 - Consider adding formal verification proofs:

Consider using formal verification to mathematically prove that your code does what is intended, and does not have any edge cases with unexpected behavior. The solidity compiler itself has this functionality [built in based off of SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html#smtchecker-and-formal-verification).


```solidity
File: Various Files


None

```

## NC043 - Assembly code blocks should be thoroughly commented:

In Solidity, assembly blocks are often harder to read and understand due to their low-level nature. Detailed comments can make the code's purpose and functionality clear, aiding in maintenance, debugging, and reviews. Moreover, comments can be crucial for auditors and other developers to understand the contract's security implications, reducing the risk of oversights and vulnerabilities.


<details>
<summary>Click to show 30 findings</summary>

```solidity
File: contracts/libraries/Math.sol


353                 assembly ("memory-safe") {
354                     let mm := mulmod(a, b, not(0))
355                     prod0 := mul(a, b)
356                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))
357                 }


362                     assembly ("memory-safe") {
363                         result := div(prod0, denominator)
364                     }


379                 assembly ("memory-safe") {
380                     remainder := mulmod(a, b, denominator)
381                 }


383                 assembly ("memory-safe") {
384                     prod1 := sub(prod1, gt(remainder, prod0))
385                     prod0 := sub(prod0, remainder)
386                 }


393                 assembly ("memory-safe") {
394                     denominator := div(denominator, twos)
395                 }


398                 assembly ("memory-safe") {
399                     prod0 := div(prod0, twos)
400                 }


404                 assembly ("memory-safe") {
405                     twos := add(div(sub(0, twos), twos), 1)
406                 }


467                 assembly ("memory-safe") {
468                     let mm := mulmod(a, b, not(0))
469                     prod0 := mul(a, b)
470                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))
471                 }


476                     assembly ("memory-safe") {
477                         // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
478                         res := shr(64, prod0)
479                     }


493                 assembly ("memory-safe") {
494                     remainder := mulmod(a, b, 0x10000000000000000)
495                 }


497                 assembly ("memory-safe") {
498                     prod1 := sub(prod1, gt(remainder, prod0))
499                     prod0 := sub(prod0, remainder)
500                 }


503                 assembly ("memory-safe") {
504                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
505                     prod0 := shr(64, prod0)
506                 }


530                 assembly ("memory-safe") {
531                     let mm := mulmod(a, b, not(0))
532                     prod0 := mul(a, b)
533                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))
534                 }


539                     assembly ("memory-safe") {
540                         // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
541                         res := shr(96, prod0)
542                     }


556                 assembly ("memory-safe") {
557                     remainder := mulmod(a, b, 0x1000000000000000000000000)
558                 }


560                 assembly ("memory-safe") {
561                     prod1 := sub(prod1, gt(remainder, prod0))
562                     prod0 := sub(prod0, remainder)
563                 }


566                 assembly ("memory-safe") {
567                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
568                     prod0 := shr(96, prod0)
569                 }


607                 assembly ("memory-safe") {
608                     let mm := mulmod(a, b, not(0))
609                     prod0 := mul(a, b)
610                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))
611                 }


616                     assembly ("memory-safe") {
617                         // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
618                         res := shr(128, prod0)
619                     }


633                 assembly ("memory-safe") {
634                     remainder := mulmod(a, b, 0x100000000000000000000000000000000)
635                 }


637                 assembly ("memory-safe") {
638                     prod1 := sub(prod1, gt(remainder, prod0))
639                     prod0 := sub(prod0, remainder)
640                 }


643                 assembly ("memory-safe") {
644                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
645                     prod0 := shr(128, prod0)
646                 }


684                 assembly ("memory-safe") {
685                     let mm := mulmod(a, b, not(0))
686                     prod0 := mul(a, b)
687                     prod1 := sub(sub(mm, prod0), lt(mm, prod0))
688                 }


693                     assembly ("memory-safe") {
694                         // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
695                         res := shr(192, prod0)
696                     }


710                 assembly ("memory-safe") {
711                     remainder := mulmod(a, b, 0x1000000000000000000000000000000000000000000000000)
712                 }


714                 assembly ("memory-safe") {
715                     prod1 := sub(prod1, gt(remainder, prod0))
716                     prod0 := sub(prod0, remainder)
717                 }


720                 assembly ("memory-safe") {
721                     // Right shift by n is equivalent and 2 gas cheaper than division by 2^n
722                     prod0 := shr(192, prod0)
723                 }


739             assembly ("memory-safe") {
740                 result := add(div(a, b), gt(mod(a, b), 0))
741             }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L739:741

```solidity
File: contracts/libraries/SafeTransferLib.sol


55              assembly ("memory-safe") {
56                  // Get free memory pointer - we will store our calldata in scratch space starting at the offset specified here.
57                  let p := mload(0x40)
58      
59                  // Write the abi-encoded calldata into memory, beginning with the function selector.
60                  mstore(p, 0xa9059cbb00000000000000000000000000000000000000000000000000000000)
61                  mstore(add(4, p), to) // Append the "to" argument.
62                  mstore(add(36, p), amount) // Append the "amount" argument.
63      
64                  success := and(
65                      // Set success to whether the call reverted, if not we check it either
66                      // returned exactly 1 (can't just be non-zero data), or had no return data.
67                      or(and(eq(mload(0), 1), gt(returndatasize(), 31)), iszero(returndatasize())),
68                      // We use 68 because that's the total length of our calldata (4 + 32 * 2)
69                      // Counterintuitively, this call() must be positioned after the or() in the
70                      // surrounding and() because and() evaluates its arguments from right to left.
71                      call(gas(), token, 0, p, 68, 0, 32)
72                  )
73              }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L55:73

```solidity
File: contracts/multicall/Multicall.sol


25                      assembly ("memory-safe") {
26                          revert(add(result, 32), mload(result))
27                      }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L25:27

</details>

## NC044 - Large multiples of ten should use scientific notation (e.g. 1e6) rather than decimal literals (e.g. 1000000), for readability:

Using scientific notation for large multiples of ten improves code readability. Instead of writing large decimal literals, consider using scientific notation.


<details>
<summary>Click to show 7 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


206                         10_000 ** 2 +


81          int128 internal constant DECIMALS_128 = 10_000;


208                         10_000 ** 3


77          uint256 internal constant DECIMALS = 10_000;


204                         10_000 +


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L204:204

```solidity
File: contracts/PanopticPool.sol


1329                return balanceCross >= Math.unsafeDivRoundingUp(thresholdCross * buffer, 10_000);


174         uint256 internal constant NO_BUFFER = 10_000;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L174:174

</details>

## NC045 - Polymorphic functions make security audits more time-consuming and error-prone:

The instances below point to one of two functions with the same name. Consider naming each function differently, in order to make code navigation and analysis easier.


<details>
<summary>Click to show 15 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


894         function delegate(address delegatee, uint256 assets) external onlyPanopticPool {


975         function refund(address refunder, address refundee, int256 assets) external onlyPanopticPool {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L975:975

```solidity
File: contracts/PanopticPool.sol


586         function burnOptions(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L586:586

```solidity
File: contracts/libraries/Math.sol


49          function min(int256 a, int256 b) internal pure returns (int256) {


65          function max(int256 a, int256 b) internal pure returns (int256) {


318         function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L318:318

```solidity
File: contracts/libraries/PanopticMath.sol


445         function convertCollateralData(


524         function convert0to1(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {


547         function convert1to0(int256 amount, uint160 sqrtPriceX96) internal pure returns (int256) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L547:547

```solidity
File: contracts/types/LeftRight.sol


46          function rightSlot(LeftRightSigned self) internal pure returns (int128) {


78          function toRightSlot(


108         function leftSlot(LeftRightSigned self) internal pure returns (int128) {


134         function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {


194         function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {


232         function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L232:232

</details>

## NC046 - Consider splitting long calculations:

The longer a string of operations is, the harder it is to understand it. Consider splitting the full calculation into more steps, with more descriptive temporary variable names, and add extensive comments.


<details>
<summary>Click to show 14 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


201                 TICK_DEVIATION = uint256(
202                     2230 +
203                         (12500 * ratioTick) /
204                         10_000 +
205                         (7812 * ratioTick ** 2) /
206                         10_000 ** 2 +
207                         (6510 * ratioTick ** 3) /
208                         10_000 ** 3
209                 );


1570                    spreadRequirement = (notional < notionalP)
1571                        ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)
1572                        : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);


1362                        uint160 ratio = tokenType == 1 // tokenType
1363                            ? Math.getSqrtRatioAtTick(
1364                                Math.max24(2 * (atTick - strike), Constants.MIN_V3POOL_TICK)
1365                            ) // puts ->  price/strike
1366                            : Math.getSqrtRatioAtTick(
1367                                Math.max24(2 * (strike - atTick), Constants.MIN_V3POOL_TICK)
1368                            ); // calls -> strike/price


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1362:1368

```solidity
File: contracts/PanopticPool.sol


1725                        s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1726                            .wrap(0)
1727                            .toRightSlot(
1728                                uint128(
1729                                    (grossCurrent[0] *
1730                                        positionLiquidity +
1731                                        grossPremiumLast.rightSlot() *
1732                                        totalLiquidityBefore) / (totalLiquidity)
1733                                )
1734                            )
1735                            .toLeftSlot(
1736                                uint128(
1737                                    (grossCurrent[1] *
1738                                        positionLiquidity +
1739                                        grossPremiumLast.leftSlot() *
1740                                        totalLiquidityBefore) / (totalLiquidity)
1741                                )
1742                            );


1633                LeftRightSigned realizedPremia = LeftRightSigned
1634                    .wrap(0)
1635                    .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))
1636                    .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));


1545                        premiaByLeg[leg] = LeftRightSigned
1546                            .wrap(0)
1547                            .toRightSlot(
1548                                int128(
1549                                    int256(
1550                                        ((premiumAccumulatorsByLeg[leg][0] -
1551                                            premiumAccumulatorLast.rightSlot()) *
1552                                            (liquidityChunk.liquidity())) / 2 ** 64
1553                                    )
1554                                )
1555                            )
1556                            .toLeftSlot(
1557                                int128(
1558                                    int256(
1559                                        ((premiumAccumulatorsByLeg[leg][1] -
1560                                            premiumAccumulatorLast.leftSlot()) *
1561                                            (liquidityChunk.liquidity())) / 2 ** 64
1562                                    )
1563                                )
1564                            );


308                 s_miniMedian =
309                     (uint256(block.timestamp) << 216) +
310                     // magic number which adds (7,5,3,1,0,2,4,6) order and minTick in positions 7, 5, 3 and maxTick in 6, 4, 2
311                     // see comment on s_miniMedian initialization for format of this magic number
312                     (uint256(0xF590A6F276170D89E9F276170D89E9F276170D89E9000000000000)) +
313                     (uint256(uint24(currentTick)) << 24) + // add to slot 4
314                     (uint256(uint24(currentTick))); // add to slot 3


1928                            s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929                                ? LeftRightUnsigned
1930                                    .wrap(0)
1931                                    .toRightSlot(
1932                                        uint128(
1933                                            uint256(
1934                                                Math.max(
1935                                                    (int256(
1936                                                        grossPremiumLast.rightSlot() *
1937                                                            totalLiquidityBefore
1938                                                    ) -
1939                                                        int256(
1940                                                            _premiumAccumulatorsByLeg[_leg][0] *
1941                                                                positionLiquidity
1942                                                        )) + int256(legPremia.rightSlot() * 2 ** 64),
1943                                                    0
1944                                                )
1945                                            ) / totalLiquidity
1946                                        )
1947                                    )
1948                                    .toLeftSlot(
1949                                        uint128(
1950                                            uint256(
1951                                                Math.max(
1952                                                    (int256(
1953                                                        grossPremiumLast.leftSlot() *
1954                                                            totalLiquidityBefore
1955                                                    ) -
1956                                                        int256(
1957                                                            _premiumAccumulatorsByLeg[_leg][1] *
1958                                                                positionLiquidity
1959                                                        )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960                                                    0
1961                                                )
1962                                            ) / totalLiquidity
1963                                        )
1964                                    )
1965                                : LeftRightUnsigned
1966                                    .wrap(0)
1967                                    .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968                                    .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1928:1968

```solidity
File: contracts/SemiFungiblePositionManager.sol


1388                        uint256 numerator = totalLiquidity ** 2 -
1389                            totalLiquidity *
1390                            removedLiquidity +
1391                            ((removedLiquidity ** 2) / 2 ** (VEGOID));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1388:1391

```solidity
File: contracts/libraries/PanopticMath.sol


223                         newOrderMap = newOrderMap + ((rank + 1) << (3 * (i + shift - 1)));


177                 medianTick =
178                     (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +
179                         int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /
180                     2;


149                     ticks[i] =
150                         (tickCumulatives[i] - tickCumulatives[i + 1]) /
151                         int256(timestamps[i] - timestamps[i + 1]);


475                 uint256 notional = asset == 0
476                     ? convert0to1(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2))
477                     : convert1to0(contractSize, Math.getSqrtRatioAtTick((tickUpper + tickLower) / 2));


226                     updatedMedianData =
227                         (block.timestamp << 216) +
228                         (uint256(newOrderMap) << 192) +
229                         uint256(uint192(medianData << 24)) +
230                         uint256(uint24(lastObservedTick));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L226:230

</details>

## NC047 - High cyclomatic complexity:

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.


<details>
<summary>Click to show 7 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


1510        function _computeSpread(
1511            TokenId tokenId,
1512            uint128 positionSize,
1513            uint256 index,
1514            uint256 partnerIndex,
1515            uint128 poolUtilization
1516        ) internal view returns (uint256 spreadRequirement) {
1517            // compute the total amount of funds moved for the position's current leg
1518            LeftRightUnsigned amountsMoved = PanopticMath.getAmountsMoved(tokenId, positionSize, index);
1519    
1520            // compute the total amount of funds moved for the position's partner leg
1521            LeftRightUnsigned amountsMovedPartner = PanopticMath.getAmountsMoved(
1522                tokenId,
1523                positionSize,
1524                partnerIndex
1525            );
1526    
1527            // amount moved is right slot if tokenType=0, left slot otherwise
1528            uint128 movedRight = amountsMoved.rightSlot();
1529            uint128 movedLeft = amountsMoved.leftSlot();
1530    
1531            // amounts moved for partner
1532            uint128 movedPartnerRight = amountsMovedPartner.rightSlot();
1533            uint128 movedPartnerLeft = amountsMovedPartner.leftSlot();
1534    
1535            uint256 tokenType = tokenId.tokenType(index);
1536    
1537            // compute the max loss of the spread
1538    
1539            // if asset is NOT the same as the tokenType, the required amount is simply the difference in notional values
1540            // ie. asset = 1, tokenType = 0:
1541            if (tokenId.asset(index) != tokenType) {
1542                unchecked {
1543                    // always take the absolute values of the difference of amounts moved
1544                    if (tokenType == 0) {
1545                        spreadRequirement = movedRight < movedPartnerRight
1546                            ? movedPartnerRight - movedRight
1547                            : movedRight - movedPartnerRight;
1548                    } else {
1549                        spreadRequirement = movedLeft < movedPartnerLeft
1550                            ? movedPartnerLeft - movedLeft
1551                            : movedLeft - movedPartnerLeft;
1552                    }
1553                }
1554            } else {
1555                unchecked {
1556                    uint256 notional;
1557                    uint256 notionalP;
1558                    uint128 contracts;
1559                    if (tokenType == 1) {
1560                        notional = movedRight;
1561                        notionalP = movedPartnerRight;
1562                        contracts = movedLeft;
1563                    } else {
1564                        notional = movedLeft;
1565                        notionalP = movedPartnerLeft;
1566                        contracts = movedRight;
1567                    }
1568                    // the required amount is the amount of contracts multiplied by (notional1 - notional2)/min(notional1, notional2)
1569                    // can use unsafe because denominator is always nonzero
1570                    spreadRequirement = (notional < notionalP)
1571                        ? Math.unsafeDivRoundingUp((notionalP - notional) * contracts, notional)
1572                        : Math.unsafeDivRoundingUp((notional - notionalP) * contracts, notionalP);
1573                }
1574            }
1575    
1576            // calculate the spread requirement as max(max_loss, long_leg_col_req)
1577            // narrower spreads will be very capital efficient (1/3 of non-partnered CR!), but
1578            // wider spreads (an uncommon position w/ high max loss) may not benefit from risk partnering
1579            spreadRequirement = Math.max(
1580                spreadRequirement,
1581                _getRequiredCollateralAtUtilization(
1582                    tokenType == 0 ? movedRight : movedLeft,
1583                    1,
1584                    tokenType == 0
1585                        ? int64(uint64(poolUtilization))
1586                        : int64(uint64(poolUtilization >> 64))
1587                )
1588            );
1589        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1510:1589

```solidity
File: contracts/SemiFungiblePositionManager.sol


958         function _createLegInAMM(
959             IUniswapV3Pool univ3pool,
960             TokenId tokenId,
961             uint256 leg,
962             LiquidityChunk liquidityChunk,
963             bool isBurn
964         )
965             internal
966             returns (
967                 LeftRightSigned moved,
968                 LeftRightSigned itmAmounts,
969                 LeftRightUnsigned collectedSingleLeg
970             )
971         {
972             uint256 tokenType = tokenId.tokenType(leg);
973             // unique key to identify the liquidity chunk in this uniswap pool
974             bytes32 positionKey = keccak256(
975                 abi.encodePacked(
976                     address(univ3pool),
977                     msg.sender,
978                     tokenType,
979                     liquidityChunk.tickLower(),
980                     liquidityChunk.tickUpper()
981                 )
982             );
983     
984             // update our internal bookkeeping of how much liquidity we have deployed in the AMM
985             // for example: if this _leg is short, we add liquidity to the amm, make sure to add that to our tracking
986             uint128 updatedLiquidity;
987             uint256 isLong = tokenId.isLong(leg);
988             LeftRightUnsigned currentLiquidity = s_accountLiquidity[positionKey]; //cache
989             {
990                 // did we have liquidity already deployed in Uniswap for this chunk range from some past mint?
991     
992                 // s_accountLiquidity is a LeftRight. The right slot represents the liquidity currently sold (added) in the AMM owned by the user
993                 // the left slot represents the amount of liquidity currently bought (removed) that has been removed from the AMM - the user owes it to a seller
994                 // the reason why it is called "removedLiquidity" is because long options are created by removing -ie.short selling LP positions
995                 uint128 startingLiquidity = currentLiquidity.rightSlot();
996                 uint128 removedLiquidity = currentLiquidity.leftSlot();
997                 uint128 chunkLiquidity = liquidityChunk.liquidity();
998     
999                 if (isLong == 0) {
1000                    // selling/short: so move from msg.sender *to* uniswap
1001                    // we're minting more liquidity in uniswap: so add the incoming liquidity chunk to the existing liquidity chunk
1002                    updatedLiquidity = startingLiquidity + chunkLiquidity;
1003    
1004                    /// @dev If the isLong flag is 0=short but the position was burnt, then this is closing a long position
1005                    /// @dev so the amount of removed liquidity should decrease.
1006                    if (isBurn) {
1007                        removedLiquidity -= chunkLiquidity;
1008                    }
1009                } else {
1010                    // the _leg is long (buying: moving *from* uniswap to msg.sender)
1011                    // so we seek to move the incoming liquidity chunk *out* of uniswap - but was there sufficient liquidity sitting in uniswap
1012                    // in the first place?
1013                    if (startingLiquidity < chunkLiquidity) {
1014                        // the amount we want to move (liquidityChunk.legLiquidity()) out of uniswap is greater than
1015                        // what the account that owns the liquidity in uniswap has (startingLiquidity)
1016                        // we must ensure that an account can only move its own liquidity out of uniswap
1017                        // so we revert in this case
1018                        revert Errors.NotEnoughLiquidity();
1019                    } else {
1020                        // startingLiquidity is >= chunkLiquidity, so no possible underflow
1021                        unchecked {
1022                            // we want to move less than what already sits in uniswap, no problem:
1023                            updatedLiquidity = startingLiquidity - chunkLiquidity;
1024                        }
1025                    }
1026    
1027                    /// @dev If the isLong flag is 1=long and the position is minted, then this is opening a long position
1028                    /// @dev so the amount of removed liquidity should increase.
1029                    if (!isBurn) {
1030                        // we can't remove more liquidity than we add in the first place, so this can't overflow
1031                        unchecked {
1032                            removedLiquidity += chunkLiquidity;
1033                        }
1034                    }
1035                }
1036    
1037                // update the starting liquidity for this position for next time around
1038                s_accountLiquidity[positionKey] = LeftRightUnsigned
1039                    .wrap(0)
1040                    .toLeftSlot(removedLiquidity)
1041                    .toRightSlot(updatedLiquidity);
1042            }
1043    
1044            // track how much liquidity we need to collect from uniswap
1045            // add the fees that accumulated in uniswap within the liquidityChunk:
1046            {
1047                /** if the position is NOT long (selling a put or a call), then _mintLiquidity to move liquidity
1048                    from the msg.sender to the uniswap v3 pool:
1049                    Selling(isLong=0): Mint chunk of liquidity in Uniswap (defined by upper tick, lower tick, and amount)
1050                           ┌─────────────────────────────────┐
1051                    ▲     ┌▼┐ liquidityChunk                 │
1052                    │  ┌──┴─┴──┐                         ┌───┴──┐
1053                    │  │       │                         │      │
1054                    └──┴───────┴──►                      └──────┘
1055                       Uniswap v3                      msg.sender
1056                
1057                 else: the position is long (buying a put or a call), then _burnLiquidity to remove liquidity from univ3
1058                    Buying(isLong=1): Burn in Uniswap
1059                           ┌─────────────────┐
1060                    ▲     ┌┼┐                │
1061                    │  ┌──┴─┴──┐         ┌───▼──┐
1062                    │  │       │         │      │
1063                    └──┴───────┴──►      └──────┘
1064                        Uniswap v3      msg.sender 
1065                */
1066                moved = isLong == 0
1067                    ? _mintLiquidity(liquidityChunk, univ3pool)
1068                    : _burnLiquidity(liquidityChunk, univ3pool); // from msg.sender to Uniswap
1069                // add the moved liquidity chunk to amount we need to collect from uniswap:
1070    
1071                // Is this _leg ITM?
1072                // if tokenType is 1, and we transacted some token0: then this leg is ITM!
1073                if (tokenType == 1) {
1074                    // extract amount moved out of UniswapV3 pool
1075                    itmAmounts = itmAmounts.toRightSlot(moved.rightSlot());
1076                }
1077                // if tokenType is 0, and we transacted some token1: then this leg is ITM
1078                if (tokenType == 0) {
1079                    // Add this in-the-money amount transacted.
1080                    itmAmounts = itmAmounts.toLeftSlot(moved.leftSlot());
1081                }
1082            }
1083    
1084            // if there was liquidity at that tick before the transaction, collect any accumulated fees
1085            if (currentLiquidity.rightSlot() > 0) {
1086                collectedSingleLeg = _collectAndWritePositionData(
1087                    liquidityChunk,
1088                    univ3pool,
1089                    currentLiquidity,
1090                    positionKey,
1091                    moved,
1092                    isLong
1093                );
1094            }
1095    
1096            // position has been touched, update s_accountFeesBase with the latest values from the pool.positions
1097            // round up the stored feesbase to minimize Δfeesbase when we next calculate it
1098            s_accountFeesBase[positionKey] = _getFeesBase(
1099                univ3pool,
1100                updatedLiquidity,
1101                liquidityChunk,
1102                true
1103            );
1104        }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L958:1104

```solidity
File: contracts/libraries/InteractionHelper.sol


48          function computeName(
49              address token0,
50              address token1,
51              bool isToken0,
52              uint24 fee,
53              string memory prefix
54          ) external view returns (string memory) {
55              // get the underlying token symbols
56              // it's not guaranteed that they support the metadata extension
57              // so we need to let them fail and return placeholder if not
58              string memory symbol0;
59              string memory symbol1;
60              try IERC20Metadata(token0).symbol() returns (string memory _symbol) {
61                  symbol0 = _symbol;
62              } catch {
63                  symbol0 = "???";
64              }
65              try IERC20Metadata(token1).symbol() returns (string memory _symbol) {
66                  symbol1 = _symbol;
67              } catch {
68                  symbol1 = "???";
69              }
70              unchecked {
71                  return
72                      string.concat(
73                          prefix,
74                          " ",
75                          isToken0 ? symbol0 : symbol1,
76                          " LP on ",
77                          symbol0,
78                          "/",
79                          symbol1,
80                          " ",
81                          Strings.toString(fee),
82                          "bps"
83                      );
84              }
85          }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L48:85

```solidity
File: contracts/libraries/Math.sol


128         function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160) {
129             unchecked {
130                 uint256 absTick = tick < 0 ? uint256(-int256(tick)) : uint256(int256(tick));
131                 if (absTick > uint256(int256(Constants.MAX_V3POOL_TICK))) revert Errors.InvalidTick();
132     
133                 uint256 sqrtR = absTick & 0x1 != 0
134                     ? 0xfffcb933bd6fad37aa2d162d1a594001
135                     : 0x100000000000000000000000000000000;
136                 // RealV: 0xfffcb933bd6fad37aa2d162d1a594001
137                 if (absTick & 0x2 != 0) sqrtR = (sqrtR * 0xfff97272373d413259a46990580e213a) >> 128;
138                 // RealV: 0xfff97272373d413259a46990580e2139
139                 if (absTick & 0x4 != 0) sqrtR = (sqrtR * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;
140                 // RealV: 0xfff2e50f5f656932ef12357cf3c7fdca
141                 if (absTick & 0x8 != 0) sqrtR = (sqrtR * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;
142                 // RealV: 0xffe5caca7e10e4e61c3624eaa0941ccd
143                 if (absTick & 0x10 != 0) sqrtR = (sqrtR * 0xffcb9843d60f6159c9db58835c926644) >> 128;
144                 // RealV: 0xffcb9843d60f6159c9db58835c92663e
145                 if (absTick & 0x20 != 0) sqrtR = (sqrtR * 0xff973b41fa98c081472e6896dfb254c0) >> 128;
146                 // RealV: 0xff973b41fa98c081472e6896dfb254b6
147                 if (absTick & 0x40 != 0) sqrtR = (sqrtR * 0xff2ea16466c96a3843ec78b326b52861) >> 128;
148                 // RealV: 0xff2ea16466c96a3843ec78b326b5284f
149                 if (absTick & 0x80 != 0) sqrtR = (sqrtR * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;
150                 // RealV: 0xfe5dee046a99a2a811c461f1969c3032
151                 if (absTick & 0x100 != 0) sqrtR = (sqrtR * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;
152                 // RealV: 0xfcbe86c7900a88aedcffc83b479aa363
153                 if (absTick & 0x200 != 0) sqrtR = (sqrtR * 0xf987a7253ac413176f2b074cf7815e54) >> 128;
154                 // RealV: 0xf987a7253ac413176f2b074cf7815dd0
155                 if (absTick & 0x400 != 0) sqrtR = (sqrtR * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;
156                 // RealV: 0xf3392b0822b70005940c7a398e4b6ff1
157                 if (absTick & 0x800 != 0) sqrtR = (sqrtR * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;
158                 // RealV: 0xe7159475a2c29b7443b29c7fa6e887f2
159                 if (absTick & 0x1000 != 0) sqrtR = (sqrtR * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;
160                 // RealV: 0xd097f3bdfd2022b8845ad8f792aa548c
161                 if (absTick & 0x2000 != 0) sqrtR = (sqrtR * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;
162                 // RealV: 0xa9f746462d870fdf8a65dc1f90e05b52
163                 if (absTick & 0x4000 != 0) sqrtR = (sqrtR * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;
164                 // RealV: 0x70d869a156d2a1b890bb3df62baf27ff
165                 if (absTick & 0x8000 != 0) sqrtR = (sqrtR * 0x31be135f97d08fd981231505542fcfa6) >> 128;
166                 // RealV: 0x31be135f97d08fd981231505542fbfe8
167                 if (absTick & 0x10000 != 0) sqrtR = (sqrtR * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;
168                 // RealV: 0x9aa508b5b7a84e1c677de54f3e988fe
169                 if (absTick & 0x20000 != 0) sqrtR = (sqrtR * 0x5d6af8dedb81196699c329225ee604) >> 128;
170                 // RealV: 0x5d6af8dedb81196699c329225ed28d
171                 if (absTick & 0x40000 != 0) sqrtR = (sqrtR * 0x2216e584f5fa1ea926041bedfe98) >> 128;
172                 // RealV: 0x2216e584f5fa1ea926041bedeaf4
173                 if (absTick & 0x80000 != 0) sqrtR = (sqrtR * 0x48a170391f7dc42444e8fa2) >> 128;
174                 // RealV: 0x48a170391f7dc42444e7be7
175     
176                 if (tick > 0) sqrtR = type(uint256).max / sqrtR;
177     
178                 // Downcast + rounding up to keep is consistent with Uniswap's
179                 return uint160((sqrtR >> 32) + (sqrtR % (1 << 32) == 0 ? 0 : 1));
180             }
181         }


753         function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {
754             unchecked {
755                 int256 i = left;
756                 int256 j = right;
757                 if (i == j) return;
758                 int256 pivot = arr[uint256(left + (right - left) / 2)];
759                 while (i < j) {
760                     while (arr[uint256(i)] < pivot) i++;
761                     while (pivot < arr[uint256(j)]) j--;
762                     if (i <= j) {
763                         (arr[uint256(i)], arr[uint256(j)]) = (arr[uint256(j)], arr[uint256(i)]);
764                         i++;
765                         j--;
766                     }
767                 }
768                 if (left < j) quickSort(arr, left, j);
769                 if (i < right) quickSort(arr, i, right);
770             }
771         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L753:771

```solidity
File: contracts/libraries/PanopticMath.sol


768         function haircutPremia(
769             address liquidatee,
770             TokenId[] memory positionIdList,
771             LeftRightSigned[4][] memory premiasByLeg,
772             LeftRightSigned collateralRemaining,
773             CollateralTracker collateral0,
774             CollateralTracker collateral1,
775             uint160 sqrtPriceX96Final,
776             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) storage settledTokens
777         ) external returns (int256, int256) {
778             unchecked {
779                 // get the amount of premium paid by the liquidatee
780                 LeftRightSigned longPremium;
781                 for (uint256 i = 0; i < positionIdList.length; ++i) {
782                     TokenId tokenId = positionIdList[i];
783                     uint256 numLegs = tokenId.countLegs();
784                     for (uint256 leg = 0; leg < numLegs; ++leg) {
785                         if (tokenId.isLong(leg) == 1) {
786                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
787                         }
788                     }
789                 }
790                 // Ignore any surplus collateral - the liquidatee is either solvent or it converts to <1 unit of the other token
791                 int256 collateralDelta0 = -Math.min(collateralRemaining.rightSlot(), 0);
792                 int256 collateralDelta1 = -Math.min(collateralRemaining.leftSlot(), 0);
793                 int256 haircut0;
794                 int256 haircut1;
795                 // if the premium in the same token is not enough to cover the loss and there is a surplus of the other token,
796                 // the liquidator will provide the tokens (reflected in the bonus amount) & receive compensation in the other token
797                 if (
798                     longPremium.rightSlot() < collateralDelta0 &&
799                     longPremium.leftSlot() > collateralDelta1
800                 ) {
801                     int256 protocolLoss1 = collateralDelta1;
802                     (collateralDelta0, collateralDelta1) = (
803                         -Math.min(
804                             collateralDelta0 - longPremium.rightSlot(),
805                             PanopticMath.convert1to0(
806                                 longPremium.leftSlot() - collateralDelta1,
807                                 sqrtPriceX96Final
808                             )
809                         ),
810                         Math.min(
811                             longPremium.leftSlot() - collateralDelta1,
812                             PanopticMath.convert0to1(
813                                 collateralDelta0 - longPremium.rightSlot(),
814                                 sqrtPriceX96Final
815                             )
816                         )
817                     );
818     
819                     haircut0 = longPremium.rightSlot();
820                     haircut1 = protocolLoss1 + collateralDelta1;
821                 } else if (
822                     longPremium.leftSlot() < collateralDelta1 &&
823                     longPremium.rightSlot() > collateralDelta0
824                 ) {
825                     int256 protocolLoss0 = collateralDelta0;
826                     (collateralDelta0, collateralDelta1) = (
827                         Math.min(
828                             longPremium.rightSlot() - collateralDelta0,
829                             PanopticMath.convert1to0(
830                                 collateralDelta1 - longPremium.leftSlot(),
831                                 sqrtPriceX96Final
832                             )
833                         ),
834                         -Math.min(
835                             collateralDelta1 - longPremium.leftSlot(),
836                             PanopticMath.convert0to1(
837                                 longPremium.rightSlot() - collateralDelta0,
838                                 sqrtPriceX96Final
839                             )
840                         )
841                     );
842     
843                     haircut0 = collateralDelta0 + protocolLoss0;
844                     haircut1 = longPremium.leftSlot();
845                 } else {
846                     // for each token, haircut until the protocol loss is mitigated or the premium paid is exhausted
847                     haircut0 = Math.min(collateralDelta0, longPremium.rightSlot());
848                     haircut1 = Math.min(collateralDelta1, longPremium.leftSlot());
849     
850                     collateralDelta0 = 0;
851                     collateralDelta1 = 0;
852                 }
853     
854                 {
855                     address _liquidatee = liquidatee;
856                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));
857                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));
858                 }
859     
860                 for (uint256 i = 0; i < positionIdList.length; i++) {
861                     TokenId tokenId = positionIdList[i];
862                     LeftRightSigned[4][] memory _premiasByLeg = premiasByLeg;
863                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864                         if (tokenId.isLong(leg) == 1) {
865                             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
866                                 storage _settledTokens = settledTokens;
867     
868                             // calculate amounts to revoke from settled and subtract from haircut req
869                             uint256 settled0 = Math.unsafeDivRoundingUp(
870                                 uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871                                 uint128(longPremium.rightSlot())
872                             );
873                             uint256 settled1 = Math.unsafeDivRoundingUp(
874                                 uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875                                 uint128(longPremium.leftSlot())
876                             );
877     
878                             bytes32 chunkKey = keccak256(
879                                 abi.encodePacked(
880                                     tokenId.strike(0),
881                                     tokenId.width(0),
882                                     tokenId.tokenType(0)
883                                 )
884                             );
885     
886                             // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
887                             // for the haircut directly to the accumulator
888                             settled0 = Math.max(
889                                 0,
890                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891                             );
892                             settled1 = Math.max(
893                                 0,
894                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895                             );
896     
897                             _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
898                                 LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
899                                     uint128(settled1)
900                                 )
901                             );
902                         }
903                     }
904                 }
905     
906                 return (collateralDelta0, collateralDelta1);
907             }
908         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L768:908

```solidity
File: contracts/types/TokenId.sol


500         function validate(TokenId self) internal pure {
501             if (self.optionRatio(0) == 0) revert Errors.InvalidTokenIdParameter(1);
502     
503             // loop through the 4 (possible) legs in the tokenId `self`
504             unchecked {
505                 // extract strike, width, and tokenType
506                 uint256 chunkData = (TokenId.unwrap(self) & CHUNK_MASK) >> 64;
507                 for (uint256 i = 0; i < 4; ++i) {
508                     if (self.optionRatio(i) == 0) {
509                         // final leg in this position identified;
510                         // make sure any leg above this are zero as well
511                         // (we don't allow gaps eg having legs 1 and 4 active without 2 and 3 is not allowed)
512                         if ((TokenId.unwrap(self) >> (64 + 48 * i)) != 0)
513                             revert Errors.InvalidTokenIdParameter(1);
514     
515                         break; // we are done iterating over potential legs
516                     }
517     
518                     // prevent legs touching the same chunks - all chunks in the position must be discrete
519                     uint256 numLegs = self.countLegs();
520                     for (uint256 j = i + 1; j < numLegs; ++j) {
521                         if (uint48(chunkData >> (48 * i)) == uint48(chunkData >> (48 * j))) {
522                             revert Errors.InvalidTokenIdParameter(6);
523                         }
524                     }
525                     // now validate this ith leg in the position:
526     
527                     // The width cannot be 0; the minimum is 1
528                     if ((self.width(i) == 0)) revert Errors.InvalidTokenIdParameter(5);
529                     // Strike cannot be MIN_TICK or MAX_TICK
530                     if (
531                         (self.strike(i) == Constants.MIN_V3POOL_TICK) ||
532                         (self.strike(i) == Constants.MAX_V3POOL_TICK)
533                     ) revert Errors.InvalidTokenIdParameter(4);
534     
535                     // In the following, we check whether the risk partner of this leg is itself
536                     // or another leg in this position.
537                     // Handles case where riskPartner(i) != i ==> leg i has a risk partner that is another leg
538                     uint256 riskPartnerIndex = self.riskPartner(i);
539                     if (riskPartnerIndex != i) {
540                         // Ensures that risk partners are mutual
541                         if (self.riskPartner(riskPartnerIndex) != i)
542                             revert Errors.InvalidTokenIdParameter(3);
543     
544                         // Ensures that risk partners have 1) the same asset, and 2) the same ratio
545                         if (
546                             (self.asset(riskPartnerIndex) != self.asset(i)) ||
547                             (self.optionRatio(riskPartnerIndex) != self.optionRatio(i))
548                         ) revert Errors.InvalidTokenIdParameter(3);
549     
550                         // long/short status of associated legs
551                         uint256 _isLong = self.isLong(i);
552                         uint256 isLongP = self.isLong(riskPartnerIndex);
553     
554                         // token type status of associated legs (call/put)
555                         uint256 _tokenType = self.tokenType(i);
556                         uint256 tokenTypeP = self.tokenType(riskPartnerIndex);
557     
558                         // if the position is the same i.e both long calls, short put's etc.
559                         // then this is a regular position, not a defined risk position
560                         if ((_isLong == isLongP) && (_tokenType == tokenTypeP))
561                             revert Errors.InvalidTokenIdParameter(4);
562     
563                         // if the two token long-types and the tokenTypes are both different (one is a short call, the other a long put, e.g.), this is a synthetic position
564                         // A synthetic long or short is more capital efficient than each leg separated because the long+short premia accumulate proportionally
565                         // unlike short stranlges, long strangles also cannot be partnered, because there is no reduction in risk (both legs can earn premia simultaneously)
566                         if (((_isLong != isLongP) || _isLong == 1) && (_tokenType != tokenTypeP))
567                             revert Errors.InvalidTokenIdParameter(5);
568                     }
569                 } // end for loop over legs
570             }
571         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L500:571

</details>

## NC048 - Use of override is unnecessary:

Starting with Solidity version 0.8.8, using the override keyword when the function solely overrides an interface function, and the function doesn't exist in multiple base contracts, is unnecessary.


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


    function transfer(
        address recipient,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool) {
        // make sure the caller does not have any open option positions
        // if they do: we don't want them sending panoptic pool shares to others
        // since that's like reducing collateral

        if (s_panopticPool.numberOfPositions(msg.sender) != 0) revert Errors.PositionCountNotZero();

        return ERC20Minimal.transfer(recipient, amount);
    }

    function transferFrom(
        address from,
        address to,
        uint256 amount
    ) public override(ERC20Minimal) returns (bool) {
        // make sure the caller does not have any open option positions
        // if they do: we don't want them sending panoptic pool shares to others
        // as this would reduce their amount of collateral against the opened positions

        if (s_panopticPool.numberOfPositions(from) != 0) revert Errors.PositionCountNotZero();

        return ERC20Minimal.transferFrom(from, to, amount);
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L341:353

```solidity
File: contracts/SemiFungiblePositionManager.sol


    function safeTransferFrom(
        address from,
        address to,
        uint256 id,
        uint256 amount,
        bytes calldata data
    ) public override {
        // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
        // so just check if there is an active reentrancy lock for the relevant pool on the token we're transferring
        if (s_poolContext[TokenId.wrap(id).poolId()].locked) revert Errors.ReentrantCall();

        // update the position data
        registerTokenTransfer(from, to, TokenId.wrap(id), amount);

        // transfer the token (note that all state updates are completed before reentrancy is possible through onReceived callbacks)
        super.safeTransferFrom(from, to, id, amount, data);
    }

    function safeBatchTransferFrom(
        address from,
        address to,
        uint256[] calldata ids,
        uint256[] calldata amounts,
        bytes calldata data
    ) public override {
        // we don't need to reentrancy lock on transfers, but we can't allow transfers for a pool during mint/burn with a reentrant call
        // so just check if there is an active reentrancy lock for the relevant pool on each token
        for (uint256 i = 0; i < ids.length; ) {
            if (s_poolContext[TokenId.wrap(ids[i]).poolId()].locked) revert Errors.ReentrantCall();
            registerTokenTransfer(from, to, TokenId.wrap(ids[i]), amounts[i]);
            unchecked {
                ++i;
            }
        }

        // transfer the token (note that all state updates are completed before reentrancy is possible)
        super.safeBatchTransferFrom(from, to, ids, amounts, data);
    }

```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L566:585

</details>

## NC049 - Non-`external`/`public` function names should begin with an underscore:

According to the Solidity Style Guide, non-`external`/`public` function names should begin with an underscore


<details>
<summary>Click to show 5 findings</summary>

```solidity
File: contracts/PanopticPool.sol


1450        function getUniV3TWAP() internal view returns (int24 twapTick) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1450:1450

```solidity
File: contracts/SemiFungiblePositionManager.sol


320         function beginReentrancyLock(uint64 poolId) internal {


330         function endReentrancyLock(uint64 poolId) internal {


593         function registerTokenTransfer(address from, address to, TokenId id, uint256 amount) internal {


756         function swapInAMM(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L756:756

</details>

## NC050 - Unused import:

The identifier is imported but never used within the file


```solidity
File: contracts/types/LiquidityChunk.sol


5       import {TokenId} from "@types/TokenId.sol";


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L5:5

## NC051 - Unsafe conversion from unsigned to signed values:

Solidity follows [two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) rules for its integers, meaning that the most significant bit for signed integers is used to denote the sign, and converting between the two requires inverting all of the bits and adding one. Because of this, casting an unsigned integer to a signed one may result in a change of the sign and or magnitude of the value. For example, `int8(type(uint8).max)` is not equal to `type(int8).max`, but is equal to `-1`. `type(uint8).max` in binary is `11111111`, which if cast to a signed value, means the first binary `1` indicates a negative value, and the binary `1`s, invert to all zeroes, and when one is added, it becomes one, but negative, and therefore the decimal value of binary `11111111` is `-1`.


<details>
<summary>Click to show 72 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


1585                        ? int64(uint64(poolUtilization))


731                     .toRightSlot(int128((longAmounts.rightSlot() * fee) / DECIMALS_128))


1003                int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;


732                     .toLeftSlot(int128((longAmounts.leftSlot() * fee) / DECIMALS_128));


1085                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) - (shortAmount - longAmount)));


718                                     int128(uint128(oracleValue1)) - int128(uint128(currentValue1))


1329                ? int64(uint64(poolUtilization))


200                 int256 ratioTick = (int256(_sellerCollateralRatio) - 2000);


1586                        : int64(uint64(poolUtilization >> 64))


1637                    uint128(uint64(-int64(poolUtilization0 == 0 ? 1 : poolUtilization0))) +


1330                : int64(uint64(poolUtilization >> 64));


715                                     int128(uint128(oracleValue0)) - int128(uint128(currentValue0))


1638                    (uint128(uint64(-int64(poolUtilization1 == 0 ? 1 : poolUtilization1))) << 64);


959                         uint256(Math.max(1, int256(totalAssets()) - int256(assets)))


668                             int256(
669                                 Math.unsafeDivRoundingUp(
670                                     uint24(positionId.width(leg) * positionId.tickSpacing()),
671                                     2
672                                 )
673                             )


743                 return int256((s_inAMM * DECIMALS) / totalAssets());


1115                    exchangedAmount = intrinsicValue + int256(swapCommission);


667                         int24 range = int24(
668                             int256(
669                                 Math.unsafeDivRoundingUp(
670                                     uint24(positionId.width(leg) * positionId.tickSpacing()),
671                                     2
672                                 )
673                             )
674                         );


1029                s_inAMM = uint128(uint256(int256(uint256(s_inAMM)) + (shortAmount - longAmount)));


1119                exchangedAmount += int256(
1120                    Math.unsafeDivRoundingUp(
1121                        uint256(uint128(shortAmount + longAmount)) * COMMISSION_FEE,
1122                        DECIMALS
1123                    )
1124                );


1052                int256 updatedAssets = int256(uint256(s_poolAssets)) - swappedAmount;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1052:1052

```solidity
File: contracts/PanopticPool.sol


1557                                int128(
1558                                    int256(
1559                                        ((premiumAccumulatorsByLeg[leg][1] -
1560                                            premiumAccumulatorLast.leftSlot()) *
1561                                            (liquidityChunk.liquidity())) / 2 ** 64
1562                                    )
1563                                )


1636                    .toLeftSlot(int128(int256((accumulatedPremium.leftSlot() * liquidity) / 2 ** 64)));


1952                                                    (int256(
1953                                                        grossPremiumLast.leftSlot() *
1954                                                            totalLiquidityBefore
1955                                                    ) -


1935                                                    (int256(
1936                                                        grossPremiumLast.rightSlot() *
1937                                                            totalLiquidityBefore
1938                                                    ) -


1959                                                        )) + int256(legPremia.leftSlot()) * 2 ** 64,


1548                                int128(
1549                                    int256(
1550                                        ((premiumAccumulatorsByLeg[leg][0] -
1551                                            premiumAccumulatorLast.rightSlot()) *
1552                                            (liquidityChunk.liquidity())) / 2 ** 64
1553                                    )
1554                                )


1549                                    int256(
1550                                        ((premiumAccumulatorsByLeg[leg][0] -
1551                                            premiumAccumulatorLast.rightSlot()) *
1552                                            (liquidityChunk.liquidity())) / 2 ** 64
1553                                    )


1942                                                        )) + int256(legPremia.rightSlot() * 2 ** 64),


1635                    .toRightSlot(int128(int256((accumulatedPremium.rightSlot() * liquidity) / 2 ** 64)))


1956                                                        int256(
1957                                                            _premiumAccumulatorsByLeg[_leg][1] *
1958                                                                positionLiquidity
1959                                                        )) + int256(legPremia.leftSlot()) * 2 ** 64,


1939                                                        int256(
1940                                                            _premiumAccumulatorsByLeg[_leg][0] *
1941                                                                positionLiquidity
1942                                                        )) + int256(legPremia.rightSlot() * 2 ** 64),


1558                                    int256(
1559                                        ((premiumAccumulatorsByLeg[leg][1] -
1560                                            premiumAccumulatorLast.leftSlot()) *
1561                                            (liquidityChunk.liquidity())) / 2 ** 64
1562                                    )


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1558:1562

```solidity
File: contracts/SemiFungiblePositionManager.sol


1242                    -int128(int256(amount1))


1215                int128(int256(amount1))


1214            movedAmounts = LeftRightSigned.wrap(0).toRightSlot(int128(int256(amount0))).toLeftSlot(


1169                        int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside0LastX128, liquidity)))


1241                movedAmounts = LeftRightSigned.wrap(0).toRightSlot(-int128(int256(amount0))).toLeftSlot(


1172                        int128(int256(Math.mulDiv128RoundingUp(feeGrowthInside1LastX128, liquidity)))


1176                    .toRightSlot(int128(int256(Math.mulDiv128(feeGrowthInside0LastX128, liquidity))))


1177                    .toLeftSlot(int128(int256(Math.mulDiv128(feeGrowthInside1LastX128, liquidity))));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1177:1177

```solidity
File: contracts/libraries/FeesCalc.sol


69                              value0 += int256(amount0);


70                              value1 += int256(amount1);


74                              value0 -= int256(amount0);


75                              value1 -= int256(amount1);


118                     .toLeftSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken1X128, liquidity))));


117                     .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L117:117

```solidity
File: contracts/libraries/Math.sol


312             if ((downcastedInt = int128(toCast)) < 0) revert Errors.CastingError();


327             return int256(toCast);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L327:327

```solidity
File: contracts/libraries/PanopticMath.sol


194                         lastObservedTick = int24(
195                             (tickCumulative_last - tickCumulative_old) /
196                                 int256(timestamp_last - timestamp_old)
197                         );


257                     twapMeasurement[i] = int24(
258                         (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))
259                     );


681                     bonus0 = int256(Math.mulDiv128(bonusCross, requiredRatioX128));


217                         entry = int24(uint24(medianData >> (rank * 24)));


140                             (int256(observationIndex) - int256(i * period)) +


856                     if (haircut0 != 0) collateral0.exercise(_liquidatee, 0, 0, 0, int128(haircut0));


141                                 int256(observationCardinality)


857                     if (haircut1 != 0) collateral1.exercise(_liquidatee, 0, 0, 0, int128(haircut1));


938                                     int256(
939                                         PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
940                                     ) + refundValues.leftSlot()


956                                     int256(
957                                         PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
958                                     ) + refundValues.rightSlot()


178                     (int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 3)) % 8) * 24))) +


955                                 int128(
956                                     int256(
957                                         PanopticMath.convert1to0(uint256(balanceShortage), sqrtPriceX96)
958                                     ) + refundValues.rightSlot()
959                                 )


155                 return int24(Math.sort(ticks)[cardinality / 2]);


196                                 int256(timestamp_last - timestamp_old)


151                         int256(timestamps[i] - timestamps[i + 1]);


937                                 int128(
938                                     int256(
939                                         PanopticMath.convert0to1(uint256(balanceShortage), sqrtPriceX96)
940                                     ) + refundValues.leftSlot()
941                                 )


266                 return int24(sortedTicks[10]);


188                                 int256(observationIndex) - int256(1) + int256(observationCardinality)


179                         int24(uint24(medianData >> ((uint24(medianData >> (192 + 3 * 4)) % 8) * 24)))) /


683                     bonus1 = int256(
684                         PanopticMath.convert0to1(
685                             Math.mulDiv128(bonusCross, 2 ** 128 - requiredRatioX128),
686                             sqrtPriceX96Final
687                         )
688                     );


258                         (tickCumulatives[i] - tickCumulatives[i + 1]) / int56(uint56(twapWindow / 20))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L258:258

```solidity
File: contracts/types/TokenId.sol


160                 return int24(int256(TokenId.unwrap(self) >> (64 + legIndex * 48 + 12)));


171                 return int24(int256((TokenId.unwrap(self) >> (64 + legIndex * 48 + 36)) % 4096));


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L171:171

</details>

## NC052 - Add inline comments for unnamed variables:

`function foo(address x, address)` -> `function foo(address x, address /* y */)`


```solidity
File: contracts/CollateralTracker.sol


444         function maxMint(address) external view returns (uint256 maxShares) {


392         function maxDeposit(address) external pure returns (uint256 maxAssets) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L392:392

## NC053 - Style guide: State and local variables should be named using lowerCamelCase:

The Solidity style guide says to use mixedCase for local and state variable names. Note that while OpenZeppelin may not follow this advice, it still is the recommended way of naming variables.


<details>
<summary>Click to show 715 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


89          address internal s_underlyingToken;


93          bool internal s_initialized;


96          address internal s_univ3token0;


99          address internal s_univ3token1;


102         bool internal s_underlyingIsToken0;


109         PanopticPool internal s_panopticPool;


112         uint128 internal s_poolAssets;


115         uint128 internal s_inAMM;


121         uint128 internal s_ITMSpreadFee;


124         uint24 internal s_poolFee;


131         uint256 immutable TICK_DEVIATION;


136         uint256 immutable COMMISSION_FEE;


141         uint256 immutable SELLER_COLLATERAL_RATIO;


145         uint256 immutable BUYER_COLLATERAL_RATIO;


149         int256 immutable FORCE_EXERCISE_COST;


154         uint256 immutable TARGET_POOL_UTIL;


158         uint256 immutable SATURATED_POOL_UTIL;


162         uint256 immutable ITM_SPREAD_MULTIPLIER;


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


773             uint256 min_sell_ratio = SELLER_COLLATERAL_RATIO;


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


185             uint256 _ITMSpreadMultiplier


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L185:185

```solidity
File: contracts/PanopticFactory.sol


63          IUniswapV3Factory internal immutable UNIV3_FACTORY;


66          SemiFungiblePositionManager internal immutable SFPM;


69          IDonorNFT internal immutable DONOR_NFT;


72          address internal immutable POOL_REFERENCE;


75          address internal immutable COLLATERAL_REFERENCE;


78          address internal immutable WETH;


96          address internal s_owner;


99          bool internal s_initialized;


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


185                     msg.sender,


116             address _WETH9,


117             SemiFungiblePositionManager _SFPM,


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L117:117

```solidity
File: contracts/PanopticPool.sol


179         SemiFungiblePositionManager internal immutable SFPM;


186         IUniswapV3Pool internal s_univ3pool;


225         uint256 internal s_miniMedian;


231         CollateralTracker internal s_collateralToken0;


233         CollateralTracker internal s_collateralToken1;


238         mapping(address account => mapping(TokenId tokenId => mapping(uint256 leg => LeftRightUnsigned premiaGrowth)))
239             internal s_options;


245         mapping(bytes32 chunkKey => LeftRightUnsigned lastGrossPremium) internal s_grossPremiumLast;


251         mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens) internal s_settledTokens;


258         mapping(address account => mapping(TokenId tokenId => LeftRightUnsigned balanceAndUtilizations))
259             internal s_positionBalance;


272         mapping(address account => uint256 positionsHash) internal s_positionsHash;


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


439             address c_user = user;


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


185         /// @dev The Uniswap v3 pool that this instance of Panoptic is deployed on


116         /// @dev Flag on the function `updateSettlementPostBurn`


117         /// @dev 'COMMIT_LONG_SETTLED' commits both collected Uniswap fees and settled long premium to `s_settledTokens`


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L117:117

```solidity
File: contracts/SemiFungiblePositionManager.sol


137         IUniswapV3Factory internal immutable FACTORY;


145         mapping(address univ3pool => uint256 poolIdData) internal s_AddrToPoolIdData;


150         mapping(uint64 poolId => PoolAddressAndLock contextData) internal s_poolContext;


177         mapping(bytes32 positionKey => LeftRightUnsigned removedAndNetLiquidity)
178             internal s_accountLiquidity;


287         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumOwed;


289         mapping(bytes32 positionKey => LeftRightUnsigned accountPremium) private s_accountPremiumGross;


295         mapping(bytes32 positionKey => LeftRightSigned baseFees0And1) internal s_accountFeesBase;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


611                 bytes32 positionKey_from = keccak256(


620                 bytes32 positionKey_to = keccak256(


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


1342                uint256 premium0X64_base;


1343                uint256 premium1X64_base;


1363                    uint128 premium0X64_owed;


1364                    uint128 premium1X64_owed;


1384                    uint128 premium0X64_gross;


1385                    uint128 premium1X64_gross;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


185             s_accountPremiumGross and s_accountPremiumOwed accumulators.


116             IUniswapV3Pool pool;


117             bool locked;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L117:117

```solidity
File: contracts/libraries/CallbackLib.sol








```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L117:117

```solidity
File: contracts/libraries/FeesCalc.sol


185                 } else {


116                     .wrap(0)


117                     .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))


185                 } else {


116                     .wrap(0)


117                     .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))


185                 } else {


116                     .wrap(0)


117                     .toRightSlot(int128(int256(Math.mulDiv128(ammFeesPerLiqToken0X128, liquidity))))


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L117:117

```solidity
File: contracts/libraries/InteractionHelper.sol




116     }


117     




116     }


117     




116     }


117     




116     }


117     


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L117:117

```solidity
File: contracts/libraries/Math.sol


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


185         //////////////////////////////////////////////////////////////*/


116             }


117         }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L117:117

```solidity
File: contracts/libraries/PanopticMath.sol


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


186                         (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(


186                         (uint256 timestamp_old, int56 tickCumulative_old, , ) = univ3pool.observations(


192                         (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool


192                         (uint256 timestamp_last, int56 tickCumulative_last, , ) = univ3pool


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


185                     {


116         /// @dev Each period has a minimum length of blocktime * period, but may be longer if the Uniswap pool is relatively inactive.


117         /// @dev The final price used in the array (of length `cardinality`) is the average of all observations comprising `period` (which is itself a number of observations).


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L117:117

```solidity
File: contracts/libraries/SafeTransferLib.sol














```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L117:117

```solidity
File: contracts/multicall/Multicall.sol








```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L117:117

```solidity
File: contracts/tokens/ERC1155Minimal.sol


185             // the array index counter which cannot possibly overflow.


116                 ) {


117                     revert UnsafeRecipient();


185             // the array index counter which cannot possibly overflow.


116                 ) {


117                     revert UnsafeRecipient();


185             // the array index counter which cannot possibly overflow.


116                 ) {


117                     revert UnsafeRecipient();


185             // the array index counter which cannot possibly overflow.


116                 ) {


117                     revert UnsafeRecipient();


185             // the array index counter which cannot possibly overflow.


116                 ) {


117                     revert UnsafeRecipient();


185             // the array index counter which cannot possibly overflow.


116                 ) {


117                     revert UnsafeRecipient();


185             // the array index counter which cannot possibly overflow.


116                 ) {


117                     revert UnsafeRecipient();


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L117:117

```solidity
File: contracts/tokens/ERC20Minimal.sol




116                             INTERNAL MINT/BURN LOGIC


117         //////////////////////////////////////////////////////////////*/




116                             INTERNAL MINT/BURN LOGIC


117         //////////////////////////////////////////////////////////////*/




116                             INTERNAL MINT/BURN LOGIC


117         //////////////////////////////////////////////////////////////*/




116                             INTERNAL MINT/BURN LOGIC


117         //////////////////////////////////////////////////////////////*/




116                             INTERNAL MINT/BURN LOGIC


117         //////////////////////////////////////////////////////////////*/




116                             INTERNAL MINT/BURN LOGIC


117         //////////////////////////////////////////////////////////////*/


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L117:117

```solidity
File: contracts/types/LeftRight.sol


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


285             uint128 z_xR = (uint256(x.rightSlot()) + dx.rightSlot()).toUint128Capped();


286             uint128 z_xL = (uint256(x.leftSlot()) + dx.leftSlot()).toUint128Capped();


287             uint128 z_yR = (uint256(y.rightSlot()) + dy.rightSlot()).toUint128Capped();


288             uint128 z_yL = (uint256(y.leftSlot()) + dy.leftSlot()).toUint128Capped();


290             bool r_Enabled = !(z_xR == type(uint128).max || z_yR == type(uint128).max);


291             bool l_Enabled = !(z_xL == type(uint128).max || z_yL == type(uint128).max);


185                     (uint128(LeftRightUnsigned.unwrap(z)) > uint128(LeftRightUnsigned.unwrap(x)))


116     


117         /// @notice Add to the "left" slot in a 256-bit pattern.


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L117:117

```solidity
File: contracts/types/LiquidityChunk.sol


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


185     


116         /// @param _tickUpper The upper tick to add to `self`


117         /// @return `self` with added upper tick `_tickUpper`


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L117:117

```solidity
File: contracts/types/TokenId.sol


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


185                 return TokenId.wrap(TokenId.unwrap(self) + _poolId);


116         /// @param legIndex The leg index of this position (in {0,1,2,3})


117         /// @return The number of contracts multiplier for leg `legIndex`


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L117:117

</details>

## NC054 - Unusual loop variable:

The normal name for loop variables is i, and when there is a nested loop, to use j. Not following this convention may lead to some reviewer confusion.


<details>
<summary>Click to show 16 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


662                 for (uint256 leg = 0; leg < positionId.countLegs(); ++leg) {
663                     // short legs are not counted - exercise is intended to be based on long legs
664                     if (positionId.isLong(leg) == 0) continue;
665     
666                     {
667                         int24 range = int24(
668                             int256(
669                                 Math.unsafeDivRoundingUp(
670                                     uint24(positionId.width(leg) * positionId.tickSpacing()),
671                                     2
672                                 )
673                             )
674                         );
675                         maxNumRangesFromStrike = Math.max(
676                             maxNumRangesFromStrike,
677                             uint256(Math.abs(currentTick - positionId.strike(leg)) / range)
678                         );
679                     }
680     
681                     uint256 currentValue0;
682                     uint256 currentValue1;
683                     uint256 oracleValue0;
684                     uint256 oracleValue1;
685     
686                     {
687                         LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
688                             positionId,
689                             leg,
690                             positionBalance
691                         );
692     
693                         (currentValue0, currentValue1) = Math.getAmountsForLiquidity(
694                             currentTick,
695                             liquidityChunk
696                         );
697     
698                         (oracleValue0, oracleValue1) = Math.getAmountsForLiquidity(
699                             oracleTick,
700                             liquidityChunk
701                         );
702                     }
703     
704                     uint256 tokenType = positionId.tokenType(leg);
705                     // compensate user for loss in value if chunk has lost money between current and median tick
706                     // note: the delta for one token will be positive and the other will be negative. This cancels out any moves in their positions
707                     if (
708                         (tokenType == 0 && currentValue1 < oracleValue1) ||
709                         (tokenType == 1 && currentValue0 < oracleValue0)
710                     )
711                         exerciseFees = exerciseFees.sub(
712                             LeftRightSigned
713                                 .wrap(0)
714                                 .toRightSlot(
715                                     int128(uint128(oracleValue0)) - int128(uint128(currentValue0))
716                                 )
717                                 .toLeftSlot(
718                                     int128(uint128(oracleValue1)) - int128(uint128(currentValue1))
719                                 )
720                         );
721                 }


1255                for (uint256 index = 0; index < numLegs; ++index) {
1256                    // revert if the tokenType does not match the current collateral token
1257                    if (tokenId.tokenType(index) != (underlyingIsToken0 ? 0 : 1)) continue;
1258                    // Increment the tokenRequired accumulator
1259                    tokenRequired += _getRequiredCollateralSingleLeg(
1260                        tokenId,
1261                        index,
1262                        positionSize,
1263                        atTick,
1264                        poolUtilization
1265                    );
1266                }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1255:1266

```solidity
File: contracts/PanopticPool.sol


441             for (uint256 k = 0; k < pLength; ) {
442                 TokenId tokenId = positionIdList[k];
443     
444                 balances[k][0] = TokenId.unwrap(tokenId);
445                 balances[k][1] = LeftRightUnsigned.unwrap(s_positionBalance[c_user][tokenId]);
446     
447                 (
448                     LeftRightSigned[4] memory premiaByLeg,
449                     uint256[2][4] memory premiumAccumulatorsByLeg
450                 ) = _getPremia(
451                         tokenId,
452                         LeftRightUnsigned.wrap(balances[k][1]).rightSlot(),
453                         c_user,
454                         computeAllPremia,
455                         atTick
456                     );
457     
458                 uint256 numLegs = tokenId.countLegs();
459                 for (uint256 leg = 0; leg < numLegs; ) {
460                     if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
461                         bytes32 chunkKey = keccak256(
462                             abi.encodePacked(
463                                 tokenId.strike(leg),
464                                 tokenId.width(leg),
465                                 tokenId.tokenType(leg)
466                             )
467                         );
468     
469                         LeftRightUnsigned availablePremium = _getAvailablePremium(
470                             _getTotalLiquidity(tokenId, leg),
471                             s_settledTokens[chunkKey],
472                             s_grossPremiumLast[chunkKey],
473                             LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
474                             premiumAccumulatorsByLeg[leg]
475                         );
476                         portfolioPremium = portfolioPremium.add(
477                             LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478                         );
479                     } else {
480                         portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
481                     }
482                     unchecked {
483                         ++leg;
484                     }
485                 }
486     
487                 unchecked {
488                     ++k;
489                 }
490             }


459                 for (uint256 leg = 0; leg < numLegs; ) {
460                     if (tokenId.isLong(leg) == 0 && !includePendingPremium) {
461                         bytes32 chunkKey = keccak256(
462                             abi.encodePacked(
463                                 tokenId.strike(leg),
464                                 tokenId.width(leg),
465                                 tokenId.tokenType(leg)
466                             )
467                         );
468     
469                         LeftRightUnsigned availablePremium = _getAvailablePremium(
470                             _getTotalLiquidity(tokenId, leg),
471                             s_settledTokens[chunkKey],
472                             s_grossPremiumLast[chunkKey],
473                             LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(premiaByLeg[leg]))),
474                             premiumAccumulatorsByLeg[leg]
475                         );
476                         portfolioPremium = portfolioPremium.add(
477                             LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
478                         );
479                     } else {
480                         portfolioPremium = portfolioPremium.add(premiaByLeg[leg]);
481                     }
482                     unchecked {
483                         ++leg;
484                     }
485                 }


745             for (uint256 leg = 0; leg < numLegs; ) {
746                 // Extract base fee (AMM swap/trading fees) for the position and add it to s_options
747                 // (ie. the (feeGrowth * liquidity) / 2**128 for each token)
748                 (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
749                 uint256 isLong = tokenId.isLong(leg);
750                 {
751                     (uint128 premiumAccumulator0, uint128 premiumAccumulator1) = SFPM.getAccountPremium(
752                         address(s_univ3pool),
753                         address(this),
754                         tokenId.tokenType(leg),
755                         tickLower,
756                         tickUpper,
757                         type(int24).max,
758                         isLong
759                     );
760     
761                     // update the premium accumulators
762                     s_options[msg.sender][tokenId][leg] = LeftRightUnsigned
763                         .wrap(0)
764                         .toRightSlot(premiumAccumulator0)
765                         .toLeftSlot(premiumAccumulator1);
766                 }
767                 // verify base Liquidity limit only if new position is long
768                 if (isLong == 1) {
769                     // Move this into a new function
770                     _checkLiquiditySpread(
771                         tokenId,
772                         leg,
773                         tickLower,
774                         tickUpper,
775                         uint64(Math.min(effectiveLiquidityLimitX32, MAX_SPREAD))
776                     );
777                 }
778                 unchecked {
779                     ++leg;
780                 }
781             }


864             for (uint256 leg = 0; leg < numLegs; ) {
865                 if (tokenId.isLong(leg) == 0) {
866                     // Check the liquidity spread, make sure that closing the option does not exceed the MAX_SPREAD allowed
867                     (int24 tickLower, int24 tickUpper) = tokenId.asTicks(leg);
868                     _checkLiquiditySpread(tokenId, leg, tickLower, tickUpper, MAX_SPREAD);
869                 }
870                 s_options[owner][tokenId][leg] = LeftRightUnsigned.wrap(0);
871                 unchecked {
872                     ++leg;
873                 }
874             }


1518            for (uint256 leg = 0; leg < numLegs; ) {
1519                uint256 isLong = tokenId.isLong(leg);
1520                if ((isLong == 1) || computeAllPremia) {
1521                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1522                        tokenId,
1523                        leg,
1524                        positionSize
1525                    );
1526                    uint256 tokenType = tokenId.tokenType(leg);
1527    
1528                    (premiumAccumulatorsByLeg[leg][0], premiumAccumulatorsByLeg[leg][1]) = SFPM
1529                        .getAccountPremium(
1530                            address(s_univ3pool),
1531                            address(this),
1532                            tokenType,
1533                            liquidityChunk.tickLower(),
1534                            liquidityChunk.tickUpper(),
1535                            atTick,
1536                            isLong
1537                        );
1538    
1539                    unchecked {
1540                        LeftRightUnsigned premiumAccumulatorLast = s_options[owner][tokenId][leg];
1541    
1542                        // if the premium accumulatorLast is higher than current, it means the premium accumulator has overflowed and rolled over at least once
1543                        // we can account for one rollover by doing (acc_cur + (acc_max - acc_last))
1544                        // if there are multiple rollovers or the rollover goes past the last accumulator, rolled over fees will just remain unclaimed
1545                        premiaByLeg[leg] = LeftRightSigned
1546                            .wrap(0)
1547                            .toRightSlot(
1548                                int128(
1549                                    int256(
1550                                        ((premiumAccumulatorsByLeg[leg][0] -
1551                                            premiumAccumulatorLast.rightSlot()) *
1552                                            (liquidityChunk.liquidity())) / 2 ** 64
1553                                    )
1554                                )
1555                            )
1556                            .toLeftSlot(
1557                                int128(
1558                                    int256(
1559                                        ((premiumAccumulatorsByLeg[leg][1] -
1560                                            premiumAccumulatorLast.leftSlot()) *
1561                                            (liquidityChunk.liquidity())) / 2 ** 64
1562                                    )
1563                                )
1564                            );
1565    
1566                        if (isLong == 1) {
1567                            premiaByLeg[leg] = LeftRightSigned.wrap(0).sub(premiaByLeg[leg]);
1568                        }
1569                    }
1570                }
1571                unchecked {
1572                    ++leg;
1573                }
1574            }


1672            for (uint256 leg = 0; leg < numLegs; ++leg) {
1673                bytes32 chunkKey = keccak256(
1674                    abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1675                );
1676                // add any tokens collected from Uniswap in a given chunk to the settled tokens available for withdrawal by sellers
1677                s_settledTokens[chunkKey] = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1678    
1679                if (tokenId.isLong(leg) == 0) {
1680                    LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
1681                        tokenId,
1682                        leg,
1683                        positionSize
1684                    );
1685    
1686                    // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (R + N)
1687                    uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1688    
1689                    // We need to adjust the grossPremiumLast value such that the result of
1690                    // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostMint/2**64 is equal to (grossPremium - grossPremiumLast)*totalLiquidityBeforeMint/2**64
1691                    // G: total gross premium
1692                    // T: totalLiquidityBeforeMint
1693                    // R: positionLiquidity
1694                    // C: current grossPremium value
1695                    // L: current grossPremiumLast value
1696                    // Ln: updated grossPremiumLast value
1697                    // T * (C - L) = G
1698                    // (T + R) * (C - Ln) = G
1699                    //
1700                    // T * (C - L) = (T + R) * (C - Ln)
1701                    // (TC - TL) / (T + R) = C - Ln
1702                    // Ln = C - (TC - TL)/(T + R)
1703                    // Ln = (CT + CR - TC + TL)/(T+R)
1704                    // Ln = (CR + TL)/(T+R)
1705    
1706                    uint256[2] memory grossCurrent;
1707                    (grossCurrent[0], grossCurrent[1]) = SFPM.getAccountPremium(
1708                        address(s_univ3pool),
1709                        address(this),
1710                        tokenId.tokenType(leg),
1711                        liquidityChunk.tickLower(),
1712                        liquidityChunk.tickUpper(),
1713                        type(int24).max,
1714                        0
1715                    );
1716    
1717                    unchecked {
1718                        // L
1719                        LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1720                        // R
1721                        uint256 positionLiquidity = liquidityChunk.liquidity();
1722                        // T (totalLiquidity is (T + R) after minting)
1723                        uint256 totalLiquidityBefore = totalLiquidity - positionLiquidity;
1724    
1725                        s_grossPremiumLast[chunkKey] = LeftRightUnsigned
1726                            .wrap(0)
1727                            .toRightSlot(
1728                                uint128(
1729                                    (grossCurrent[0] *
1730                                        positionLiquidity +
1731                                        grossPremiumLast.rightSlot() *
1732                                        totalLiquidityBefore) / (totalLiquidity)
1733                                )
1734                            )
1735                            .toLeftSlot(
1736                                uint128(
1737                                    (grossCurrent[1] *
1738                                        positionLiquidity +
1739                                        grossPremiumLast.leftSlot() *
1740                                        totalLiquidityBefore) / (totalLiquidity)
1741                                )
1742                            );
1743                    }
1744                }
1745            }


1852            for (uint256 leg = 0; leg < numLegs; ) {
1853                LeftRightSigned legPremia = premiaByLeg[leg];
1854    
1855                bytes32 chunkKey = keccak256(
1856                    abi.encodePacked(tokenId.strike(leg), tokenId.width(leg), tokenId.tokenType(leg))
1857                );
1858    
1859                // collected from Uniswap
1860                LeftRightUnsigned settledTokens = s_settledTokens[chunkKey].add(collectedByLeg[leg]);
1861    
1862                if (LeftRightSigned.unwrap(legPremia) != 0) {
1863                    // (will be) paid by long legs
1864                    if (tokenId.isLong(leg) == 1) {
1865                        if (commitLongSettled)
1866                            settledTokens = LeftRightUnsigned.wrap(
1867                                uint256(
1868                                    LeftRightSigned.unwrap(
1869                                        LeftRightSigned
1870                                            .wrap(int256(LeftRightUnsigned.unwrap(settledTokens)))
1871                                            .sub(legPremia)
1872                                    )
1873                                )
1874                            );
1875                        realizedPremia = realizedPremia.add(legPremia);
1876                    } else {
1877                        uint256 positionLiquidity = PanopticMath
1878                            .getLiquidityChunk(tokenId, leg, positionSize)
1879                            .liquidity();
1880    
1881                        // new totalLiquidity (total sold) = removedLiquidity + netLiquidity (T - R)
1882                        uint256 totalLiquidity = _getTotalLiquidity(tokenId, leg);
1883                        // T (totalLiquidity is (T - R) after burning)
1884                        uint256 totalLiquidityBefore = totalLiquidity + positionLiquidity;
1885    
1886                        LeftRightUnsigned grossPremiumLast = s_grossPremiumLast[chunkKey];
1887    
1888                        LeftRightUnsigned availablePremium = _getAvailablePremium(
1889                            totalLiquidity + positionLiquidity,
1890                            settledTokens,
1891                            grossPremiumLast,
1892                            LeftRightUnsigned.wrap(uint256(LeftRightSigned.unwrap(legPremia))),
1893                            premiumAccumulatorsByLeg[leg]
1894                        );
1895    
1896                        // subtract settled tokens sent to seller
1897                        settledTokens = settledTokens.sub(availablePremium);
1898    
1899                        // add available premium to amount that should be settled
1900                        realizedPremia = realizedPremia.add(
1901                            LeftRightSigned.wrap(int256(LeftRightUnsigned.unwrap(availablePremium)))
1902                        );
1903    
1904                        // We need to adjust the grossPremiumLast value such that the result of
1905                        // (grossPremium - adjustedGrossPremiumLast)*updatedTotalLiquidityPostBurn/2**64 is equal to
1906                        // (grossPremium - grossPremiumLast)*totalLiquidityBeforeBurn/2**64 - premiumOwedToPosition
1907                        // G: total gross premium (- premiumOwedToPosition)
1908                        // T: totalLiquidityBeforeMint
1909                        // R: positionLiquidity
1910                        // C: current grossPremium value
1911                        // L: current grossPremiumLast value
1912                        // Ln: updated grossPremiumLast value
1913                        // T * (C - L) = G
1914                        // (T - R) * (C - Ln) = G - P
1915                        //
1916                        // T * (C - L) = (T - R) * (C - Ln) + P
1917                        // (TC - TL - P) / (T - R) = C - Ln
1918                        // Ln = C - (TC - TL - P) / (T - R)
1919                        // Ln = (TC - CR - TC + LT + P) / (T-R)
1920                        // Ln = (LT - CR + P) / (T-R)
1921    
1922                        unchecked {
1923                            uint256[2][4] memory _premiumAccumulatorsByLeg = premiumAccumulatorsByLeg;
1924                            uint256 _leg = leg;
1925    
1926                            // if there's still liquidity, compute the new grossPremiumLast
1927                            // otherwise, we just reset grossPremiumLast to the current grossPremium
1928                            s_grossPremiumLast[chunkKey] = totalLiquidity != 0
1929                                ? LeftRightUnsigned
1930                                    .wrap(0)
1931                                    .toRightSlot(
1932                                        uint128(
1933                                            uint256(
1934                                                Math.max(
1935                                                    (int256(
1936                                                        grossPremiumLast.rightSlot() *
1937                                                            totalLiquidityBefore
1938                                                    ) -
1939                                                        int256(
1940                                                            _premiumAccumulatorsByLeg[_leg][0] *
1941                                                                positionLiquidity
1942                                                        )) + int256(legPremia.rightSlot() * 2 ** 64),
1943                                                    0
1944                                                )
1945                                            ) / totalLiquidity
1946                                        )
1947                                    )
1948                                    .toLeftSlot(
1949                                        uint128(
1950                                            uint256(
1951                                                Math.max(
1952                                                    (int256(
1953                                                        grossPremiumLast.leftSlot() *
1954                                                            totalLiquidityBefore
1955                                                    ) -
1956                                                        int256(
1957                                                            _premiumAccumulatorsByLeg[_leg][1] *
1958                                                                positionLiquidity
1959                                                        )) + int256(legPremia.leftSlot()) * 2 ** 64,
1960                                                    0
1961                                                )
1962                                            ) / totalLiquidity
1963                                        )
1964                                    )
1965                                : LeftRightUnsigned
1966                                    .wrap(0)
1967                                    .toRightSlot(uint128(premiumAccumulatorsByLeg[_leg][0]))
1968                                    .toLeftSlot(uint128(premiumAccumulatorsByLeg[_leg][1]));
1969                        }
1970                    }
1971                }
1972    
1973                // update settled tokens in storage with all local deltas
1974                s_settledTokens[chunkKey] = settledTokens;
1975    
1976                unchecked {
1977                    ++leg;
1978                }
1979            }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1852:1979

```solidity
File: contracts/SemiFungiblePositionManager.sol


601             for (uint256 leg = 0; leg < numLegs; ) {
602                 // for this leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
603                 // @dev see `contracts/types/LiquidityChunk.sol`
604                 LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
605                     id,
606                     leg,
607                     uint128(amount)
608                 );
609     
610                 //construct the positionKey for the from and to addresses
611                 bytes32 positionKey_from = keccak256(
612                     abi.encodePacked(
613                         address(univ3pool),
614                         from,
615                         id.tokenType(leg),
616                         liquidityChunk.tickLower(),
617                         liquidityChunk.tickUpper()
618                     )
619                 );
620                 bytes32 positionKey_to = keccak256(
621                     abi.encodePacked(
622                         address(univ3pool),
623                         to,
624                         id.tokenType(leg),
625                         liquidityChunk.tickLower(),
626                         liquidityChunk.tickUpper()
627                     )
628                 );
629     
630                 // Revert if recipient already has that position
631                 if (
632                     (LeftRightUnsigned.unwrap(s_accountLiquidity[positionKey_to]) != 0) ||
633                     (LeftRightSigned.unwrap(s_accountFeesBase[positionKey_to]) != 0)
634                 ) revert Errors.TransferFailed();
635     
636                 // Revert if sender has long positions in that chunk or the entire liquidity is not being transferred
637                 LeftRightUnsigned fromLiq = s_accountLiquidity[positionKey_from];
638                 if (LeftRightUnsigned.unwrap(fromLiq) != liquidityChunk.liquidity())
639                     revert Errors.TransferFailed();
640     
641                 LeftRightSigned fromBase = s_accountFeesBase[positionKey_from];
642     
643                 //update+store liquidity and fee values between accounts
644                 s_accountLiquidity[positionKey_to] = fromLiq;
645                 s_accountLiquidity[positionKey_from] = LeftRightUnsigned.wrap(0);
646     
647                 s_accountFeesBase[positionKey_to] = fromBase;
648                 s_accountFeesBase[positionKey_from] = LeftRightSigned.wrap(0);
649                 unchecked {
650                     ++leg;
651                 }
652             }


882             for (uint256 leg = 0; leg < numLegs; ) {
883                 LeftRightSigned _moved;
884                 LeftRightSigned _itmAmounts;
885                 LeftRightUnsigned _collectedSingleLeg;
886     
887                 {
888                     // cache the univ3pool, tokenId, isBurn, and _positionSize variables to get rid of stack too deep error
889                     IUniswapV3Pool _univ3pool = univ3pool;
890                     TokenId _tokenId = tokenId;
891                     bool _isBurn = isBurn;
892                     uint128 _positionSize = positionSize;
893                     uint256 _leg;
894     
895                     unchecked {
896                         // Reverse the order of the legs if this call is burning a position (LIFO)
897                         // We loop in reverse order if burning a position so that any dependent long liquidity is returned to the pool first,
898                         // allowing the corresponding short liquidity to be removed
899                         _leg = _isBurn ? numLegs - leg - 1 : leg;
900                     }
901     
902                     // for this _leg index: extract the liquidity chunk: a 256bit word containing the liquidity amount and upper/lower tick
903                     // @dev see `contracts/types/LiquidityChunk.sol`
904                     LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
905                         _tokenId,
906                         _leg,
907                         _positionSize
908                     );
909     
910                     (_moved, _itmAmounts, _collectedSingleLeg) = _createLegInAMM(
911                         _univ3pool,
912                         _tokenId,
913                         _leg,
914                         liquidityChunk,
915                         _isBurn
916                     );
917     
918                     collectedByLeg[_leg] = _collectedSingleLeg;
919     
920                     unchecked {
921                         // increment accumulators of the upper bound on tokens contained across all legs of the position at any given tick
922                         amount0 += Math.getAmount0ForLiquidity(liquidityChunk);
923     
924                         amount1 += Math.getAmount1ForLiquidity(liquidityChunk);
925                     }
926                 }
927     
928                 totalMoved = totalMoved.add(_moved);
929                 itmAmounts = itmAmounts.add(_itmAmounts);
930     
931                 unchecked {
932                     ++leg;
933                 }
934             }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L882:934

```solidity
File: contracts/libraries/FeesCalc.sol


51              for (uint256 k = 0; k < positionIdList.length; ) {
52                  TokenId tokenId = positionIdList[k];
53                  uint128 positionSize = userBalance[tokenId].rightSlot();
54                  uint256 numLegs = tokenId.countLegs();
55                  for (uint256 leg = 0; leg < numLegs; ) {
56                      LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
57                          tokenId,
58                          leg,
59                          positionSize
60                      );
61      
62                      (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
63                          atTick,
64                          liquidityChunk
65                      );
66      
67                      if (tokenId.isLong(leg) == 0) {
68                          unchecked {
69                              value0 += int256(amount0);
70                              value1 += int256(amount1);
71                          }
72                      } else {
73                          unchecked {
74                              value0 -= int256(amount0);
75                              value1 -= int256(amount1);
76                          }
77                      }
78      
79                      unchecked {
80                          ++leg;
81                      }
82                  }
83                  unchecked {
84                      ++k;
85                  }
86              }


55                  for (uint256 leg = 0; leg < numLegs; ) {
56                      LiquidityChunk liquidityChunk = PanopticMath.getLiquidityChunk(
57                          tokenId,
58                          leg,
59                          positionSize
60                      );
61      
62                      (uint256 amount0, uint256 amount1) = Math.getAmountsForLiquidity(
63                          atTick,
64                          liquidityChunk
65                      );
66      
67                      if (tokenId.isLong(leg) == 0) {
68                          unchecked {
69                              value0 += int256(amount0);
70                              value1 += int256(amount1);
71                          }
72                      } else {
73                          unchecked {
74                              value0 -= int256(amount0);
75                              value1 -= int256(amount1);
76                          }
77                      }
78      
79                      unchecked {
80                          ++leg;
81                      }
82                  }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L55:82

```solidity
File: contracts/libraries/PanopticMath.sol


395             for (uint256 leg = 0; leg < numLegs; ) {
396                 // Compute the amount of funds that have been removed from the Panoptic Pool
397                 (LeftRightSigned longs, LeftRightSigned shorts) = _calculateIOAmounts(
398                     tokenId,
399                     positionSize,
400                     leg
401                 );
402     
403                 longAmounts = longAmounts.add(longs);
404                 shortAmounts = shortAmounts.add(shorts);
405     
406                 unchecked {
407                     ++leg;
408                 }
409             }


784                     for (uint256 leg = 0; leg < numLegs; ++leg) {
785                         if (tokenId.isLong(leg) == 1) {
786                             longPremium = longPremium.sub(premiasByLeg[i][leg]);
787                         }
788                     }


863                     for (uint256 leg = 0; leg < tokenId.countLegs(); ++leg) {
864                         if (tokenId.isLong(leg) == 1) {
865                             mapping(bytes32 chunkKey => LeftRightUnsigned settledTokens)
866                                 storage _settledTokens = settledTokens;
867     
868                             // calculate amounts to revoke from settled and subtract from haircut req
869                             uint256 settled0 = Math.unsafeDivRoundingUp(
870                                 uint128(-_premiasByLeg[i][leg].rightSlot()) * uint256(haircut0),
871                                 uint128(longPremium.rightSlot())
872                             );
873                             uint256 settled1 = Math.unsafeDivRoundingUp(
874                                 uint128(-_premiasByLeg[i][leg].leftSlot()) * uint256(haircut1),
875                                 uint128(longPremium.leftSlot())
876                             );
877     
878                             bytes32 chunkKey = keccak256(
879                                 abi.encodePacked(
880                                     tokenId.strike(0),
881                                     tokenId.width(0),
882                                     tokenId.tokenType(0)
883                                 )
884                             );
885     
886                             // The long premium is not commited to storage during the liquidation, so we add the entire adjusted amount
887                             // for the haircut directly to the accumulator
888                             settled0 = Math.max(
889                                 0,
890                                 uint128(-_premiasByLeg[i][leg].rightSlot()) - settled0
891                             );
892                             settled1 = Math.max(
893                                 0,
894                                 uint128(-_premiasByLeg[i][leg].leftSlot()) - settled1
895                             );
896     
897                             _settledTokens[chunkKey] = _settledTokens[chunkKey].add(
898                                 LeftRightUnsigned.wrap(0).toRightSlot(uint128(settled0)).toLeftSlot(
899                                     uint128(settled1)
900                                 )
901                             );
902                         }
903                     }


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L863:903

</details>

## NC055 - Use the latest solidity (prior to 0.8.20 if on L2s) for deployment:

Since deployed contracts should not use floating pragmas, I've flagged all instances where a version prior to 0.8.19 is allowed by the version pragma


<details>
<summary>Click to show 20 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L2:2

```solidity
File: contracts/PanopticFactory.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L2:2

```solidity
File: contracts/PanopticPool.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L2:2

```solidity
File: contracts/SemiFungiblePositionManager.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L2:2

```solidity
File: contracts/libraries/CallbackLib.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L2:2

```solidity
File: contracts/libraries/Constants.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L2:2

```solidity
File: contracts/libraries/Errors.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol#L2:2

```solidity
File: contracts/libraries/FeesCalc.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L2:2

```solidity
File: contracts/libraries/InteractionHelper.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L2:2

```solidity
File: contracts/libraries/Math.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L2:2

```solidity
File: contracts/libraries/PanopticMath.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L2:2

```solidity
File: contracts/libraries/SafeTransferLib.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L2:2

```solidity
File: contracts/multicall/Multicall.sol


2       pragma solidity ^0.8.18;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L2:2

```solidity
File: contracts/tokens/ERC1155Minimal.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L2:2

```solidity
File: contracts/tokens/ERC20Minimal.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L2:2

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L2:2

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L2:2

```solidity
File: contracts/types/LeftRight.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L2:2

```solidity
File: contracts/types/LiquidityChunk.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L2:2

```solidity
File: contracts/types/TokenId.sol


2       pragma solidity ^0.8.0;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L2:2

</details>

## NC056 - Visibility should be set explicitly rather than defaulting to internal:

Visibility of state variables should be set explicitly rather than defaulting to internal.


<details>
<summary>Click to show 8 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


131         uint256 immutable TICK_DEVIATION;


136         uint256 immutable COMMISSION_FEE;


141         uint256 immutable SELLER_COLLATERAL_RATIO;


145         uint256 immutable BUYER_COLLATERAL_RATIO;


149         int256 immutable FORCE_EXERCISE_COST;


154         uint256 immutable TARGET_POOL_UTIL;


158         uint256 immutable SATURATED_POOL_UTIL;


162         uint256 immutable ITM_SPREAD_MULTIPLIER;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L162:162

</details>

## NC057 - Use bit shifts in an imutable variable rather than long bit masks of a single bit, for readability:




```solidity
File: contracts/libraries/Constants.sol


9           uint256 internal constant FP96 = 0x1000000000000000000000000;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L9:9

## NC058 - Event declarations should have NatSpec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 11 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


49          event Deposit(address indexed sender, address indexed owner, uint256 assets, uint256 shares);


57          event Withdraw(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L57:57

```solidity
File: contracts/PanopticFactory.sol


34          event OwnershipTransferred(address indexed oldOwner, address indexed newOwner);


43          event PoolDeployed(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L43:43

```solidity
File: contracts/PanopticPool.sol


62          event PremiumSettled(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L62:62

```solidity
File: contracts/SemiFungiblePositionManager.sol


80          event PoolInitialized(address indexed uniswapPool, uint64 poolId);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L80:80

```solidity
File: contracts/tokens/ERC1155Minimal.sol


22          event TransferSingle(


36          event TransferBatch(


48          event ApprovalForAll(address indexed owner, address indexed operator, bool approved);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L48:48

```solidity
File: contracts/tokens/ERC20Minimal.sol


18          event Transfer(address indexed from, address indexed to, uint256 amount);


24          event Approval(address indexed owner, address indexed spender, uint256 amount);


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L24:24

</details>

## NC059 - Function definitions should have NatSpec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 146 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


178         constructor(


289         function name() external view returns (string memory) {


303         function symbol() external view returns (string memory) {


310         function decimals() external view returns (uint8) {


361         function asset() external view returns (address assetTokenAddress) {


379         function convertToShares(uint256 assets) public view returns (uint256 shares) {


386         function convertToAssets(uint256 shares) public view returns (uint256 assets) {


392         function maxDeposit(address) external pure returns (uint256 maxAssets) {


399         function previewDeposit(uint256 assets) public view returns (uint256 shares) {


444         function maxMint(address) external view returns (uint256 maxShares) {


453         function previewMint(uint256 shares) public view returns (uint256 assets) {


518         function previewWithdraw(uint256 assets) public view returns (uint256 shares) {


572         function maxRedeem(address owner) public view returns (uint256 maxShares) {


581         function previewRedeem(uint256 shares) public view returns (uint256 assets) {


591         function redeem(


911         function revoke(


995         function takeCommissionAddData(


1096        function _getExchangedAmount(


1245        function _getRequiredCollateralAtTickSinglePosition(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L1245:1245

```solidity
File: contracts/PanopticFactory.sol


115         constructor(


134         function initialize(address _owner) public {


147         function transferOwnership(address newOwner) external {


159         function owner() external view returns (address) {


335         function _mintFullRange(


420         function getPanopticPool(IUniswapV3Pool univ3pool) external view returns (PanopticPool) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticFactory.sol#L420:420

```solidity
File: contracts/PanopticPool.sol


280         constructor(SemiFungiblePositionManager _sfpm) {


352         function optionPositionBalance(


429         function _calculateAccumulatedPremia(


499         function _getSlippageLimits(


522         function pokeMedian() external {


547         function mintOptions(


614         function _mintOptions(


794         function _burnAllOptionsFrom(


826         function _burnOptions(


859         function _updatePositionDataBurn(address owner, TokenId tokenId) internal {


955         function _burnAndHandleExercise(


1290        function _checkSolvencyAtTick(


1339        function _getSolvencyBalances(


1425        function univ3pool() external view returns (IUniswapV3Pool) {


1431        function collateralToken0() external view returns (CollateralTracker collateralToken) {


1437        function collateralToken1() external view returns (CollateralTracker) {


1444        function numberOfPositions(address user) public view returns (uint256 _numberOfPositions) {


1450        function getUniV3TWAP() internal view returns (int24 twapTick) {


1465        function _checkLiquiditySpread(


1503        function _getPremia(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/PanopticPool.sol#L1503:1503

```solidity
File: contracts/SemiFungiblePositionManager.sol


330         function endReentrancyLock(uint64 poolId) internal {


341         constructor(IUniswapV3Factory _factory) {


504         function mintTokenizedPosition(


680         function _validateAndForwardToAMM(


756         function swapInAMM(


1110        function _updateStoredPremia(


1255        function _collectAndWritePositionData(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L1255:1255

```solidity
File: contracts/libraries/CallbackLib.sol


30          function validateCallback(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L30:30

```solidity
File: contracts/libraries/FeesCalc.sol


46          function getPortfolioValue(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/FeesCalc.sol#L46:46

```solidity
File: contracts/libraries/InteractionHelper.sol


24          function doApprovals(


91          function computeSymbol(


107         function computeDecimals(address token) external view returns (uint8) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/InteractionHelper.sol#L107:107

```solidity
File: contracts/libraries/Math.sol


25          function min24(int24 a, int24 b) internal pure returns (int24) {


33          function max24(int24 a, int24 b) internal pure returns (int24) {


41          function min(uint256 a, uint256 b) internal pure returns (uint256) {


49          function min(int256 a, int256 b) internal pure returns (int256) {


57          function max(uint256 a, uint256 b) internal pure returns (uint256) {


65          function max(int256 a, int256 b) internal pure returns (int256) {


91          function mostSignificantNibble(uint160 x) internal pure returns (uint256 r) {


207         function getAmount1ForLiquidity(LiquidityChunk liquidityChunk) internal pure returns (uint256) {


221         function getAmountsForLiquidity(


296         function toUint128(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {


302         function toUint128Capped(uint256 toDowncast) internal pure returns (uint128 downcastedInt) {


311         function toInt128(uint128 toCast) internal pure returns (int128 downcastedInt) {


318         function toInt128(int256 toCast) internal pure returns (int128 downcastedInt) {


325         function toInt256(uint256 toCast) internal pure returns (int256) {


440         function mulDivRoundingUp(


458         function mulDiv64(uint256 a, uint256 b) internal pure returns (uint256) {


521         function mulDiv96(uint256 a, uint256 b) internal pure returns (uint256) {


584         function mulDiv96RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {


598         function mulDiv128(uint256 a, uint256 b) internal pure returns (uint256) {


661         function mulDiv128RoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {


675         function mulDiv192(uint256 a, uint256 b) internal pure returns (uint256) {


738         function unsafeDivRoundingUp(uint256 a, uint256 b) internal pure returns (uint256 result) {


753         function quickSort(int256[] memory arr, int256 left, int256 right) internal pure {


776         function sort(int256[] memory data) internal pure returns (int256[] memory) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L776:776

```solidity
File: contracts/libraries/PanopticMath.sol


59          function incrementPoolPattern(uint64 poolId) internal pure returns (uint64) {


75          function numberOfLeadingHexZeros(address addr) external pure returns (uint256) {


289         function getLiquidityChunk(


338         function getTicks(


390         function computeExercisedAmounts(


419         function convertCollateralData(


445         function convertCollateralData(


574         function getAmountsMoved(


607         function _calculateIOAmounts(


651         function getLiquidationBonus(


917         function getRefundAmounts(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L917:917

```solidity
File: contracts/libraries/SafeTransferLib.sol


21          function safeTransferFrom(address token, address from, address to, uint256 amount) internal {


52          function safeTransfer(address token, address to, uint256 amount) internal {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L52:52

```solidity
File: contracts/multicall/Multicall.sol


12          function multicall(bytes[] calldata data) public payable returns (bytes[] memory results) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/multicall/Multicall.sol#L12:12

```solidity
File: contracts/tokens/ERC1155Minimal.sol


81          function setApprovalForAll(address operator, bool approved) public {


200         function supportsInterface(bytes4 interfaceId) public pure returns (bool) {


214         function _mint(address to, uint256 id, uint256 amount) internal {


236         function _burn(address from, uint256 id, uint256 amount) internal {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L236:236

```solidity
File: contracts/tokens/ERC20Minimal.sol


49          function approve(address spender, uint256 amount) public returns (bool) {


61          function transfer(address to, uint256 amount) public virtual returns (bool) {


103         function _transferFrom(address from, address to, uint256 amount) internal {


122         function _mint(address to, uint256 amount) internal {


136         function _burn(address from, uint256 amount) internal {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L136:136

```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


13          function issueNFT(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L13:13

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol


27          function transfer(address to, uint256 amount) external;


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L27:27

```solidity
File: contracts/types/LeftRight.sol


39          function rightSlot(LeftRightUnsigned self) internal pure returns (uint128) {


46          function rightSlot(LeftRightSigned self) internal pure returns (int128) {


59          function toRightSlot(


78          function toRightSlot(


101         function leftSlot(LeftRightUnsigned self) internal pure returns (uint128) {


108         function leftSlot(LeftRightSigned self) internal pure returns (int128) {


121         function toLeftSlot(


134         function toLeftSlot(LeftRightSigned self, int128 left) internal pure returns (LeftRightSigned) {


148         function add(


171         function sub(


194         function add(LeftRightUnsigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {


214         function add(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {


232         function sub(LeftRightSigned x, LeftRightSigned y) internal pure returns (LeftRightSigned z) {


251         function subRect(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L251:251

```solidity
File: contracts/types/LiquidityChunk.sol


70          function createChunk(


89          function addLiquidity(


102         function addTickLower(


118         function addTickUpper(


135         function updateTickLower(


151         function updateTickUpper(


171         function tickLower(LiquidityChunk self) internal pure returns (int24) {


180         function tickUpper(LiquidityChunk self) internal pure returns (int24) {


189         function liquidity(LiquidityChunk self) internal pure returns (uint128) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L189:189

```solidity
File: contracts/types/TokenId.sol


87          function poolId(TokenId self) internal pure returns (uint64) {


96          function tickSpacing(TokenId self) internal pure returns (int24) {


118         function optionRatio(TokenId self, uint256 legIndex) internal pure returns (uint256) {


128         function isLong(TokenId self, uint256 legIndex) internal pure returns (uint256) {


138         function tokenType(TokenId self, uint256 legIndex) internal pure returns (uint256) {


148         function riskPartner(TokenId self, uint256 legIndex) internal pure returns (uint256) {


158         function strike(TokenId self, uint256 legIndex) internal pure returns (int24) {


183         function addPoolId(TokenId self, uint64 _poolId) internal pure returns (TokenId) {


193         function addTickSpacing(TokenId self, int24 _tickSpacing) internal pure returns (TokenId) {


221         function addOptionRatio(


240         function addIsLong(


255         function addTokenType(


273         function addRiskPartner(


291         function addStrike(


310         function addWidth(


336         function addLeg(


404         function countLongs(TokenId self) internal pure returns (uint256) {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L404:404

</details>

## NC060 - Function definitions should have NatSpec @notice annotations:

Explain to an end user what this does


<details>
<summary>Click to show 4 findings</summary>

```solidity
File: contracts/CollateralTracker.sol


178         constructor(


323         function transfer(


341         function transferFrom(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/CollateralTracker.sol#L341:341

```solidity
File: contracts/SemiFungiblePositionManager.sol


680         function _validateAndForwardToAMM(


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/SemiFungiblePositionManager.sol#L680:680

</details>

## NC061 - Interface declarations should have NatSpec @title annotations:

A title that should describe the contract/interface


```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


6       interface IDonorNFT {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L6:6

## NC062 - Interface declarations should have NatSpec @author annotations:

The name of the author


```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


6       interface IDonorNFT {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L6:6

## NC063 - Interface declarations should have NatSpec @notice annotations:

Explain to an end user what this does


```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


6       interface IDonorNFT {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L6:6

```solidity
File: contracts/tokens/interfaces/IERC20Partial.sol


11      interface IERC20Partial {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IERC20Partial.sol#L11:11

## NC064 - Interface declarations should have NatSpec @dev annotations:

Explain to a developer any extra details


```solidity
File: contracts/tokens/interfaces/IDonorNFT.sol


6       interface IDonorNFT {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/interfaces/IDonorNFT.sol#L6:6

## NC065 - Abstract contract declarations should have NatSpec @notice annotations:

Explain to an end user what this does


```solidity
File: contracts/tokens/ERC1155Minimal.sol


11      abstract contract ERC1155 {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC1155Minimal.sol#L11:11

```solidity
File: contracts/tokens/ERC20Minimal.sol


9       abstract contract ERC20Minimal {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/tokens/ERC20Minimal.sol#L9:9

## NC066 - Library declarations should have Natspec @title annotations:

A title that should describe the contract/interface


```solidity
File: contracts/libraries/SafeTransferLib.sol


11      library SafeTransferLib {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/SafeTransferLib.sol#L11:11

## NC067 - Library declarations should have Natspec @notice annotations:

Explain to an end user what this does


```solidity
File: contracts/libraries/PanopticMath.sol


18      library PanopticMath {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L18:18

## NC068 - Library declarations should have Natspec @dev annotations:

Explain to a developer any extra details


<details>
<summary>Click to show 8 findings</summary>

```solidity
File: contracts/libraries/CallbackLib.sol


12      library CallbackLib {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/CallbackLib.sol#L12:12

```solidity
File: contracts/libraries/Constants.sol


7       library Constants {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Constants.sol#L7:7

```solidity
File: contracts/libraries/Errors.sol


7       library Errors {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Errors.sol#L7:7

```solidity
File: contracts/libraries/Math.sol


13      library Math {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/Math.sol#L13:13

```solidity
File: contracts/libraries/PanopticMath.sol


18      library PanopticMath {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/libraries/PanopticMath.sol#L18:18

```solidity
File: contracts/types/LeftRight.sol


17      library LeftRightLibrary {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LeftRight.sol#L17:17

```solidity
File: contracts/types/LiquidityChunk.sol


52      library LiquidityChunkLibrary {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/LiquidityChunk.sol#L52:52

```solidity
File: contracts/types/TokenId.sol


60      library TokenIdLibrary {


```

https://github.com/code-423n4/2024-04-panoptic/tree/main/contracts/types/TokenId.sol#L60:60

</details>
