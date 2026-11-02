# Imobi Lançamentos
## AI-Assisted Real Estate Discovery & Business Management Platform

**Project type:** Real-estate digital product · Web platform · Android application  
**Public website:** https://imobilancamentos.com.br/  
**Android app:** https://play.google.com/store/apps/details?id=com.imobilancamentos.app  
**Development repository:** Private client repository — source code is not publicly available.

## Overview

Imobi Lançamentos is a real-estate technology platform focused on property launches in São Paulo, Brazil. It brings property discovery, AI-assisted search, buyer context, lead workflows and agency operations into a connected digital experience.

The product serves different parts of the property journey: people researching a home, real-estate agents handling opportunities, partner agencies managing their teams and platform administrators overseeing integrations and modules.

The platform is available through a public website and an Android application published on Google Play.

## Product experience

### Property discovery

- Browse new developments and properties using catalogue pages, filters and property details.
- Explore locations, photos, videos, floor plans and commercial information.
- Save favourite properties and continue the discovery journey.
- Request visits and contact real-estate professionals when ready.

### Imobi IA

The public product includes an AI-assisted property discovery experience. It helps users ask questions about the available catalogue, compare property options and explore choices in the context of budget and preferences.

The product also includes conversational and video-tour experiences intended to make property research more accessible and self-directed.

### Buyer Intelligence

The codebase documents a buyer-intelligence model that brings together:

- Buyer profile information, such as motivation, preferred location, property requirements, financial context, timeline and objections.
- Behavioural signals and engagement history.
- Explainable scoring dimensions, including intent, timeline, financial capacity, clarity and engagement.
- Eligibility filters before property matching.
- Ranked property recommendations with explanations that agents can discuss with buyers.
- CRM views for reviewing buyer context, signals, scores and recommended next actions.

**Implementation status:** The repository contains the buyer-profile, scoring, matching and recommendation work, including database migrations and server-function workflows. The project handoff documentation also identifies deployment steps still required for full activation, including applying specific migrations, publishing Edge Functions, scheduling the intelligence job and completing event instrumentation. Therefore, this case study does not claim that every signal or automated workflow is fully active in production.

### Agency and lead operations

The platform's documented business-management capabilities include:

- Agency and broker account workflows.
- Lead intake, assignment and ownership management.
- CRM pipeline and lead activity history.
- Visits, proposals and credit-analysis workflows.
- Property catalogue management and approval workflows.
- Partner and platform administration.
- Integration management and synchronization history.

### Financing tools

The product includes a financing simulator oriented to Brazil's Minha Casa, Minha Vida context. It presents estimates to help users understand possible financing scenarios. These outputs are indicative and are not a bank approval or a guarantee of eligibility.

### Android application

The Android application extends the product to mobile users. Its Google Play listing describes property discovery in São Paulo, browsing developments, viewing photos, videos and floor plans, searching by region, exploring Minha Casa, Minha Vida opportunities, simulating financing, saving favourites and contacting agents.

**Google Play:** https://play.google.com/store/apps/details?id=com.imobilancamentos.app

## Technical architecture

The private repository documents a modular web application and a separate Expo / React Native mobile application sharing the product's Supabase backend.

### Web application

- React 19 and TypeScript
- TanStack Start and TanStack Router
- Vite
- Tailwind CSS
- Radix UI
- TanStack Query
- Supabase client integration

### Backend and data

- Supabase
- PostgreSQL
- Supabase Auth and Row Level Security policies
- Database migrations for product domains and workflows
- Server and Edge Function patterns for application services
- Background video-processing worker

### Mobile application

- React Native
- Expo SDK
- Expo Router
- Supabase client integration
- Native maps, location, notifications, media and audio capabilities

### Integrations and product services

The repository documents integrations and workflows including:

- Órulo OAuth connection and development-catalogue synchronization.
- XML and API property feeds.
- Push notifications and web push.
- WhatsApp-related lead and conversation workflows.
- Payment and sponsorship modules.
- Video processing and streaming workflows.

The presence of a module or integration in the codebase does not by itself establish that every external service is enabled or fully operational in production.

## Modular product architecture

The web application organises major business domains under a module registry. Documented domains include properties, agencies, leads, proposals, visits, credit, feeds, Órulo, sponsorships, AI, SEO, public API, administration, accounts, mobile experience, marketing and WhatsApp.

The registry supports module-level metadata and feature availability, helping the product evolve without treating every capability as one monolithic feature.

## My contribution

I worked across the product's development and delivery, including:

- Web platform development and implementation of business-facing workflows.
- Development of the Android application.
- Integration of the mobile experience with the platform's backend and services.
- Implementation work around AI-assisted property discovery and buyer-intelligence capabilities.
- Product integration and release work, including publishing the Android application on Google Play.

This description focuses on my contribution to the product. It does not imply sole authorship of every part of the platform or disclose client-owned source code.

## Engineering considerations

The project involved more than building screens. It required coordinating multiple product surfaces and business domains, including:

- Keeping web and mobile experiences aligned with shared data.
- Modelling real-estate entities and lead lifecycles.
- Designing role-aware workflows for buyers, brokers, agencies and administrators.
- Maintaining data-access boundaries through authentication and Row Level Security.
- Integrating external property catalogues and communication channels.
- Distinguishing AI-generated recommendations and financing estimates from definitive financial decisions.
- Tracking which capabilities are implemented, which require external configuration and which remain pending release or validation.

## Project status and transparency

The public website and Android application are available. The private repository contains ongoing development history and documentation, including features whose final production activation depends on external configuration, migrations, integrations or further validation.

The project is evolving; this case study describes documented capabilities and the public product experience rather than claiming that every planned feature is complete.

## Links

- [Visit Imobi Lançamentos](https://imobilancamentos.com.br/)
- [Install the Android application](https://play.google.com/store/apps/details?id=com.imobilancamentos.app)
- [GitHub profile — Gabriel Nathan Tati](https://github.com/gabrielnathantati2)

---

*Case study prepared for professional portfolio purposes. Client source code, credentials, customer records and internal operational details are intentionally excluded.*
