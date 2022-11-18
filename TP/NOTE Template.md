---
created: <% tp.file.creation_date("dddd DD.MM.YYYY, HH:mm") %>
cssclass:
aliases:
tags:
---
###### `=this.file.path`
###### `=dateformat(this.file.mtime, "DDDD, HH:mm")`
---
<% tp.file.rename(tp.date.now("YYYY MM DD HHmm SS")) -%>
