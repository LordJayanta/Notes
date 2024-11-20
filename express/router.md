# router : How to create router 

1. create a `Router` folder in backend
2. create a file `Router` folder. In my case, I will create create `User.js` for sign up, login and other user related apies.
and pest this code on the file:

```
const express = require('express');
const router = express.Router();
router.post('/login', (req, res) => {
    try {
        res.json({
            success: true
        })
    } catch (error) {
        console.log(error);
        res.json({
            success: false
        })
    }
})
module.exports = router;
```

3. import and use it on `index.js`
```
app.use('/api', require('./Routes/User'))  // api/login
```