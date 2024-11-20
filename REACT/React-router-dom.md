# React router dom
_________________________________________________________________


### sourses
- https://www.npmjs.com/package/react-router-dom
- https://reactrouter.com/en/main/start/tutorial#adding-a-router

## Step 1
- install react dom : `npm i react-router-dom`
- add this line to your `App.jsx`
```
import {createBrowserRouter, RouterProvider} from "react-router-dom";
```
```
function App() {
  const router = createBrowserRouter([
    {
      path: "/",
      element: <><Navbar /><Home /></>
    },
    {
      path: "/login",
      element: <><Navbar /><Login /></>
    },
  ])

  return (
    <>
      <RouterProvider router={router} />
    </>
  )
}
```

## Step 2
- import `Link` 
```
import { Link } from 'react-router-dom'
```
- replace this code
```
<a href="#">Pricing</a>
```
- to this
```
<Link to="#">Pricing</Link>
```


_________________________________________________________________

# You can also use this :
```
import {
  BrowserRouter as Router,
  Routes,
  Route,
} from "react-router-dom";
```
```
return (
    <>
      <Router>
        <div>
          <Routes>
            <Route exact path='/' element={<Home/>}/>
          </Routes>
        </div>
      </Router>
    </>
  )
}

export default App
```