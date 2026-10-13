# Storefront

A shopping cart that keeps its money in whole pence, so a price is never a
float and an order is never a penny out.

```js
import { Cart, formatPounds } from './src/cart.js';

const cart = new Cart().add('mug', 799, 2).add('print', 1005).applyDiscount(10);

cart.itemCount;              // 3
cart.subtotalPence;          // 2603
formatPounds(cart.totalPence); // "£23.43"
```

| Method | What it does |
| --- | --- |
| `add(sku, pricePence, quantity = 1)` | Adds an item. Adding it again sums the quantity. The same item at a different price is refused. |
| `remove(sku)` | Removes the whole line. |
| `applyDiscount(percent)` | A whole percentage from 0 to 100. A second call replaces the first. |
| `itemCount`, `subtotalPence`, `totalPence` | What is in the cart and what it costs. The discount rounds to the nearest penny, halves up. |
