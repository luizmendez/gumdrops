The `<Select>` component is used to allow the user to choose a value from a set of options. It is recommended that you wrap it with the `<FormGroup>` component.

**NOTE**: This component can be controlled or uncontrolled. This component accepts any prop that you may want to add. The only drawback is that there is not validation for unlisted props. **It is highly recommended that you use controlled components in React.**

*Recommended Props*: `name`, `value`, `defaultValue`, `onChange`

**OPTIONS NOTE**: The default format for your options is `{ name: 'my name', value: 'my value' }`. If your options are in a different format, you may pass in `customValue` and/or `customName` props to override the default values of "name" and "value". For example, if your data looks like `{ id: 'my id', value: 'my value' }`, you can pass in `customName="id"`.

**Uncontrolled example**:
```
_handleSubmit = ({ target }) => console.log(target.fruit.value);

render() {
    return (
        <form onSubmit={ this._handleSubmit }>
            <FormGroup>
                <FormGroupLabel text="Fruits" />
                <Select
                   options={ myOptions }
                   name="fruit"
                   defaultValue="3"
                />
            </FormGroup>
        </form>
    );
}
```

**Controlled example**:
```
// Your state holds the name of each of your parent component's selects (if you have multiple selects on a page)
// You should give your state the default value you want it to have (the first value if it doesn't matter)
    state {
        fruit: 1,
        vegetable: 1
    }

    _handleSelectChange = (e) => {
        e.preventDefault();
        const { name, value } = e.target;
        this.setState({ [name]: value });
    };
    render() {
        return (
            <FormGroup>
                <FormGroupLabel text="Fruits" />
                <Select
                   options={ myOptions }
                   name="fruit"
                   value={ this.state.fruit }
                   onChange={ this._handleSelectChange }
                />
            </FormGroup>
        )
    }
    
const myOptions = [
    { name: 'bananas', value: 1 },
    { name: 'apples', value: 2 }
];
```
