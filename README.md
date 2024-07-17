# BigCommerce StoreInsight API

## Description:
The BigCommerce StoreInsight API provides developers with the ability to access and analyze various metrics and insights related to BigCommerce stores. This API allows users to retrieve valuable data on stores, traffic, customer behavior, and product performance, enabling informed decision-making and strategic planning for online retail operations. This API can be found on rapidapi -> https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/bigcommerce-storeinsight-api

## Key Features:
- Access to detailed store info & analytics.
- Insights into customer interactions and purchase patterns.
- Performance metrics for products and categories.
- Traffic analysis to understand visitor behavior.

## Search Stores Endpoint

### Description:
This endpoint allows searching stores based on provided query parameters such as `query`, `page`, and `perPage`. It retrieves results from a CSV file and returns them as JSON.

### HTTP Method:
GET

### URL Path:
`/store/search`

### Query Parameters:
- `query` (required): Specifies the search term.
- `page` (optional, default: 1): Specifies the page number for paginated results.
- `perPage` (optional, default: 10, max: 35): Specifies the number of results per page. Maximum value allowed is 35.

### Responses:
- **200 OK**: Returns JSON data with search results.
- **400 Bad Request**:
  - If `perPage` is not provided.
  - If `perPage` exceeds the maximum limit of 35.
  - If `query` is not provided.
- **500 Internal Server Error**: If an error occurs while processing the CSV file.

## Get Random Store Endpoint

### Description:
This endpoint retrieves a random selection of stores with pagination options, allowing users to specify the number of results per page and the page number.

### HTTP Method:
GET

### URL Path:
`/store/random`

### Query Parameters:
- `page` (required, default: 1): Specifies the page number for paginated results.
- `perPage` (required, default: 10, max: 35): Specifies the number of results per page. The maximum value allowed is 35.

### Responses:
- **200 OK**: Returns JSON data with a random selection of stores.
- **400 Bad Request**:
  - If `page` is not provided.
  - If `perPage` is not provided.
  - If `perPage` exceeds the maximum limit of 35.
- **500 Internal Server Error**: If an error occurs while processing the CSV file.

## Get All Stores Endpoint

### Description:
This endpoint retrieves a paginated list of all stores, allowing users to specify the number of results per page and the page number.

### HTTP Method:
GET

### URL Path:
`/store/all`

### Query Parameters:
- `page` (required, default: 1): Specifies the page number for paginated results.
- `perPage` (required, default: 10, max: 35): Specifies the number of results per page. The maximum value allowed is 35.

### Responses:
- **200 OK**: Returns JSON data with a paginated list of all stores.
- **400 Bad Request**:
  - If `page` is not provided.
  - If `perPage` is not provided.
  - If `perPage` exceeds the maximum limit of 35.
- **500 Internal Server Error**: If an error occurs while processing the CSV file.

## Product Description Endpoint

### Description:
This endpoint retrieves the description of a product based on its URL. It also utilizes caching to improve performance by storing and retrieving data for previously requested product URLs.

### HTTP Method:
GET

### URL Path:
`/product/description`

### Query Parameters:
- `productUrl` (required): The URL of the product whose description is to be fetched.

### Responses:
- **200 OK**: Returns JSON data containing the product description.
- **400 Bad Request**: If `productUrl` is not provided.
- **500 Internal Server Error**: If an error occurs while processing the request.

### Caching:
- The endpoint checks if the product description is already cached using a key based on the product URL. If found, it returns the cached data, otherwise, it fetches the description from an external source.

## Get All Products Endpoint

### Description:
This endpoint retrieves a paginated list of all products from a specified store URL. It supports caching for improved performance, allowing for faster retrieval of previously requested data.

### HTTP Method:
GET

### URL Path:
`/store/products`

### Query Parameters:
- `storeUrl` (required): The URL of the store from which to fetch the products.
- `page` (optional, default: 1): Specifies the page number for paginated results.
- `perPage` (optional, default: 10, max: 15): Specifies the number of results per page. The maximum value allowed is 15.

### Responses:
- **200 OK**: Returns JSON data containing the list of products.
- **400 Bad Request**:
  - If `storeUrl` is not provided.
  - If `page` is not provided.
  - If `perPage` is not provided.
  - If `perPage` exceeds the maximum limit of 15.
- **500 Internal Server Error**: If an error occurs while processing the request.

### Caching:
- The endpoint checks for cached data using a key based on the store URL, page number, and results per page. If cached data is available, it returns that data instead of querying again.

## Store Info Endpoint

### Description:
This endpoint retrieves detailed information about a specified store based on its URL. It employs caching to enhance performance by storing and reusing data from previous requests.

### HTTP Method:
GET

### URL Path:
`/store/info`

### Query Parameters:
- `storeUrl` (required): The URL of the store whose information is to be fetched.

### Responses:
- **200 OK**: Returns JSON data containing the store information.
- **400 Bad Request**: If `storeUrl` is not provided.
- **500 Internal Server Error**: If an error occurs while processing the request.

### Caching:
- The endpoint checks if the store information is already cached using a key based on the store URL. If cached data is found, it returns that data instead of making a new request.

## Search All Products Endpoint

