---
description: Guidelines regarding general portal structure
---

# Developer Portal Structure

### Portal UI sections

Number Developer Portal constists of 4 main UI sections:

{% stepper %}
{% step %}
**Navigation column**

This is where all new subpages that make up the documentation section should be added.

{% hint style="danger" %}
**Avoid adding too many navigation items under a single category. After expanding, navigation items need to be manually collapsed by the user, and the nav may become cluttered.**
{% endhint %}

{% hint style="warning" %}
The structure of the pages, categories, and subcategories are the result of information and competition analysis, as well as analysis of the original documentation.&#x20;

When adding any new subpage, make sure that it is assigned to the appropriate group, category, and subcategory for a consistent structure.
{% endhint %}

The structure of the navigation column should be clear and allow easy access to the most important information.
{% endstep %}

{% step %}
**Table of contents**

This is a part that fills in automatically and is based on the content of subpages. There is no way to edit this section manually. All content in the form of H1 and H2 (but not H3) text will be added here while writing content in the main content block.

{% hint style="info" %}
You may reference headers in the current page or other pages by using '#' symbol, e.g. by entering a new line and typing '#Tableofcontents'. **Those will always use the same text as the referenced header, updating automatically.**&#x20;

Make sure those headers are not too long and clear. **Feel free to classify them further to make them more clear when out of context of the parent header or the parent page**, e.g. instead of using a header like "Table of contents", you may want to use "Developer Portal table of contents" when it seems beneficial.
{% endhint %}
{% endstep %}

{% step %}
T**op navigation bar**

These are links that allow you to switch between instances such as: Documentation, API Reference, Ask AI (AI Assistant, which is a separate web app and cannot be edited from GitBook).

It's not recommended to edit the links. In case you need to make changes, you can go to docs site customization to change them.
{% endstep %}

{% step %}
**Page content block**

The place on the page where the documentation content is located.
{% endstep %}
{% endstepper %}

<figure><img src="../../.gitbook/assets/Developer Portal Structure (1).png" alt=""><figcaption></figcaption></figure>



***



### Portal structure

The base information architecture for the portal is as follows:

{% stepper %}
{% step %}
**Home**

An introductory section for Number services which aims to provide a brief on the services we provide as well as recommend next steps.
{% endstep %}

{% step %}
**Developer Quickstart**

Simple step-by-step integration or use case guides that may serve as an introduction for developers to working through certain integration steps or use case implementation.&#x20;

The guides are designed to be viewed in order, and need to provide enough resources for someone to follow them from start to finish without prior experience with the system. **They do not have to go into all options in details.**&#x20;
{% endstep %}

{% step %}
**Getting Started**

More detailed integration and user guides. **Being the source of general knowledge, Getting Started guides should outline as much information as available.**
{% endstep %}

{% step %}
#### Specific use-case guides

Guides focused on specific use cases such as card present payments, storing the card on file, or surcharging. **They should describe all of the available options in details.**
{% endstep %}

{% step %}
**Testing**

Information about the sandbox environment and testing for various errors.
{% endstep %}

{% step %}
**Resources**

Items that should be easily accessible, that need to be used as a reference: downloads, vocabulary, querying reference, etc.
{% endstep %}

{% step %}
**API reference**

Complete list of API methods with descriptions for request and response parameters. It may include additional tips or examples for most used methods.
{% endstep %}

{% step %}
**Customer Support**

Contact information and general information about customer support.
{% endstep %}

{% step %}
**Guidelines**

The hidden guideline sections outline rules to follow when updating the documentation to maintain a consistent and professional feel and ensure content clarity.
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
**When adding new content, follow the** [#portal-structure](developer-portal-structure.md#portal-structure "mention") **for the intended experience. Mixing up content into a wrong section can result in the portal becoming difficult to navigate or in users missing the details they need.**&#x20;
{% endhint %}



***



### Good practices

We recommend the following solutions when adding additional content to the developer portal:

* Before adding a section, category, or subcategory in the navigation column, **make sure there is no other place on the page where the content may be assigned**.<br>
* If there is a need to add a link to an external site, we can divide them into three categories:
  * A link that complements the content of a specific subpage/category/subcategory: in this case, the link should be located in the content it complements.
  * A link that supplements the content of the entire page: in this case, the link should be placed as a separate item in the top navigation bar.
  * A link to the external page that supplements the documentation overall, like AI Assistant, Number informational website etc: in this case, the link should be placed as a separate item in the top navigation bar.<br>
* Each main category of the page should have **an icon** assigned (from the Gitbook icon collection - you can select them at "Page title")<br>
* Each main category of the website should have **a graphic in the hero section** - to assist the user in navigating through extensive documentation.<br>
* The content of the page should be added in a legible way, making it easier to find information by **visually diversifying the content** (using components available in GitBook - which are described in [Content Guidelines](component-guidelines.md))



