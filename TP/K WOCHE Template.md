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
let fWeekLong = "[Woche ]WW";
let fWeekFull = "GGGG [W]WW";

let fMonth = "MM";
let fMonthLong = "MMMM";
let fMonthFull = "YYYY MM";

let fQuarter = "[Q]Q";
let fQuarterLong = "Q[. Quartal]";
let fQuarterFull = "YYYY [Q]Q";

let fYear = "YYYY";

let m = moment(tp.file.title, fWeekFull);

let week = m.format(fWeek);
let month = m.format(fMonth);
let quarter = m.format(fQuarter);
let year = m.format(fYear);

let weekLong = m.format(fWeekLong);
let monthLong = m.format(fMonthLong);
let quarterLong = m.format(fQuarterLong);

let mPrev = moment(m).subtract(1, "weeks");
let mNext = moment(m).add(1, "weeks");

let weekPrev = mPrev.format(fWeek);
let weekNext = mNext.format(fWeek);

let weekLink = pathW + m.format(fWeekFull);
let weekPrevLink = pathW + mPrev.format(fWeekFull);
let weekNextLink = pathW + mNext.format(fWeekFull);

let m1 = moment(m).day(1);
let m2 = moment(m).day(2);
let m3 = moment(m).day(3);
let m4 = moment(m).day(4);
let m5 = moment(m).day(5);
let m6 = moment(m).day(6);
let m7 = moment(m).day(7);

let d1 = m1.format(fDayShort);
let d2 = m2.format(fDayShort);
let d3 = m3.format(fDayShort);
let d4 = m4.format(fDayShort);
let d5 = m5.format(fDayShort);
let d6 = m6.format(fDayShort);
let d7 = m7.format(fDayShort);

let d1Link = pathD + m1.format(fDayFull);
let d2Link = pathD + m2.format(fDayFull);
let d3Link = pathD + m3.format(fDayFull);
let d4Link = pathD + m4.format(fDayFull);
let d5Link = pathD + m5.format(fDayFull);
let d6Link = pathD + m6.format(fDayFull);
let d7Link = pathD + m7.format(fDayFull);

let d1Date = m1.format(fDateShort);
let d7Date = m7.format(fDateShort);

let monthLink = pathM + m.format(fMonthFull);
let quarterLink = pathQ + m.format(fQuarterFull);
let yearLink = pathY + year;
-%>
---
###### `=this.file.path`
###### `=dateformat(this.file.mtime, "DDDD, HH:mm")`
# <% weekLong %> - <% d1Date %>-<% d7Date %>  [[<% weekPrevLink %>|<]] [[<% weekNextLink %>|>]]
[[<% monthLink %>|<% monthLong %> (<% month %>)]] [[<% quarterLink %>|<% quarter %>]] [[<% yearLink %>|<% year %>]]
[[<% d1Link %>|<% d1 %>]] [[<% d2Link %>|<% d2 %>]] [[<% d3Link %>|<% d3 %>]] [[<% d4Link %>|<% d4 %>]] [[<% d5Link %>|<% d5 %>]] [[<% d6Link %>|<% d6 %>]] [[<% d7Link %>|<% d7 %>]]

---

## NEU
## Erreicht, erkannt, entschieden
## Erledigt

```tasks
# done after last Sunday, before next Monday
# filename = ISO week of year, date = first day of week
done after <% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "GGGG [W]WW") %>
done before <% tp.date.now("YYYY-MM-DD", 7, tp.file.title, "GGGG [W]WW") %>
```

## To-Do

==In dieser Woche fällig (due)==
```tasks
not done
is not recurring
# due before next Monday
due before <% tp.date.now("YYYY-MM-DD", 7, tp.file.title, "GGGG [W]WW") %>
```

==In dieser Woche geplant (scheduled)==
```tasks
not done
is not recurring
# scheduled before next Monday
scheduled before <% tp.date.now("YYYY-MM-DD", 7, tp.file.title, "GGGG [W]WW") %>
```

==In dieser Woche Routine (recurring)==
```tasks
not done
is recurring
# happens after last Sunday, before next Monday
happens after <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "GGGG [W]WW") %>
happens before <% tp.date.now("YYYY-MM-DD", 7, tp.file.title, "GGGG [W]WW") %>
```

==Bis Anfang dieser Woche nicht erledigt (backlog)==
```tasks
not done
# happens before last Monday ??? -1 ???
happens before <% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "GGGG [W]WW") %>
```

==Ohne Datum==
```tasks
not done
no due date
no scheduled date
no start date
```
