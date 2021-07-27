I am a full-stack developer and have worked as an "analyst" programmer for the last 20 years—with the "analyst" part, I do real problem-solving.  I have always liked solving problems, and programming became my favorite tool that brought my solutions to life.

And programming goes hand to hand with data. After working on a huge and variety of applications, I wanted to play with the data and unearth hidden things. Of course, back then, there were no modern AI, data science, machine learning technologies, or services to speak of. I created OLAP cubes, wrote mind-boggling MDX queries, and waited patiently for our local servers to generate the result. Then, the cloud only meant the thing in the sky, and when an algorithm is mentioned, it only meant another quick sorting logic :)

I have begun my journey to formal data science around 2019 with Microsoft Professional Data Science Certificate Program.

# Programming Experience

## Infini CRM & Infini SCM
Web based CRM application tailored for pharma companies.

### *Technologies used* ###
* SQL Server Database Engine
* SQL Server Analysis Services
* SQL Server Reporting Services
* ASP.NET MVC
* JavaScript
* Ext.JS

```SQL
; with
Store(Date, IsWorkDay, RespUnitId, OwnerCardId,
  PlannedVisitCount, RealizedVisitCount, RealizedVisitCountDr,
  RealizedVisitCountPh, VisitCount, VisitCountDr, VisitCountPh,
  ActivityCount, PlannedRealizedVisitCount)
as
(
  select cd.Date, cd.IsWorkDay, mi.RespUnitId, min(mi.CardId) as OwnerCardId,
    sum(case when ap.IsVisitType = 1 and ap.IsPlanned = 1 then 1 else 0 end),
    sum(case when ap.IsVisitType = 1 and ap.IsRealized = 1 then 1 else 0 end),
    sum(case when ap.IsVisitType = 1 and ap.IsRealized = 1 and c.CardTypeId = @CardType_Doctor then 1 else 0 end),
    sum(case when ap.IsVisitType = 1 and ap.IsRealized = 1 and c.CardTypeId <> @CardType_Doctor then 1 else 0 end),
    sum(case when ap.IsVisitType = 1 then 1 else 0 end),
    sum(case when ap.IsVisitType = 1 and c.CardTypeId = @CardType_Doctor then 1 else 0 end),
    sum(case when ap.IsVisitType = 1 and c.CardTypeId <> @CardType_Doctor then 1 else 0 end),
    sum(case when ap.IsVisitType = 0 and ap.IsRealized = 1 then 1 else 0 end),
    sum(case when ap.IsVisitType = 1 and ap.IsPlanned = 1 and ap.IsRealized = 1 then 1 else 0 end)
  from
    @MsrInfo mi
    cross join (select Date, IsWorkDay from dbo.CalendarDate where Date between @SelectedPeriod and @EndDate) as cd
    left join dbo.ActivityPlan ap on ap.Date = cd.Date and ap.OwnerCardId = mi.CardId and ap.Id = ap.RefId
    left join dbo.Card c on c.Id = ap.CardId
  group by cd.Date, cd.IsWorkDay, mi.RespUnitId
),
YtdVisit(OwnerCardId, PlannedVisitCountYtd, PlannedVisitCountYtdDr,
  PlannedVisitCountYtdPh, RealizedVisitCountYtd, RealizedVisitCountYtdDr,
  RealizedVisitCountYtdPh, PlannedRealizedVisitCountYtd)
as
(
  select
    ap.OwnerCardId,
    sum(case when ap.IsPlanned = 1 then 1 else 0 end),
    sum(case when ap.IsPlanned = 1 and c.CardTypeId = @CardType_Doctor then 1 else 0 end),
    sum(case when ap.IsPlanned = 1 and c.CardTypeId <> @CardType_Doctor then 1 else 0 end),
...
```

![Infini Sample Analysis](/programming/images/infini_01.png)

## Machining Studio
A simulation application tailored for machine tooling (CNC) operations.
### *Technologies used* ###
* SQL Compact
* .NET
* WPF (Windows Presentation Foundation)
* MEF (Managed Extensibility Framework)

![Broaching Tool](/programming/images/machining_studio_01.png)

![Milling Process Simulation](/programming/images/machining_studio_02.png)

![BOSS BaseAnalysis sample code](/programming/code_samples/Boss.Base.BaseAnalysis.png)

## MedIX
A custom application for MedIX (Hospital Information System application), that can work like a mediator between any laboratory machine (communicating with them through RS232 port) and MedIX in order to send MedIX laboratory orders to machines and then to get results from machines to MedIX.
### *Technologies used* ###
* .NET
* Oracle DB
* Windows Services

## Cerebrum ERP & CDS Data Analysis Tool
Client/Server architecture ERP application with a included cost accounting, integrated manufacturing modules.
### *Technologies used* ###
* SQL Server
* Analysis Services / OLAP
* Object Pascal
* Delphi


![CDS Sample Screen](/programming/images/cds_01.png)

# Data Analysis

And programming goes hand to hand with data. After working on a huge and variety of applications, I wanted to play with the data and unearth hidden things. Of course, back then, there were no modern AI, data science, machine learning technologies, or services to speak of. I created OLAP cubes, wrote mind-boggling MDX queries, and waited patiently for our local servers to generate the result. Then, the cloud only meant the thing in the sky, and when an algorithm is mentioned, it only meant another quick sorting logic :)

I have begun my journey to formal data science around 2019 with Microsoft Professional Data Science Certificate Program. However, since I did not switch careers from programming to data engineer, I continued to improve my data science knowledge by taking other online programs, and I learned a lot :)

Here are some of the projects and files that are the outputs of my education:

1. *A descriptive analysis with Jupyter Notebook*: [Green Energy Analysis](data_science/jupyter/green_energy/Green Energy Analysis.html)

Visual Analysis with Power BI
1. *Manitoba-Quebec-Ontario Crime Analysis, 2009-2019*
<img src="data_science/powerbi/crime_report/images/crime_report.png" style="width:200px;"/>
2. [Canadian Community Health Survey - Smoking Analysis, 2015-2019] 
<img src="data_science/powerbi/cchs/images/cchs_smoking_01.png" style="width:200px;"/>
<img src="data_science/powerbi/cchs/images/cchs_smoking_02.png" style="width:200px;"/>
