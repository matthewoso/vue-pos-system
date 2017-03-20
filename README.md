# Vue POS system

## Introduction

Your task for this homework is to build a "point of sale" system for a small restaurant. Included in the /src/assets folder is an inventory file and images for each of the different foods that the restaurant sells.

Your POS system will be simple, but contain important functionality that would actually be usable at a small restaurant. This application would be, for example, used by a cashier to take orders from customers.

## Functionality

Your app should have the following functionality:

  * Allow the cashier to click on items to add them to an order.
  * Display a list of the items in the current order and display the running total of that order.
  * Remove items from an order if the customer decides they no longer want them & update the running total.
  * Display a subtotal, tax amount (8.5% sales tax), and total (subtotal + tax)
  * Press a button to clear the order and start a new order for the next customer. (No need to print a completed order, handle money, etc.)

## Example

The user should be able to tap a button multiple times to add several items to an order. For example:

```
  User orders 2 sandwiches and 1 soda. These are added to the order. A subtotal (6.50 * 2 + 0.99) = 13.99 is displayed. Tax is (13.99 * 0.085) = 1.18. Total displayed is (13.99 + 1.18) = 15.17.
 ```

 If the user decides they want to cancel one of the sandwiches, it should be trivial for the user to remove one sandwich from the order, and the subtotal, etc. will be updated.

## Hints

Look at our finance app, which will be very similar to this app.

Work on one piece of functionality at a time.

Ask questions as soon as you get stuck, especially if it's probably a syntax error.
