#Item Stock

##Problem Statement
Items in Shopee can have their stocks derived from other items. For example, 1 stock of item A can be derived from 2 stock of item B
and 3 stock of item C. We can say item B and item C are parents of item A.

For this problem, we are only interested when an item can only have 1 parent item.
In this case, we can see the structure of stock derivation will form a rooted tree.

There are 2 kinds of derivation:

1. Dynamic stock derivation
- Suppose that `1` stock of item A equals to `Qty` stock of item B. Then, the stock of item
 A will be equal to floor(item_B_stock / Qty ).
 
2. Fixed stock derivation
- Suppose that `1` stock of item A equals to Qty stock of item B, and we initially have `S` stock of item A. Then, 
item A will deduct stock from its lowest ancestor which is fixed stock, to make sure that item A
will have sufficient stock. It can be assumed that the root of the tree (1st item) will always be
fixed stock. Note that the number of reserved stocks depends on the the multiplication of the `Qty` from the 
path of item A to that ancestor, not just the `Qty` to item B.

At first, we only have item 1, which initially has `M` stock. Then, we add `N-1` items one by one, possbily 
changing the stock of some items at each step. In the end, what will be the stock 
of each item?

## Input

The first line contains 2 integers `N` and `M`, denoting the number of items and the
initial stock of the 1st item.

The next line `N-1` lines contains the description of the `i-th` (starting from 2), which can
be one of the two following formats:

- P<sub>i</sub>Qty<sub>i</sub> ( 1 <= P<sub>i</sub> < i, 1 <= Qty<sub>i</sub> < 10 ), which means that the i-th item
has dynamic stock with parent item P<sub>i</sub> and 1 stock of it equals to Qty<sub>i</sub> stock of its parent.

-  P<sub>i</sub>Qty<sub>i</sub>S<sub>i</sub> ( 1 <= P<sub>i</sub> < i, 1 <= Qty<sub>i</sub> < 10, 1 <= S<sub>i</sub> <= 1,000,000,000  ), which means
that the i-th item has fixed stock with  parent item P<sub>i</sub>, 1 stock of it equals to Qty<sub>i</sub> stock of its parent,
 and has inital stock of S<sub>i</sub>.
 
 It is guaranteed that at the end, the stock for each item will be non-negative.