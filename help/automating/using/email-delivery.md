---
title: Email delivery
seo-title: Email delivery
description: Email delivery
seo-description: The Email delivery activity allows you to configure sending a single send email or a recurring email in a workflow.
uuid: ff51e164-2f13-40e8-93b6-6d076d25957d
content-encoding: ISO-8859-1
aemsrcnodepath: /content/help/en/campaign/standard/automating/using/email-delivery
contentOwner: sauviat
cq-designpath: /etc/designs/help
cq-lastmodified: 2018-09-10T07 26 54.289-0400
cq-lastreplicated: 2018-09-07T15 04 12.446-0400
cq-lastreplicatedby: sauviat
cq-lastreplicationaction: Activate
products: SG_CAMPAIGN/STANDARD
audience: automating
content-type: reference
topic-tags: channel-activities
cq-template: /apps/help/templates/article-3
discoiquuid: 718e2184-36c9-43f9-a2db-bc6e2df1660b
firstPublishExternalDate: 2018-09-07T15:04:10.009-0400
herogradient: light
isreadyforlocalization: false
jcr-created: 2018-03-15T09 02 57.540-0400
jcr-createdby: admin
jcr-description: Email delivery
jcr-ischeckedout: true
jcr-language: en_us
lastPublishExternalDate: 2018-09-07T15:04:10.009-0400
lochandoffdate: 2018-09-10T07 26 54.288-0400
loclangtag: locales fr;locales de;locales ja
lr-lastreplicatedby: sauviat@adobe.com
navTitle: Email delivery
publishexternaldate: 2018-09-07T15 04 10.009-0400
publishExternalURL: https://helpx.adobe.com/campaign/standard/automating/using/email-delivery.html
sha1: a277fcc7abda65cb8b23ee80f262f2e5fda3c799
topicBrowsingSortDate: 2018-09-07T15:04:10.009-0400
index: y
internal: n
snippet: y
---

# Email delivery

Email delivery

## Description

![](assets/email.png)  ![](assets/recurrentEmail.png)

The **Email delivery** activity allows you to configure sending an email in a workflow. This can be a **single send** email and sent just once, or it can be a **recurring** email.

Single send emails are standard emails, sent once.

Recurring emails allow you to send the same email multiple times to different targets over a defined period. You can aggregate the deliveries per period in order to get reports that correspond to your needs.

## Context of use

The **Email delivery** activity is generally used to automate sending an email to a target calculated in the same workflow.

When linked to a scheduler, you can define recurring emails.

Email recipients are defined upstream of the activity in the same workflow, via targeting activities such as queries, intersections, etc.

The message preparation is triggered according to the workflow execution parameters. From the message dashboard, you can select whether to request or not a manual confirmation to send the message (required by default). You can start the workflow manually or place a scheduler activity in the workflow to automate execution.

## Configuration

1. Drag and drop an **Email delivery** activity into your workflow.
1. Select the activity, then open it using the  ![](assets/edit_darkgrey-24px.png)

   button from the quick actions that appear.

   >[!NOTE]
   >
   >You can access the general properties and advanced options of the activity (and not of the delivery itself) via the  ![](assets/dlv_activity_params-24px.png) button from the activity's quick actions. This button is specific to the **Email delivery** activity. The email's properties can be accessed via the action bar in the email dashboard.

1. Select the email send mode:

    * **Email**: the email is sent a single time. You can specify here whether or not you would like to add an outbound transition to the activity. The different transition types are detailed in step 7 of this procedure.
    * **Recurring email**: the email is sent several times, according to the frequency defined in a **Scheduler** activity. Select the aggregation period of the sends. This allows you to regroup all the sends that occur during the defined period in one single email that is also called **Recurring execution** and can be accessed from the application's marketing activity list.

      For example, for a recurring birthday email, that is sent daily, you can choose to aggregate the sends per month. This allows you to receive reports on your delivery on a monthly basis although the email is sent every day.

1. Select an email type. The email types come from email templates defined in the **Resources** &gt; **Templates** &gt; **Delivery templates** menu.
1. Enter the general properties for the email. You can also attach it to an existing campaign. The label of the workflow's delivery activity is updated with the email label.
1. Define the email content. Refer to the section concerning [content editing](../../designing/using/about-email-content-design.md#using-the-email-content-editor).
1. By default, the **Email delivery** activity does not include any outbound transitions. If you would like to add an outbound transition to your **Email delivery** activity, go to the **General** tab of the advanced activity options (  ![](assets/dlv_activity_params-24px.png)

   button in the activity's quick actions) then check one of the following options:

    * **Add outbound transition without the population**: this lets you generate an outbound transition that contains the exact same population as the inbound transition.
    * **Add outbound transition with the population**: this lets you generate an outbound transition containing the population to whom the email was sent. The members of the target excluded during the delivery preparation (quarantine, invalid email, etc.) are excluded from this transition.

1. Confirm the configuration of your activity and save your workflow.

When you reopen the activity, you are taken directly to the email dashboard. Only its content can be edited.

By default, starting a delivery workflow only triggers the message preparation. The sending of messages created from a workflow still needs to be confirmed after the workflow has been started. But from the message dashboard, and only if the message was created from a workflow, you can disable the **Request confirmation before sending messages** option. By unchecking this option, messages are sent without further notice once the preparation is done.

## Remarks

The deliveries created within a workflow can be accessed in the application's marketing activity list. You can view the workflow's execution status using the dashboard. Links in the email summary pane allow you to directly access linked elements (workflow, campaign, parent delivery in case of a recurring email).

![](assets/wkf_display_recurrent_executions_2.png)

The executions of recurring deliveries are masked by default, though. To view them, check the **Show recurring executions** option in the marketing activities' search panel.

![](assets/wkf_display_recurrent_executions.png)

In the parent deliveries, which can be accessed from the marketing activity list or directly via the associated recurring executions, you can view the total number of sends that have been processed (according to the aggregation period specified when the **Email delivery** activity was configured). To do this, open the detail view of the parent delivery's **Deployment** block by selecting  ![](assets/wkf_dlv_detail_button.png)

.

![](assets/wkf_display_recurrent_executions_3.png) 

## Example

![](assets/wkf_delivery_example_1.png)

This example is a birthday workflow. Every day an email is sent to profiles whose birthday it is on that day. To do this:

* The **Scheduler** allows you to start the workflow every day at 8am.

  ![](assets/wkf_delivery_example_2.png)

* The **Query** activity allows you to calculate the profiles who have provided an email and whose birthday it is on the current day, every time the workflow is executed. The birthday calculation is carried out using a predefined filter available in the palette in the query editing tool.

  ![](assets/wkf_delivery_example_3.png)

* The **Email** is recurring. The sends are aggregated by month. So, all emails sent in a month are aggregated into a single view. In one year, 365 deliveries are therefore executed but they are regrouped into 12 views (also called **recurring executions**) in the Adobe Campaign interface. History and report details are displayed every month and not for every send.

  ![](assets/wkf_delivery_example_4.png)
