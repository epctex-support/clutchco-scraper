# Actor - Clutch.co Scraper

## Clutch.co scraper

Since Clutch.co doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Clutch.co data scraper supports the following features:

- Search any keyword - You can search any keyword you would like to have and get the results

- Scrape lists - Scrape any list that you'd like to get from Clutch.co

- Scrape reviews - If you want the reviews for the companies then it is very easy to make it done.

- Scrape company profile - Scrape a very detailed information for each of the companies that you'd like to get.


## Bugs, fixes, updates and changelog
This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/tugkan/clutchco-scraper/issues).

### Incoming Changes
- Retrieve resource details
- Search any keyword on resources
- Enrich the reviews part, integration of full reviews.


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Clutch.co that should be visited. Required fields are:

| Field | Type | Description |
| ----- | ---- | ----------- |
| startUrls | Array | (optional) List of Clutch.co URLs. You should only provide list or detail URLs |
| search | String | (optional) Keyword that you want to search on Clutch.co. It is required when `mode` is defined. |
| mode | String | (optional) Mode that you want to use the search keyword on. The values can only be: `profiles` and `companies`. It is required when `search` field is defined. |
| includeReviews | Boolean | (optional) Adding reviews into the profile objects is optional and by default it is `false`. If you want to scrape the reviews of the companies then you can make this option as `true`. |
| endPage | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`. |
| maxItems | Integer | (optional) You can limit scraped profiles. This should be useful when you search through the big lists.|
| proxy | Object | Proxy configuration |
| extendOutputFunction | String | (optional) Function that takes a JQuery handle ($) as argument and returns object with data |
This solution requires the use of **Proxy servers**, either your own proxy servers or you can use <a href="https://www.apify.com/docs/proxy">Apify Proxy</a>.

##### Tip
When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

Please also keep in mind that the `includeReviews` parameter will add multiple requests per company, on top of your actor. That's why the number of requests or the CUs that are consumed might be higher if you make this option as `true`.


### Compute Unit Consumption
The actor optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.07-0.08 compute units.

### Clutch.co Scraper Input example
```json
{
  "startUrls":[
    {"url":"https://clutch.co/profile/smartsites"}
  ],
  "search": "api",
  "mode": "companies",
  "endPage": 5,
  "maxItems": 100,
  "includeReviews": true
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Clutch.co Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Clutch.co actor.

## Scraped Clutch.co Company Profiles
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
