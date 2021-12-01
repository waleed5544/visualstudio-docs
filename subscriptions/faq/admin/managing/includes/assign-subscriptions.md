---
title: How do I assign Visual Studio subscriptions?
description: You can assign subscriptions to your end users one at a time, or using the Bulk add feature to quickly and easily upload a larger...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: evanwindom
ms.author: amast
ms.date: 12/03/2020
---

## How do I assign Visual Studio subscriptions?

You can assign subscriptions to your end users one at a time, or using the Bulk add feature to quickly and easily upload a larger number of subscribers at a time.

To assign subscriptions individually:

1. Select the [Manage Subscribers tab](https://manage.visualstudio.com/subscribers) at the top of the page on [manage.visualstudio.com](https://manage.visualstudio.com)
2. Select Add and type the name and email address of the user you'd like to assign a subscription to.
    1. If your organization is using Azure Active Directory the name field will search to find people in your current directory. You can select from the search results, or add someone manually.
3. If you want the subscriber to have access to software downloads when they sign into the [Visual Studio Subscriptions Portal](https://my.visualstudio.com/), make sure to leave the downloads toggle enabled in the Download settings section.
4. Complete the Communication Preferences section so that we know what language to send your subscribers assignment email in.
5. If you'd like to add any notes associated with the assignment, please use the Reference selection.
6. Select Add at the bottom of the fly-out panel to complete your subscription assignment. Your subscriber will receive an email and can begin using their Visual Studio subscription immediately (there is no activation needed from your subscriber).

To Bulk assign subscriptions:

1. Select the [Manage Subscribers tab](https://manage.visualstudio.com/subscribers) at the top of the page on [manage.visualstudio.com](https://manage.visualstudio.com).
2. Select Bulk add, download the Excel template, and save a local copy.
3. All fields are required, with the exception of the Reference field.
    1. Ensure that none of the form fields contain commas.
    2. Remove spaces before and after form fields.
    3. Ensure names do not contain extra spaces between two-part first or last names (for example, if a person has a two-part first name such as 'Maggie May', it should be typed as 'MaggieMay').
4. Return to [manage.visualstudio.com](https://manage.visualstudio.com), select Bulk add, and upload your saved copy of the Excel template.
5. When the upload is successful you will see a confirmation page, and your subscriber list populated with your new subscribers. Your subscribers will receive an email and can begin using their Visual Studio subscription immediately (there is no activation needed from your subscribers).

[Read more information](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) about assigning subscriptions in the Visual Studio Subscriptions Administrator portal to learn more about quickly and easily assigning subscriptions.  [Learn more](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) about managing Visual Studio subscriptions with GitHub Enterprise. 

## What is the GitHub Enterprise setup process? 

GitHub Enterprise is set up and managed separately from Visual Studio subscriptions. Following a Visual Studio subscription with GitHub Enterprise purchase, a GitHub Enterprise account setup process is initiated in parallel with (but separate from) establishing an agreement in manage.visualstudio.com. Establishing this GitHub Enterprise account may take some time.  

After your company has set up a GitHub Enterprise account, subscribers who have been assigned Visual Studio subscriptions with GitHub Enterprise will receive an email from GitHub notifying them that their Visual Studio subscriptions have been linked. After subscribers receive this email, they can reach out to their GitHub organization administrator to receive an invitation to the appropriate organization. 

[Read more](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) about managing Visual Studio subscriptions with GitHub Enterprise. Reference [subscriber documentation](https://docs.microsoft.com/visualstudio/subscriptions/access-github) for additional details on the GitHub Enterprise set up process. 