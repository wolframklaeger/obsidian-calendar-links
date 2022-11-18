---
created: <% tp.file.creation_date("dddd DD.MM.YYYY, HH:mm") %>
cssclass:
aliases:
<%*
let pathD = "KALENDER/TAGE/";
let pathW = "KALENDER/WOCHEN/";
let pathM = "KALENDER/MONATE/";
let pathQ = "KALENDER/QUARTALE/";
let pathY = "KALENDER/JAHRE/";

let fDate = "DD.MM.YYYY";
let fDateShort = "DD.MM.";
let fDateLong = "dddd, D. MMMM YYYY";
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
let fWeekLong = "[Woche ]WW";
let fWeekFull = "GGGG [W]WW";

let fMonth = "MM";
let fMonthLong = "MMMM";
let fMonthFull = "YYYY MM";

let fQuarter = "[Q]Q";
let fQuarterLong = "Q[. Quartal]";
let fQuarterFull = "YYYY [Q]Q";

let fYear = "YYYY";

let m = moment(tp.file.title, fQuarterFull);

let year = m.format(fYear);
let yearLink = pathY + year;

let quarter = m.format(fQuarter);
let quarterLink = pathQ + m.format(fQuarterFull);
let quarterLong = m.format(fQuarterLong);

let qMonthLinks = "";

let m1Short = m.format(fMonth);
let m1Long = m.format(fMonthLong);
let m1Link = pathM + m.format(fMonthFull);

qMonthLinks += "[[" + m1Link + "|" + m1Long + " (" + m1Short + ")]] ";

let m2 = moment(m).add(1, "months");
let m2Short = m2.format(fMonth);
let m2Long = m2.format(fMonthLong);
let m2Link = pathM + m2.format(fMonthFull);

qMonthLinks += "[[" + m2Link + "|" + m2Long + " (" + m2Short + ")]] ";

let m3 = moment(m).add(2, "months");
let m3Short = m3.format(fMonth);
let m3Long = m3.format(fMonthLong);
let m3Link = pathM + m3.format(fMonthFull);

qMonthLinks += "[[" + m3Link + "|" + m3Long + " (" + m3Short + ")]]";

let qPrev = moment(m).add(-1, "quarters");
let qNext = moment(m).add(1, "quarters");
let quarterPrev = qPrev.format(fQuarter);
let quarterNext = qNext.format(fQuarter);
let quarterPrevLink = pathQ + qPrev.format(fQuarterFull);
let quarterNextLink = pathQ + qNext.format(fQuarterFull);

let qWeeks = [];
let qWeekLinks = "";
let qStart = moment(m).startOf("quarter");
let qEnd = moment(m).endOf("quarter");

let dateBefore = qStart.subtract(1, "days").format("YYYY-MM-DD");

let dateAfter = qEnd.add(1, "days").format("YYYY-MM-DD");

let n = qEnd.diff(qStart, "weeks");

for (let i = 0; i <= n; i++) {
  let w = moment(qStart).add(i, "weeks");
  let qWeek = w.format(fWeekShort);
  if (qWeeks.indexOf(qWeek) === -1) {
    qWeeks.push(qWeek);
    qWeekLinks += "[[" + pathW + w.format(fWeekFull) + "|" + qWeek + "]] ";
  }
};
-%>
---
###### `=this.file.path`
###### `=dateformat(this.file.mtime, "DDDD, HH:mm")`
# <% quarterLong %> <% year %> (<% quarter %>) [[<% quarterPrevLink %>|<]] [[<% quarterNextLink %>|>]]
<% qMonthLinks %> [[<% yearLink %>|<% year %>]]
<% qWeekLinks %>

---

## NEU
## Erreicht, erkannt, entschieden
## Erledigt

```tasks
done after <% dateBefore %>
done before <% dateAfter %>
```

## To-Do

==In diesem Quartal fällig (due)==
```tasks
not done
is not recurring
due after <% dateBefore %>
due before <% dateAfter %>
```

==In diesem Monat geplant (scheduled)==
```tasks
not done
is not recurring
scheduled after <% dateBefore %>
scheduled before <% dateAfter %>
```

==In diesem Monat Routine (recurring)==
```tasks
not done
is recurring
due after <% dateBefore %>
due before <% dateAfter %>
```

==Bis Anfang dieses Monats **nicht erledigt** (backlog)==
```tasks
not done
happens before <% dateBefore %>
```

==Ohne Datum==
```tasks
not done
no due date
no scheduled date
no start date
```
