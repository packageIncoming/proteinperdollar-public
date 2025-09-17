# ProteinPerDollar.com (PPD)

A comprehensive platform for budget-conscious nutrition optimization, helping users find the most cost-effective sources of protein and other nutrients.

<img width="7680" height="4320" alt="home page not signed in" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/home%20page%20not%20signed%20in.png" />

## Note
You are currently viewing the public version of this repository. To see the actual code, please email me at mertisik329@gmail.com.

## Overview

ProteinPerDollar.com is a website and progressive web application dedicated to helping users make informed decisions about their food purchases by comparing nutritional content per dollar. The platform enables users to optimize their diet for both health and budget through data-driven insights and powerful comparison tools.

## Technical Details
- The backend was implemented using the Django framework in Python, utilizing DigitalOcean's managed app and managed database services and Cloudflare's CDN
- The frontend consists of standard HTML/CSS/JS with the Quagga2 library used as part of the barcode scanning functionality
- API endpoints on the server connected to Stripe webhooks update subscription status for users and provide features like the Journal Insights data aggregation and autocomplete in search for Grocery Lists, Daily Journaling, and Comparison
- Sentry integration for error monitoring and logging

## Core Features

### Search over a database of 400,000+ items
PPD provides a database of over 400,000 items with nutritional information obtained from the USDA FoodData Central database. This includes macronutrients (fat, protein, carbohydrates), minerals, and calculated information such as serving sizes and servings per container. PPD allows users to set their own purchasing price for every item in the database to calculate crucial information for budgeting a healthy diet including _protein per dollar, calories per dollar, and cost per serving_.

<img width="7620" height="8776" alt="item detail page" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/item%20detail%20page.png" />

PPD addresses a large pain-point found in many other nutrition-tracking applications: incorrect data. This is done by allowing _item overrides_, effectively allowing the user to set their own data for pre-existing items in case it is incorrect to their own needs. This preserves the original data while allowing the user to customize their own experience.

<img width="7620" height="9080" alt="item override view" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/item%20override%20view.png" />

Finally, if a user does not find an item in the database, PPD provides _Custom Item Creation_ which extends the full functionality of regular items to allow users to add their own items to the database. These are private and reinforce PPD's goal of meeting user needs.

<img width="7620" height="6552" alt="custom item creation" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/custom%20item%20creation.png" />

PPD allows users to access items either through the website's search engine or by scanning barcodes. Both regular items AND custom items can be assigned barcodes, allowing quick access to any item by the scan of a barcode. Barcodes can also be manually typed and searched on devices without cameras (Screenshot taken on a PC without a camera for reference).
<img width="7680" height="4320" alt="barcode scanner" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/barcode%20scanner.png" />
The homepage search feature comes with advanced filtering by macroutrients and cost to fine-tune searches in the database.
<img width="7680" height="4320" alt="search with advanced filters" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/search%20with%20advanced%20filters.png" />

### Favorite your frequently-accessed items to your Library
Users can favorite items to add to their library for quick-access and summaries of key financial and nutritional data. The library also provides  _Premium users_ with quick access to filtering items by tags and their _grocery lists_ .
<img width="7680" height="4320" alt="library view" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/library%20view.png" />

## Subscription model and Premium Features
PPD's primary monetization comes from PPD Premium, a subscription to the website powered by Stripe which provides users with a host of additional features. These features include _tags, grocery lists, a comprehensive comparison tool, a daily journal, and a daily data insights aggregator_.
<img width="7680" height="4320" alt="stripe integration" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/stripe%20integration.png" />

**Tags** are a simple but powerful organization tool provided to PPD Premium users, allowing items to be grouped by custom tags for easier access in chunks (such as in the _comparison tool_).
<img width="1361" height="1361" alt="library view tag focus" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/library%20view%20tag%20focus.png" />

**The Comparison Tool** allows Premium users to compare the financial and nutritional information of multiple items at once and extracts important insights such as the item with the highest protein per dollar in a given comparison set.
<img width="4320" height="7680" alt="compare page" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/compare%20page.png" />

**Grocery Lists** provide aggregated data on collections of items based on quantity and price, mirroring user grocery lists.
<img width="7680" height="4320" alt="grocerylist creation" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/grocerylist%20creation.png" />
<img width="7620" height="5888" alt="grocery list" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/grocery%20list.png" />

**The Journal and Journal Insights features** allow users to track their daily consumption by both nutrition and cost AND provide insights on consumption over a customizable date range. This allows users to visualize their daily spending trends, nutritional intake, and more.
<img width="7680" height="4320" alt="daily journal" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/daily%20journal.png" />
<img width="7620" height="10716" alt="journal insights" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/journal%20insights.png" />
