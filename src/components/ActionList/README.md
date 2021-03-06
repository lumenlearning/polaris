---
name: Action list
category: Actions
keywords:
  - ActionList
  - dropdown
  - drop down
  - popover
  - pop over
  - menu
  - drop-down
  - select
  - options
---

# Action list

Action lists render a list of actions or selectable options. This component is usually placed inside a [popover container](/components/overlays/popover) to create a dropdown menu or to let merchants select from a list of options.

---

## Purpose

Put the merchant first by identifying the problem they face and the component that helps them solve it.

### Problem

There are lots of different paths a merchant can take. Listing them all out in the interface would make the experience feel overwhelming and cluttered.

### Solution

Action lists in popovers let merchants expose additional information and actions when they’re ready to explore them.

---

## Best practices

Actions lists should:

* Be used for secondary or less important information and actions since they’re hidden until the merchant exposes them by opening a popover
* Contain actions that are related to each other

---

## Content guidelines

### Action lists

Each item in an action list should be clear and predictable. Merchants should be able to anticipate what will happen when they click on an action item.

<!-- usagelist -->

#### Do
Buy shipping label

#### Don’t
Buy

<!-- end -->

Each item in an action list should always lead with a strong verb that encourages action. To provide enough context use the {verb}+{noun} format unless the action is clear with a single verb.

<!-- usagelist -->

#### Do
- Rename
- Edit HTML

#### Don’t
- File name changes
- HTML editing options

<!-- end -->

Each item in an action list should be scannable avoiding unnecessary words and articles such as the, an, or a.

<!-- usagelist -->

#### Do
- Add menu item

#### Don’t
- Add a menu item

<!-- end -->

## Examples

### Action list in a popover

Use for the least important actions so the merchant isn’t distracted by secondary tasks. Can also be used for a set of actions that won’t fit in the available screen space.

```jsx
class ActionListExample extends React.Component {
  state = {
    active: false,
  };

  togglePopover = () => {
    this.setState(({active}) => {
      return {active: !active};
    });
  }

  render() {
    const activator = (
      <Button onClick={this.togglePopover}>More actions</Button>
    );

    return (
      <div style={{height: '250px'}}>
        <Popover
          active={this.state.active}
          activator={activator}
          onClose={this.togglePopover}
        >
          <ActionList
            items={[
              {content: 'Import file', onAction: () => {
                console.log('File imported')
              }},
              {content: 'Export file', onAction: () => {
                console.log('File exported')
              }},
            ]}
          />
        </Popover>
      </div>
    );
  }
}
```

### Action list with icons or image

Use when the items benefit from an associated action or image (e.g. a list of products).

```jsx
class ActionListExample extends React.Component {
  state = {
    active: false,
  };

  togglePopover = () => {
    this.setState(({active}) => {
      return {active: !active};
    });
  }

  render() {
    const activator = (
      <Button onClick={this.togglePopover}>More actions</Button>
    );

    return (
      <div style={{height: '200px'}}>
        <Popover
          active={this.state.active}
          activator={activator}
          onClose={this.togglePopover}
        >
          <ActionList
            items={[
              {content: 'Import file', icon: 'import'},
              {content: 'Export file', icon: 'export'},
            ]}
          />
        </Popover>
      </div>
    );
  }
}
```

### Sectioned action list

Use when the items benefit from sections to help differentiate actions.

```jsx
class ActionListExample extends React.Component {
  state = {
    active: false,
  };

  togglePopover = () => {
    this.setState(({active}) => {
      return {active: !active};
    });
  }

  render() {
    const activator = (
      <Button onClick={this.togglePopover}>More actions</Button>
    );

    return (
      <div style={{height: '250px'}}>
        <Popover
          active={this.state.active}
          activator={activator}
          onClose={this.togglePopover}
        >
          <ActionList
            sections={[{
              title: "File options",
              items: [
                {content: 'Import file', icon: 'import'},
                {content: 'Export file', icon: 'export'},
              ]
            }]}
          />
        </Popover>
      </div>
    );
  }
}
```
---

## Related components

* To combine more than one button in a single layout, [use the button group component](/components/actions/button-group)
* To display a list of related content, [use the list component](/components/lists/list)
