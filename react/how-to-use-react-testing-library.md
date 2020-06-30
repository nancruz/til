# How to use React Testing Library

* [Search elements](#search-elements)
    * [getBy vs queryBy vs findBy](#getBy-queryBy-findBy)
        * getBy
        * queryBy
        * findBy
        * Auxiliary table
    * [Priorities]((#search-priorities))
* [User events](#user-events)
* [Async calls](#async-calls)
* [Debugging](#debugging)
* [Useful links](#useful-links)

## [Search elements](#search-elements)

Search function are available in the `screen` object.

```js
import { render, screen } from '@testing-library/react';
```

### [_getBy_ vs _queryBy_ vs _findBy_](#getBy-queryBy-findBy)

#### *getBy*
* Throws if element is not found;
* Shouldn't be used to assert missing elements;

#### *queryBy*
* Returns `null` if the element is not found;
* Should be used to assert missing elements;

#### *findBy*
* Same behaviour as *getBy* with the difference that it is async;
* Should be used to assert elements that will eventually appear in the DOM;

#### Auxiliary table
| | No Match | 1 Match | 1+ Match | Await? |
|-|----------|---------|----------|--------|
| getBy | throw | return | throw | No |
| findBy | throw | return | throw | Yes |
| queryBy | null | return | throw | No |
| getAllBy | throw | array | array | No |
| findAllBy | throw | array | array | Yes |
| queryAllBy | [] | array | array | No |

### [Priorities](#search-priorities)
1. `getByRole`
2. `getByLabelText`
3. `getByPlaceholderText`
4. `getByText`
5. `getByDisplayValue`
6. `getByAltText`
7. `getByTitle`
8. `getByTestId`

## [User events](#user-events)

User event functions are available in `userEvent` object.

```js
import userEvent from '@testing-library/user-event';
```

The `userEvent` API is an extension of the `fireEvent` API. It is recommended to use the `userEvent` API instead because it mimics the actual browser behaviour more closely that the `fireEvent` API.

The `fireEvent` API is available in:

```js
import { render, screen, fireEvent } from '@testing-library/react';
```

## [Async calls](#async-calls)

The example below shows how to explicitly wait for async data. It can be an alternative to the *findBy* function.

```jsx
import React from 'react';
import axios from 'axios';
import { render, screen, act } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
 
import App from './App';
 
jest.mock('axios');
 
describe('App', () => {
  test('fetches stories from an API and displays them', async () => {
    const stories = [
      { objectID: '1', title: 'Hello' },
      { objectID: '2', title: 'React' },
    ];
 
    const promise = Promise.resolve({ data: { hits: stories } });
 
    axios.get.mockImplementationOnce(() => promise);
 
    render(<App />);
 
    await userEvent.click(screen.getByRole('button'));
 
    // This is where we wait for the promise to resolve.
    await act(() => promise); 
 
    expect(screen.getAllByRole('listitem')).toHaveLength(2);
  });
});
```

## [Debugging](#debuggin)
The `screen.debug()` function can be used oo output the DOM tree in the console.

```jsx
import React from 'react';
import { render, screen } from '@testing-library/react';
 
import App from './App';
 
describe('App', () => {
  test('renders App component', () => {
    render(<App />);
 
    screen.debug();
  });
});
```

## [Useful links](#useful-links)
- [How to use React Testing Library](https://www.robinwieruch.de/react-testing-library)
- [Common mistakes with React Testing Library](https://kentcdodds.com/blog/common-mistakes-with-react-testing-library)
- [React Testing Library - Cheatsheet](https://testing-library.com/docs/react-testing-library/cheatsheet)
- [React Testing Library - API](https://testing-library.com/docs/react-testing-library/api)
