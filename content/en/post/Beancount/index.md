---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Beancount"
subtitle: ""
summary: "Beancount is a double-entry bookkeeping computer language."
authors: []
tags: ['Beancount']
categories: ['finance']
date: 2019-07-31T10:18:09-04:00
lastmod: 2019-07-31T10:18:09-04:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

## Introduction
Beancount is a double-entry bookkeeping computer language that lets you define financial transaction records in a text file, read them in memory, generate a variety of reports from them, and provides a web interface. You can visit the documentation via this link.

## Running the tests

```bash
nosetests -s -v --all-modules ./importers/
```

## Import documents into Beancount

#### Step 1:

Download statement documents from Bank of America, Chase and Discover website. Rename BoA checking and savings statements as the form stmt_checking or stmt_savings

#### Step 2:

Move these documents in to downloads folder under Beancount folder. Then rename some documents:

```bash
ofx.csv -> ofx_YYYYMMDD_Amex_Rose_Gold.csv  # Amex Rose Gold credit card rename rule
activity.csv -> activity_YYYYMMDD_Amex_Rose_Gold.csv # Amex Rose Gold credit card rename rule
```

#### Step 3:

Identify these documents category and make sure everything is ok.

```bash
bean-identify finance.import ./downloads/
```

#### Step 4:

Back up the original beancount file

``` bash
cp finance.main.beancount finance.main.beancount.backup
```

Extract data from these documents.

Dry run this command first to make sure no bug occurs in running.

``` bash
bean-extract finance.import ./downloads/
```

Export them to the tail of the beancount file if everything goes ok.

```bash
bean-extract finance.import ./downloads/ >> finance.main.beancount
```

Add balance assertions (find balance statement from bank website) , usually you need to add 4 assertions at the end like below codes.

``` bash
2018-03-29 balance Liabilities:US:CreditCard:Discover:Discover           214.04  USD       ; Feb 26, 2018 to March 29, 2018
2018-03-24 balance Liabilities:US:CreditCard:Chase:Freedom               0.00    USD
2018-03-23 balance Liabilities:US:CreditCard:BofA:CashRewards           -52.92   USD
2018-03-23 balance Liabilities:US:CreditCard:BofA:TravelRewards         -9.95    USD
2018-11-08 balance Liabilities:US:CreditCard:AmericanExpress:AmexGold   -285.01  USD
2018-04-23 balance Assets:US:Stock:Robinhood:Cash                        0.00    USD
```

#### Step 5:

Add stock price in finance.stock.price.beancount

```bash
bean-price finance.main.beancount
```

If no error occurs, then:

``` bash
bean-price finance.main.beancount >> finance.stock.price.beancount
```

Check the beancount file whether changed as expected.

``` bash
bean-check finance.main.beancount
```

If everything goes fine, remove backup beancount file.

``` bash
rm finance.main.beancount.backup
```

#### Step 6:
Move these documents files into documents folder.

Dry run the command below and check if the destinations are as expected.

```bash
bean-file finance.import ./downloads/ --dry-run -o ./documents/
```

Then move them into the folder.

```bash
bean-file finance.import ./downloads/ -o ./documents/
```

#### Step 7:
Push these changes via VScode and PowerShell.

```bash
git push
```

Done! Enjoy

Visualization
fava finance.beancount