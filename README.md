# End-to-End AI Invoice Processing and Notification System (n8n Workflow)

## Project Overview

This project demonstrates a robust, automated workflow built using **n8n** that handles the complete lifecycle of an incoming or outgoing invoice. It uses AI to extract structured data from unstructured documents, logs the information, and automatically generates and sends professional email notifications to the internal billing team.

This automation significantly reduces manual data entry and ensures timely record-keeping and communication.

## Features

The workflow is a seamless integration of cloud services, file processing, and advanced AI:

1.  **Automated Trigger:** Watches a specified folder on **Google Drive** for new invoice file uploads (e.g., PDF or Image).
2.  **AI-Powered Data Extraction:** The workflow uses the **Information Extractor** node, which is powered by a Language Model (LLM), to parse the invoice document and accurately extract all key invoice data, including **Invoice Number, Client Details, Total Amount, Invoice Date, and Due Date**.
3.  **Database Logging:** The extracted information is then automatically **appended to a Google Sheets database** ("Invoice DB") for permanent record-keeping.
4.  **Dynamic Email Generation:** An **OpenAI Model (GPT-4o-mini)** is used to dynamically generate a professional email **Subject** and **Body** tailored to the notification.
5.  **Notification Delivery:** The workflow concludes by sending this customized notification email via **Gmail** to the designated internal billing team.

## Workflow Diagram (Steps)

The automation process follows this sequence:

`Google Drive Trigger` -> `Download Binary` -> `Extract from File` -> `Information Extractor` (Powered by Gemini) -> `Update DB` (Google Sheets) -> `Message a model` (OpenAI for Email Content) -> `Send Email` (Gmail)

## Setup and Installation

### Prerequisites

To run this workflow, you will need access to:

* A running **n8n Instance** (Self-hosted or Cloud).
* **Google Drive** Credentials (OAuth2) for file triggering and downloading.
* **Google Sheets** Credentials (OAuth2) for database logging.
* **OpenAI API Key** (for generating email content).
* **Gmail** Credentials (OAuth2) for sending notifications.
* A **Google Gemini/PaLM** API Key (used by the Information Extractor).

### Steps

1.  **Import Workflow:**
    * Download the `Invoice Processing.json` file.
    * In your n8n canvas, click **"Import from JSON"** and upload the file.

2.  **Connect Credentials:**
    * Update all credential fields (Google Drive, Google Sheets, OpenAI, Gmail) within the respective nodes to connect them to your accounts.

3.  **Configure Paths:**
    * In the **Google Drive Trigger** node, specify the Folder ID where you will upload your invoices.
    * In the **Update DB** node, link the correct Google Sheet Document ID and Sheet Name.
    * In the **Send Email** node, change the `To` email address to your internal billing team's email.

4.  **Activate:**
    * Save the workflow and toggle the "Active" switch to enable the automation.

## Related Resources

* [Your YouTube/Facebook Video Link Here] - Watch a video demo of this workflow in action!
