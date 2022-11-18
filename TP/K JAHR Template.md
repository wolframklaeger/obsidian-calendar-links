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

let m = moment(tp.file.title, fYear);

let year = m.format(fYear);
let yearLink = pathY + year;

let q2 = moment(m).add(1, "quarters");
let q3 = moment(m).add(2, "quarters");
let q4 = moment(m).add(3, "quarters");

let q1Link = pathQ + m.format(fQuarterFull);
let q2Link = pathQ + q2.format(fQuarterFull);
let q3Link = pathQ + q3.format(fQuarterFull);
let q4Link = pathQ + q4.format(fQuarterFull);

let q1Long = m.format(fQuarterLong) + " " + m.format(fQuarter);
let q2Long = q2.format(fQuarterLong) + " " + q2.format(fQuarter);
let q3Long = q3.format(fQuarterLong) + " " + q3.format(fQuarter);
let q4Long = q4.format(fQuarterLong) + " " + q4.format(fQuarter);

let m1 = m;
let m2 = moment(m).add(1, "months");
let m3 = moment(m).add(2, "months");
let m4 = moment(m).add(3, "months");
let m5 = moment(m).add(4, "months");
let m6 = moment(m).add(5, "months");
let m7 = moment(m).add(6, "months");
let m8 = moment(m).add(7, "months");
let m9 = moment(m).add(8, "months");
let m10 = moment(m).add(9, "months");
let m11 = moment(m).add(10, "months");
let m12 = moment(m).add(11, "months");

let m1Link = pathM + m1.format(fMonthFull);
let m2Link = pathM + m2.format(fMonthFull);
let m3Link = pathM + m3.format(fMonthFull);
let m4Link = pathM + m4.format(fMonthFull);
let m5Link = pathM + m5.format(fMonthFull);
let m6Link = pathM + m6.format(fMonthFull);
let m7Link = pathM + m7.format(fMonthFull);
let m8Link = pathM + m8.format(fMonthFull);
let m9Link = pathM + m9.format(fMonthFull);
let m10Link = pathM + m10.format(fMonthFull);
let m11Link = pathM + m11.format(fMonthFull);
let m12Link = pathM + m12.format(fMonthFull);

let m1Long = m1.format(fMonthLong);
let m2Long = m2.format(fMonthLong);
let m3Long = m3.format(fMonthLong);
let m4Long = m4.format(fMonthLong);
let m5Long = m5.format(fMonthLong);
let m6Long = m6.format(fMonthLong);
let m7Long = m7.format(fMonthLong);
let m8Long = m8.format(fMonthLong);
let m9Long = m9.format(fMonthLong);
let m10Long = m10.format(fMonthLong);
let m11Long = m11.format(fMonthLong);
let m12Long = m12.format(fMonthLong);

let m1Short = m1.format(fMonth);
let m2Short = m2.format(fMonth);
let m3Short = m3.format(fMonth);
let m4Short = m4.format(fMonth);
let m5Short = m5.format(fMonth);
let m6Short = m6.format(fMonth);
let m7Short = m7.format(fMonth);
let m8Short = m8.format(fMonth);
let m9Short = m9.format(fMonth);
let m10Short = m10.format(fMonth);
let m11Short = m11.format(fMonth);
let m12Short = m12.format(fMonth);

let yPrev = moment(m).subtract(1, "years");
let yNext = moment(m).add(1, "years");
let yearPrev = yPrev.format(fYear);
let yearNext = yNext.format(fYear);
let yearPrevLink = pathY + yPrev.format(fYear);
let yearNextLink = pathY + yNext.format(fYear);

let dateBefore = yearPrev + "-12-31";
let dateAfter = yearNext + "-01-01";
-%>
---
###### `=this.file.path`
###### `=dateformat(this.file.mtime, "DDDD, HH:mm")`
# <% year %> [[<% yearPrevLink %>|<]] [[<% yearNextLink %>|>]]
[[<% q1Link %>|<% q1Long %>]] [[<% m1Link %>|<% m1Long %> (<% m1Short %>)]] [[<% m2Link %>|<% m2Long %> (<% m2Short %>)]] [[<% m3Link %>|<% m3Long %> (<% m3Short %>)]]
[[<% q2Link %>|<% q2Long %>]] [[<% m4Link %>|<% m4Long %> (<% m4Short %>)]] [[<% m5Link %>|<% m5Long %> (<% m5Short %>)]] [[<% m6Link %>|<% m6Long %> (<% m6Short %>)]]
[[<% q3Link %>|<% q3Long %>]] [[<% m7Link %>|<% m7Long %> (<% m7Short %>)]] [[<% m8Link %>|<% m8Long %> (<% m8Short %>)]] [[<% m9Link %>|<% m9Long %> (<% m9Short %>)]]
[[<% q4Link %>|<% q4Long %>]] [[<% m10Link %>|<% m10Long %> (<% m10Short %>)]] [[<% m11Link %>|<% m11Long %> (<% m11Short %>)]] [[<% m12Link %>|<% m12Long %> (<% m12Short %>)]]

---

## NEU
## Erreicht, erkannt, entschieden
## Erledigt

```tasks
done after <% dateBefore %>
done before <% dateAfter %>
```

## To-Do

==In diesem Jahr fällig (due)==
```tasks
not done
is not recurring
due after <% dateBefore %>
due before <% dateAfter %>
```

==In diesem Jahr geplant (scheduled)==
```tasks
not done
is not recurring
scheduled after <% dateBefore %>
scheduled before <% dateAfter %>
```

==In diesem Jahr Routine (recurring)==
```tasks
not done
is recurring
due after <% dateBefore %>
due before <% dateAfter %>
```

==Bis Anfang dieses Jahres nicht erledigt (backlog)==
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

