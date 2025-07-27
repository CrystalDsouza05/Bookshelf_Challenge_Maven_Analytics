# 📚 Goodreads Book Explorer Dashboard

An interactive Power BI dashboard built for the **Maven Analytics Bookshelf Challenge**.  
The goal: **Help users discover their ideal summer reads** through an intuitive and insightful book browsing experience using Goodreads data.

---

## 🚀 Project Objective

To design a data exploration tool that allows users to search and filter books based on their preferences—genres, ratings, reviews, and more—just like a custom search engine for books.

---

## 📊 Dataset Overview

The dataset includes:
- **13,000+ books**
- **1 million+ reviews**
- Book metadata (author, genre, publication year, ratings)
- Review counts and text reviews

---

## 🧠 Key DAX Measures

```DAX
-- Total Books
Total Books = CALCULATE(DISTINCTCOUNT(goodreads_works[work_id]))

-- Total Reviews
Total Reviews = SUM(goodreads_works[reviews_count])

-- Text Reviews
Text Reviews = SUM(goodreads_works[text_reviews_count])

-- Average Rating
Average Rating = AVERAGE(goodreads_works[avg_rating])

-- Concatenated Genres for a Book
Concatenated Genres =
VAR SelectedWorkID = SELECTEDVALUE(goodreads_works[work_id])
RETURN
CALCULATE(
    CONCATENATEX(
        VALUES(goodreads_works[genres]),
        goodreads_works[genres],
        " | "
    ),
    goodreads_works[work_id] = SelectedWorkID
)

-- Top Rated Book Description
Top Rated Book Description =
VAR TopBook =
    TOPN(
        1,
        ADDCOLUMNS(
            goodreads_works,
            "AvgRating", goodreads_works[avg_rating]
        ),
        [AvgRating],
        DESC
    )
RETURN
    CONCATENATEX(
        TopBook,
        goodreads_works[description],
        ""
    )
```

---

## 🛠 Tools Used

- **Power BI**: Core platform for data visualization  
- **DAX**: Custom measures and logic  
- **Excel**: Initial data prep and exploration  
- **Data Modeling**: Building relationships between tables  
- **Figma**: Layout planning and background designs  
- **PowerPoint**: Dashboard design elements  
- **Tooltips**: Added book insights and details  
- **Slicers**: Genre based slicers

---

## 🙏 Acknowledgment

Big thanks to **[Maven Analytics](https://www.mavenanalytics.io/)** for this engaging and brain-teasing challenge! It helped me build something truly interactive, and I explored search functionalities in Power BI for the very first time!

---

## 📎 Preview

Page 1:
<img width="1280" height="737" alt="Home Page" src="https://github.com/user-attachments/assets/41e240fb-39f5-4b9d-95d5-8dda4bcc689a" />

Page 2:
<img width="1280" height="737" alt="Main Page" src="https://github.com/user-attachments/assets/471eb375-3c3d-4837-9590-beb19064c31e" />

Page 3:
<img width="1280" height="738" alt="Search Engine" src="https://github.com/user-attachments/assets/ec655671-094d-42e8-8804-0368bdfc4040" />

ToolTip 1:
<img width="1282" height="720" alt="image" src="https://github.com/user-attachments/assets/06c2e54f-7429-4214-949a-f1b8883ec76a" />

ToolTip 2:
<img width="1277" height="715" alt="image" src="https://github.com/user-attachments/assets/249f22fa-9f69-4c0f-a296-728ab1cd8db5" />
