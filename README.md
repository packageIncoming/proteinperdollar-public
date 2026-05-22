# ProteinPerDollar.com

> A comprehensive nutrition optimization platform helping users maximize nutritional value per dollar across 400,000+ food items

**[📧Contact](mailto:mertisik329@gmail.com)**

[![Django](https://img.shields.io/badge/Django-4.2-green.svg)](https://www.djangoproject.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue.svg)](https://www.postgresql.org/)
[![Python](https://img.shields.io/badge/Python-3.11-yellow.svg)](https://www.python.org/)

<img width="7680" height="4320" alt="ProteinPerDollar.com home page" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/home%20page%20not%20signed%20in.png" />

---

## Overview

ProteinPerDollar.com is a data-driven nutrition platform that empowers budget-conscious users to optimize their diet through comparative nutritional economics. By analyzing cost-per-nutrient metrics across a massive USDA-sourced database, the platform enables users to make informed purchasing decisions that maximize both health outcomes and financial efficiency.

### The Problem
Traditional nutrition tracking focuses solely on consumption without addressing the economic dimension of food choices. Users struggle to answer: "Which protein source gives me the best nutritional value for my money?"

### The Solution
A full-stack platform that calculates and ranks food items by **protein per dollar**, **calories per dollar**, and custom nutrient-per-dollar metrics across 400,000+ items, with intelligent search, real-time cost tracking, and actionable spending insights.

---

## Tech Stack

### Backend
- **Framework:** Django 4.2 (Python)
- **Database:** PostgreSQL 15 with custom GIN indexing
- **API Integration:** Stripe (payment processing), USDA FoodData Central (data ingestion)
- **Real-time Processing:** Asynchronous search endpoints with autocomplete

### Frontend
- **Core:** HTML5, CSS3, JavaScript (ES6+)
- **Libraries:** Quagga2 (barcode scanning via WebRTC)
- **PWA:** Progressive Web App capabilities for mobile experience

### Infrastructure & DevOps
- **Hosting:** DigitalOcean Managed App Platform
- **CDN:** Cloudflare (edge caching, DDoS protection)
- **Database:** DigitalOcean Managed PostgreSQL (high availability)
- **Monitoring:** Sentry (error tracking), Google Analytics (user insights)

---

## Key Technical Achievements

### Database Performance Optimization
**Optimized PostgreSQL search performance on 400,000-item dataset by implementing GIN Indexes and custom SearchVector annotations, reducing query latency by ~80% (to <1s) for common searches while supporting 13+ concurrent filtering parameters**

- Custom full-text search with search vectors and GIN indexes 
- Materialized views for expensive aggregation queries
- Query plan optimization for complex JOIN operations

### ETL Pipeline Engineering
**Engineered Python ETL script to ingest and normalize USDA FoodData datasets, utilizing bulk update with atomic transactions to maximize write throughput**

- Automated data validation using Pint library for unit conversion
- Idempotent import process handling 400K+ records
- Programmatic serving size calculations from nutritional data

### Dynamic Ranking Algorithm
**Architected ranking algorithm using Django ORM expressions (F() objects and Case/When) to dynamically sort products by 'Protein-Per-Dollar' and 'Macro-Ratios' in real-time without degrading database performance**

- User-defined pricing system (custom cost per item)
- Real-time calculation of cost-per-serving, protein-per-dollar, calories-per-dollar
- Complex aggregation queries optimized for sub-second response times (13+ different filters and ranges including text search)

### Premium Subscription System
**Implemented Stripe API integration with webhook-driven subscription management for premium tier features**

- Secure payment processing with PCI compliance
- Automated subscription status updates via webhooks
- Tiered feature access control

---

## Core Features

### Intelligent Search Engine

Search across 400,000+ USDA-verified food items with advanced filtering capabilities.

<img width="7680" height="4320" alt="Advanced search with filtering" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/search%20with%20advanced%20filters.png" />

**Technical implementation:**
- PostgreSQL full-text search with GIN indexes
- 13+ concurrent filter parameters (protein, fat, carbs, price, calories, cost metrics)
- Sub-second query response with proper indexing strategy
- Real-time autocomplete via asynchronous API endpoints

---

### Barcode Scanning Integration

Instant item lookup via camera or manual barcode entry using WebRTC and Quagga2 library.

<img width="7680" height="4320" alt="Barcode scanner interface" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/barcode%20scanner.png" />

**Technical implementation:**
- WebRTC camera access for real-time barcode detection
- Quagga2 library for barcode decoding (UPC-A, UPC-E, EAN-13)
- Fallback manual entry for devices without cameras
- Custom barcode assignment for user-created items

---

### Comprehensive Item Database

Detailed nutritional and economic data for every food item.

<img width="7620" height="8776" alt="Item detail page with metrics" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/item%20detail%20page.png" />

**Key metrics displayed:**
- Macronutrients (protein, fat, carbohydrates) per serving
- Minerals and micronutrients (USDA data)
- User-defined pricing for cost calculations
- **Protein per dollar** (ranked metric)
- **Calories per dollar** (ranked metric)
- **Cost per serving** (calculated field)
- Servings per container (programmatically calculated)

---

### Item Overrides & Custom Entries

Address data accuracy issues by allowing user-controlled item data.

<img width="7620" height="9080" alt="Item override interface" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/item%20override%20view.png" />

**Technical implementation:**
- Shadow table architecture (original USDA data preserved)
- User-specific overrides stored separately
- Priority system: User override > Original data
- All cost-per-nutrient metrics recalculated on override

<img width="7620" height="6552" alt="Custom item creation form" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/custom%20item%20creation.png" />

**Custom item creation:**
- Private user-generated entries
- Full CRUD operations (create, read, update, delete)
- Same functionality as USDA items (tagging, comparison, journaling)
- Barcode assignment capability

---

### Smart Library System

Organize frequently-accessed items with favorites and intelligent filtering.

<img width="7680" height="4320" alt="Library with favorites" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/library%20view.png" />

**Features:**
- Quick-access favorites (one-click save)
- Aggregated financial and nutritional summaries
- Premium: Tag-based filtering and organization
- Premium: Direct integration with grocery lists

---

## Premium Features (Stripe-Powered)

<img width="7680" height="4320" alt="Stripe payment integration" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/stripe%20integration.png" />

### Smart Tagging System

Organize items into custom categories for batch operations.

<img width="1361" height="1361" alt="Tag-based organization" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/library%20view%20tag%20focus.png" />

**Use cases:**
- Group by meal type (breakfast, lunch, dinner)
- Group by dietary goal (high protein, low carb, budget)
- Group by shopping location (Trader Joe's, Costco, etc.)

---

### Advanced Comparison Tool

Side-by-side analysis of multiple items with automated insights extraction.

<img width="4320" height="7680" alt="Multi-item comparison interface" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/compare%20page.png" />

**Technical capabilities:**
- Compare unlimited items simultaneously
- Automatic highlighting of best value (highest protein-per-dollar, lowest cost-per-serving)
- Macro-ratio visualization
- Export comparison data

---

### Grocery List Aggregation

Smart shopping lists with real-time cost and nutrition totals.

<img width="7680" height="4320" alt="Grocery list creation" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/grocerylist%20creation.png" />

<img width="7620" height="5888" alt="Grocery list summary" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/grocery%20list.png" />

**Features:**
- Quantity-based item addition
- Automatic cost summation (user-defined prices × quantities)
- Nutritional totals across all items
- Shareable lists for household shopping

---

### Daily Journal + Analytics

Track daily consumption with comprehensive spending and nutrition insights.

<img width="7680" height="4320" alt="Daily food journal" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/daily%20journal.png" />

<img width="7620" height="10716" alt="Journal insights dashboard" src="https://github.com/packageIncoming/proteinperdollar-public/blob/main/journal%20insights.png" />

**Analytics engine:**
- Custom date range analysis (day, week, month, year)
- Spending trends visualization
- Macro-nutrient intake patterns
- Cost-per-nutrient efficiency over time
- Identifies optimization opportunities

**Technical implementation:**
- Asynchronous aggregation queries via Django ORM
- Server-side data preprocessing for chart rendering
- Efficient time-series data handling

---

## System Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                     Cloudflare CDN                          │
│            (Edge Caching + DDoS Protection)                 │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│              DigitalOcean App Platform                      │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐   │
│  │            Django Application Layer                  │   │
│  │                                                      │   │
│  │  ┌─────────────────────────────────────────────┐     │   │
│  │  │  Views (Request Handlers)                   │     │   │
│  │  │  - Search, Item Detail, Journal, Lists      │     │   │
│  │  └──────────────────┬──────────────────────────┘     │   │
│  │                     │                                │   │
│  │  ┌──────────────────▼──────────────────────────┐     │   │
│  │  │  Business Logic (Models + Managers)         │     │   │
│  │  │  - Cost Calculations (F() expressions)      │     │   │
│  │  │  - Ranking Algorithms (annotate + order)    │     │   │
│  │  │  - ETL Pipeline (bulk operations)           │     │   │
│  │  └──────────────────┬──────────────────────────┘     │   │
│  │                     │                                │   │
│  │  ┌──────────────────▼──────────────────────────┐     │   │
│  │  │  Django ORM (Query Layer)                   │     │   │
│  │  │  - Query optimization, prefetch_related     │     │   │
│  │  └──────────────────┬──────────────────────────┘     │   │
│  └──────────────────────────────────────────────────────┘   │
└────────────────────────┬────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────┐
│      DigitalOcean Managed PostgreSQL (High Availability)    │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐    │
│  │  Items Table (400K+ rows)                           │    │
│  │  - GIN index on search_vector (full-text search)    │    │
│  │  - B-tree indexes on filter columns                 │    │
│  └─────────────────────────────────────────────────────┘    │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐    │
│  │  User Tables (accounts, overrides, custom items)    │    │
│  └─────────────────────────────────────────────────────┘    │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐    │
│  │  Premium Tables (tags, lists, journal entries)      │    │
│  └─────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────┘

          ┌──────────────────┐        ┌──────────────────┐
          │   Stripe API     │        │   Sentry         │
          │   (Webhooks)     │        │   (Monitoring)   │
          └──────────────────┘        └──────────────────┘
```

---

## Performance Characteristics

### Search Performance
- **Cold query (no cache):** <1 second for filtered search across 400K items
- **Warm query (cached):** <100ms for repeated searches
- **Concurrent users:** Handles 13+ simultaneous filter parameters without degradation

### Database Metrics
- **Total records:** 400,000+ food items (USDA FoodData Central)
- **Query optimization:** GIN indexes reduce full-text search from 5-10s → <1s (80% improvement)
- **Data ingestion:** Bulk import pipeline processes 400K records in <15 minutes

### User Experience
- **Page load time:** <2 seconds (Cloudflare edge caching)
- **API response time:** <800ms for autocomplete suggestions
- **Barcode scanning:** Real-time detection with <800ms lookup latency

---

## Key Technical Challenges Solved

### Challenge 1: Search Performance at Scale
**Problem:** Full-text search across 400K items was taking 5-10 seconds with basic PostgreSQL queries.

**Solution:**
- Implemented GIN (Generalized Inverted Index) on custom SearchVector field
- Materialized views for expensive aggregations
- Result: 80% latency reduction (<1s queries)

### Challenge 2: Dynamic Cost Calculations
**Problem:** Each user sets their own prices, requiring per-user cost-per-nutrient calculations that were killing performance.

**Solution:**
- Django ORM F() expressions for database-level calculations
- Avoided N+1 query problems with select_related and prefetch_related
- Cached expensive computations in database with periodic updates
- Result: Real-time ranking without performance degradation

### Challenge 3: Data Quality & Accuracy
**Problem:** USDA data contains errors, inconsistencies, and missing values.

**Solution:**
- User override system (shadow table architecture)
- Custom item creation with full feature parity
- Programmatic validation using Pint library for unit conversions
- Result: Users can fix bad data without corrupting source

### Challenge 4: Stripe Integration Reliability
**Problem:** Payment webhooks can fail, retry, or arrive out-of-order, causing subscription status inconsistencies.

**Solution:**
- Idempotent webhook handlers with database-level uniqueness constraints
- Automatic retry logic with exponential backoff
- Manual reconciliation tools for admin intervention
- Result: 99.9%+ webhook processing success rate

---

## Future Roadmap

### Infrastructure Improvements
- Migration to AWS (ECS + RDS) for enhanced scalability
- Redis caching layer for frequently accessed data
- CDN optimization for image delivery

### Feature Enhancements
- Mobile native app (React Native)
- Meal planning with optimization algorithms
- Recipe database with cost-per-serving calculations
- Social features (share lists, compare with friends)

### Data Expansion
- Restaurant menu data integration
- Real-time price tracking via web scraping
- International food database expansion

---

## About This Project

ProteinPerDollar.com is a project focused on solving a real problem: optimizing food budgets while maintaining nutritional goals. The platform combines data engineering, full-stack web development, and UX design to create a tool that helps users make smarter food purchasing decisions.

**Production URL:** [https://proteinperdollar.com](https://proteinperdollar.com)

---

## Contact

**Mert Isik**
- Email: [mertisik329@gmail.com](mailto:mertisik329@gmail.com)
- LinkedIn: [linkedin.com/in/mert-c-isik](https://linkedin.com/in/mert-c-isik)
- GitHub: [@packageIncoming](https://github.com/packageIncoming)

---

**Built with Django, PostgreSQL, and a focus on performance optimization for large-scale data processing.**
