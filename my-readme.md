## Working with Arrays.

i have a list of css colors and i want them to be separated in `li` in `ol`.

```js
function ColorList() {
  const colors = [
    "firebrick",
    "rebeccapurple",
    "salmon",
    "darkslategray",
    "hotpink",
  ];

  return (
    <div>
      <h1>Top 5 CSS Colors</h1>
      <ol>
        <li style={{ color: colors[0] }}>{colors[0]}</li>
        <li style={{ color: colors[1] }}>{colors[1]}</li>
        <li style={{ color: colors[2] }}>{colors[2]}</li>
        <li style={{ color: colors[3] }}>{colors[3]}</li>
        <li style={{ color: colors[4] }}>{colors[4]}</li>
      </ol>
    </div>
  );
}
```

`This is okay but have to create it` **dynamically**

Here i'll be using the **.map() method**

I have an array of 5 strings and i want an array of 5 JSX elements instead.

```js

function ColorList() {
  const colors = [
    "firebrick",
    "rebeccapurple",
    "salmon",
    "darkslategray",
    "hotpink",
  ];

  const colorElements = colors.map((color) => {
    return <li style={{ color: color }}>{color}</li>;
  });
  return (
    <div>
      <h1>Top 5 CSS Colors</h1>
      <ol>
        {/* display the array of <li> elements here! */}
        {colorElements}
      </ol>
    </div>
  );
}
```

## The key Prop

if i runthe above code it will be an error;

Warning: Each child in a list should have a unique "key" prop.
  Check the render method of `ColorList`.

  to fix this

  ```jsx
const colorElements = colors.map((color) => {
  return (
    <li key={color} style={{ color: color }}>
      {color}
    </li>
  );
});
```
This help to keep track of deleted or updated colors.

**Any time you are creating an array of JSX elements, you must use the key prop.**


## With Objects

While dealing with array of objects use obj's  `id` as key

```jsx
const users = [
  { id: 1, firstName: "Duane", lastName: "Watson" },
  { id: 2, firstName: "Duane", lastName: "Johnson" },
];

const userHeadings = users.map((user) => {
  return <h1 key={user.id}>{user.firstName}</h1>;
});
```

## With Nested Components

Here i want to create a separate components to display the colors like the above;

```js
// ColorItem component
function ColorItem(props) {
  return <li style={{ color: props.color }}>{props.color}</li>;
}

// ColorList component
function ColorList() {
  const colors = [
    "firebrick",
    "rebeccapurple",
    "salmon",
    "darkslategray",
    "hotpink",
  ];

  const colorElements = colors.map((color) => {
    return <ColorItem key={color} color={color} />;
  });
  // etc
}
```







































