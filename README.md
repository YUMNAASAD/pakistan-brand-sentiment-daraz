# 🇵🇰 Pakistani Social Media Content Detective: Daraz

## 1. Business Question
**"What type of social-media content gets Pakistani audiences to engage, and what should a Pakistani brand do next?"**

We acted as junior digital-marketing data scientists for the brand **Daraz** (Pakistan's largest e-commerce platform). We collected audience comments from Pakistan-region YouTube videos, measured sentiment and engagement, found patterns, and generated a data-driven marketing recommendation.

## 2. Data
- **Source:** YouTube Data API v3 (region: Pakistan)
- **Brand:** Daraz
- **Videos searched:** 419, of which the 60 most-commented Daraz-related videos were kept
- **Comments collected:** 7,939 (7,888 after cleaning)
- **Languages:** English 4,224 | Roman Urdu 3,444 | Urdu 220
- **Engagement metric:** comment likes + replies

## 3. Methodology
1. **Collection:** YouTube API (videos, statistics, comments, timestamps)
2. **Cleaning:** lowercase, URL removal, emoji-to-text, Roman Urdu spelling normalization, language detection (Urdu / Roman Urdu / English), timestamps converted to Pakistan time (PKT)
3. **Sentiment model:** multilingual transformer `cardiffnlp/twitter-xlm-roberta-base-sentiment` (positive / neutral / negative)
4. **Analysis:** engagement by content type, sentiment, hour, day, language, hashtags
5. **Complaint mining:** keyword-theme analysis on negative comments
6. **Big data processing:** PySpark used for aggregations (sentiment, language, hour, day)
7. **Recommendation:** rule-based, data-driven marketing recommendation

## 4. Results

### Sentiment distribution
| Sentiment | Comments | Share |
|---|---|---|
| Neutral | 3,518 | 45% |
| Negative | 2,661 | 34% |
| Positive | 1,709 | 22% |

### The 7 project questions
| # | Question | Finding |
|---|---|---|
| 1 | Which platform performs better? | Only YouTube was analysed (see limitations), so no cross-platform comparison was made. |
| 2 | Which content type gets more engagement? | **Medium-length videos (1-5 min)** |
| 3 | Popular topics / hashtags | #daraz (23), #shorts (13), #darazcourse (6), #business (6), #ecommerce (6) |
| 4 | What sentiment generates engagement? | **Negative** comments received the highest average engagement |
| 5 | Best time / day | **Friday, around 7:00 AM PKT** |
| 6 | Which audience segment is more responsive? | **English-language** commenters had the highest average engagement; Roman Urdu is the second-largest segment (3,444 comments) |
| 7 | What should the brand post next? | See recommendation below |

### What needs improvement? (complaint themes in negative comments)
| Theme | Negative comments |
|---|---|
| Seller / Affiliate account issues | 370 |
| Refund / Return | 195 |
| Delivery | 171 |
| App / Website | 162 |
| Customer Service | 114 |
| Price | 108 |
| Quality / Fake products | 74 |

## 5. Marketing Recommendation for Daraz
1. **Content:** Publish medium-length (1-5 min) videos, which earned the most engagement.
2. **Timing:** Post on Friday around 7:00 AM PKT.
3. **Language:** Use English plus Roman Urdu captions and replies, since these two segments make up almost all comments.
4. **Hashtags:** #daraz, #shorts, #ecommerce, #business.
5. **Fix first:** seller/affiliate account onboarding and payments, refund/return process, and delivery speed. These are the top complaint themes.
6. **Community management:** Negative comments attract the most engagement, so reply to them quickly and publicly. This can turn complaints into visible customer service.

## 6. Limitations
- **Only YouTube** was used. Free APIs for Facebook, Instagram and TikTok are not available, so platform comparison was not possible.
- Much of the data comes from **creator/affiliate-course videos**, not Daraz's official channel. This inflates the "Seller / Affiliate account" theme.
- The multilingual sentiment model is **less accurate on Roman Urdu** (code-mixing, spelling variation, sarcasm). Some comments may be mislabeled.
- Engagement is based on **comment likes + replies**, not post-level likes, shares or views.
- Complaint themes use **keyword matching**, which can miss context.
- Best hour/day reflects *when comments were posted*, not necessarily when videos were published.

## 7. Tech Stack
Python, Google Colab, YouTube Data API v3, pandas, Hugging Face Transformers (XLM-RoBERTa), matplotlib, PySpark

## 8. Files
- `daraz_sentiment_project.ipynb`: full notebook (code and outputs, including all charts)
- `final_data.csv`: cleaned dataset with sentiment labels

## 9. 
- Yumna Asad
- f2024376191
- Course: Big Data Analytics
