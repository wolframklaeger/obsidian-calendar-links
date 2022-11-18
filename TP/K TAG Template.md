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

let m = moment(tp.file.title);

let day = m.format(fDate);
let dayDate = m.format(fDateLong);
let dayLink = pathD + m.format(fDayFull);

let prev = moment(m).subtract(1, "days");
let prevDay = prev.format(fDate);
let prevDayLink = pathD + prev.format(fDayFull);

let next = moment(m).add(1, "days");
let nextDay = next.format(fDate);
let nextDayLink = pathD + next.format(fDayFull);

let week = m.format(fWeek);
let weekLink = pathW + m.format(fWeekFull);

let month = m.format(fMonth);
let monthLink = pathM + m.format(fMonthFull);
let monthLong = m.format(fMonthLong);

let quarter = m.format(fQuarter);
let quarterLink = pathQ + m.format(fQuarterFull);

let year = m.format(fYear);
let yearLink = pathY + year;
-%>
---
###### `=this.file.path`
###### `=dateformat(this.file.mtime, "DDDD, HH:mm")`
# <% dayDate %> [[<% prevDayLink %>|<]] [[<% nextDayLink %>|>]]
[[<% weekLink %>|<% week %> (<% m.format(fDayYear) %>)]] [[<% monthLink %>|<% monthLong %> (<% month %>)]] [[<% quarterLink %>|<% quarter %>]] [[<% yearLink %>|<% year %>]]

---

## NEU
## Erreicht, erkannt, entschieden
## Erledigt

```tasks
# done today, from filename
done on <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY MM DD") %>
```

## To-Do

==Heute fällig (due)==
```tasks
not done
is not recurring
# due today, from filename
due on <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY MM DD") %>
hide due date
```

==Heute geplant (scheduled)==
```tasks
not done
is not recurring
# scheduled today, from filename
scheduled on <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY MM DD") %>
hide scheduled date
```

==Heute Routine (recurring)==
```tasks
not done
is recurring
# happens today, from filename
happens on <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY MM DD") %>
```

==Bis heute nicht erledigt (backlog)==
```tasks
not done
# happens before today, from filename
happens before <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY MM DD") %>
hide edit button
```

==Ohne Datum==
```tasks
not done
no due date
no scheduled date
no start date
```
