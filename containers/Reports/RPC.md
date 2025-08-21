# Reports.Api

## Overview
## RPC Calls by Category

### 1. Receival of the data, aggregated within the EventWerehousing service group on schedule

#### 1.1 Bet Event Statistics Rollup
- **Contract**: `RemotelyInvokable<RollupCollection<BetEventStatistic>, EmptyResponse, string>()`
- **Request Type**: `RollupCollection<BetEventStatistic>`
- **Response Type**: `EmptyResponse` (no data)

#### 1.2 Placed Bet Events Rollup
- **Contract**: `RemotelyInvokable<RollupCollection<PlacedBetEventRollup>, EmptyResponse, string>()`
- **Request Type**: `RollupCollection<PlacedBetEventRollup>`
- **Response Type**: `EmptyResponse` (no data)

#### 1.3 Paid Bet Events Rollup
- **Contract**: `RemotelyInvokable<RollupCollection<PaidBetEventRollup>, EmptyResponse, string>()`
- **Request Type**: `RollupCollection<PaidBetEventRollup>`
- **Response Type**: `EmptyResponse` (no data)

#### 1.4 Deposit Currency Operations Rollup
- **Contract**: `RemotelyInvokable<RollupCollection<DepositCurrencyOperationRollup>, EmptyResponse, string>()`
- **Request Type**: `RollupCollection<DepositCurrencyOperationRollup>`
- **Response Type**: `EmptyResponse` (no data)

#### 1.5 Withdrawal Currency Operations Rollup
- **Contract**: `RemotelyInvokable<RollupCollection<WithdrawalCurrencyOperationRollup>, EmptyResponse, string>()`
- **Request Type**: `RollupCollection<WithdrawalCurrencyOperationRollup>`
- **Response Type**: `EmptyResponse` (no data)

#### 1.6 Unique Players Rollup
- **Contract**: `RemotelyInvokable<RollupCollection<UniquePlayerRollup>, EmptyResponse, string>()`
- **Request Type**: `RollupCollection<UniquePlayerRollup>`
- **Response Type**: `EmptyResponse` (no data)

#### 1.7 Used Equipment Rollup
- **Contract**: `RemotelyInvokable<RollupCollection<UsedEquipment>, EmptyResponse, string>()`
- **Request Type**: `RollupCollection<UsedEquipment>`
- **Response Type**: `EmptyResponse` (no data)

### 2. Reports built from the read models, aggregating total amounts (money) over operations of different kinds

#### 2.1 Placed Bet Events Report
- **Contract**: `RemotelyInvokable<AnalyticsReportRequest, YearlyReportsWithUniquePlayers, string>("placed")`
- **Request Type**: `AnalyticsReportRequest`
- **Response Type**: `YearlyReportsWithUniquePlayers`

#### 2.2 Should Be Paid Report
- **Contract**: `RemotelyInvokable<AnalyticsReportRequest, YearlyReportsWithUniquePlayers, string>("shouldBePaid")`
- **Request Type**: `AnalyticsReportRequest`
- **Response Type**: `YearlyReportsWithUniquePlayers`

#### 2.3 Paid Bet Events Report
- **Contract**: `RemotelyInvokable<AnalyticsReportRequest, YearlyReportsWithUniquePlayers, string>("paid")`
- **Request Type**: `AnalyticsReportRequest`
- **Response Type**: `YearlyReportsWithUniquePlayers`

#### 2.4 GGR (Gross Gaming Revenue) Report
- **Contract**: `RemotelyInvokable<AnalyticsReportRequest, YearlyReports, string>()`
- **Request Type**: `AnalyticsReportRequest`
- **Response Type**: `YearlyReports`

#### 2.5 Tax Report
- **Contract**: `RemotelyInvokable<AnalyticsReportRequest, YearlyTaxReports, string>()`
- **Request Type**: `AnalyticsReportRequest`
- **Response Type**: `YearlyTaxReports`

#### 2.6 Revenue Report
- **Contract**: `RemotelyInvokable<RevenueReportRequest, RevenueReportResponse, string>()`
- **Request Type**: `RevenueReportRequest`
- **Response Type**: `RevenueReportResponse`

#### 2.7 Currency Exchange Report
- **Contract**: `RemotelyInvokable<CurrencyExchangeReportRequest, CurrencyExchangeReportResponse, string>()`
- **Request Type**: `CurrencyExchangeReportRequest`
- **Response Type**: `CurrencyExchangeReportResponse`

#### 2.8 Unique Players Report
- **Contract**: `RemotelyInvokable<UniquePlayersReportRequest, UniquePlayersReportResponse, string>()`
- **Request Type**: `UniquePlayersReportRequest`
- **Response Type**: `UniquePlayersReportResponse`

#### 2.9 Players Tax Report
- **Contract**: `RemotelyInvokable<PlayersTaxReportRequest, PlayersTaxReportResponse, string>()`
- **Request Type**: `PlayersTaxReportRequest`
- **Response Type**: `PlayersTaxReportResponse`

### 3. Reports, built of read models counting the gambling activities number and used equipment number

#### 3.1 Bet Event Statistic By Equipment - By Hour
- **Contract**: `RemotelyInvokable<ByEquipment.ByHourRequest, Response, string>()`
- **Request Type**: `ByEquipment.ByHourRequest`
- **Response Type**: `Response`

#### 3.2  Bet Event Statistic By Equipment - By Day
- **Contract**: `RemotelyInvokable<ByEquipment.ByDayRequest, Response, string>()`
- **Request Type**: `ByEquipment.ByDayRequest`
- **Response Type**: `Response`

#### 3.3  Bet Event Statistic By Establishment - By Hour
- **Contract**: `RemotelyInvokable<ByEstablishment.ByHourRequest, Response, string>()`
- **Request Type**: `ByEstablishment.ByHourRequest`
- **Response Type**: `Response`

#### 3.4  Bet Event Statistic By Establishment - By Day
- **Contract**: `RemotelyInvokable<ByEstablishment.ByDayRequest, Response, string>()`
- **Request Type**: `ByEstablishment.ByDayRequest`
- **Response Type**: `Response`

#### 3.5 Unused Equipment Report 
- **Contract**: `RemotelyInvokable<UnusedEquipmentAnalyticsRequest, UnusedEquipmentAnalyticsResponse, string>()`
- **Request Type**: `UnusedEquipmentAnalyticsRequest`
- **Response Type**: `UnusedEquipmentAnalyticsResponse`