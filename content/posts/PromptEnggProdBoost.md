---
title: "Prompt Engineering - Productivity on Steriods"
date: 2024-02-03T18:25:18-05:00
draft: false

weight: 100

cover:
  image: "images/ChatGPT_logo.png"
  Alt: Azure
  imageWidth: 300
  imageHeight: 300

tags:
  [
    "ChatGPT",
    "Data Engineering",
    "Azure",
    "Azure Data Factory",
    "Prompt Engineering",
  ]
categories:
  [
    "ChatGPT",
    "Data Engineering",
    "Azure",
    "Azure Data Factory",
    "Prompt Engineering",
  ]
---

In my recent data engineering quest, I had to wrangle data from seven sources and fill our data warehouse using Azure Data Factory. The end result? Twenty-one pipelines doing a synchronized dance, populating twenty-six tables. Back in the pre-ChatGPT era, this Herculean task would've demanded three full-time heroes for six months. Enter ChatGPT: in just five months, with the power of 1.25 FTEs, Mission Accomplished.

But that's not all! ChatGPT Playground's prompts turned me into a coding sorcerer. Copy-paste JSON, and voila! DDLs appeared like magic. Python programs swooped in as trusty sidekicks, vanquishing data consistency issues with superhero speed. It wasn't just a data conquest; it was a tale of efficiency, savings, and a touch of digital enchantment.

Here is a sample of that magical brew that we now call Prompt Engineering.

```Text
    You are MS SQL Admin. You are tasked with creating a table.

    1. I will give a JSON object with sample data.
    2. Use nvarchar(60) for string data values
    3. Add drop table if the table exists.
    4. If the column name is 'id', it is the primary key and prefix it with the root element name.
    5. Do not use the IDENTITY column type
    6. Table name is suffixed with '_staging'.
    7. If the value is an array, use nvarchar(max).
    8. If the value is a nested JSON object, use nvarchar(max).
    9. Schema name is FreshWorks.

    Say ready when ready to receive the JSON object.

```

{{<rawhtml>}}

<link rel="stylesheet" href="//cdn.jsdelivr.net/gh/highlightjs/cdn-release@10.3.2/build/styles/an-old-hope.min.css"></link>
<style>

.flex-container {
display: flex;
flex-direction: row;
}
.flex-item {  
 flex: 50%;
padding: 5px;
}

/_ Responsive layout - makes a one column layout instead of a two-column layout _/
@media (max-width: 800px) {
.flex-container {
flex-direction: column;

}
}
</style>

<div class="flex-container">
  <div class="flex-item">
    <div>
        <div class="code">
          <pre>
          <code>
            /* 
              Sample JSON response from 
              https://api.freshservice.com/#view_a_ticket 
            */
            {
              "ticket": {
                "cc_emails": [],
                "fwd_emails": [],
                "reply_cc_emails": [],
                "fr_escalated": false,
                "spam": false,
                "email_config_id": null,
                "group_id": null,
                "priority": 3,
                "requester_id": 1000000678,
                "requested_for_id": 1000000670,
                "responder_id": null,
                "source": 2,
                "status": 2,
                "subject": "Ticket Title",
                "to_emails": null,
                "sla_policy_id": 1000000029,
                "department_id": null,
                "id": 266,
                "type": "Incident",
                "due_by": "2017-09-08T23:03:44Z",
                "fr_due_by": "2017-09-08T15:03:44Z",
                "is_escalated": false,
                "description": "&lt;div&gt;this is a sample ticket&lt;/div&gt;",
                "description_text": "this is a sample ticket",
                "custom_fields": {
                  "custom_text": null,
                  "auto_checkbox": false
                },
                "created_at": "2017-09-08T11:03:44Z",
                "updated_at": "2017-09-08T11:37:01Z",
                "urgency": 1,
                "impact": 1,
                "category": null,
                "sub_category": null,
                "item_category": null,
                "deleted": false,
                "attachments": [
                  {
                    "content_type": "text/plain",
                    "size": 5,
                    "name": "attachment.txt",
                    "attachment_url": 
                      "https://cdn.freshservice/data/Helpdesk/attachments/
                          production/19852343/original/attachment.txt",
                    "created_at": "2017-09-08T11:03:45Z",
                    "updated_at": "2017-09-08T11:03:45Z"
                  }
                ],
                "workspace_id": 3,
                "created_within_business_hours": false,
                "approval_status": 4,
                "approval_status_name": "Not Requested"
              }
            }			
          </code>
          </pre>
        </div>
      </div>
    </div>
    <div class="flex-item">
      <div class="code">
        <pre class="sql">
          <code class="language-sql">
            # Table creation DDL
                        
                        IF OBJECT_ID('FreshWorks.ticket_staging', 'U') IS NOT NULL
                DROP TABLE FreshWorks.ticket_staging;
            GO

            CREATE TABLE FreshWorks.ticket_staging (
                ticket_id INT PRIMARY KEY,
                cc_emails NVARCHAR(MAX),
                fwd_emails NVARCHAR(MAX),
                reply_cc_emails NVARCHAR(MAX),
                fr_escalated BIT,
                spam BIT,
                email_config_id INT,
                group_id INT,
                priority INT,
                requester_id INT,
                requested_for_id INT,
                responder_id INT,
                source INT,
                status INT,
                subject NVARCHAR(60),
                to_emails NVARCHAR(MAX),
                sla_policy_id INT,
                department_id INT,
                type NVARCHAR(60),
                due_by DATETIME,
                fr_due_by DATETIME,
                is_escalated BIT,
                description NVARCHAR(MAX),
                description_text NVARCHAR(60),
                custom_fields NVARCHAR(MAX),
                created_at DATETIME,
                updated_at DATETIME,
                urgency INT,
                impact INT,
                category NVARCHAR(60),
                sub_category NVARCHAR(60),
                item_category NVARCHAR(60),
                deleted BIT,
                attachments NVARCHAR(MAX),
                workspace_id INT,
                created_within_business_hours BIT,
                approval_status INT,
                approval_status_name NVARCHAR(60)
            );


          ## Couple of points to note
          ##    deleted column is of type boolean
          ##    attachments column is of type nvarchar(max)
          ##    approval_status is of type INT.

          ## All of them recognized from sample data





            &nbsp;

</code>
</pre>
</div>
</div>

  </div>

{{</rawhtml>}}
