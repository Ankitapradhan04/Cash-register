# Cash Register 

---

## Overview

The **Cash Register** function, `checkCashRegister()`, simulates the operation of a cash register drawer. It accepts three arguments: the purchase price (`price`), the payment amount (`cash`), and the cash-in-drawer (`cid`). The function processes these inputs to determine the status of the cash register and the change to be returned to the customer.

## Function Signature

```javascript
function checkCashRegister(price, cash, cid) {
  // Function implementation
}
```

## Arguments

- **price**: (Number) The purchase price of the item(s).
- **cash**: (Number) The payment amount provided by the customer.
- **cid**: (Array) A 2D array representing the cash-in-drawer. Each sub-array contains:
  - The denomination name (String)
  - The total amount of that denomination available (Number)

## Cash-in-Drawer Format

The `cid` array should be structured as follows:

```javascript
[
  ["PENNY", 1.01],
  ["NICKEL", 2.05],
  ["DIME", 3.10],
  ["QUARTER", 4.25],
  ["ONE", 90.00],
  ["FIVE", 55.00],
  ["TEN", 20.00],
  ["TWENTY", 60.00],
  ["ONE HUNDRED", 100.00]
]
```

## Return Object

The `checkCashRegister()` function returns an object with the following keys:

- **status**: (String) The status of the cash register, which can be one of the following:
  - `"INSUFFICIENT_FUNDS"`: When the cash-in-drawer is less than the change due or if exact change cannot be returned.
  - `"CLOSED"`: When the cash-in-drawer is equal to the change due, and the drawer should be closed.
  - `"OPEN"`: When there is enough cash-in-drawer to return the change, and the drawer remains open.

- **change**: (Array) An array of arrays, where each sub-array contains:
  - The denomination name (String)
  - The amount of that denomination to be returned as change (Number)

## Example Returns

- **Insufficient Funds**

  ```javascript
  {
    status: "INSUFFICIENT_FUNDS",
    change: []
  }
  ```

- **Closed**

  ```javascript
  {
    status: "CLOSED",
    change: [
      ["PENNY", 1.01],
      ["NICKEL", 2.05],
      ["DIME", 3.10],
      ["QUARTER", 4.25],
      ["ONE", 90.00],
      ["FIVE", 55.00],
      ["TEN", 20.00],
      ["TWENTY", 60.00],
      ["ONE HUNDRED", 100.00]
    ]
  }
  ```

- **Open**

  ```javascript
  {
    status: "OPEN",
    change: [
      ["TWENTY", 60.00],
      ["TEN", 20.00],
      ["QUARTER", 4.25]
    ]
  }
  ```

## Example Usage

```javascript
const price = 19.50;
const cash = 20.00;
const cid = [
  ["PENNY", 1.01],
  ["NICKEL", 2.05],
  ["DIME", 3.10],
  ["QUARTER", 4.25],
  ["ONE", 90.00],
  ["FIVE", 55.00],
  ["TEN", 20.00],
  ["TWENTY", 60.00],
  ["ONE HUNDRED", 100.00]
];

console.log(checkCashRegister(price, cash, cid));
```

This example would output:

```javascript
{
  status: "OPEN",
  change: [
    ["QUARTER", 0.50]
  ]
}
```

## Important Notes

- The change should be returned in the highest denomination first, sorted from highest to lowest.
- Ensure proper handling of floating-point arithmetic to avoid precision errors.
- The function should efficiently handle cases where exact change cannot be returned due to insufficient denominations, even if the total cash-in-drawer exceeds the change due.

## Screenshot

![Screenshot](https://github.com/Ankitapradhan04/Cash-register/assets/67707036/c71ee5bb-0952-48f9-bd33-7e05ca5694c9)

---

This README provides a comprehensive guide to implementing and understanding the `checkCashRegister()` function. Ensure all edge cases are tested thoroughly to guarantee the function's robustness and reliability.
