---
<%*
// Sets date based on title of file
let date = moment(tp.file.title, "[Day ] DDD - dddd MMMM Do YYYY");

let daily = {link: "[The Journal/Daily]/YYYY/MMMM/[Day ] DDD, dddd MMMM Do, YYYY", display: "ddd DD"};
let weekly = {link: "[The Journal/Weekly]/YYYY/[Week ] w (YYYY-MM-DD)", display: "[Week ] w"};
let monthly = {link: "[The Journal/Monthly]/YYYY-MMMM", display: "MMM"};
let quarterly = {link: "[The Journal/Quarterly]/YYYY-[Q]Q", display: "[Q]Q"};
let yearly = {link: "[The Journal/Yearly]/YYYY", display: "YYYY"};
-%>
banner_y: 0.4
banner: "![[<% date.format("MMMM") %> Banner.jpg]]"
type: Journal
scope: The Daily
title:
aliases: 
created: 
modified: 
obsidianUIMode: preview
obsidianEditingMode: source
tags: 
---

# ☀ <% date.format("[Day ] DDD - dddd MMMM Do YYYY") %> 

<%*
// Current year link|display
tR += `##### [[${date.format(yearly.link)}| ↵ ${date.format(yearly.display)}]]`;

// Current month link|display
tR += ` [[${date.format(monthly.link)}| ◎ ${date.format(monthly.display)}]] `;

// Current quarter link|display
tR += `[[${date.format(quarterly.link)}| ◆ ${date.format(quarterly.display)} ◆  ]] `;

// Add 1 month
let nextMonth = date.clone().add(1, "month");

// Next month link|display
tR += `[[${nextMonth.format(monthly.link)}| ${nextMonth.format(monthly.display)} ◎ ]] `;

// Add 1 year
let nextYear = date.clone().add(1, "year");

// Next year link|display
tR += `[[${nextYear.format(yearly.link)}| ${nextYear.format(yearly.display)} ↳ ]] `;

// Sets start of the week to Sunday
let sunday = date.clone().startOf("week");

// Prints the link|display for Sunday
tR += `\n##### [[${sunday.clone().format(daily.link)}| ● ${sunday.clone().format(daily.display)}]] `;

// Iterates through the days of the week for daily notes
for (let i = 1; i < 8; i++) {
	let weekday = sunday.clone().add(i, "day");
	let dayLink = `[[${weekday.format(daily.link)}| ● ${weekday.format(daily.display)}]] `;

	// Bolds the current note
	if (weekday.isoWeekday() == date.isoWeekday()) {
		dayLink = ` **${dayLink}** `;
	}
	// Prints the link|display for each day of week
	tR += dayLink;
}
-%>

---

## 🔥 Hello Gorgeous 🔥

> [!objectives] 

=== multi-column-start: mood

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

##### 🫀 How you Doing?

- #mood/

=== end-column ===

##### 🌧 How Wet Is it?

<% tp.user.fetchWeather() %>

=== multi-column-end

## 🔎 At a Glance 🔍

=== multi-column-start: glance

```column-settings
Col Count: 3
Alignment: Center
Border: off
```

### 👟 Just Do It!

```tasks
due <% date.format("YYYY-MM-DD") %>
not done
```

=== end-column ===
### 🐢 It Can Wait

```tasks
due after <% date.format("YYYY-MM-DD") %> and before <% date.clone().add(1, "week").format("YYYY-MM-DD") %>
not done
```

=== end-column ===
### 💩 Shiiiiit

```tasks
due before <% date.format("YYYY-MM-DD") %> 
not done
```

=== multi-column-end


## ⏳ Quick Additions ⌛

=== multi-column-start: jot

```column-settings
Col Count: 1
Alignment: Center
Border: off
```

### 🖊 Jot it Down

- [ ] #jotitdown/🖊️ 

=== multi-column-end

### 👥 Appointments

=== multi-column-start: appts

```column-settings
Col Count: 4
Alignment: Left
Border: off
```

##### ⚕ Medical

- [ ] #appt/⚕ 

=== end-column ===

##### 🍎 Education

- [ ] #appt/🍎

=== end-column ===

##### 💅 Self-Care

- [ ] #appt/💅 

=== end-column ===

