---
title: "API Pagination in the wild"
date: 2024-01-31T18:25:18-05:00
draft: false

weight: 100

cover:
  image: "images/CopyActivity.png"
  Alt: MIT logo
  imageWidth: 200
  imageHeight: 200

tags: ["Azure", "Azure Data Factory", "REST", "API"]
categories: ["Azure", "Azure Data Factory", "REST", "API"]
---

In the dynamic API economy, service providers acknowledge the crucial role of API monetization in creating revenue streams. APIs have evolved into the backbone of modern software development, facilitating seamless data exchange between applications. As their complexity and usage increase, the need for efficient data retrieval becomes paramount. Recognizing the symbiotic relationship between API monetization and effective data handling is key for service providers to navigate the evolving landscape successfully, ensuring not only a seamless user experience but also the maximization of revenue potential.

API pagination is a crucial element in data consumption, involving the practice of breaking down extensive datasets into manageable chunks. While it is a common strategy for efficient data retrieval, navigating the challenges within the API pagination landscape is essential. This blog post explores the intricacies of API pagination and introduces a low-code solution using Copy Activity in Azure Data Factory to address these challenges.

Let's use a set of service providers and explore Azure Data Factory-Copy Activity can be used to extract data using config settings

## ENVI

[Envi Inventory Optimization Solutions (IOS), builds and markets web-based supply chain solutions](https://www.envi.com/)

**Envi JSON response for Inventory Item**

![](envi_response.png)

**Azure ADF Copy activity settings for ENVI**

![](envi_copy_activity.png)

The ENVI service provides the absolute URL within the property labeled '@data.nextLink.' Utilizing bracket notation becomes necessary to access the link to the next page due to the presence of special character in the property name.

## CareMessage

[Powering the care of underserved populations](https://www.caremessage.org/)

**CareMessage JSON response for activity logs**
![](cm_response.png)

**Azure ADF Copy activity settings for CareMessage**

![](cm_copy_activity.png)

## FreshWorks

[Customer service, IT, and CRM software that’s powerful yet easy to use. Now supercharged with generative AI.](https://www.freshworks.com/)

**FreshWorks JSON response for service tickets**
![](fw_response.png)

**Azure ADF Copy activity settings for FreshWorks**

![](fw_copy_activity.png)

FreshWorks stands out as the most straightforward service for implementing API pagination by adhering to the RFC 5988 standard. The simplicity is reflected in the clarity of its settings, which effectively convey the necessary information.

## RingCentral

[AI-First Communications You Can Trust](https://www.ringcentral.com/)

**RingCentral JSON response for service tickets**
![](rc_response.png)

**Azure ADF Copy activity settings for RingCentral**

![](rc_copy_activity.png)

RingCentral offers comprehensive guidance for implementing API pagination through various methods. In this specific example, the navigation section is employed due to its simplicity, providing a straightforward approach to implementation.

## WhatConverts

[A lead tracking and reporting software trusted by top PPC and SEO professionals to grow value for clients.](https://www.whatconverts.com/)

**WhatConvert JSON response for leads**
![](wc_response.png)

**Azure ADF Copy activity settings for WhatConverts**

![](wc_copy_activity.png)

```javascript
{{BaseURL}}/leads?start_date=@{dataset().startDate}&end_date=@{dataset().endDate}&leads_per_page=2000&page_number={page_number}
```

WhatConverts offers basic information as part of the response, necessitating an additional effort to construct the URL for retrieving the next page. To address this, a query parameter named 'page_number' is defined on the REST dataset, with the value injected from the copy activity.
