---
created: <% tp.file.creation_date("dddd DD.MM.YYYY, HH:mm") %>
cssclass:
aliases:
<%*
let pathD = "CALENDAR/DAYS/";
let pathW = "CALENDAR/WEEKS/";
let pathM = "CALENDAR/MONTHS/";
let pathQ = "CALENDAR/QUARTERS/";
let pathY = "CALENDAR/YEARS/";

let fDate = "MM/DD/YYYY";
let fDateShort = "MM/DD";
let fDateLong = "dddd, MMMM D, YYYY";
let fDateISO = "YYYY-MM-DD";

let fDay = "D";
let fDayWeek = "d";
let fDayMonth = "DD";
let fDayYear = "DDD";
let fDayShort = "dd";
let fDayLong = "dddd";
let fDayFull = "YYYY MM DD";

let fWeek = "[W]WW";
let fWeekShort = "W";
let fWeekLong = "[Week ]WW";
let fWeekFull = "GGGG [W]WW";

let fMonth = "MM";
let fMonthLong = "MMMM";
let fMonthFull = "YYYY MM";

let fQuarter = "[Q]Q";
let fQuarterLong = "Q[. Quarter]";
let fQuarterFull = "YYYY [Q]Q";

let fYear = "YYYY";

let m = moment(tp.file.title, fMonthFull);

let year = m.format(fYear);
let yearLink = pathY + year;

let quarter = m.format(fQuarter);
let quarterLink = pathQ + m.format(fQuarterFull);
let quarterLong = m.format(fQuarterLong);

let month = m.format(fMonth);
let monthLink = pathM + m.format(fMonthFull);
let monthLong = m.format(fMonthLong);

let mPrev = moment(m).subtract(1, "months");
let mNext = moment(m).add(1, "months");
let monthPrev = mPrev.format(fMonth);
let monthNext = mNext.format(fMonth);
let monthPrevLink = pathM + mPrev.format(fMonthFull);
let monthNextLink = pathM + mNext.format(fMonthFull);

let mStart = moment(m).startOf("month");
let mEnd = moment(m).endOf("month");

let dateFirst = mStart.format(fDateShort);
let dateFirstLink = pathD + mStart.format(fDayFull);
let dateBefore = mStart.subtract(1, "days").format("YYYY-MM-DD");

let dateLast = mEnd.format(fDateShort);
let dateLastLink = pathD + mEnd.format(fDayFull);
let dateAfter = mEnd.add(1, "days").format("YYYY-MM-DD");

let mDays = mEnd.diff(mStart, "days");
let mWeeks = [];
let monthWeekLinks = "";
for (let i = 0; i <= mDays; i++) {
  let mDay = moment(mStart).add(i, "days");
  let mWeek = mDay.format(fWeek);
  if (mWeeks.indexOf(mWeek) === -1) {
    mWeeks.push(mWeek);
    monthWeekLinks += "[[" + pathW + mDay.format(fWeekFull) + "|" + mWeek + "]] ";
  }
};
-%>
---
###### `=this.file.path`
###### `=dateformat(this.file.mtime, "DDDD, HH:mm")`
# <% monthLong %> <% year %> [[<% monthPrevLink %>|<]] [[<% monthNextLink %>|>]]
[[<% dateFirstLink %>|<% dateFirst %>]] [[<% dateLastLink %>|<% dateLast %>]] [[<% quarterLink %>|<% quarter %>]] [[<% yearLink %>|<% year %>]]
<% monthWeekLinks %>

---

## NEW
## Achieved, recognized, decided
## Done

```tasks
done after <% dateBefore %>
done before <% dateAfter %>
```

## To-Do

Due this month
```tasks
not done
is not recurring
due after <% dateBefore %>
due before <% dateAfter %>
```

Scheduled this month
```tasks
not done
is not recurring
scheduled after <% dateBefore %>
scheduled before <% dateAfter %>
```

Recurring this month
```tasks
not done
is recurring
due after <% dateBefore %>
due before <% dateAfter %>
```

Backlog this month
```tasks
not done
happens before <% dateBefore %>
```

Someday
```tasks
not done
no due date
no scheduled date
no start date
```
