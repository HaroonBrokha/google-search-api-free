# Google Custom Search API Endpoint Documentation

## Version: 1.01

### Overview
The **Google Custom Search API** is a versatile and powerful interface that allows developers to integrate Google's search capabilities into their applications. With this API, you can access and retrieve search results from Google, spanning multiple categories including **web search**, **image search**, and potentially more as the API evolves. It is designed to be simple to implement while offering flexibility in how search results are queried, handled, and displayed.

This API offers a straightforward yet customizable way for applications to query Google's vast search index and return highly relevant results. By utilizing Google Custom Search Engine (CSE), this API makes it easy to filter and focus searches according to specific needs, ranging from general web content to images and more. This capability can be incredibly useful for developers building apps with search-related functionalities, whether they are targeting general queries or more specialized searches (like for images, videos, or specific domains).

### Key Features
- 🧭 **Search Results Flexibility**: The API allows you to query for a wide range of data, including but not limited to text-based results (web pages, news, etc.) and visual content (images).
- ⚙️ **User-Defined Search Customization**: Developers can define which content types to include, filter results, and modify how data is returned and presented in their application.
- 📈 **Scalability**: Whether you're integrating search capabilities into a small personal project or a large-scale enterprise application, the Google Custom Search API can scale to handle a variety of workloads.
- 🗂 **Structured JSON Output**: The response from the API is structured as a clean, easy-to-parse JSON object, ensuring that developers can easily process and display the data in their applications.

### API Endpoint
The API endpoint used to interact with Google's Custom Search service is located at:


```
https://google-search-api-iota.vercel.app/search
```

### Supported Query Parameters

| Parameter | Description                                                                 |
|-----------|-----------------------------------------------------------------------------|
| `q`       | **Required**: The search query term (e.g., "weather in Islamabad").          |
| `type`    | **Optional**: The content type of search results. Can be `image` for image searches. |
| `cx`      | **Optional**: The custom search engine ID to specify the engine for the query. |

### Example Queries

1. **Standard Web Search** (Example: "Today’s weather in Islamabad"):
    ```
    https://google-search-api-iota.vercel.app/search?q=today%20weather%20in%20islamabad
    ```

2. **Image Search** (Example: "Weather in Islamabad, Type Image"):
    ```
    https://google-search-api-iota.vercel.app/search?q=today%20weather%20in%20islamabad&type=image
    ```

### Response Structure

The API response is a **JSON object** containing several useful fields, which are easy to process and display in your application. Each search result comes with additional metadata and attributes, such as the rank of the result and a link to the source.

#### Response Example:

```json
{
  "query": "today weather in islamabad",
  "results": [
    {
      "rank": 1,
      "title": "10-day weather forecast for Islamabad",
      "link": "https://weather.com/en-PK/weather/tenday/l/Islamabad+Islamabad+Capital+Territory?canonicalCityId=0d5ed3bbc3987ada5e00f6f71f4ea0cc37c42e6b77e962c63c64c8565a442703",
      "snippet": "Be prepared with the most accurate 10-day forecast for Islamabad...",
      "metadata": {
        "watermark": "Haroon Brokha"
      }
    },
    {
      "rank": 2,
      "title": "Islamabad Weather Forecast | AccuWeather",
      "link": "https://www.accuweather.com/en/pk/islamabad/258278/weather-forecast/258278",
      "snippet": "Hourly Weather · 1 PM 68°. rain drop 0% · 2 PM 69°.",
      "metadata": {
        "watermark": "Haroon Brokha"
      }
    }
  ]
}
```
### Standard Web Search Response Example:
```json
{
  "query": "today weather in islamabad",
  "results": [
    {
      "rank": 1,
      "title": "10-day weather forecast for Islamabad, Islamabad Capital Territory ...",
      "link": "https://weather.com/en-PK/weather/tenday/l/Islamabad+Islamabad+Capital+Territory?canonicalCityId=0d5ed3bbc3987ada5e00f6f71f4ea0cc37c42e6b77e962c63c64c8565a442703",
      "snippet": "Be prepared with the most accurate 10-day forecast for Islamabad, Islamabad Capital Territory with highs, lows, chance of precipitation from The Weather ...",
      "metadata": {
        "watermark": "Haroon Brokha"
      }
    },
    {
      "rank": 2,
      "title": "Islamabad, Islamabad, Pakistan Weather Forecast | AccuWeather",
      "link": "https://www.accuweather.com/en/pk/islamabad/258278/weather-forecast/258278",
      "snippet": "Hourly Weather · 1 PM 68°. rain drop 0% · 2 PM 69°. rain drop 0% · 3 PM 72°. rain drop 0% · 4 PM 70°.",
      "metadata": {
        "watermark": "Haroon Brokha"
      }
    }
  ]
}
```
## Image Search Response Example:

