# `.type() => String | Function | null`

Returns the type of the only node of this wrapper.
If it's a React component, this will be the component constructor.
If it's a native DOM node, it will be a string with the tag name.
If it's `null`, it will be `null`. It must be a single-node wrapper.


#### Returns

`String | Function | null`: The type of the node


#### Examples

```jsx
function Foo() {
  return <div />;
}
const wrapper = mount(<Foo />).childAt(0);
expect(wrapper.type()).to.equal('div');
```

```jsx
function Foo() {
  return (
    <div>
      <button type="button" className="btn">Button</button>
    </div>
  );
}
const wrapper = mount(<Foo />);
expect(wrapper.find('.btn').type()).to.equal('button');
```

```jsx
function Foo() {
  return <Bar />;
}
const wrapper = mount(<Foo />);
expect(wrapper.type()).to.equal(Foo);
expect(wrapper.childAt(0).type()).to.equal(Bar);
```

```jsx
function Null() {
  return null;
}
const wrapper = mount(<Null />);
expect(wrapper.type()).to.equal(null);
```
