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































## Data Sources

<details>
  <summary><b>Dimension Tables</b></summary>

### Dimension Tables
The following **dimension tables** are in MySQL schema `gdb023`. Sample records from the dimension tables are provided below.

**dim_customer**
| customer_code | customer         | platform     | channel   | market       | sub_zone | region |
|-------------:|:---------------|:--------------|:------------|:------------|:---------|:-------|
| 90004067     | Amazon          | E-Commerce  | Retailer | Japan      | ROA     | APAC   |
| 90004068     | Amazon          | E-Commerce  | Retailer | Japan      | ROA     | APAC   |
| 90007197     | Amazon          | E-Commerce  | Retailer | South Korea | ROA     | APAC   |
| 90022081     | Amazon          | E-Commerce  | Retailer | USA        | NA      | NA     |
| 90022082     | Amazon          | E-Commerce  | Retailer | USA        | NA      | NA     |
| 90023023     | Amazon          | E-Commerce  | Retailer | Canada     | NA      | NA     |
| 90023030     | Amazon          | E-Commerce  | Retailer | Canada     | NA      | NA     |
| 70004070     | Atliq e Store   | E-Commerce  | Direct   | Japan      | ROA     | APAC   |
| 70007199     | Atliq e Store   | E-Commerce  | Direct   | South Korea | ROA     | APAC   |
| 70022085     | Atliq e Store   | E-Commerce  | Direct   | USA        | NA      | NA     |
| 70023032     | Atliq e Store   | E-Commerce  | Direct   | Canada     | NA      | NA     |
| 70004069     | Atliq Exclusive | Brick & Mortar | Direct | Japan      | ROA     | APAC   |
| 70007198     | Atliq Exclusive | Brick & Mortar | Direct | South Korea | ROA     | APAC   |
| 70022084     | Atliq Exclusive | Brick & Mortar | Direct | USA        | NA      | NA     |
| 70023031     | Atliq Exclusive | Brick & Mortar | Direct | Canada     | NA      | NA     |
| 90022078     | Costco          | Brick & Mortar | Retailer | USA      | NA      | NA     |
| 90023027     | Costco          | Brick & Mortar | Retailer | Canada   | NA      | NA     |
| 90022080     | Staples         | Brick & Mortar | Retailer | USA      | NA      | NA     |
| 90023029     | Staples         | Brick & Mortar | Retailer | Canada   | NA      | NA     |
| 80001019	   | Neptune	       | Brick & Mortar | Distributor	| China |	ROA |	APAC |
| 80006154	   | Synthetic	     | Brick & Mortar	| Distributor	| Philiphines |	ROA |	APAC |
 
Notes:
* `customer_code` is a primary key field. 


**dim_product**
| 	product_code	 | 	division	 | 	segment	 | 	category	 | 	product	 | 	variant	 |
| 	-:	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 |
| A7119160102    | N & S    | Networking | Wi fi extender         | AQ Wi Power Dx1  | Plus        |
| A7119160103    | N & S    | Networking | Wi fi extender         | AQ Wi Power Dx1  | Premium     |
| A7118160101    | N & S    | Networking | Wi fi extender         | AQ Wi Power Dx1  | Standard    |
| A6419160302    | N & S    | Storage    | External Solid State Drives | AQ Clx1      | Plus        |
| A6419160303    | N & S    | Storage    | External Solid State Drives | AQ Clx1      | Premium     |
| A6419160301    | N & S    | Storage    | External Solid State Drives | AQ Clx1      | Standard    |
| A3119150303    | P & A    | Accessories| Keyboard               | AQ Gamers        | Plus 1      |
| A3120150304    | P & A    | Accessories| Keyboard               | AQ Gamers        | Plus 2      |
| A3120150305    | P & A    | Accessories| Keyboard               | AQ Gamers        | Premium 1   |
| A3120150306    | P & A    | Accessories| Keyboard               | AQ Gamers        | Premium 2   |
| A3119150301    | P & A    | Accessories| Keyboard               | AQ Gamers        | Standard 1  |
| A3119150302    | P & A    | Accessories| Keyboard               | AQ Gamers        | Standard 2  |
| A0721150402    | P & A    | Peripherals| Graphic Card           | AQ GT 21         | Plus 1      |
| A0721150403    | P & A    | Peripherals| Graphic Card           | AQ GT 21         | Plus 2      |
| A0721150404    | P & A    | Peripherals| Graphic Card           | AQ GT 21         | Premium     |
| A0721150401    | P & A    | Peripherals| Graphic Card           | AQ GT 21         | Standard    |
| A4118110105    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Plus Blue   |
| A4118110104    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Plus Grey   |
| A4118110106    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Plus Red    |
| A4118110107    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Premium Black|
| A4118110102    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Standard Blue|
| A4118110101    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Standard Grey|
| A4118110103    | PC       | Notebook   | Personal Laptop        | AQ Aspiron       | Standard Red|