```json
{
  "query": "today weather in islamabad?type=image",
  "results": [
    {
      "rank": 1,
      "title": "Three types of boreal summer intraseasonal oscillation found to ...",
      "link": "https://scx2.b-cdn.net/gfx/news/2023/three-types-of-boreal.jpg",
      "snippet": "Three types of boreal summer intraseasonal oscillation found to ...",
      "metadata": {
        "watermark": "Haroon Brokha"
      }
    },
    {
      "rank": 2,
      "title": "Pakistan battles forest fires amidst heat wave | Reuters",
      "link": "https://www.reuters.com/resizer/v2/5QJ2XZJ7NJK4FMFU6H6ZRVNQT4.jpg?auth=8418977821493cb015cf21ef94764708b030e62094774e0e21518c43323824ca&width=1080&quality=80",
      "snippet": "Pakistan battles forest fires amidst heat wave | Reuters",
      "metadata": {
        "watermark": "Haroon Brokha"
      }
    }
  ]
}

```
## Fields Explained

- **rank**: This field represents the rank or order of the search result. The top result will have a rank of 1, the second result will have a rank of 2, and so on.
- **title**: The title is the clickable heading or label of the result. For web search results, this is usually the headline of the page or article. For images, this may be the name or description of the image.
- **link**: The URL to the full resource or source page for the result.
- **snippet**: A brief excerpt from the search result, which helps users understand what the result is about.
- **metadata**: This contains extra data about the search result:
  - **watermark**: This field can be used for tracking and branding purposes. It is custom and can be populated with information to track who is using the API.
- **image** (only in image search): The URL to the image itself. This is only present in the response when the query explicitly requests image results using the `type=image` parameter.

## Querying for Images

To query for images, you must append `?type=image` to the query. This will ensure that the API returns image results in addition to other search results.

### Example Image Query:
```
https://google-search-api-iota.vercel.app/search?q=today%20weather%20in%20islamabad&type=image
```

## Cost

This API is currently **free** to use. However, usage may be subject to limitations such as a **rate limit** (depending on the usage policies of the Google Custom Search API).

## Rate Limiting & Quotas

While this API is free, Google Custom Search APIs typically have usage limits. These limits are detailed in Google's own documentation and may be subject to changes based on API policies. Please refer to the official Google Custom Search API documentation for further information about rate limits, quotas, and potential fees for higher usage.

## Error Handling

The API will return standard **HTTP response codes**:
- **200 OK**: The request was successful, and the response body will contain the search results.
- **400 Bad Request**: The request was missing a required parameter (e.g., the query parameter `q`).
- **500 Internal Server Error**: An error occurred while processing the request on the server side.

## Caching and Performance

This API may cache responses internally to improve performance and reduce load on the backend systems. Cache expiration depends on the system and may vary. Responses are typically fast, but the response time will depend on the external Google API and internet connectivity.

## Conclusion

This Google Custom Search API endpoint allows you to easily query Google Search results and retrieve web search or image search results. The API provides a clean, structured JSON output that is easy to integrate into applications. By simply adding the `type=image` parameter, you can access image search results as well.

