# Content Guidelines

## Typography

The font family selected in GitBook settings to create this page is **Inter** - a modern font that can also be used on other Number pages and materials.

> The administrator cannot manipulate the size and style of individual fonts.

<figure><img src="../../.gitbook/assets/Typography (1).png" alt=""><figcaption></figcaption></figure>

### Font size

**To build page content, we recommend using the following font types available in GitBook:**

{% stepper %}
{% step %}
Heading 1

It is recommended on subpages consisting of nested subsections - only H1 and H2 text appears in the table of contents on the right.
{% endstep %}

{% step %}
**Heading 2**

It should be used in place of H1 on subpages where one level of category will be sufficient. Otherwise, use it to create subsections within H1.
{% endstep %}

{% step %}
**Heading 3**

Use it to create subsections within H2.
{% endstep %}

{% step %}
**Paragraph bold**

Recommended for lowest-level subsection titles and parts of paragraphs that should be highlighted. **When creating longer paragraphs, highlighting using bold font can also help break up the text.**

{% hint style="danger" %}
**When creating danger-level hints, use the bold font and keep the text brief.**
{% endhint %}
{% endstep %}

{% step %}
**Paragraph regular**

It should be used in paragraph text and as the main content of other available components (e.g. hints, ordered / unordered lists, cards, etc.).
{% endstep %}
{% endstepper %}

{% hint style="info" %}
H1, H2, H3, and the paragraph all create a different type of spacing and may appear differently from the editor on the finished website.
{% endhint %}



### Text casing

Only main navigation items in the navigation column on the left should use Title Case. Navigation groups should use UPPERCASE. **All headers and page content should use regular text casing.**



***



## Spaces and dividers

<figure><img src="../../.gitbook/assets/Content implementation.png" alt=""><figcaption></figcaption></figure>

To make the page content more readable, it is recommended to use an empty row of paragraph text as an additional spacer between the sections.

**Follow the recommendations for the spaces between the specific sections:**&#x20;

* **End of page**\
  \- Empty paragraph row x2
* **Main site sections**\
  \- Empty paragraph row + divider + empty paragraph row
* **2nd level sections**\
  \- An empty paragraph row
* **3rd level sections**\
  \- No empty rows or dividers, just use the spacing created by H3.
* **Parameter descriptions**\
  \- Add dividers on both sides
* **Content-rich subpage**\
  \- Make sure to correctly use the headings and rules above to divide the content as it should be enough. Only make exceptions in the rarest of cases.



***



## Available components

To create this page, we used most of the components available in GitBook. Below are some recommendations for their use in future iterations of the documentation.

{% hint style="info" %}
It is recommended to use different types of content styles - the aim is to increase the readability of the information provided.
{% endhint %}

You can find all available components by clicking on "+" icon next to each main content section type. You may also enter a new line by pressing "Enter" and hit forward slash "/" to get the same options.

<figure><img src="../../.gitbook/assets/Components.png" alt=""><figcaption></figcaption></figure>

We highly recommend mixing the content by adding:



### Lists

* **Stepper:**\
  A component that is ideally suited to describe a process with steps that logically follow each other or a more complex list with longer descriptions. This component can also be used to differentiate the look of content.
* **Unordered list:**\
  For all other bullet point style elements that do not form logical steps/points.
* **Ordered lists:**\
  A minimalistic version of the stepper for when you need to form logical steps or need to assign numbers to each option, but do not have that much content to add in the list.
* **Task lists:**\
  A list of checkboxes added to allow the user to mark the completion of individual necessary tasks.



### Hints

We can use 4 types of hints: info, success, warning, and danger. **Hints should always have all of the necessary context to understand them and not depend on the adjecent content.** Avoid using words like "this" to begin a hint and instead fully clarify the object of the hint.

{% hint style="info" %}
Info hint is used to highlight informative content with a neutral message and to increase content readability. Most commonly used hint.

Example: "With the Verifone Windows event log installed, a merchant can export the log and send it to Number if any unexpected behavior is encountered."
{% endhint %}

{% hint style="success" %}
Success hint is used to highlight content with a positive message such as special features that can be optionally enabled.

Example: "You can also use our **custom desktop application** as an alternative to the Virtual Terminal. The desktop application supports much of the same features."
{% endhint %}

{% hint style="warning" %}
Warning hint is use to bring attention to potential issues and things to look out for, and provide solutions for those scenarios.

