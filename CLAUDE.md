# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static marketing/landing page for **Wellspring Mental Health & Wellness Ministry** (wellspringthrive.com). Lead generation site for a free downloadable guide ("When the Church Becomes the Frontline") targeting church leaders. Founder: Gina Colclazier.

## Tech Stack

- **Pure HTML/CSS/vanilla JavaScript** — no frameworks, no build tools, no package manager
- **Hosted on GitHub Pages** with custom domain via CNAME
- **CSS custom properties** for theming, flexbox/grid layouts, CSS animations
- **Fonts**: Raleway (headings) + Source Sans 3 (body) via Google Fonts

## Architecture

**Single-page site** — everything lives in `index.html` (~975 lines) with inline `<style>` and `<script>` tags.

### External Services
- **Mailchimp** (us13, list ID: `f9674ff996`) — lead capture via JSONP, drip campaign with 3 emails
- **Google Analytics GA4** (`G-E33B1W7X6V`) — custom event tracking for CTAs, section views, form submissions
- **Calendly** — discovery call booking (`calendly.com/gina-wellspringthrive/30min`)
- **Canva** — guide design (ID: `DAHGHpMRnPU`)

### Drip Email Sequence
Three standalone HTML email templates designed for Mailchimp:
- `drip-1-guide-delivery.html` — immediate, delivers PDF link
- `drip-2-key-insight.html` — day 3, key insight + re-download
- `drip-3-discovery-call.html` — day 7, Calendly CTA

Guide PDF hosted on Mailchimp: `mcusercontent.com/8916cf1013f9ba45c244a58d4/files/...`

### Design System (CSS Variables)
- Primary: Navy `#122a3a`, Cyan `#00aeef`, Copper `#cc8a48`
- Background: Cream `#faf8f5`, warm grays
- Container max-width: `1140px`

## Deployment

Push to `master` branch → GitHub Pages auto-deploys. Custom domain `wellspringthrive.com` configured via `CNAME` file and GoDaddy DNS.

## Key Files

- `index.html` — the entire landing page
- `mailchimp-setup.sh` — Bash script for Mailchimp API setup (API key, templates, automation)
- `CNAME` — GitHub Pages custom domain config
- `email-logo.svg` — email header logo (referenced by Mailchimp templates)

## Mailchimp API

API key and list ID are in `mailchimp-setup.sh`. Datacenter: `us13`. Base URL: `https://us13.api.mailchimp.com/3.0`. Domain `wellspringthrive.com` is authenticated (SPF + DKIM configured in GoDaddy DNS).
