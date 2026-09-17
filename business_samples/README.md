# Business Samples

This directory is dedicated to storing sample documents and emails for each business, as well as their official rules and publicly available standards.

To help the agent understand the tone, type, and specific writing style for each distinct business, please create a subfolder for each business and include:
1. **Sample Documents:** Past emails, tone guidelines, templates.
2. **Visual Identity:** A `visual_identity.md` (copy it from `_TEMPLATE/`) recording the email signature, letterhead, fonts, and colours, plus a `brand_assets/` subfolder holding the actual files (logo, letterhead template, signature image).
3. **Official Rules & Standards:** PDFs, links (e.g., in a `links.txt` or `urls.md` file), or text documents outlining industry regulations, public compliance rules, or official policies that the business must adhere to in their correspondence.

## Example Structure:

```
business_samples/
├── Business_A/
│   ├── sample_email_1.txt
│   ├── brand_guidelines.pdf
│   ├── customer_support_replies.md
│   ├── official_regulations.pdf
│   ├── visual_identity.md
│   └── brand_assets/
│       ├── logo.png
│       └── letterhead.docx
└── Business_B/
    ├── tone_of_voice_guide.md
    ├── sales_pitch_example.txt
    └── compliance_links.md
```

`_TEMPLATE/` is a blank starting point for new businesses. The agent ignores it when drafting.

Once the samples are provided, the agent will analyze them in conjunction with the imported `managing-brands` and `humanizing-text` skills to craft perfectly tailored responses.
