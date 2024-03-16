Here are some free APIs that you can use for testing:

1. **Public APIs**: Get a list of any or all public APIs currently cataloged in the project.
2. **Cat Facts**: Get random cat facts via text message every day.
3. **CoinDesk**: View the Bitcoin Price Index (BPI) in real-time.
4. **Bored**: Bored is a free API to find something to do by getting suggestions for random activities.
5. **Agify.io**: Predict the age of a person based on their name.
6. **Genderize.io**: Predict the gender of a person based on their name.
7. **Nationalize.io**: Predict the nationality of a person based on their name.
8. **Data USA**: Get US public data (e.g., population data, etc.).
9. **Dogs**: Cheer yourself up with random dog images.
10. **IPify**: IPify is a free API that allows you to get your current IP address.
11. **JSON Placeholder**: [https://jsonplaceholder.typicode.com/](https://jsonplaceholder.typicode.com/)

You can test these APIs directly in your browser or using any API testing tool. Since these APIs don't require any keys, 

you can simply copy and paste the sample URLs into your browser or tool to see the responses.

Here's an example of how you can use Node.js and Express to make requests to the APIs mentioned above. I'll use the `axios` library to make HTTP requests.

```javascript
const express = require('express');
const axios = require('axios');
const app = express();
app.use(express.json());

// Public APIs
app.get('/public-apis', async (req, res) => {
    try {
        const response = await axios.get('https://api.publicapis.org/entries');
        res.json(response.data);
    } catch (error) {
        res.json({ message: error.message });
    }
});

// Cat Facts
app.get('/cat-facts', async (req, res) => {
    try {
        const response = await axios.get('https://catfact.ninja/fact');
        res.json(response.data);
    } catch (error) {
        res.json({ message: error.message });
    }
});

// CoinDesk
app.get('/coindesk', async (req, res) => {
    try {
        const response = await axios.get('https://api.coindesk.com/v1/bpi/currentprice.json');
        res.json(response.data);
    } catch (error) {
        res.json({ message: error.message });
    }
});

// Bored
app.get('/bored', async (req, res) => {
    try {
        const response = await axios.get('https://www.boredapi.com/api/activity');
        res.json(response.data);
    } catch (error) {
        res.json({ message: error.message });
    }
});

// Agify.io
app.get('/agify/:name', async (req, res) => {
    try {
        const response = await axios.get(`https://api.agify.io/?name=${req.params.name}`);
        res.json(response.data);
    } catch (error) {
        res.json({ message: error.message });
    }
});

// Start the server
const port = process.env.PORT || 3000;
app.listen(port, () => console.log(`Server is running on port ${port}`));
```

To run this code, you need to have Node.js and npm installed on your machine. You can install the required packages using npm:

```bash
npm install express axios
```

Then, save the above code in a file, say `app.js`, and run it using Node.js:

```bash
node app.js
```

Now, you can test the endpoints using any API testing tool or even your browser for GET requests. For example, you can navigate to `http://localhost:3000/public-apis` to get a list of public APIs. Replace `public-apis` with other paths to test other APIs. For the `agify` API, 
you can use a path like `http://localhost:3000/agify/john` to get the predicted age for the name "John".