##### 💰 Financial

- [ ] #appt/💰

=== multi-column-end

=== multi-column-start: events

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

### 🎁 This Shit is Eventful

- [ ] #event/🎁 

=== end-column ===

### 🧠 Forget to Remember

- [ ] #memory/🧠 

=== multi-column-end

## 🪴 Water your Garden 🪴

=== multi-column-start: habits1

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

##### 💊 Addy

- #habits/💊 

=== end-column ===

##### 🚲 Biking

- #habits/🚲 


=== multi-column-end

=== multi-column-start: habits2

```column-settings
Col Count: 2
Alignment: Left
Border: off
```
##### 🍽 Cooking

- #habits/🍽 

=== end-column ===
##### 🍾 Partying

- #habits/🍾 

=== multi-column-end

=== multi-column-start: habits3

```column-settings
Col Count: 2
Alignment: Left
Border: off
```
##### 🏋🏼‍♀️ Exercise

- #habits/💪 

=== end-column ===

##### 🥤 Fast Food

- #habits/🥤 

=== multi-column-end 

=== multi-column-start: habits4

```column-settings
Col Count: 2
Alignment: Left
Border: off
```
##### 🧘🏼‍♀️ Mindfulness

- #habits/🧘 

=== end-column ===
##### 💨 Vape

- #habits/💨

=== multi-column-end

## 🌺 Weed it Out 🌺

=== multi-column-start: freya

```column-settings
Col Count: 1
Alignment: Center
Border: off
```

##### 🐈 Freya

- [ ] #chores/🐈

=== multi-column-end

=== multi-column-start: chores1

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

##### 🚽 Bathroom

- [ ] #chores/🚽 

=== end-column ===

##### 🚰 Dishes

- [ ] #chores/🚰 

=== multi-column-end

=== multi-column-start: chores2

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

##### 🛒 Groceries

- [ ] #chores/🛒 

=== end-column ===

##### 🧺 Laundry 

- [ ] #chores/🧺

=== multi-column-end

=== multi-column-start: chores3

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

##### 🧹 Sweep

- [ ] #chores/🧹 

=== end-column ===

##### 🗑 Trash/Recycling

- [ ] #chores/🗑️ 

=== multi-column-end

## 🫚 Nourish Thy Roots 🫚

###  🏗 New Projects

- #projects/

### 🧬 Ancestry Research

- #hobby/🧬 

### 🪲 Hacking

- #hobby/🪲 

### 🎓 Tutorials

- #hobby/🎓  

### 💻 Other Coding

- #hobby/💻  

### 🧵 Stitching

- #hobby/🧵  

###  🎨 Coloring

- #hobby/🎨 

###  🛋️ Refurbishing/Organizing

- #hobby/🛋 


## 🌱 Sow a Seed 🌱

=== multi-column-start: finance1

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

### 💰 Income

- #finance/💰 

=== end-column ===

### 💳 Spending

- #finance/💳  

=== multi-column-end

=== multi-column-start: finance2

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

### 🏦 Savings

- #finance/🏦  

=== end-column ===

### 📈 Debts

- #finance/📈 

=== multi-column-end

=== multi-column-start: finance3

```column-settings
Col Count: 2
Alignment: Left
Border: off
```

### 🛒 Wish List

- #shopping/🛒 

=== end-column ===

### 📦 Deliveries

- #shopping/📦  

=== multi-column-end

## 🌲 Forest through the Trees 🌲

- #personal/📜 


## 🔗 Other Notes from Today

### Notes Modified

```dataview
TABLE WITHOUT ID link(file.link, aliases[0]) as "File", scope as "Scope", type as "Type", description as "Description"
WHERE file.mtime >= date(<% date.format("YYYY-MM-DD") %>) - dur(1 day) 
	AND file.path != this.file.path
	AND file.ctime != date(<% date.format("YYYY-MM-DD") %>)
SORT file.mtime DESC
```

### Notes Created

```dataview
TABLE WITHOUT ID link(file.link, aliases[0]) as "File", scope as "Scope", type as "Type", description as "Description"
WHERE file.ctime >= date(<% date.format("YYYY-MM-DD") %>) - dur(1 day) 
	AND file.path != this.file.path
SORT file.ctime DESC
```


