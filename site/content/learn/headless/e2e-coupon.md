---
title: E2E Coupon
subTitle: Applying and verifying a discount
date: 2020-07-13
author: Giovanni Rago
githubUser: ragog
tags:
  - e2e
  - assertions
weight: 11
menu:
  learn:
    parent: "E2E examples"
---

Webshops and subscription-based services often offer discounts through coupon codes. Applying a valid coupon code during checkout might reduce the price of one, several, or all items in the shopping cart.

<!-- more -->

## Steps

While discount coupons will be applied in different ways depending on the service or shop they are relevant to, in most cases:
1. Having selected one or more products will be a prerequisite for applying the coupon
2. Entering a valid coupon will result in visible feedback, i.e. a reduction of the previous product/cart price

The following example, running against our [test site](https://danube-webshop.herokuapp.com/), will add a variable number of items to the cart, then proceed to compare the total price before and after applying the coupon. The coupon is reducing the price of the whole shopping cart by 20%, therefore we will be asserting that the discounted price is reduced by the right amount. For this step we have chosen [Chai](https://www.chaijs.com/api/assert/), but any solid assertion library will do.

{{< tabs "1" >}}
{{< tab "Playwright" >}}
```js
{{< readfile filename="samples/playwright/coupon.js" >}}
```
{{< run-in-checkly "/samples/playwright/coupon.js" "playwright"  >}}
{{< /tab >}}
{{< tab "Puppeteer" >}}
```js
{{< readfile filename="samples/puppeteer/coupon.js" >}}
```
{{< run-in-checkly "/samples/puppeteer/coupon.js" "puppeteer"  >}}
{{< /tab >}}
{{< /tabs >}}

Run this example as follows:

{{< tabs "2" >}}
{{< tab "macOS" >}}
```sh
PRODUCTS_NUMBER=3 node coupon.js
```
{{< /tab >}}
{{< tab "Windows" >}}
```sh
SET PRODUCTS_NUMBER=3
node coupon.js
```
{{< /tab >}}
{{< /tabs >}}

## Takeaways

1. We can simply verify that coupons are accepted, or also check that they command the right discount.
2. Assertion libraries are useful when non-trivial assertions are required.

