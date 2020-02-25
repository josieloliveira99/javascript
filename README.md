# Bibliotecas

## History

[History](https://github.com/ReactTraining/history/blob/master/docs/Navigation.md)

## Slug

[slug](https://www.npmjs.com/package/slug)

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

# React snippets

## Router 404

```javascript
{/*dentro do <Switch> apenas a primeira rota com match é renderizada*/}
render() {
  <Router>
    <div>
      <ul>
        <li><Link to="/">Home</Link></li>
        <li><Link to="/will-match">Will Match</Link></li>
        <li><Link to="/old-match">Will Match</Link></li>
        <li><Link to="/will-not-match">Will Not Match</Link></li>
        <li><Link to="/also/will/not/match">Also Will Not Match</Link></li>
      </ul>

      <Switch>
        <Route path="/" exact component={Home}/>
        {/* se entrar na url old-match será redirecionado para will-match. É preciso estar dentro do <Switch> prá que isso ocorra */}  
        <Redirect from="/old-match" to="/will-match"/>
        <Route path="/will-match" component={WillMatch}/>
        <Route component={NoMatch} />
      </Switch>
    </div>
  </Router>
}

```

## Passando dados de forma dinâmica através das rotas

```javascript

<Route path='/:handle' component={Profile} />

...

<Link to={{
  pathname: '/tylermcginnis',
  state: {
    fromNotifications: true
  }
}}>Tyler McGinnis</Link>

...

class Profile extends React.Component {
  state = {
    user: null
  }
  componentDidMount () {
    const { handle } = this.props.match.params
    const { fromNotifications } = this.props.location.state

    fetch(`https://api.twitter.com/user/${handle}`)
      .then((user) => {
        this.setState(() => ({ user }))
      })
  }
  render() {
    ...
  }
}

```

## Async requests com hooks

```javascript

// inside render
const [pets, setPets] = useState([]);

// below state declarations
async function requestPets() {
  const { animals } = await pet.animals({
    location,
    breed,
    type: animal
  });

  setPets(animals || []);
}

// replace <form>
<form
  onSubmit={e => {
    e.preventDefault();
    requestPets();
  }}
>

```