### Description:
This endpoint allows users to search for products within a specified store URL, providing pagination options for managing the number of results displayed per page. It also utilizes caching to enhance performance by storing previously fetched search results.

### HTTP Method:
GET

### URL Path:
`/store/products/search`

### Query Parameters:
- `storeUrl` (required): The URL of the store to search for products.
- `query` (required): The search term to filter products.
- `page` (optional, default: 1): Specifies the page number for paginated results.
- `perPage` (optional, default: 10, max: 15): Specifies the number of results per page. The maximum value allowed is 15.

### Responses:
- **200 OK**: Returns JSON data containing the search results for products.
- **400 Bad Request**:
  - If `query` is not provided.
  - If `storeUrl` is not provided.
  - If `page` is not provided.
  - If `perPage` is not provided.
  - If `perPage` exceeds the maximum limit of 15.
- **500 Internal Server Error**: If an error occurs while processing the request.

### Caching:
- The endpoint checks if the search results are already cached using a key based on the store URL, search query, page number, and results per page. If cached data is available, it returns that data instead of querying again.

## Get Personal Contacts Endpoint

### Description:
This endpoint retrieves personal contact information for a specified store based on its URL. It employs caching to improve performance by storing previously fetched contact details.

### HTTP Method:
GET

### URL Path:
`/store/contacts`

### Query Parameters:
- `storeUrl` (required): The URL of the store whose contact information is to be fetched.

### Responses:
- **200 OK**: Returns JSON data containing the available contact information for the store.
- **400 Bad Request**: If `storeUrl` is not provided.
- **404 Not Found**: If no contact information is available for the specified store.
- **500 Internal Server Error**: If an error occurs while processing the request.

### Caching:
- The endpoint checks if the contact information is already cached using a key based on the store URL. If cached data is available, it returns that data instead of making a new request.

## Get Analytics Endpoint

### Description:
This endpoint retrieves analytics data for a specified store based on its URL. It uses caching to enhance performance by storing previously fetched analytics data.

### HTTP Method:
GET

### URL Path:
`/store/analytics`

### Query Parameters:
- `storeUrl` (required): The URL of the store for which analytics data is to be fetched.

### Responses:
- **200 OK**: Returns JSON data containing the analytics information for the store.
- **400 Bad Request**: If `storeUrl` is not provided.
- **404 Not Found**: If there is an issue retrieving analytics for the specified store (e.g., invalid domain).
- **500 Internal Server Error**: If an error occurs while processing the request.

### Caching:
- The endpoint checks if the analytics data is already cached using a key based on the store URL. If cached data is available, it returns that data instead of making a new request.

## Get Analytics v2 Endpoint

### Description:
This endpoint retrieves enhanced analytics data for a specified store based on its URL. It employs caching to improve performance by storing previously fetched analytics data.

### HTTP Method:
GET

### URL Path:
`/store/analyticsv2`

### Query Parameters:
- `storeUrl` (required): The URL of the store for which analytics data is to be fetched.

### Responses:
- **200 OK**: Returns JSON data containing the enhanced analytics information for the store.
- **400 Bad Request**: If `storeUrl` is not provided.
- **404 Not Found**: If there is an issue retrieving analytics for the specified store (e.g., invalid domain).
- **500 Internal Server Error**: If an error occurs while processing the request.

### Caching:
- The endpoint checks if the analytics data is already cached using a key based on the store URL. If cached data is available, it returns that data instead of making a new request.

## Store Competitors Endpoint

### Description:
This endpoint retrieves competitor data for a specified store using SemRush. It allows users to set a limit on the number of competitors returned and employs caching to enhance performance by storing previously fetched data.

### HTTP Method:
GET

### URL Path:
`/store/competitors`

### Query Parameters:
- `storeUrl` (required): The URL of the store for which competitors are to be fetched.
- `limit` (optional, default: 10): Specifies the maximum number of competitors to return.

### Responses:
- **200 OK**: Returns JSON data containing the competitor information for the store.
- **400 Bad Request**:
  - If `storeUrl` is not provided.
  - If `limit` is not provided.
- **404 Not Found**: If there is an issue retrieving competitors for the specified store (e.g., insufficient data).
- **500 Internal Server Error**: If an error occurs while processing the request.

### Caching:
- The endpoint checks if the competitors' data is already cached using a key based on the store URL and limit. If cached data is available, it returns that data instead of making a new request.


## Commonly Asked Questions:

### 1. **What data can I access using the StoreInsight API?**
You can access a range of metrics including sales data, customer behavior analytics, product performance, and traffic insights for your BigCommerce store.

### 2. **How do I authenticate with the StoreInsight API?**
Authentication is done using the rapidapi platform. You will need to obtain an access token using your client credentials.

### 3. **What endpoints are available in the StoreInsight API?**
The API provides various endpoints for retrieving analytics data, including endpoints for sales metrics, customer insights, product performance, and more.

### 4. **Is there a limit on the number of requests I can make to the API?**
Yes, the API has rate limits to ensure fair usage and performance. Be sure to check the API documentation for specific rate limit details.

### 5. **Can I integrate the StoreInsight API with other analytics tools?**
Absolutely! You can integrate data retrieved from the StoreInsight API with other analytics platforms and tools for more comprehensive data analysis.





:



