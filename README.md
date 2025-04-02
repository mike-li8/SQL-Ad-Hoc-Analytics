# SQL-Ad-Hoc-Analytics

## Project Overview
The [Codebasics](https://codebasics.io/) [Data Analytics Bootcamp](https://codebasics.io/bootcamps/data-analytics-bootcamp-with-practical-job-assistance) exhibits a fictional company called AtliQ Technologies. In a previous project, [Power BI Business Insights 360](https://github.com/mike-li8/Power-BI-Business-Insights-360/blob/main/README.md), I built a dashboard that provided insights into various business verticals (finance, sales, marketing, supply chain, and executive).

While the Power BI dashboard answered many common business questions, AtliQ’s upper management team now has ten new ad-hoc business questions that cannot be easily addressed by the dashboard. The objective of this project is to use SQL in MySQL to answer these questions and present the insights back to the upper management team in a clear and concise data storytelling format.










## AtliQ Business Model

<details>
  <summary><b>Overview</b></summary>

### Overview
AtliQ manufactures computer hardware **products** (e.g., mouse, keyboard, printer, monitor) and then sells them to various **customers** which are stores such as Amazon and Best Buy. Hence, AtliQ's customers are in the form of <ins>store businesses</ins> (e.g., Amazon, Best Buy) and should not be confused with customers in the form of people (i.e., the people purchasing products from Amazon or Best Buy).
</details>

<details>
  <summary><b>Customers</b></summary>

### Customers
AtliQ's customers are categorized into two different **platforms**:
1. Brick & Motar
   * stores that have physical location(s)
2. E-Commerce
   * stores which only sell products online

AtliQ's customers are categorized into three different **channels**:
1. Retailer
   * Stores not owned by AtliQ (e.g. Amazon, Best Buy)
3. Direct
   * Stores owned by AtliQ. These are AltiQ Exclusive and AtliQ E-Store.
5. Distributor
   * Some markets have laws/regulations which only allow AtliQ to sell products to a distributor type customer within that market. AtliQ sells products to the distributor; the distributor then sells the products to various stores within that market.
</details>





<details>
  <summary><b>Condensed Profit and Loss (P&L) Statement</b></summary>

### Condensed Profit and Loss (P&L) Statement
This example of a simplified P&L statement should give a better understanding of AtliQ's business model. In this example, the P&L calculations and values are derived from one sales transaction of one product being sold to one customer.
| Line Item | Description | P & L Value Formula | P&L Value Calculation | P & L Value |
| :- | :- | :- | :- | -: |
| Gross Price |  The base price of a product | not applicable | `not applicable` | `$50.00` |
| Pre-Invoice Deduction | For every fiscal year, the sales team determines a<br>pre-invoice deduction percentage for each<br><ins>specific customer</ins>. The pre-invoice deduction<br>percentage is based on AtliQ's relationship and<br>experience with the customer. The pre-invoice<br>deduction is applied to the gross price of the<br>product before it is billed to the customer. In this<br>example, the customer receives a pre-invoice<br>deduction of 10% of gross price. | (Gross Price $) *<br> (Pre&nbsp;Invoice&nbsp;Deduction&nbsp;%) | `$50.00` *<br>`0.10` | `$5.00` |
| Net Invoice Sales | The amount of money that is billed to the<br>customer to obtain the product, after<br>pre invoice deductions are subtracted<br>from gross price. | (Gross Price $) -<br>(Pre&nbsp;Invoice Deduction $) | `$50.00` -<br>`$5.00` | `$45.00` |
| Post-Invoice Deudctions | For&nbsp;each&nbsp;calendar&nbsp;month,&nbsp;the&nbsp;sales&nbsp;team<br>determines&nbsp;a&nbsp;post-invoice&nbsp;deduction&nbsp;percentage<br>based&nbsp;on&nbsp;a&nbsp;<ins>specific&nbsp;customer&nbsp;and&nbsp;product</ins>.&nbsp;For<br>example,&nbsp;if&nbsp;AtliQ&nbsp;sells&nbsp;a&nbsp;product&nbsp;to&nbsp;a&nbsp;customer<br>and&nbsp;that&nbsp;customer&nbsp;agrees&nbsp;to&nbsp;display&nbsp;the&nbsp;product&nbsp;at<br>a&nbsp;prime&nbsp;location&nbsp;within&nbsp;the&nbsp;store&nbsp;during&nbsp;a<br>specific&nbsp;calendar&nbsp;month,&nbsp;AtliQ&nbsp;may&nbsp;pay&nbsp;that<br>customer&nbsp;a&nbsp;post-invoice&nbsp;deduction.&nbsp;AtliQ&nbsp;pays&nbsp;a<br>post-invoice&nbsp;deduction&nbsp;amount&nbsp;as&nbsp;a&nbsp;rebate&nbsp;to&nbsp;the<br>customer&nbsp;after&nbsp;net&nbsp;invoice&nbsp;sales.&nbsp;In&nbsp;this&nbsp;example,<br>the&nbsp;customer&nbsp;receives&nbsp;a&nbsp;post-invoice&nbsp;deduction&nbsp;of<br>20%&nbsp;of&nbsp;net&nbsp;invoice&nbsp;sales. | not applicable | `$45.00` *<br>`0.20` | `$9.00` |
| Net Sales | AtliQ's Revenue | (Net Invoice Sales $) -<br>(Post-Invoice Deudctions $) | `$45.00` -<br>`$9.00` | `$36.00` |
| Cost of Goods Sold (COGS $) | Expenses AtliQ incurs such as manufacturing<br>products, shipping products, and storing products<br>in warehouses. | (Manufacturing Cost $) +<br>(Freight Cost $) +<br>(Other COGS $) | `not applicable` | `$16.00` |
| Gross Margin | AtliQ's Profit after deducing COGS from Net Sales. | (Net Sales $) -<br>(COGS $) | `$36.00` -<br>`$16.00` | `$20.00` |
| Operational Expenses | Expenses AtliQ incurs from activities such as<br>advertising and promotions of products<br>performed by the marketing team. | (Ads & Promotions $) +<br>(Other&nbsp;Operational&nbsp;Expense&nbsp;$) | `not applicable` | `$15.00` |
| Net Profit | AtliQ's Profit after deducting operational expenses<br>from gross margin. | (Gross Margin $) -<br>(Operational Expenses $) | `$20.00` -<br>`$15.00` | `$5.00` |
</details>


<details>
  <summary><b>AtliQ Fiscal Year</b></summary>

### AtliQ Fiscal Year
AtliQ's fiscal year begins in September and ends in August the following year. The example below shows AtliQ's fiscal dates (for fiscal year 2021) compared to calendar dates.
| 	Calendar Month and Year	 | 	AtliQ Fiscal Year	 | 	AtliQ Fiscal Month Number | 	AtliQ Fiscal Quarter	 |
| 	-:	 | 	-:	 | 	-:	 | 	-:	 |
| 	September 2020	 | 	2021	 | 	1	 | 	Q1	 |
| 	October 2020	 | 	2021	 | 	2	 | 	Q1	 |
| 	November 2020	 | 	2021	 | 	3	 | 	Q1	 |
| 	December 2020	 | 	2021	 | 	4	 | 	Q2	 |
| 	January 2021	 | 	2021	 | 	5	 | 	Q2	 |
| 	February 2021	 | 	2021	 | 	6	 | 	Q2	 |
| 	March 2021	 | 	2021	 | 	7	 | 	Q3	 |
| 	April 2021	 | 	2021	 | 	8	 | 	Q3	 |
| 	May 2021	 | 	2021	 | 	9	 | 	Q3	 |
| 	June 2021	 | 	2021	 | 	10	 | 	Q4	 |
| 	July 2021	 | 	2021	 | 	11	 | 	Q4	 |
| 	August 2021	 | 	2021	 | 	12	 | 	Q4	 |
</details>












