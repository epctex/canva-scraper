[https://apify.com/epctex/canva-scraper](https://apify.com/epctex/canva-scraper?fpr=yhdrb)

# Actor - Canva Scraper

## Canva scraper

Since Canva doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Canva data scraper supports the following features:

-   Search any keyword - You can search any keyword you would like to have and get the results

-   Scrape lists - Scrape any list that you'd like to get from Canva

-   Scrape users - You can check the users and scrape their created templates.

-   Scrape template detail - Scrape very detailed information for each of the templates that you'd like to get.


## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/canva-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Canva that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Canva.

- `startUrls`: (Optional) (Array) List of Canva URLs. You should only provide search, list, user, or detail URLs.

- `includeReviews`: (Optional) (Boolean) This will add all the reviews that Canva provides into the detail objects. Please keep in mind that the time and resources the actor uses will increase proportionally to the number of reviews.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. The default is `Infinite`. This applies to all `search` requests and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns an object with data.

- `customMapFunction`: (Optional) (String) Function that takes each object's handle as an argument and returns the object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If the actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.03-0.05 compute units.

### Canva Scraper Input example

```json
{
  "startUrls":[
    "https://www.canva.com/posters/templates/",
    "https://www.canva.com/templates/?query=baby&continuation=50",
    "https://www.canva.com/p/templates/EAFCgIJdXTw-brown-aesthetic-new-dad-fist-bumps-father-s-day-instagram-post/",
    "https://www.canva.com/p/donnamoritz/"
  ],
  "search": "baby instagram",
  "proxy":{
    "useApifyProxy":true
  },
  "endPage": 3,
  "maxItems": 20
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Canva Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Canva actor.

## Scraped Canva Properties

The structure of each item in Canva looks like this:

### Item Detail

```json
{
  "id": "EAE2D4Zdd5M",
  "url": "https://www.canva.com/p/templates/EAE2D4Zdd5M-baby-instagram-template/",
  "title": "Baby Instagram Template",
  "breadcrumbs": [
    "Baby Instagram Template"
  ],
  "image": "https://marketplace.canva.com/EAE2D4Zdd5M/1/0/1600w/canva-baby-instagram-template-fcw840AqWBM.jpg",
  "creatorName": "Azruca",
  "creatorLink": "https://www.canva.com/p/azruca/",
  "Colors": [
    "#f1f1ef",
    "#b9e4e9",
    "#d17dbc",
    "#ebb0a7",
    "#f9e487"
  ],
  "Fonts": [
    "Blueberry",
    "Cerebri",
    "Beautiful"
  ],
  "Size": [
    "1080 × 1080 px"
  ]
}
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
