B2B Supply Chain Command Center - Power BI
🚀 Project Overview
This project is an advanced, end-to-end business intelligence solution designed to simulate a B2B Supply Chain Command Center. The goal was to build a comprehensive analytics tool for a mock industrial equipment company, providing deep insights into sales performance, supplier efficiency, customer behavior, and logistics.

The solution was built entirely in the Power BI ecosystem and demonstrates skills equivalent to a BI Developer with 3-5 years of experience. It moves beyond simple visualization to incorporate a professional star schema data model, advanced DAX calculations, enterprise-level security (RLS), interactive drill-through capabilities, and a pixel-perfect paginated report for operational exports.

📊 Dashboard Preview
The final report is a multi-page application that provides a seamless user experience, from a high-level executive overview to a detailed supplier analysis. The design focuses on a clean, professional UI with a clear visual hierarchy and interactive elements.

🛠️ Key Features & Technical Implementation
Star Schema Data Model: Transformed the initial flat CSV file into a robust and high-performance star schema in Power Query, with a central FactOrders table and multiple dimension tables (DimDate, DimSupplier, DimProduct, etc.). This professional data model is the foundation for all efficient analysis.

Advanced DAX Calculations: Authored over 15 DAX measures, including complex time intelligence (YoY Revenue Growth %), dynamic "What-If" parameters (On-Time Delivery %), and ranking functions (RANKX) to provide deep, actionable business insights.

Interactive "What-If" Analysis: Implemented a numeric parameter to allow users to dynamically set the "On-Time Delivery Target," instantly seeing the impact on performance KPIs.

Strategic Quadrant Analysis: The Executive Overview features a scatter plot with dynamic average lines, segmenting suppliers into four strategic quadrants (e.g., Stars, Underperformers) based on revenue and profit margin.

Row-Level Security (RLS): Implemented a "Supplier Manager" role that restricts data visibility, ensuring a user can only see the data for their assigned supplier. This demonstrates a key enterprise governance skill.

Drill-Through Functionality: Created a detailed, hidden Supplier Detail page. Users can right-click any supplier in a visual and drill through to this page for a focused deep-dive analysis.

Paginated Reporting: Developed a pixel-perfect, printable Supplier Performance Report using Power BI Report Builder. This operational report is connected live to the Power BI dataset and includes parameters for dynamic filtering.

Advanced UI/UX: Designed a custom, multi-page report with a collapsible filter pane using bookmarks and selection groups, creating a seamless and application-like user experience.

🧱 Architecture & Data Flow
The project follows a best-practice BI architecture, all within the Power BI environment.

Data Source (CSV) -> Power Query (ETL & Star Schema) -> Power BI Data Model (DAX & Relationships) -> Interactive Dashboard -> Paginated Report

🧮 Sample DAX Measures
Below are examples of the professional-grade DAX used in this project, featuring variables, robust error handling, and advanced analytical patterns.

YoY Revenue Growth % (for Latest Year):

YoY Revenue Growth % (Latest Year) = 
CALCULATE(
    [YoY Revenue Growth %],
    FILTER(
        ALL(DimDate[Year]),
        DimDate[Year] = [_Latest Year With Sales]
    )
)

Dynamic On-Time Delivery %:

On-Time Delivery % = 
VAR TargetLeadTime = 'On-Time Delivery Target'[On-Time Delivery Target Value]
VAR OnTimeAndDeliveredOrders =
    CALCULATE(
        COUNTROWS(FactOrders),
        FILTER(
            FactOrders,
            FactOrders[LeadTimeDays] <= TargetLeadTime &&
            TRIM(UPPER(FactOrders[Status])) = "DELIVERED" 
        )
    )
VAR TotalDeliveredOrders =
    CALCULATE(
        COUNTROWS(FactOrders),
        TRIM(UPPER(FactOrders[Status])) = "DELIVERED"
    )
RETURN
    DIVIDE(OnTimeAndDeliveredOrders, TotalDeliveredOrders)

🔧 How to View This Project
Explore the Data Model: The Power BI file (.pbix) contains the complete data model, including all Power Query transformations and DAX measures.

View the Interactive Dashboard: The project is best viewed by downloading the .pbix file and opening it with Power BI Desktop to experience the full interactivity, including the collapsible filter pane and drill-through features.

Data Source: The project uses a B2B Supply Chain dataset. The raw data is included in this repository for replication purposes.

✍️ Author
Rushikesh Bedre

Portfolio: rushibedre.github.io

LinkedIn: linkedin.com/in/rushikesh-bedre

GitHub: github.com/rushibedre
