## Features
Clutch.co doesn't provide a very flexible or free API, but this scraper acts as an unofficial Clutch API to help you extract the data you need, when you need it, and at scale.

Clutch.co Scraper supports the following features:

-   **Search any keyword**

-   **Scrape lists**

-   **Scrape reviews**

-   **Scrape company profile**

Clutch provides a "platform of in-depth client reviews, data-driven content, and vetted market leaders". Scraping that content and extracting it in structured format could give you invaluable business insights and an edge over the competition.

## Tutorial
Check out this blog post on [how to extract data from Clutch.co with unofficial Clutch API](https://blog.apify.com/how-to-extract-data-from-clutch-co-without-api/) for more information on the scraper.

## Bugs, fixes, updates and changelog
This scraper is under active development. If you have any feature requests, you can create an issue from [here](https://github.com/tugkan/clutchco-scraper/issues).

### Upcoming changes

-   Retrieve resource details.
-   Search any keyword or resources.
-   Enrich the reviews part, integration of full reviews.

## Setup & usage

You can see how this actor works in this video:

### Search

[![Apify - Clutch.co Scraper - Search](https://img.youtube.com/vi/jkdNRYdUCLI/0.jpg)](https://www.youtube.com/watch?v=jkdNRYdUCLI)

You can check the output of this video [here](https://api.apify.com/v2/datasets/xJMmbumkwgUcM0t79/items?clean=true&format=json).

### Start URLs

[![Apify - Clutch.co Scraper - Start URLs](https://img.youtube.com/vi/Oz_GSovWjX0/0.jpg)](https://www.youtube.com/watch?v=Oz_GSovWjX0)

You can check the output of this video [here](https://api.apify.com/v2/datasets/flUJ63yhGJPqJjMlq/items?clean=true&format=json).

## Input parameters

The input of this scraper should be JSON containing the list of pages on Clutch.co that should be visited. Required fields are:

| Field                | Type    | Description                                                                                                                                                                              |
| -------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| search               | String  | (optional) Keyword that you want to search on Clutch.co. This is required when `mode` is defined.                                                                                          |
| mode                 | String  | (optional) Mode that you want to use the search keyword on. The values can only be: `profiles` and `companies`. This is required when `search` field is defined.                           |
| includeReviews       | Boolean | (optional) Adding reviews into the profile objects is optional and by default it is `false`. If you want to scrape the reviews of the companies, then you can set this option as `true`. |
| maxItems             | Integer | (optional) You can limit scraped profiles. This should be useful when you search big lists.                                                                                  |
| startUrls            | Array   | (optional) List of Clutch.co URLs. You should only provide list or detail URLs.                                                                                                           |
| endPage              | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`.                                                                                                          |
| proxy                | Object  | Proxy configuration.                                                                                                                                                                      |
| extendOutputFunction | String  | (optional) Function that takes a JQuery handle ($) as argument and returns object with data.                                                                                              |
| customMapFunction    | String  | (optional) Function that takes company profile object as argument and returns object with the mapping function.                                                                           |

This solution **requires the use of proxy servers**, either your own proxy servers or [Apify Proxy](https://www.apify.com/docs/proxy).

### Tips

When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startURL**.

If you would like to scrape only the first page of a list, then add the link for the page and have the `endPage` as 1.

Please also keep in mind that the `includeReviews` parameter will add multiple requests per company. That's why the number of requests or CUs that are consumed might be higher if you set this option as `true`.

## Compute unit consumption

Clutch.co Scraper is optimized to run extremely fast and scrape many as listings as possible, so it forefronts all listing detail requests. If the actor doesn't get blocked very often, it will scrape 100 listings in 2 minutes and consume ~0.07-0.08 compute units.

### Clutch.co Scraper input example

```json
{
    "startUrls": [
        "https://clutch.co/profile/smartsites",
        "https://clutch.co/web-developers/freelance",
        "https://clutch.co/profile/blue-collar-agency"
    ],
    "search": "api",
    "mode": "companies",
    "endPage": 1,
    "maxItems": 50,
    "includeReviews": false,
    "customMapFunction": "(object) => { return object }"
}
```

## During the run
During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.

When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## Clutch.co export
During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node.js/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Clutch.co actor.

## Scraped Clutch.co company profiles

The structure of each item in Clutch.co listings looks like this:

```json
{
    "url": "https://clutch.co/profile/smartsites",
    "summary": {
        "name": "SmartSites",
        "logo": "https://img.shgstatic.com/clutchco-static/image/scale/60x60/s3fs-public/logos/a33a9494d9c0f41b112e8a1b4354a3e9.png",
        "title": "Think Web. Think Smart. 💡",
        "rating": 5,
        "noOfReviews": 56,
        "description": "Outsmart the competition with best-in-class digital marketing services. With over 450 ⭐⭐⭐⭐⭐ reviews online, SmartSites is America's #1 rated digital marketing agency. Call 📞 (201) 870 6000 for a free consultation! Get more traffic. Acquire more customers. Sell more stuff. SmartSites works for businesses of all sizes. SmartSites is a Google Premier Partner and Facebook Marketing Partner. Winner of dozens website design awards and four-time Inc5000 (2017-2020) fastest growing company. Let us grow your company.Read more...",
        "verificationStatus": "GOLD VERIFIED",
        "minProjectSize": "$1,000+",
        "averageHourlyRate": "$100 - $149 / hr",
        "employees": "10 - 49",
        "founded": "Founded 2011",
        "addresses": [
            {
                "title": "headquarters",
                "street": "45 Eisenhower Drive",
                "locality": "Paramus",
                "region": "NJ",
                "postalCode": "07652",
                "country": "United States",
                "phone": "+1.201.870.6000"
            }
        ]
    },
    "focus": [
        {
            "title": "Client focus",
            "values": [
                {
                    "name": "Small Business (<$10M)",
                    "percentage": 80
                },
                {
                    "name": "Midmarket ($10M - $1B)",
                    "percentage": 20
                }
            ]
        }
    ],
    "portfolio": [
        {
            "image": "https://static2.clutch.co/s3fs-public/portfolio/28eae3874f8afd9e23a14f332d86353d.jpeg?N66vx9xl9cXLR5H6.euqT_BkCwjjAYD8",
            "description": "Web Design, SEO, PPC"
        }
    ],
    "verification": {
        "verificationStatus": "GOLD VERIFIED",
        "businessEntity": {
            "name": "Melen, LLC",
            "status": "Active",
            "jurisdictionOfFormation": "New Jersey",
            "ID": "0600372607",
            "source": "New Jersey Division of Revenue & Enterprise Services",
            "lastUpdated": "November 1, 2020",
            "dateOfFormation": "May 15, 2011"
        },
        "paymentLegalFilings": {
            "bankruptcy": "No",
            "taxLienFilings": "0",
            "judgementFilings": "0",
            "collectionsCount": "0",
            "source": "New Jersey Division of Revenue & Enterprise Services",
            "lastUpdated": "November 1, 2020",
            "fullBusinessCreditReport": "https://www.smartbusinessreports.com/search2.aspx?link=1352&fn=951794204"
        }
    },
    "reviews": [
        {
            "name": " SEO & PPC Services for Outdoor Refinishing Company ",
            "datePublished": "May 25, 2021",
            "project": {
                "name": "SEO & PPC Services for Outdoor Refinishing Company",
                "category": "SEO & PPC",
                "size": "$10,000 to $49,999$10,000 to $49,999",
                "length": "Sep. 2020 - Jun. 2021Sep. 2020 - Jun. 2021",
                "description": "SmartSites provided SEO and PPC services for an outdoor refinishing company including adding backlinks and creating new content. They planned monthly activities to raise the traffic and conversions."
            },
            "review": {
                "rating": 5,
                "quality": 5,
                "schedule": 5,
                "cost": 5,
                "willingToRefer": 5,
                "comments": "The team's work resulted in increased traffic and conversions. Thanks to SmartSites' efforts, cost per conversion (CPC) went down by 25%. They provided consistent updates and showed detailed reports about the project's status. Their timeliness and remarkable work ensured the engagement's success."
            },
            "reviewer": {
                "title": "Owner, General Manager, Teak & Deck",
                "name": "Drew Isaacman",
                "industry": "Construction",
                "size": "1-10 Employees",
                "location": "Carlsbad, California",
                "reviewType": "Online Review",
                "verified": "Verified"
            }
        }
    ]
}
```
