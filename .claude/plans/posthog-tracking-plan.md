# PostHog User Journey Tracking Plan

## Overview
Extend `_includes/posthog.html` to track key business actions for potential mediation clients. Focus on high-value conversion signals, not granular product analytics.

## User Context
**Target persona**: Professional or individual seeking mediation services
**Discovery method**: Business card, Google search for "Mediation Berlin", referral
**Goal**: Evaluate credibility, understand services, initiate contact

## What to Track: Business-Critical Actions

### 1. Contact Intent Signals (Highest Priority)
These are the actions that matter - actual conversion attempts.

**Events to track**:
- `Phone Clicked` - Click-to-call on mobile or phone number click
  - Properties: `page_location` (homepage, services, contact, about)
  - **Why**: Direct conversion signal, immediate intent to talk
  
- `Email Clicked` - Click on email address
  - Properties: `page_location`
  - **Why**: Alternative contact method preference
  
- `Contact Form Started` - First interaction with form
  - Properties: none needed
  - **Why**: Serious intent to engage, but may drop off
  
- `Contact Form Submitted` - Already tracked, enhance
  - Properties: `subject_category` (which service area selected)
  - **Why**: Completed conversion, shows service demand

### 2. Service Interest Signals (High Priority)
Understand which services drive inquiries.

**Events to track**:
- `Service Page Viewed` - Visit to /services/
  - Properties: `referrer_page`
  - **Why**: Core page for understanding offerings
  
- `Contact Form Subject Selected` - Dropdown selection in contact form
  - Properties: `service_category` (mediation, beratung, gesellschaftsrecht, baurecht, familie, etc.)
  - **Why**: Direct signal of which service area they need
  
- `Consultation CTA Clicked` - "Beratungstermin vereinbaren" button
  - Properties: `cta_location` (homepage, services_page)
  - **Why**: High-intent action, measures CTA effectiveness

### 3. Credibility Verification (Medium Priority)
Track trust-building page visits.

**Events to track**:
- `About Page Viewed` - Visit to /about/
  - Properties: `came_from` (direct navigation or homepage)
  - **Why**: Checking credentials before committing to contact
  
- `Blog Post Read` - Any blog post view (already happens via pageview)
  - Properties: `post_title`
  - **Why**: Content marketing effectiveness, thought leadership

## Priority Implementation Order

### Phase 1: Must Have (Core Conversion Tracking)
1. Phone Clicked
2. Email Clicked
3. Contact Form Started
4. Contact Form Subject Selected (enhance existing submission tracking)

### Phase 2: Should Have (Service Demand Insights)
5. Consultation CTA Clicked
6. Service Page Viewed

### Phase 3: Nice to Have (Context)
7. About Page Viewed
8. Blog Post engagement (basic pageview sufficient)

## Implementation Approach

### Technical Strategy
1. **Click event listeners** - Attach to phone links (`tel:` links) and email links (`mailto:`)
2. **Form event listeners** - Track form focus (started) and subject dropdown change
3. **CTA tracking** - Find links to contact page, especially "Beratungstermin vereinbaren"
4. **Page context** - Use `window.location.pathname` for page_location properties
5. **Simple and clean** - Minimal code, no complex tracking logic

### Data Privacy
- **No PII** - Never track actual form values, only that fields were interacted with
- **GDPR compliant** - Respect DNT (already configured in existing code)
- **Subject categories OK** - Generic service categories are not PII

## Critical Files

### Files to Modify
- `_includes/posthog.html` - Add event tracking JavaScript (lines 49-64)

### Files to Reference (Read-Only)
- `contact.md` - Contact form structure, phone/email links
- `index.md` - Homepage CTA buttons
- `services.md` - Services page CTA buttons

## Verification Plan

### Local Testing
1. Run Jekyll: `bundle exec jekyll serve --config _config.yml,_config_posthog_local.yml`
2. Open browser console (F12)
3. Navigate site and test each action
4. Verify PostHog events in console and PostHog dashboard

### Test Scenarios
1. **Phone click** - Click phone number on any page → See "Phone Clicked" event
2. **Email click** - Click email address → See "Email Clicked" event  
3. **CTA click** - Click "Beratungstermin vereinbaren" → See "Consultation CTA Clicked" event
4. **Form start** - Click in any form field → See "Contact Form Started" event
5. **Subject select** - Choose option from subject dropdown → See "Contact Form Subject Selected" event
6. **Form submit** - Submit form → See enhanced "Contact Form Submitted" with subject_category

### Success Criteria
- All 6 event types fire correctly with appropriate properties
- No JavaScript errors in console
- Events appear in PostHog dashboard immediately
- No PII is sent (verify in PostHog event properties)

## Implementation Notes
- Keep it simple - 8 core events total
- Focus on conversion signals that answer: "What services do people want?" and "How do they prefer to contact?"
- All events use PostHog's `capture()` method already initialized
- Builds on existing form submission tracking
