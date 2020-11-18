## React Fakers

**React Fakers** is a collection of dummy data from the most popular dummy data providers such as **Json Place Holder, Faker, Pokemon, etc**, for application development testing.

[![Build Status](https://travis-ci.com/restuwahyu13/react-fakers.svg?branch=main)](https://travis-ci.com/restuwahyu13/react-fakers)

<img src="./cover.png" alt="logo" width="850" height="750" style="object-fit:cover"/>

## TABLE OF CONTENT

- [Get Started](#get-started)
  - [Installation](#INSTALLATION)
  - [Example Usage](#EXAMPLE-USAGE)
  - [API Reference](#API-REFERENCE)
  - [API Status](#API-STATUS)
  - [API List](#API-LIST)
  - [Translation](#TRANSLATION)
  - [Notes](#NOTES)
  - [Author](#AUTHOR)
  - [Contributors](#CONTRIBUTORS)
  - [Bugs](#BUGS)
  - [License](#LICENSE)

### INSTALLATION:

```sh
npm i react-fakers | yarn add react-fakers
```

### EXAMPLE USAGE

- **Hooks**

  - **useFaker**

  ```js
  import React, { useState, useEffect } from 'react'
  import { useFaker } from 'react-fakers'

  const App = () => {
    const [state, setState] = useState(false)
    const { success, error } = useFaker()

    useEffect(() => {
      if (success) {
        setState(true)
      }
    }, [])

    if (error) {
      window.alert(error.message)
    }

    return (
      <>
        {!state && <h4>Loading....</h4>}
        {state &&
          success.map((val, id) => (
            <ul key={val.uuid}>
              <li>
                {val.firstname} {val.lastname} - {val.email}
              </li>
            </ul>
          ))}
      </>
    )
  }

  export default App
  ```

  - **useJsonPlaceHolder**

  ```js
  import React, { useState, useEffect } from 'react'
  import { useJsonPlaceHolder } from 'react-fakers'

  const App = () => {
    const [state, setState] = useState(false)
    const { success, error } = useJsonPlaceHolder()

    useEffect(() => {
      if (success) {
        setState(true)
      }
    }, [])

    if (error) {
      window.alert(error.message)
    }

    return (
      <>
        {!state && <h4>Loading....</h4>}
        {state &&
          success.map((val, id) => (
            <ul key={id}>
              <li>
                {val.name} - {val.email}
              </li>
            </ul>
          ))}
      </>
    )
  }

  export default App
  ```

- **Components**

  - **Faker**

  ```js
  import React, { Component } from 'react'
  import { Faker } from 'react-fakers'

  class App extends Component {
    constructor(props) {
      super(props)
      this.state = {
        loading: false,
        data: []
      }
    }

    onSuccess = (res) => {
      this.setState({
        loading: true,
        data: res
      })
    }

    onError = (error) => {
      if (error) {
        window.alert(error.message)
      }
    }

    render() {
      return (
        <>
          <Faker success={this.onSuccess} error={this.onError} />
          {!this.state.loading && <h4>Loading....</h4>}
          {this.state.loading &&
            this.state.data.map((val, id) => (
              <ul key={val.uuid}>
                <li>
                  {val.firstname} {val.lastname} - {val.email}
                </li>
              </ul>
            ))}
        </>
      )
    }
  }

  export default App
  ```

  - **JsonPlaceHolder**

  ```js
  import React, { Component } from 'react'
  import { Faker } from 'react-fakers'

  class App extends Component {
    constructor(props) {
      super(props)
      this.state = {
        loading: false,
        data: []
      }
    }

    onSuccess = (res) => {
      this.setState({
        loading: true,
        data: res
      })
    }

    onError = (error) => {
      if (error) {
        window.alert(error.message)
      }
    }

    render() {
      return (
        <>
          <JsonPlaceHolder success={this.onSuccess} error={this.onError} />
          {!this.state.loading && <h4>Loading....</h4>}
          {this.state.loading &&
            this.state.data.map((val, id) => (
              <ul key={id}>
                <li>
                  {val.name} - {val.email}
                </li>
              </ul>
            ))}
        </>
      )
    }
  }

  export default App
  ```

### API REFERENCE

- **HOOKS**

| Name                   | Property | Type Data | Optional/Required | Default Value                       | Description                                          |
| ---------------------- | -------- | --------- | ----------------- | ----------------------------------- | ---------------------------------------------------- |
| **useFaker**           | type     | _string_  | _optional_        | users                               | To display dummy data from the Faker API             |
|                        | params   | _object_  | _optional_        | { }                                 |                                                      |
| **useJsonPlaceHolder** | type     | _string_  | _optional_        | users                               | To display dummy data from the Json Place Holder API |
|                        | params   | _object_  | _optional_        | { }                                 |                                                      |
|                        | options  | _object_  | _optional_        | { limit: 0 }                        |                                                      |
|                        | filters  | _object_  | _optional_        | { }                                 |                                                      |
| **useDummy**           | type     | _object_  | _optional_        | user                                | To display dummy data from the Dummy API             |
|                        | apiKey   | _string_  | _optional_        | 5faa1fab5317ae96860c0be3            |                                                      |
|                        | params   | _object_  | _optional_        | { }                                 |                                                      |
|                        | options  | _object_  | _optional_        | { limit: 0 }                        |                                                      |
|                        | filters  | _object_  | _optional_        | { }                                 |                                                      |
| **useUIFaces**         | apiKey   | _string_  | _optional_        | 43651248-182440F6-8653E4E2-5438FCB2 | To display dummy data from the UI Faces API          |
|                        | params   | _object_  | _optional_        | { limit: 10 }                       |                                                      |

- **COMPONENTS**

| Name                | Property | Type Data  | Optional/Required | Default Value                       | Description                                          |
| ------------------- | -------- | ---------- | ----------------- | ----------------------------------- | ---------------------------------------------------- |
| **Faker**           | success  | _function_ | _required_        |                                     | To display dummy data from the Faker API             |
|                     | error    | _function_ | _optional_        |                                     |                                                      |
|                     | type     | _string_   | _optional_        | users                               |                                                      |
|                     | params   | _object_   | _optional_        |                                     |                                                      |
| **JsonPlaceHolder** | success  | _function_ | _required_        |                                     | To display dummy data from the Json Place Holder API |
|                     | error    | _function_ | _optional_        |                                     |                                                      |
|                     | type     | _string_   | _optional_        | users                               |                                                      |
|                     | options  | _object_   | _optional_        | { limit: 0 }                        |                                                      |
|                     | filters  | _object_   | _optional_        | { }                                 |                                                      |
| **Dummy**           | success  | _function_ | _required_        |                                     | To display dummy data from the Dummy API             |
|                     | error    | _function_ | _optional_        |                                     |                                                      |
|                     | apiKey   | _string_   | _optional_        | 5faa1fab5317ae96860c0be3            |                                                      |
|                     | params   | _object_   | _optional_        | { }                                 |                                                      |
|                     | options  | _object_   | _optional_        | { limit: 0 }                        |                                                      |
|                     | filters  | _object_   | _optional_        | { }                                 |                                                      |
| **UIFaces**         | success  | _function_ | _required_        |                                     | To display dummy data from the UI Faces API          |
|                     | error    | _function_ | _optional_        |                                     |                                                      |
|                     | apiKey   | _string_   | _optional_        | 43651248-182440F6-8653E4E2-5438FCB2 |                                                      |
|                     | params   | _object_   | _optional_        | { limit: 10 }                       |                                                      |

### API STATUS

| API Name          | API Key | Call Per/Day | Call Per/Month |
| ----------------- | ------- | ------------ | -------------- |
| Faker             | No      | Unlimited    | unlimited      |
| Json Place Holder | No      | Unlimited    | unlimited      |
| Dummy API         | Yes     | 500          | undefined      |
| UI Faces          | Yes     | 500          | undefined      |

### API LIST

| API Name          | Status     | Documentation                              |
| ----------------- | ---------- | ------------------------------------------ |
| Faker             | Ready      | [Click Here](https://tinyurl.com/yy8m2xvo) |
| Json Place Holder | Ready      | [Click Here](https://tinyurl.com/y5s3yfkg) |
| Dummy API         | Ready      | [Click Here](https://tinyurl.com/y5a6dew8) |
| UI Faces          | Ready      | [Click Here](https://tinyurl.com/y4cv59qy) |
| Pokemon           | Comingsoon | [Click Here]()                             |
| Star Wars         | Comingsoon | [Click Here]()                             |
| Marvel            | Comingsoon | [Click Here]()                             |
| Harry Potter      | Comingsoon | [Click Here]()                             |
| IMDB              | Comingsoon | [Click Here]()                             |
| The Cat           | Comingsoon | [Click Here]()                             |
| Anime             | Comingsoon | [Click Here]()                             |
| Ricky And Morty   | Comingsoon | [Click Here]()                             |
| Unsplash          | Comingsoon | [Click Here]()                             |
| Listen Notes      | Comingsoon | [Click Here]()                             |

### TRANSLATION

- [Indonesian](https://github.com/restuwahyu13/react-fakers/blob/main/README_ID.md)
- [English](https://github.com/restuwahyu13/react-fakers/blob/main/README.md)

### NOTES

- For `Dummy Data` that uses `API KEY` if you have a limit, please visit the `API` provider service, to get your own `API KEY`
- For more information on the `API` available, you can visit the official documentation of each `Provider`
- To make a contribution to the project you can throw an `issue` or you can clone the repository and perform a `Pull Request`
- To find out more about using this tool, you can open the `app-dev/src/examples` in this repository

### AUTHOR

- [Restu Wahyu Saputra](https://github.com/restuwahyu13)

### BUGS

For information on bugs related to package libraries, please visit [here](https://github.com/restuwahyu13/react-fakers/issues)

### LICENSE

- [MIT](https://github.com/restuwahyu13/react-fakers/blob/main/LICENSE.md)

<p align="right" style="padding: 5px; border-radius: 100%; background-color: red; font-size: 2rem;">
  <b><a href="#React-Fakers">BACK TO TOP</a></b>
</p>
