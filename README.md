# SQL-Ad-Hoc-Analytics

## Project Overview
The [Codebasics](https://codebasics.io/) [Data Analytics Bootcamp](https://codebasics.io/bootcamps/data-analytics-bootcamp-with-practical-job-assistance) exhibits a fictional company called AtliQ Technologies. AtliQ was rapidly proliferating to various markets around the world. However, AtliQ relied on Excel files for their data analytics needs. Since AtliQ's data was spread across multiple large tables (some containing over a million records), analyzing them in Excel was cumbersome. Moreover, AtliQ frequently encountered technical difficulties using Excel as their primary tool for database. Hence, AtliQ choose **MySQL** as the new relational database management system (RDBMS) becasue it was open-source and powerful.

The objective of this project is to answer ad-hoc business questions by performing analysis in MySQL using SQL:
* User-Defined SQL Functions
* Stored Procedures
* Database Views
* Windows Functions
* Subquery
* CTE (Common Table Expression)
* Temporary Table









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
AtliQ's data engineers prepared various dimension tables and stored them in a MySQL database schema called `gdb0041`. Sample records from each table are provided below. For readability, primary key values for some tables have been converted to natural numbers.



**gdb0041.dim_customer**
| 	customer_code	 | 	customer	 | 	platform	 | 	channel	 | 	market	 | 	sub_zone	 | 	region	 |
| 	-:	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 |
| 	1	 | 	Amazon	 | 	E-Commerce	 | 	Retailer	 | 	USA	 | 	NA	 | 	NA	 |
| 	2	 | 	Amazon	 | 	E-Commerce	 | 	Retailer	 | 	Japan	 | 	ROA	 | 	APAC	 |
| 	3	 | 	Staples	 | 	Brick & Mortar	 | 	Retailer	 | 	USA	 | 	NA	 | 	NA	 |
| 	4	 | 	Staples	 | 	Brick & Mortar	 | 	Retailer	 | 	Canada	 | 	NA	 | 	NA	 |
| 	5	 | 	AltiQ Exclusive	 | 	Brick & Mortar	 | 	Direct	 | 	South Korea	 | 	ROA	 | 	APAC	 |
| 	6	 | 	Atliq e Store	 | 	E-Commerce	 | 	Direct	 | 	Newzealand	 | 	ANZ	 | 	APAC	 |
| 	7	 | 	Neptune	 | 	Brick & Mortar	 | 	Distributor	 | 	China	 | 	ROA	 | 	APAC	 |


`customer_code` is a primary key field. 

**gdb0041.dim_product**
| 	product_code	 | 	division	 | 	segment	 | 	category	 | 	product	 | 	variant	 |
| 	-:	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 | 	:-	 |
| 	1	 | 	P & A	 | 	Peripherals	 | 	Graphic Card	 | 	AQ Mforce Gen Y	 | 	Plus 1	 |
| 	2	 | 	P & A	 | 	Peripherals	 | 	Graphic Card	 | 	AQ Mforce Gen Y	 | 	Plus 2	 |
| 	3	 | 	P & A	 | 	Accessories	 | 	Mouse	 | 	AQ Master wired x1 Ms	 | 	Premium 1	 |
| 	4	 | 	P & A	 | 	Accessories	 | 	Mouse	 | 	AQ Master wired x1 Ms	 | 	Premium 2	 |
| 	5	 | 	PC	 | 	Notebook	 | 	Business Laptop	 | 	AQ BZ Compact	 | 	Standard Blue	 |
| 	6	 | 	PC	 | 	Notebook	 | 	Business Laptop	 | 	AQ BZ Compact	 | 	Standard Red	 |
| 	7	 | 	N & S	 | 	Networking	 | 	Wi fi extender	 | 	AQ Wi Power Dx1	 | 	Standard	 |
| 	8  | 	N & S	 | 	Networking	 | 	Wi fi extender	 | 	AQ Wi Power Dx2	 | 	Standard	 |
| 	9	 | 	N & S	 | 	Storage	 | 	External Solid State Drives	 | 	AQ Digit SSD	 | 	Premium	 |
|  10 | 	N & S	 | 	Storage	 | 	External&nbsp;Solid&nbsp;State&nbsp;Drives	 | 	AQ Neuer SSD	 | 	Premium	 |

`product_code` is a primary key field.
</details>



<details>
  <summary><b>Fact Tables</b></summary>

### Fact Tables
AtliQ's data engineers prepared various fact tables and stored them in a MySQL database schema called `gdb0041`. Sample records from each table are provided below.

**gdb0041.fact_forecast_monthly**
| 	date	 | 	fiscal_year	 | 	product_code	 | 	customer_code	 | 	forecast_quantity	 |
| 	-:	 | 	-:	 | 	-:	 | 	-:	 | 	-:	 |
| 	2018-09-01	 | 	2019	 | 	1	 | 	1	 | 	107	 |
| 	2018-09-01	 | 	2019	 | 	2	 | 	2	 | 	13	 |
| 	2018-10-01	 | 	2019	 | 	3	 | 	4	 | 	63	 |
| 	2018-10-01	 | 	2019	 | 	4	 | 	4	 | 	81	 |
| 	2018-11-01	 | 	2019	 | 	5	 | 	5	 | 	186	 |
| 	2018-11-01	 | 	2019	 | 	6	 | 	2	 | 	19	 |
| 	2018-12-01	 | 	2019	 | 	7	 | 	3	 | 	91	 |
| 	2018-12-01	 | 	2019	 | 	8	 | 	6	 | 	121	 |
| 	2019-01-01	 | 	2019	 | 	9	 | 	7	 | 	106	 |
| 	2019-01-01	 | 	2019	 | 	10	 | 	3	 | 	90	 |


Notes:
* This table contains data on the predicted quantity of a product required for a specific customer, on a monthly level.
* The columns `date`, `product_code`, and `customer_code` make up a **composite primary key**.


**gdb0041.fact_sales_monthly**
| 	date	 | 	fiscal_year	 | 	product_code	 | 	customer_code	 | 	sold_quantity	 |
| 	-:	 | 	-:	 | 	-:	 | 	-:	 | 	-:	 |
| 	2018-09-01	 | 	2019	 | 	1	 | 	1	 | 	70	 |
| 	2018-09-01	 | 	2019	 | 	2	 | 	2	 | 	152	 |
| 	2018-10-01	 | 	2019	 | 	3	 | 	4	 | 	129	 |
| 	2018-10-01	 | 	2019	 | 	4	 | 	4	 | 	60	 |
| 	2018-11-01	 | 	2019	 | 	5	 | 	5	 | 	164	 |
| 	2018-11-01	 | 	2019	 | 	6	 | 	2	 | 	158	 |
| 	2018-12-01	 | 	2019	 | 	7	 | 	3	 | 	163	 |
| 	2018-12-01	 | 	2019	 | 	8	 | 	6	 | 	66	 |
| 	2019-01-01	 | 	2019	 | 	9	 | 	7	 | 	140	 |
| 	2019-01-01	 | 	2019	 | 	10	 | 	3	 | 	61	 |


Notes:
* This table contains data on the actual sold quantity of a product for a specific customer, on a monthly level.
* The columns `date`, `product_code`, and `customer_code` make up a **composite primary key**.


**gdb0041.fact_freight_cost**
| 	market	 | 	fiscal_year	 | 	freight_pct	 | 	other_cost_pct	 |
| 	:-	 | 	-:	 | 	-:	 | 	-:	 |
| 	Australia	 | 	2018	 | 	0.0188	 | 	0.005	 |
| 	Australia	 | 	2019	 | 	0.0304	 | 	0.0048	 |
| 	Australia	 | 	2020	 | 	0.0254	 | 	0.0043	 |
| 	Australia	 | 	2021	 | 	0.0254	 | 	0.0043	 |
| 	Australia	 | 	2022	 | 	0.0254	 | 	0.0043	 |
| 	Bangladesh	 | 	2018	 | 	0.0219	 | 	0.0058	 |
| 	Bangladesh	 | 	2019	 | 	0.0249	 | 	0.0053	 |
| 	Bangladesh	 | 	2020	 | 	0.0258	 | 	0.0035	 |
| 	Bangladesh	 | 	2021	 | 	0.0258	 | 	0.0035	 |
| 	Bangladesh	 | 	2022	 | 	0.0258	 | 	0.0035	 |

Notes:
* Freight cost is one component of COGS. This table contains data at a fiscal year level on freight cost (as a percentage of net sales) for each specific market.
* The columns `market` and `fiscal_year` make up a **composite primary key**.


**gdb0041.fact_gross_price**
| 	product_code	 | 	fiscal_year	 | 	gross_price	 |
| 	-:	 | 	-:	 | 	-:	 |
| 	1	 | 	2018	 | 	19.363	 |
| 	1	 | 	2019	 | 	19.3442	 |
| 	1	 | 	2020	 | 	22.1317	 |
| 	1	 | 	2021	 | 	21.7795	 |
| 	1	 | 	2022	 | 	23.992	 |
| 	2	 | 	2018	 | 	19.5743	 |
| 	2	 | 	2019	 | 	18.5072	 |
| 	2	 | 	2020	 | 	20.7734	 |
| 	2	 | 	2021	 | 	22.9729	 |
| 	2	 | 	2022	 | 	23.6298	 |

Notes:
* Gross price is the base price of a product. This table contains data on the gross price of each specific product on a fiscal year level. 
* The columns `product_code` and `fiscal_year` make up a **composite primary key**.


**gdb0041.fact_manufacturing_cost**
| 	product_code	 | 	cost_year	 | 	manufacturing_cost	 |
| 	-:	 | 	-:	 | 	-:	 |
| 	1	 | 	2018	 | 	5.9469	 |
| 	1	 | 	2019	 | 	5.5306	 |
| 	1	 | 	2020	 | 	6.3264	 |
| 	1	 | 	2021	 | 	6.59	 |
| 	1	 | 	2022	 | 	7.1831	 |
| 	2	 | 	2018	 | 	5.8958	 |
| 	2	 | 	2019	 | 	5.4242	 |
| 	2	 | 	2020	 | 	6.4789	 |
| 	2	 | 	2021	 | 	6.8199	 |
| 	2	 | 	2022	 | 	7.3655	 |


Notes:
* Manufacturing cost is one component of COGS. This table contains data at a fiscal year level on manufacturing cost ($) for one unit quantity of each specific product.
* The columns `product_code` and `cost_year` make up a **composite primary key**.



**gdb0041.fact_post_invoice_deductions**
| 	customer_code	 | 	product_code	 | 	date	 | 	discounts_pct	 | 	other_deductions_pct	 |
| 	-:	 | 	-:	 | 	-:	 | 	-:	 | 	-:	 |
| 	1	 | 	1	 | 	2021-09-01	 | 	0.243105105	 | 	0.064459945	 |
| 	1	 | 	2	 | 	2021-10-01	 | 	0.318823445	 | 	0.091317288	 |
| 	1	 | 	3	 | 	2021-09-01	 | 	0.277440802	 | 	0.064933693	 |
| 	1	 | 	4	 | 	2021-10-01	 | 	0.318786084	 | 	0.092226504	 |
| 	2	 | 	1	 | 	2021-09-01	 | 	0.309472563	 | 	0.075799178	 |
| 	2	 | 	2	 | 	2021-10-01	 | 	0.262301248	 | 	0.09568491	 |
| 	2	 | 	3	 | 	2021-09-01	 | 	0.227948668	 | 	0.094501586	 |
| 	2	 | 	4	 | 	2021-10-01	 | 	0.228410097	 | 	0.074617767	 |

Notes:
* This table contains data on post invoice deductions (as a percentage of net invoice sales) of a product for a specific customer, on a monthly level.
* The columns `customer_code`, `product_code` and `date` make up a **composite primary key**.


**gdb0041.fact_pre_invoice_deductions**
| 	customer_code	 | 	fiscal_year	 | 	pre_invoice_discount_pct	 |
| 	-:	 | 	-:	 | 	-:	 |
| 	1	 | 	2018	 | 	0.082442198	 |
| 	1	 | 	2019	 | 	0.077658613	 |
| 	1	 | 	2020	 | 	0.073457811	 |
| 	1	 | 	2021	 | 	0.070269476	 |
| 	1	 | 	2022	 | 	0.10567783	 |
| 	2	 | 	2018	 | 	0.295567708	 |
| 	2	 | 	2019	 | 	0.257654803	 |
| 	2	 | 	2020	 | 	0.225480979	 |
| 	2	 | 	2021	 | 	0.206107124	 |
| 	2	 | 	2022	 | 	0.29309271	 |

Notes:
* This table contains data on pre invoice deductions (as a percentage of gross price) for each specific customer, on a fiscal year level.
* The columns `customer_code`, and `fiscal_year` make up a **composite primary key**.
</details>







## Ad Hoc Request 1
