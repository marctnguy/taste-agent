# Sector Research — Social Film Discovery & Cultural Recommendation

**Company:** Letterboxd  
**Sector:** Social film discovery / entertainment technology  
**Project:** Taste Agent for Letterboxd  
**Research stage:** Capstone Round 1

---

## 1. Research Purpose

This research examines the sector in which Letterboxd operates and the conditions that make AI-powered taste modelling a relevant opportunity.

The objective is not to estimate the total streaming or entertainment market. Letterboxd does not operate primarily as a streaming service.

Instead, the relevant sector sits at the intersection of:

- film discovery
- social media
- cultural logging and reviewing
- recommendation systems
- subscription-supported digital communities

The research focuses on three questions:

1. What differentiates Letterboxd from conventional entertainment platforms?
2. What data and user behaviours could support AI-powered discovery?
3. Where could semantic and cross-media taste intelligence create additional product value?

---

# 2. Sector Context

Digital film discovery is distributed across several types of products.

Streaming platforms such as Netflix, Disney+ and Prime Video recommend content primarily within their own catalogues.

Film databases such as IMDb provide structured information about films, casts, crews and ratings.

Social platforms enable discussion and cultural discovery but are not primarily designed around structured film consumption.

Letterboxd occupies a different position: it combines film discovery with social interaction and explicit cultural logging.

Users can:

- mark films as watched
- rate films
- create diary entries
- write reviews
- create lists
- maintain watchlists
- follow other members
- interact with other film viewers

This creates a dataset that represents not only what content exists, but how individual users interact with and evaluate it.

For an AI recommendation system, this distinction is important.

A user's Letterboxd history can contain explicit preference signals such as ratings alongside behavioural signals such as repeated engagement, watchlist activity and reviewing.

---

# 3. Letterboxd's Growth

Letterboxd has experienced substantial user growth.

According to Tiny's 2023 acquisition announcement, Letterboxd had surpassed 10 million members across more than 200 countries at the time of the acquisition.

Tiny also reported historical membership of:

- 1.8 million members in 2020
- 4.1 million members in 2021
- more than 10 million members in 2023

By Q2 2026, Tiny reported that Letterboxd had surpassed 30.7 million members.

This represented:

- 43% year-over-year growth
- 185% growth since Tiny's acquisition

The growth trajectory indicates that Letterboxd has evolved from a niche film community into a large global cultural platform.

### Membership Growth

| Period | Reported Members |
|---|---:|
| 2020 | 1.8M |
| 2021 | 4.1M |
| 2023 | 10M+ |
| Q2 2026 | 30.7M |

This growth increases the strategic importance of discovery and personalization.

As the amount of content, activity and social information available on the platform grows, helping users navigate that information becomes increasingly valuable.

---

# 4. Engagement and Data Scale

Letterboxd's value is not based only on membership size.

Its users generate a large volume of structured cultural activity.

Letterboxd's 2025 Year in Review reported:

| 2025 Activity | Volume |
|---|---:|
| Films marked watched | 898.5M |
| Ratings | 672.5M |
| Diary entries | 332.8M |
| Reviews | 143.6M |
| Lists | 12.9M |
| Comments | 11.0M |

Letterboxd also reported approximately 652 million hours of film viewing represented by activity logged during the year.

For an AI discovery product, ratings are particularly relevant because they provide an explicit preference signal associated with individual works.

A conventional content platform might know that a user watched a film.

Letterboxd can potentially know:

> The user watched this film and explicitly rated it 4.5 stars.

At scale, this creates a potentially valuable foundation for preference modelling.

---

# 5. Existing Discovery Model

Letterboxd already supports discovery through several mechanisms.

These include:

- film pages
- ratings
- reviews
- lists
- member activity
- watchlists
- social following
- search and filtering
- streaming availability
- personalized statistics for paid members

This means Taste Agent would not introduce discovery to Letterboxd.

Instead, it would attempt to introduce a different **layer of discovery**.

The distinction can be expressed as:

```text
Existing discovery
"What films are similar, popular, available or socially relevant?"

                    ↓

Semantic taste discovery
"What characteristics tend to be associated with this user's preferences?"