Example: "If your customer wants to change the schedule completely, it is recommended that you cancel the existing consent and create a new one."
{% endhint %}

{% hint style="danger" %}
**Danger hint is use to highlight information necessary to achieve a goal and avoid problems, or examples of errors.**&#x20;

**Example: "Never request a query without a limiting date factor. As the account grows, you may attempt to return an excessive number of past records and cause an error."**
{% endhint %}



### Quotes

> Quotes can be used to quote text from another website or, in rare circumstances, to help highlight some content and to separate it from a larger part.



### Files and URLs

For additional files, documents and any other types of materials that we want to make available to users, please use the "Files" component - it allows you to highlight files for download.

This will force you to upload the file to GitBook - if you absolutely need a link to a file that is supposed to change overtime and you do not plan on versioning, you can use "Embed a URL" component instead.

You should also use the "Embed a URL" component to link to external websites or use "Cards" when there are multiple options for the same thing.

{% hint style="danger" %}
**Files to download should be placed in at least two places:**

* **Next to the documentation fragment they supplement**
* **In the** [tools-and-downloads.md](../../documentation/resources/tools-and-downloads.md "mention") **section in** [resources](../../documentation/resources/ "mention")

**The same is true for links to various tools and examples**
{% endhint %}



### Tables

A table is a readable component that can be used for various purposes:

* As a standard table consisting of multiple related content&#x20;
* As a bullet point element consisting of a graphic and content (e.g. presentation of the test credit cards numbers of specific card brands)

{% hint style="warning" %}
**Warning**

For a tables with a lot of content, we recommend using a standard content width with an internal, horizontal scroll inside the table.
{% endhint %}

**Examples:**

*   Bullet points table:\


    <table data-full-width="false"><thead><tr><th width="134"></th><th width="146">Card brand</th><th width="468">Card number</th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/Discover icon 2.png" alt="" data-size="original"></td><td><strong>PIN Debit</strong></td><td><strong>4017 7799 9111 3335</strong></td></tr><tr><td><img src="../../.gitbook/assets/1 Visa icon.png" alt="" data-size="original"></td><td><strong>Visa</strong></td><td><strong>4761 5300 0111 1118</strong></td></tr><tr><td><img src="../../.gitbook/assets/1 Master card icon.png" alt="" data-size="original"></td><td><strong>MasterCard</strong></td><td><strong>5137 2211 1111 6668</strong></td></tr></tbody></table>
*   Content-heavy table with internal horizontal scroll:\


    <table data-full-width="false"><thead><tr><th width="134">Card brand</th><th width="201">Card number</th><th width="104">EXP date</th><th width="82">CVV</th><th width="513">Track data</th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/1 Visa icon.png" alt="" data-size="original"></td><td>4012 8818 8881 8888</td><td>12/28</td><td>999</td><td>%B4012881888818888^TSYS PAYMENT^25121011796251900000?;4012881888818888=25121011796251900000?</td></tr><tr><td><img src="../../.gitbook/assets/1 Master card icon.png" alt="" data-size="original"></td><td>5146 3150 0000 0055</td><td>12/28</td><td>998</td><td>%B5146315000000055^TSYS PAYMENT^251210100000?;5146315000000055=251210100000?</td></tr><tr><td><img src="../../.gitbook/assets/1 Amex icon.png" alt="" data-size="original"></td><td>3714 4963 5392 376</td><td>12/28</td><td>9997</td><td>%B371449635392376^TSYS PAYMENT^251210100000?;371449635392376=251210100000?</td></tr></tbody></table>



### Cards

A component that can replace a bullet list and can be used in many variants to improve content readability:

* 2 columns
* 3 columns&#x20;
* With full card image
* With content image&#x20;
* With redirect on click

Example: Credit card (3 columns, full card image):\


* <table data-view="cards"><thead><tr><th data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><a href="../../.gitbook/assets/Masercard.png">Masercard.png</a></td></tr><tr><td><a href="../../.gitbook/assets/Visa.png">Visa.png</a></td></tr><tr><td><a href="../../.gitbook/assets/Amex.png">Amex.png</a></td></tr></tbody></table>



### Tabs

A component that can be used to condense equivalent or similar content consisting by placing it in individual tabs.&#x20;

We highly recommend using it for multiple code blocks with different technology presentations:

{% include "../../.gitbook/includes/code-hmac.md" %}



