# Open Source Article Summarizer with OpenAI GPT-4

Sumz is an open-source article summarization tool powered by the advanced capabilities of OpenAI GPT-4. Designed to help users quickly grasp the essence of lengthy articles, Sumz transforms verbose content into clear, concise, and informative summaries. By leveraging the cutting-edge natural language processing techniques of GPT-4, Sumz ensures that generated summaries maintain context, coherence, and accuracy.

## Key Features

- Open-source
- Powered by GPT-4
- Flexible input formats
- Customizable summary length
- Easy integration
- Multi-platform compatibility

## Current Deployment

![sumz](https://github.com/PruthviGowdaV1/Article-Summarizer/assets/140374124/a6d6bd48-0372-4bbc-a082-b583ca096f53)


[Deployed Site](https://articlesumz.onrender.com/)

## Installation

Follow these steps to install and set up Sumz on your local machine:

Clone the repository:  

`https://github.com/PruthviGowdaV1/Article-Summarizer.git` . 
  
Install Dependencies:  
  
`npm i` **or** `npm install`
  
Create dotenv file:
  
`VITE_RAPID_API_KEY=yourapikey`
  
Run on your local machine:
  
`npm run dev`
  
**Enjoy Summarizing!**

## API
View The Endpoints Here:  
  
This is an API which extracts news/article body from a URL and uses GPT to summarize the article content.  
  
[RapidAPI](https://rapidapi.com/restyler/api/article-extractor-and-summarizer)
### Example Config
```js
const axios = require("axios");

const options = {
  method: 'POST',
  url: 'https://article-extractor-and-summarizer.p.rapidapi.com/summarize-text',
  headers: {
    'content-type': 'application/json',
    'X-RapidAPI-Key': 'yourapikey',
    'X-RapidAPI-Host': 'article-extractor-and-summarizer.p.rapidapi.com'
  },
  data: '{"text":"article of markdown text"}'
};

axios.request(options).then(function (response) {
	console.log(response.data);
}).catch(function (error) {
	console.error(error);
});
```

### RDTK Config
Here's I configured the request using RDTK
```js
export const articleApi = createApi({
    reducerPath: "articleApi",
    baseQuery: fetchBaseQuery({ 
        baseUrl: "https://article-extractor-and-summarizer.p.rapidapi.com/" ,
        prepareHeaders: (headers) => {
            headers.set("X-RapidAPI-Key", rapidApiKey);
            headers.set("X-RapidAPI-Host", 'article-extractor-and-summarizer.p.rapidapi.com');
            return headers;
        }
    }),
    endpoints: (builder) =>  ({
        getSummary: builder.query({
            query: (params) => `/summarize?url=${encodeURIComponent(params.articleUrl)}&length=3`
        })
    })
});
```
In order to increase the length of the summary
```js
//Adjust the length parameter:
 endpoints: (builder) =>  ({
        getSummary: builder.query({
            query: (params) => `/summarize?url=${encodeURIComponent(params.articleUrl)}&length=3` // Here
        })
    })
});
```
