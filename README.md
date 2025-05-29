**Q1) List All Products in the "Electronics" Category**
```js
db.products.aggregate([{$match:{category:"Electronics"}}])
{
  _id: ObjectId('68386b1e86a2507f9bc398e1'),
  name: 'Laptop Pro',
  category: 'Electronics',
  price: 1200,
  quantity: 10,
  tags: [
    'computer',
    'portable',
    'work'
  ],
  date_added: 2023-01-15T10:00:00.000Z,
  supplier: {
    name: 'TechGlobe',
    location: 'USA'
  }
}
{
  _id: ObjectId('68386b1e86a2507f9bc398e2'),
  name: 'Wireless Mouse',
  category: 'Electronics',
  price: 25,
  quantity: 100,
  tags: [
    'peripheral',
    'computer',
    'wireless'
  ],
  date_added: 2023-02-01T11:30:00.000Z,
  supplier: {
    name: 'GadgetPro',
    location: 'China'
  }
}
{
  _id: ObjectId('68386b1e86a2507f9bc398e3'),
  name: 'Mechanical Keyboard',
  category: 'Electronics',
  price: 75,
  quantity: 50,
  tags: [
    'peripheral',
    'computer',
    'mechanical'
  ],
  date_added: 2023-01-20T14:00:00.000Z,
  supplier: {
    name: 'TechGlobe',
    location: 'USA'
  }
}
{
  _id: ObjectId('68386b1e86a2507f9bc398e7'),
  name: 'Smartwatch',
  category: 'Electronics',
  price: 199,
  quantity: 25,
  tags: [
    'wearable',
    'gadget',
    'portable'
  ],
  date_added: 2023-04-01T12:00:00.000Z,
  supplier: {
    name: 'GadgetPro',
    location: 'China'
  }
}
{
  _id: ObjectId('68386b1e86a2507f9bc398ea'),
  name: 'Bluetooth Speaker',
  category: 'Electronics',
  price: 80,
  quantity: 60,
  tags: [
    'audio',
    'portable',
    'wireless'
  ],
  date_added: 2023-02-25T17:00:00.000Z,
  supplier: {
    name: 'SoundWave',
    location: 'USA'
  }
}
```
**Q2)Count Products per Category:**
```js
db.products.aggregate([
  {
    $group: {
      _id: "$category",       
      count: { $sum: 1 }      
    }
  }
]);
{
  _id: 'Apparel',
  count: 2
}
{
  _id: 'Accessories',
  count: 1
}
{
  _id: 'Home Goods',
  count: 1
}
{
  _id: 'Electronics',
  count: 5
}
{
  _id: 'Sports',
  count: 1
}
  
```
![Screenshot (19)](https://github.com/user-attachments/assets/c5e940f3-e068-41e2-a2ab-3f42b115a603)

 **Q3)Product Names and Prices, Sorted by Price (Descending):**
 ```js
db.products.aggregate([
{
    $sort: {
      price: -1         
    }
},
{
    $project: {
      _id: 0,           
      name: 1,          
      price: 1          
    }
}
])
{
  name: 'Laptop Pro',
  price: 1200
}
{
  name: 'Espresso Machine',
  price: 250
}
{
  name: 'Smartwatch',
  price: 199
}
{
  name: 'Bluetooth Speaker',
  price: 80
}
{
  name: 'Mechanical Keyboard',
  price: 75
}
{
  name: 'Denim Jeans',
  price: 60
}
{
  name: 'Leather Wallet',
  price: 45
}
{
  name: 'Yoga Mat',
  price: 30
}
{
  name: 'Wireless Mouse',
  price: 25
}
{
  name: 'Cotton T-Shirt',
  price: 20
}
```
 
 
