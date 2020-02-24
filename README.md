# Bibliotecas

## History

[History](https://github.com/ReactTraining/history/blob/master/docs/Navigation.md)

## Query Strings

[URLSearchParams](https://developer.mozilla.org/pt-BR/docs/Web/API/URLSearchParams)

[query-string](https://www.npmjs.com/package/query-string)

```Javascript
// https://analytics.twitter.com/user/tylermcginnis/tweets?filter=top&origin=im

import queryString from 'query-string'

...

componentDidMount() {
  const values = queryString.parse(this.props.location.search)
  console.log(values.filter) // "top"
  console.log(values.origin) // "im"
}

```
