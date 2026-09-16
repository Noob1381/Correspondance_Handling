# Correspondence Handling

This repository acts as an intelligent, automated workspace for drafting and handling emails across multiple distinct businesses. It leverages AI agent skills to automatically adapt to the specific tone, voice, and regulatory requirements of whichever business you are responding on behalf of.

## 🚀 Key Features

*   **Automatic Context Loading:** Simply ask the agent to draft an email for "Business A", and it will automatically look up Business A's tone guidelines, past emails, and official regulations.
*   **Brand Consistency:** Utilizes the `brand-identity` and `managing-brands` skills to ensure all outgoing correspondence strictly adheres to the unique persona of the respective business.
*   **Humanized Text:** Employs the `humanizing-text` skill to automatically strip out any robotic, "AI-sounding" phrasing, ensuring a natural and empathetic tone.
*   **Regulatory Compliance:** Cross-references all drafted emails against publicly available standards and official rules provided by the business.

## 📁 Repository Structure

*   **`AGENTS.md`**: The global rules engine. It dictates the protocol the AI must follow whenever it is asked to draft a response for a specific business.
*   **`business_samples/`**: The directory where all source material is stored.
    *   Create a subfolder for each business (e.g., `business_samples/Business_A/`).
    *   Place sample emails, tone of voice guidelines, and compliance links/PDFs inside.
*   **`.agents/skills/`**: Contains the core AI skills imported to run this workflow (`brand-identity`, `humanizing-text`, `managing-brands`).

## 🛠️ How to Use

1.  **Add Your Business Data:** Create a folder inside `business_samples/` (e.g., `Business_A`). Drop in any relevant sample emails, brand guidelines, and official rules.
2.  **Prompt the Agent:** In your chat, simply provide the email you received and say:
    > *"Draft a response for Business_A: [Paste email]"*
3.  **Review:** The agent will automatically run the email drafting protocol, load the specific business context, apply the brand and humanizing skills, check for compliance, and present you with the final draft.
