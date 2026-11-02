# WishChat Frontend

Modern, multi-channel AI chatbot builder and embeddable web widget platform built with **React 19**, **Tailwind CSS v4**, and **Vite 6**.

<br/>

[![React](https://img.shields.io/badge/React-19.0-15181e?style=flat-square&logo=react&logoColor=f7f5f1)](https://react.dev)
&nbsp;
[![Vite](https://img.shields.io/badge/Vite-6.1-005222?style=flat-square&logo=vite&logoColor=f7f5f1)](https://vite.dev)
&nbsp;
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-005222?style=flat-square&logo=tailwindcss&logoColor=f7f5f1)](https://tailwindcss.com)
&nbsp;
[![Framer Motion](https://img.shields.io/badge/Framer_Motion-12-15181e?style=flat-square&logo=framer&logoColor=f7f5f1)](https://www.framer.com/motion/)
&nbsp;
[![Embed Widget](https://img.shields.io/badge/Embed_Widget-Vanilla_JS-007136?style=flat-square)](https://github.com/nikace7/wishchat-redesign-frontend)
&nbsp;
[![Auth](https://img.shields.io/badge/Auth-Google_OAuth-15181e?style=flat-square&logo=google&logoColor=f7f5f1)](https://developers.google.com/identity)

---

### Overview

**WishChat** is a customer-facing SaaS frontend designed to let businesses create, customize, evaluate, and deploy intelligent conversational agents across their digital properties without writing code. The platform pairs a visual agent builder and live simulation sandbox with a zero-dependency, embeddable script-tag widget (`chatWidget.js`) that renders reliably on any target website.

---

### Key Capabilities

```
+-------------------------------------------------------------------------------+
|                            WishChat Studio UI                                 |
|                                                                               |
|  [ Builder ]  -->  [ Playground ]  -->  [ Analytics ]  -->  [ Multi-Deploy ]  |
|  Identity,         Live streaming       Chart.js event       - Web Widget     |
|  Prompt tuning,    sandbox with         telemetry &          - WhatsApp API   |
|  Palette theme     Markdown parse       session logs         - Messenger API  |
+-------------------------------------------------------------------------------+
                                         |
                                         v
                     +---------------------------------------+
                     |        Zero-Dependency Widget         |
                     |             chatWidget.js             |
                     |  - Injected via single script tag     |
                     |  - Isolated DOM & responsive tray     |
                     +---------------------------------------+
```

#### 1. Visual Agent Builder (`/build`)
- **Persona & Behavioral Tuning:** Configure system prompts, temperature guidelines, fallback behaviors, and domain boundaries.
- **Visual Styling Engine:** Customize launcher icons, header titles, accent colors (`WidgetColorForm`), and welcome greetings to match brand design systems.

#### 2. Interactive Testing Playground (`/playground`)
- **Real-Time Simulation Sandbox:** Test agent replies before deploying to production.
- **Markdown & Code Rendering:** Powered by `marked` for fast, secure parsing of rich markdown, ordered lists, and code blocks returned by LLMs.
- **Session Management:** Instant context resets and conversation branching during evaluation.

#### 3. Omni-Channel Deployment Suite (`/deploy`)
- **Embeddable Web Script (`chatWidget.js`):** A production-ready, standalone vanilla JavaScript bundle that injects an isolated chat iframe/tray into any client website via a simple `<script>` tag.
- **Domain Authorization (`WebsiteDomainForm`):** Enforce origin whitelisting so widgets only execute on authorized customer domains.
- **Messaging Connectors:** Provisioning workflows for **WhatsApp Business** and **Facebook Messenger** deployment.

#### 4. Analytics & Governance Dashboard (`/dashboard`)
- **Performance Telemetry:** Graphical breakdowns of conversation volume, engagement duration, and response quality using **Chart.js** and `react-chartjs-2`.
- **Multi-Tenant Organization Management (`/createOrganization`):** Team-based collaboration allowing teammates to manage shared agent fleets with role-scoped invitation codes.
- **Monetization & Plan Tiers:** Built-in UI flows for plan tiers, token quotas, and billing status handling.

---

### Architecture & Tech Stack

| Layer | Technology | Purpose |
| :--- | :--- | :--- |
| **Runtime & Core** | **React 19** | Concurrent rendering, modern hooks, and component lifecycle |
| **Build Tooling** | **Vite 6** | Instant Hot Module Replacement (HMR) and optimized rollup bundling |
| **Styling** | **Tailwind CSS v4** | Next-generation CSS engine with zero-config `@tailwindcss/vite` plugin |
| **Animation** | **Framer Motion 12** | Fluid drawer transitions, modal reveals, and smooth message animations |
| **Routing** | **React Router v7** | Nested routes with centralized context boundaries |
| **State Management** | **Context API (`ChatbotContext`)** | Unified state layer for active agent configuration across tabs |
| **Authentication** | **Google Identity Services** | Seamless OAuth sign-in and token delegation via `@react-oauth/google` |
| **Telemetry & Visuals** | **Chart.js 4** | Interactive metric graphs for conversation frequency and retention |

---

### Project Structure

```
src/
├── Components/
│   ├── Build/                  # Chatbot configuration & prompt tuning
│   ├── ChatbotSettings/        # Agent telemetry, billing, and detail controls
│   │   ├── ChatbotAnalytics.jsx# Chart.js engagement visualization
│   │   ├── ChatbotDetail.jsx   # Core metadata and system prompt editing
│   │   └── Payment.jsx         # Quota and subscription management
│   ├── Dashboard/              # High-level overview, pricing & teammates
│   ├── Deploy/                 # Script generation, WhatsApp/Messenger forms
│   │   ├── CustomColorForm.jsx # Real-time widget palette customization
│   │   ├── WebsiteDomainForm.jsx# Allowed origin validation
│   │   └── WebsiteForm.jsx     # Script tag copy snippet generator
│   ├── Homepage/               # Landing presentation & feature breakdown
│   ├── Playground/             # Real-time interactive testing sandbox
│   └── SignIn/                 # OAuth authentication & organization onboarding
├── context/
│   └── ChatbotContext.jsx      # Global state provider for agent attributes
├── chatWidget.js               # Standalone embeddable client widget runtime
├── App.jsx                     # Router tree & route guards
└── main.jsx                    # Application entry point
```

---

### Getting Started

#### Prerequisites
- **Node.js 18+**
- **npm** or **pnpm**

#### 1. Clone & Install Dependencies
```bash
git clone https://github.com/nikace7/wishchat-redesign-frontend.git
cd wishchat-redesign-frontend

npm install
```

#### 2. Configure Environment Variables
Create a `.env` file in the project root:
```env
VITE_API_BASE_URL=https://api.yourdomain.com
VITE_GOOGLE_CLIENT_ID=your-google-oauth-client-id
```

#### 3. Run Development Server
```bash
npm run dev
```
The application will launch on `http://localhost:5173`.

#### 4. Production Build
```bash
npm run build
npm run preview
```

---

### Embedding the Widget

To embed the client chat widget onto any static HTML page or CMS (WordPress, Webflow, Shopify):

```html
<script 
  src="https://your-domain.com/chatWidget.js" 
  data-chatbot-id="YOUR_AGENT_UUID" 
  defer>
</script>
```

---

### Author

**Nikesh Khatri**  
Software Engineer — Kathmandu, Nepal  
- Website: [nikeshkhatri.com.np](https://nikeshkhatri.com.np)  
- GitHub: [@nikace7](https://github.com/nikace7)  
- LinkedIn: [Nikesh Khatri](https://www.linkedin.com/in/nikesh-khatri-2b04582a9/)  
- Email: [khatrinikace@gmail.com](mailto:khatrinikace@gmail.com)
