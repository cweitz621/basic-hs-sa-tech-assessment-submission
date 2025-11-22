# HubSpot Integration - Solutions Architect Technical Assessment


This is a proof-of-concept application for the HubSpot Solutions Architect Technical Assessment. It demonstrates how Breezy (a smart home technology company) would integrate their platform with HubSpot to sync customer data, track trials, and manage subscriptions.

---

## A. Setup Instructions

### Prerequisites

- **Node.js** (v14 or higher)
- **npm** or **yarn**
- A **free HubSpot account**
- **HubSpot Private App** access token
- **Google Gemini API key** (for AI features)

### How to Run Locally

#### 1. Install Dependencies

```bash
npm install
```

#### 2. Get Your HubSpot Access Token

1. Sign up for a [free HubSpot account](https://offers.hubspot.com/free-trial)
2. Navigate to **Settings** → **Integrations** → **Private Apps**
3. Click **Create a private app**
4. Give it a name (e.g., "Breezy Integration App")
5. Go to the **Scopes** tab and enable:
   - `crm.objects.contacts.read`
   - `crm.objects.contacts.write`
   - `crm.objects.deals.read`
   - `crm.objects.deals.write`
6. Click **Create app** and copy your access token

#### 3. Get Your Gemini API Key

1. Go to [Google AI Studio](https://aistudio.google.com/)
2. Sign in with your Google account
3. Click **Get API Key** or navigate to the API Keys section
4. Create a new API key or copy an existing one
5. Activate key with free trial

#### 4. Configure Environment Variables

```bash
cp .env.example .env
```

Edit `.env` and add your credentials:

```env
HUBSPOT_ACCESS_TOKEN=pat-na1-your-token-here
GEMINI_API_KEY=your-gemini-api-key-here
```

#### 5. Start the Server

**For development (with hot-reloading):**

```bash
npm run dev
```

You should see:

```
✅ Server running successfully!
🌐 API available at: http://localhost:3001
📋 Health check: http://localhost:3001/health
📁 Static files served from: /public
```

**To stop the server:** Press `Ctrl+C`

#### 7. Access the Application

Open your browser and navigate to:

```
http://localhost:3001
```

### How to Test the Integration Flow

1. **Create a Contact:**
   - Fill out the "Sync Customer to HubSpot" form
   - Submit the form
   - Verify the contact appears in the contacts table

2. **Create a Trial:**
   - Select an existing contact from the dropdown
   - Fill in trial details (name, value, stage)
   - Submit the form
   - Verify the trial appears in the "Trials" column for that contact

3. **View Data:**
   - The contacts table displays:
     - Contact information (name, email, phone)
     - Trials (deal name, amount, stage, ID)
     - AI Customer Health insights (optional)

4. **Test AI Insights:**
   - Click "Get AI Insight" button for any contact
   - Modal will display AI-generated customer health analysis
   - Includes likelihood to upgrade, churn risk, and HubSpot AI tool recommendations

5. **Test Error Handling:**
   - Try creating a contact with an existing email address
   - Verify you receive a clear error message about duplicate contacts
   - Verify you can only create one trial per contact

---

## B. Project Overview

### What This POC Demonstrates

This proof-of-concept demonstrates an integration between Breezy's smart home platform and HubSpot CRM. The application simulates an admin panel that Breezy's team would use to:

1. **Sync Customer Data**: Automatically create HubSpot contacts when customers create accounts
3. **Manage Trial Signups**: Create trial deals to track which trials have converted to a paid subscription
5. **AI-Powered Insights**: Generate customer health insights using Google Gemini AI, with recommendations for HubSpot AI tools


### Key Features

- **Contact Management**: Create and view contacts
- **AI Customer Health**: Generate insights with specific HubSpot AI tool recommendations
- **Error Handling**: User-friendly error messages for common issues (e.g., duplicate emails, multiple trials)

### Technology Stack

- **Backend**: Node.js with Express.js
- **Frontend**: Vanilla JavaScript, HTML, CSS
- **API Integration**: HubSpot CRM API v3
- **AI Integration**: Google Gemini 2.0 Flash API
- **HTTP Client**: Axios
- **Documentation Tools**: Mermaid (for ERD diagrams), Google Gemini (for diagram generation)

---

## C. AI Usage Documentation

### Which AI Tools Did You Use?

- **Cursor AI**: Used as the primary AI coding assistant throughout the development process
- **Google Gemini 2.0 Flash (Experimental)**: Used for generating customer health insights
- **Google Gemini**: Used in conjunction with Mermaid to generate the Entity Relationship Diagram (ERD) for the HubSpot data architecture


### What Tasks Did You Use AI For?

1. **Code Development and Implementation**:
   - Used Cursor AI as the primary coding assistant throughout the entire project
   - Generated initial code structure for Express.js backend and frontend components
   - Implemented HubSpot API integrations (contacts, deals)
   - Built AI insight feature integration with Gemini API
   - Refactored codebase structure (separating CSS/JS files)
   - Debugged API errors and integration issues (duplicate email handling, pipeline stage loading)
   - Implemented error handling and user feedback mechanisms
   - Created responsive UI components and styling
   - Created searchable dropdown functionality for contact selection

2. **Documentation and Diagram Generation**:
   - Used Google Gemini to generate Mermaid diagram code for the Entity Relationship Diagram (ERD)
   - Gemini helped structure the complex relationships between HubSpot objects (Contacts, Deals)
   - Mermaid rendered the diagram into a visual representation of the data architecture
   - Used Cursor AI to help write and structure the README documentation
   - Generated code examples and explanations for documentation

### What Did You Learn? What Was Challenging?

**What I Learned:**
- Prompt engineering is crucial for getting structured, actionable responses from AI
- AI models need clear instructions about output format (JSON structure)
- Context matters: providing comprehensive information about the business and its goals/priorities leads to better outcomes
- **AI for Documentation**: Using Gemini to generate Mermaid diagram code demonstrated how AI can accelerate documentation tasks, helping structure complex relationships and generate visual representations of system architecture

### How Did AI Help (or Not Help)?

**How AI Helped:**
- **Rapid Development**: Cursor AI significantly accelerated development by generating boilerplate code, API integration patterns, and common functionality
- **Debugging Support**: When encountering errors (API 404s, parsing problems), Cursor helped identify root causes and suggest fixes
- **Code Refactoring**: AI assisted in restructuring code (separating CSS/JS files) and improving code organization
- **Documentation Generation**: Gemini and Cursor helped generate comprehensive documentation, ERD diagrams, and code explanations
- **Problem Solving**: AI provided alternative approaches when initial implementations didn't work (e.g., trying different API endpoints for associations)
- **Time Savings**: Reduced time spent on repetitive tasks, allowing focus on higher-level architecture and business logic

**Limitations and Challenges:** 
- **Missing Business Requirements**: A significant challenge was not knowing the customer's specific business requirements and not being able to conduct a full discovery session/s. This required making assumptions about Breezy's needs, workflows, and priorities, which may not align with their actual requirements
- **Diagram Generation Accuracy**: Gemini did not generate Mermaid diagram code accurately for the ERD. The relationship nodes and connections required manual adjustment to correctly represent the HubSpot data architecture
- **Code Review Needed**: Generated code sometimes required review and adjustment to match project requirements
- **Context Understanding**: Sometimes needed to provide additional context or clarify requirements when AI misunderstood the task
- **Error Handling**: AI-generated code sometimes lacked comprehensive error handling, requiring manual additions
- **Best Practices**: Had to verify that AI suggestions followed best practices and weren't just "working" solutions

**When AI Was Most Valuable:**
- Initial project setup and scaffolding
- Debugging complex integration issues
- Generating documentation and diagrams
- Implementing UI components with proper styling

**When I Needed to Rely More on Manual Work:**
- Understanding business requirements and translating them to code
- Making architectural decisions about data flow and structure
- Testing and validating that features worked as expected
- Ensuring code quality and maintainability
- Making final decisions on user experience and design choices

---

## D. HubSpot Data Architecture

### Entity Relationship Diagram (ERD)

![HubSpot Data Architecture ERD](assets/images/V2_BASIC_Assessment_ERD.png)

*This ERD was created using Google Gemini to generate Mermaid diagram code, which was then rendered into the visual diagram shown above. Gemini helped structure the relationships between HubSpot objects including Contacts and Deals. In this simplified architecture, deals represent both trials and subscriptions, with deal stages indicating subscription status (Converted (Active Subscription) = active subscription, Trial Ended = no subscription, Cancelled = cancelled subscription). A Company object is included in the ERD to support Breezy's potential future B2B distributor model, even though the current POC focuses on B2C operations.*

### Why This Architecture?

This simplified data model architecture provides several key benefits for Breezy's business needs:

1. **Unified Deal-Based Model**: 
   - **Deals represent both trials and subscriptions** - A single deal object tracks the entire trial-to-subscription lifecycle
   - **Deal stages indicate subscription status**: "Converted (Active Subscription)" = active subscription, "Trial Ended" = trial ended without subscription, "Cancelled" = subscription was cancelled
   - This unified approach simplifies data management and reduces complexity by using one object type instead of separate deals and subscription objects

2. **Simplified Revenue Tracking**:
   - Deal amount represents the trial/subscription value
   - No line items required for trials - deals contain the amount directly
   - Enables straightforward revenue tracking without complex line item associations
   - When a deal is closed (Converted (Active Subscription) stage), it represents an active subscription with recurring revenue

3. **Flexible Pipeline Management**:
   - Breezy Premium Subscriptions pipeline tracks the complete customer journey
   - Deal stages clearly indicate subscription status: Active, Converted (Active Subscription), Trial Ended, Cancelled
   - Easy to identify churn risk: "Cancelled" stage = high risk, "Trial Ended" = medium risk, "Converted (Active Subscription)" = low risk
   - Pipeline stages provide immediate visibility into customer health without additional queries

4. **Streamlined Data Model**:
   - Uses only standard HubSpot objects (Contacts, Deals) - no custom objects required
   - Reduces API calls and complexity by eliminating the need for subscription object lookups
   - Deal stage is the single source of truth for subscription status
   - Simpler to maintain and understand for Breezy's team

5. **Complete Customer Journey Tracking**:
   - Contacts can have one trial deal that tracks their entire subscription lifecycle
   - Deal stages provide clear progression: Active → Converted (Active Subscription) (subscription active) or Trial Ended (no subscription)
   - If subscription is cancelled, deal stage moves to "Cancelled" - providing full history
   - Single deal per contact prevents duplicate trials and simplifies tracking

6. **Reporting and Analytics**:
   - Can easily filter deals by stage to identify active subscriptions (Converted (Active Subscription)), churned customers (Cancelled), and unconverted trials (Trial Ended)
   - Track conversion rates by comparing "Converted (Active Subscription)" deals to "Trial Ended" deals
   - Calculate revenue from deal amounts for active subscriptions
   - Simple queries: all deals in "Converted (Active Subscription)" stage = active subscriptions

7. **HubSpot Best Practices**:
   - Uses standard HubSpot objects (Contacts, Deals) for native reporting and workflows
   - Leverages HubSpot's built-in deal stage functionality for subscription lifecycle management
   - No custom objects required - works with any HubSpot plan
   - Deal stages can trigger workflows (e.g., when deal moves to "Converted (Active Subscription)", send welcome email)
   - Native HubSpot reporting tools work out-of-the-box with deal stages

### Deal Pipeline Architecture


#### Breezy Premium Subscriptions Pipeline
**Purpose**: Track trial signups and subscription status

**Stages:**
- **Active Trial** - Trial is currently active
- **Converted (Active Subscription)** - Trial converted to paid subscription (active subscription)
- **Trial Ended** - Trial ended without converting to subscription
- **Cancelled** - Subscription was cancelled (customer had subscription but cancelled it)

**Deal Properties:**
- `dealname`: "Breezy Premium" (default)
- `amount`: Subscription value
- `dealstage`: Selected from dynamic pipeline stages (determines subscription status)
- `pipeline`: Breezy Premium Subscriptions pipeline

**Subscription Status Determination:**
- Deal stage = "Converted (Active Subscription)" → Customer has active subscription (low churn risk)
- Deal stage = "Trial Ended" → Trial ended without subscription (medium churn risk - re-engagement opportunity)
- Deal stage = "Cancelled" → Customer had subscription but cancelled (high churn risk - needs immediate attention)
- Deal stage = "Active" → Trial in progress


### Data Flow

1. **Contact Creation**:
   - Contact created in HubSpot with basic information (name, email, job title, company)
   - Contact is ready to be associated with trials

2. **Trial Creation**:
   - Deal created in Breezy Premium Subscriptions pipeline
   - Deal amount set to trial/subscription value
   - Deal stage set by user (typically "Active" for new trials)
   - Deal associated with contact

3. **Subscription Status Tracking**:
   - Subscription status is determined by deal stage, not a separate object
   - When trial converts to subscription: Deal stage moved to "Converted (Active Subscription)"
   - When trial ends without conversion: Deal stage moved to "Trial Ended"
   - When subscription is cancelled: Deal stage moved to "Cancelled"
   - Deal stage is the single source of truth for subscription status
   - AI insights use deal stages to determine churn risk and customer health

---

## E. AI Feature Explanation

### Describe Your AI-Powered Feature

**AI Customer Health Insight** is a feature that analyzes customer data and generates actionable insights with specific recommendations for using HubSpot AI tools. When a user clicks "Get AI Insight" for a contact, the system:

1. Aggregates customer data (trials, deal stages indicating subscription status, dates)
2. Analyzes deal stages to determine subscription health: "Converted (Active Subscription)" = active subscription (low churn risk), "Trial Ended" = no subscription (medium risk), "Cancelled" = cancelled subscription (high churn risk)
3. Sends a structured prompt to Google Gemini 2.0 Flash API with deal stage information
4. Receives analysis including:
   - **Likelihood to Upgrade**: Low/Medium/High with percentage
   - **Risk of Churn**: Low/Medium/High with percentage (based on deal stages)
   - **Suggested Action**: Specific recommendation with HubSpot AI tool suggestions
   - **Justification**: 2-3 sentence explanation

### Why Did You Choose This Feature?

1. **Real Business Value**: Customer health scoring is a common need for sales and marketing teams
2. **Demonstrates AI Integration**: Shows how AI can enhance HubSpot workflows
3. **Actionable Output**: Provides specific tool recommendations, not just insights
4. **Scalable**: Can analyze any customer without writing new rules
5. **Educational**: Shows the intersection of CRM data, AI analysis, and tool recommendations

### How Does It Make the Integration Smarter?

**Traditional Approach:**
- Manual review of customer data
- Rule-based scoring (e.g., "if trial > 20 days, high churn risk")
- Generic recommendations

**AI-Enhanced Approach:**
- **Contextual Analysis**: Considers multiple factors simultaneously (purchase history, trial activity, time patterns, conversion history)
- **Nuanced Insights**: Identifies patterns that might not be obvious (e.g., "customer with 2 thermostats but no active subscription = expansion opportunity")
- **Tool-Specific Recommendations**: Connects insights to specific HubSpot AI tools for execution
- **Justification**: Explains the "why" behind recommendations, helping teams understand and act

**Example:**
Instead of: "Customer has active trial"
AI provides: "High likelihood to upgrade (85%) - Customer purchased 2 thermostats and has active trial. Use HubSpot AI Email Assistant to draft personalized upgrade email highlighting multi-device benefits."

**Note on Proof of Concept:**
This AI feature is implemented as a proof of concept with limited data points (deal stages, trial dates, basic contact information). In a production application, the AI platform would have access to significantly more data and information that could enhance insights, including:
- Email engagement metrics (open rates, click-through rates, response rates)
- Website activity and behavior tracking
- Support ticket history and resolution times
- Product usage analytics and feature adoption
- Social media interactions and sentiment
- Marketing campaign engagement history
- Payment history and billing interactions
- Customer feedback and survey responses
- Integration usage data (e.g., smart home device connections)
- Historical communication logs and meeting notes

With this richer dataset, the AI could provide even more nuanced insights, identify subtle patterns, and generate highly personalized recommendations that account for the full customer journey and engagement history.


---

## F. Design Decisions

### Technical Choices and Why

1. **Express.js Backend**
   - **Why**: Simple, well-documented, easy to extend. Already am experienced in Express and was the provided server starting point.

2. **Vanilla JavaScript Frontend**
   - **Why**: No build step required, fast iteration, demonstrates core skills
   - **Alternative Considered**: React/Vue (would add complexity for POC)

3. **Modal for AI Insights**
   - **Why**: Keeps table compact, better UX for detailed information
   - **Alternative Considered**: Inline expansion (too much space)

4. **Dynamic Pipeline Loading**
   - **Why**: Adapts to HubSpot configuration changes without code updates
   - **Alternative Considered**: Hardcoded stages (less flexible)


### Assumptions About Breezy's Platform

1. **E-commerce Integration**: Assumed Breezy has an e-commerce platform that can trigger webhooks/API calls when:
   - Customer purchases thermostats
   - Customer signs up for trial

2. **Subscription Management**: In this simplified architecture, subscriptions are represented as deals with deal stages indicating subscription status:
   - Deal stage "Converted (Active Subscription)" = active subscription (successful trial conversion)
   - Deal stage "Trial Ended" = trial ended without subscription
   - Deal stage "Cancelled" = subscription was cancelled
   - Deal stage "Active" = trial in progress
   - This approach uses standard HubSpot objects (deals) rather than custom objects, simplifying the data model

3. **Admin Panel Usage**: Assumed Breezy's team would use this admin panel for:
   - Manual data entry (for testing/demo purposes)
   - Viewing unified customer data
   - Getting AI insights for decision-making based on deal stages

4. **Business Logic**:
   - Each contact can have only one trial deal (prevents duplicate trials)
   - Deal stages track the complete subscription lifecycle: Active → Converted (Active Subscription) (subscription) or Trial Ended (no subscription)
   - If a subscription is cancelled, the deal stage moves to "Cancelled"
   - Deal stage is the single source of truth for subscription status

### What Would You Improve With More Time?

1. **Reporting and Revenue Tracking Structure**:
   - Better understanding of Breezy's specific reporting needs and requirements
   - Establish a more set-in-stone data structure to handle reporting needs, particularly for recurring revenue tracking
   - Design subscription and revenue data models that support accurate MRR/ARR calculations and forecasting
   - Implement proper revenue recognition tracking aligned with their accounting needs

2. **Enhanced Subscription Tracking** (if needed):
   - Current architecture uses deal stages to represent subscriptions, which works well for proof-of-concept
   - If more advanced subscription features are needed (recurring billing, payment processing, renewal automation), consider:
     - HubSpot's native Subscription object (requires Commerce Hub)
     - Integration with subscription billing platforms (Stripe, Recurly, etc.)
     - Custom properties on deals to track subscription-specific data (renewal date, billing frequency, etc.)
   - For most use cases, deal stages provide sufficient subscription status tracking

3. **Error Handling**:
   - More granular error messages
   - Better validation before API calls

4. **Performance**:
   - Batch API calls where possible
   - Implement caching for pipeline stages

5. **Testing**:
   - Unit tests for API endpoints
   - Integration tests for HubSpot API calls

6. **Security**:
   - Input sanitization
   - Rate limiting


### What Would You Ask the Client Before Building Production Version?

1. **Integration Requirements**:
   - What triggers the sync? (webhooks, scheduled jobs, manual?)
   - What's the expected volume? (contacts/day, deals/day)
   - Are there other systems to integrate? (payment processors, shipping, etc.)

2. **Data Requirements**:
   - What additional contact properties are needed?
   - Are there other custom objects required?
   - What reporting/analytics are needed?
   - Do we need to track recurring revenue in HubSpot?
   - How long should historical data be retained?
   - Are there more details about the Subscription itself you need to store in HubSpot?
   - Do wish to track plan changes?

3. **Business Rules**:
   - When should deals be automatically updated?
   - What workflows should be automated?
   - Are there compliance requirements (GDPR, etc.)?


5. **Technical Constraints**:
   - What's the hosting environment? (cloud, on-premise)
   - Are there security/compliance requirements?
   - What's the budget for API calls (HubSpot, AI)?
   - Are there preferred technologies/frameworks?

7. **Timeline & Resources**:
   - What's the launch timeline?
   - Who will maintain the system?
   - What's the support model?

---

### Project Structure

```
hs-solution-architect-tech-assignment/
├── server.js              # Main Express server
├── package.json           # Dependencies and scripts
├── .env                   # Environment variables (not in git)
├── .env.example          # Example environment variables
├── .gitignore            # Git ignore rules
├── README.md             # This file
├── assets/              # Documentation assets
│   └── images/          # Images for README documentation
└── public/               # Frontend application
    ├── index.html        # Main HTML file
    ├── css/
    │   └── styles.css    # Application styles
    └── js/
        └── app.js        # Application logic
```

