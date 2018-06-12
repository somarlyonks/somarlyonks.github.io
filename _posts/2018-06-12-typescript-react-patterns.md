---
layout: post
title: React component patterns with Typescript
---

```Typescriptreact
import * as React from 'react'
```

## SFC

```Typescriptreact
// button.tsx
export interface IButtonProps {
  onClick (e: React.MouseEvent<HTMLButtonElement>): void
  children?: React.ReactNode
}

export default function Button ({onClick: handleClick, children}: IButtonProps) {
  return (
    <button onClick={handleClick}>
      {children}
    </button>
    )
}
```

Or with SFC helper.

```tsx
const Button: React.SFC<IButtonProps> = ({onClick: handleClick, children}) => (
  <button onClick={handleClick}>
    {children}
  </button>
)

export default Button
```

## Stateful Component

```tsx
const initialState = {
  clicksCount: 0
}
type State = Readonly<typeof initialState>

export default class ButtonCounter extends React.Component<object, State> {
  readonly state: State = initialState
  render () {
    const { clicksCount } = this.state
    return (
      <>
        <Button onClick={this.handleIncrement}>Increment</Button>
        <Button onClick={this.handleDecrement}>Decrement</Button>
        <span>Clicked {clicksCount} times.</span>
      </>
    )
  }

  private handleIncrement = () => this.setState(incrementClicksCount)
  private handleDecrement = () => this.setState(decrementClicksCount)
}
const incrementClicksCount = (prevState: State) => ({ clicksCount: prevState.clicksCount + 1 })
const decrementClicksCount = (prevState: State) => ({ clicksCount: prevState.clicksCount - 1 })
```

## defaultProps

### class

```tsx
interface IProps {
  className: string
  color: string
}

const defaultProps = {
  className: '',
  children: null,
}

type CardDefaultProps = Readonly<typeof defaultProps>

export default class Card extends React.Component<ICardProp, object> {
  readonly defaultProps: CardDefaultProps = defaultProps
  render () {
    const { className, children, ...otherProps } = this.props
    return (
      <div className={className} {...otherProps}>
        {children}
      </div>
    )
  }
}
```

### SFC

```tsx
// withDefaultProps.ts
export default <P extends object, DP extends Partial<P> = Partial<P>> (
  defaultProps: DP,
  Cmp: React.ComponentType<P>
) => {
  // type RequiredProps = Omit<P, keyof DP>
  type RequiredProps = Pick<P, Exclude<keyof P, keyof DP>>
  type Props = Partial<DP> & Required<RequiredProps>
  Cmp.defaultProps = defaultProps

  return (Cmp as React.ComponentType<any>) as React.ComponentType<Props>
}
```

```tsx
// button.tsx
const defaultProps = {
  color: 'red'
}
type DefaultProps = typeof defaultProps
type ButtonProps = {
  onClick (e: React.MouseEvent<HTMLElement>): void
} & DefaultProps

const Button: React.SFC<ButtonProps> = ({onClick: handleClick, color, children}) => (
  <button style={{color}} onClick={handleClick}>
    {children}
  </button>
)

export default withDefaultProps(defaultProps, Button)
```