Notes:
* `product_code` is a primary key field.
</details>



<details>
  <summary><b>Fact Tables</b></summary>

### Fact Tables
The following **fact tables** are in MySQL schema `gdb023`. Sample records from the fact tables are provided below.


**fact_sales_monthly**
| date       | product_code | customer_code | sold_quantity | fiscal_year |
|------------|--------------|---------------|---------------|-------------|
| 2019-09-01 | A0118150101  | 70002017      | 137           | 2020        |
| 2019-09-01 | A0118150101  | 70002018      | 47            | 2020        |
| 2019-09-01 | A0118150102  | 70002017      | 122           | 2020        |
| 2019-09-01 | A0118150102  | 70002018      | 24            | 2020        |
| 2019-10-01 | A0118150101  | 70002017      | 40            | 2020        |
| 2019-10-01 | A0118150101  | 70002018      | 32            | 2020        |
| 2019-10-01 | A0118150102  | 70002017      | 189           | 2020        |
| 2019-10-01 | A0118150102  | 70002018      | 139           | 2020        |
| 2020-09-01 | A0118150101  | 70002017      | 248           | 2021        |
| 2020-09-01 | A0118150101  | 70002018      | 240           | 2021        |
| 2020-09-01 | A0118150102  | 70002017      | 42            | 2021        |
| 2020-09-01 | A0118150102  | 70002018      | 91            | 2021        |
| 2020-10-01 | A0118150101  | 70002017      | 297           | 2021        |
| 2020-10-01 | A0118150101  | 70002018      | 119           | 2021        |
| 2020-10-01 | A0118150102  | 70002017      | 275           | 2021        |
| 2020-10-01 | A0118150102  | 70002018      | 284           | 2021        |

Notes:
* This table contains data on the sold quantity of products for specific customers, on a monthly level
* The columns `date`, `product_code`, and `customer_code` make up a **composite primary key**
* Sales data is available for fiscal years 2020 and 2021



**fact_gross_price**
| product_code | fiscal_year | gross_price |
|--------------|-------------|-------------|
| A0118150101  | 2020        | 16.2323     |
| A0118150101  | 2021        | 19.0573     |
| A0118150102  | 2020        | 19.8577     |
| A0118150102  | 2021        | 21.4565     |
| A0118150103  | 2020        | 22.1317     |
| A0118150103  | 2021        | 21.7795     |

Notes:
* Gross price is the base price of a product
* This table contains data on the gross price of each specific product on a fiscal year level
* The columns `product_code` and `fiscal_year` make up a **composite primary key**
* Gross price data is available for fiscal years 2020 and 2021


**fact_manufacturing_cost**
| product_code | cost_year | manufacturing_cost |
|--------------|-----------|--------------------|
| A0118150101  | 2020      | 5.0207             |
| A0118150101  | 2021      | 5.5172             |
| A0118150102  | 2020      | 5.7180             |
| A0118150102  | 2021      | 6.2835             |
| A0118150103  | 2020      | 6.3264             |
| A0118150103  | 2021      | 6.5900             |

Notes:
* Manufacturing cost is one component of COGS
* This table contains data on the manufacturing cost ($) for one unit quantity of each specific product on a fiscal year level
* The columns `product_code` and `cost_year` make up a **composite primary key**
* Manufacturing cost ($) data is available for fiscal years 2020 and 2021




**fact_pre_invoice_deductions**
| 	customer_code	 | 	fiscal_year	 | 	pre_invoice_discount_pct	 |
| 	-:	 | 	-:	 | 	-:	 |
| 70002017      | 2020        | 0.0735                   |
| 70002017      | 2021        | 0.0703                   |
| 70002018      | 2020        | 0.2255                   |
| 70002018      | 2021        | 0.2061                   |
| 70003181      | 2020        | 0.0531                   |
| 70003181      | 2021        | 0.0974                   |

Notes:
* This table contains data on pre-invoice deductions (as a percentage of gross sales) for each specific customer, on a fiscal year level
* The columns `customer_code`, and `fiscal_year` make up a **composite primary key**
* Pre-invoice deductions data is available for fiscal years 2020 and 2021

</details>

























































