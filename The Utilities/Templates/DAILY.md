---
<%*
// Sets date based on title of file
let date = moment(tp.file.title, "[Day ] DDD - dddd MMMM Do YYYY");

let daily = {link: "[The Journal/Daily]/YYYY/MMMM/[Day ] DDD - dddd MMMM Do YYYY", display: "ddd DD"};
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

> [!objectives] 
> 

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

### 🖊 Jot it Down

- [ ] #jotitdown/🖊️ 

### 👥 Appointments

- [ ] #appt/

### 🎁 This Shit is Eventful

- [ ] #event/🎁 

### 🔼 Let Me Upgrade You

- [ ] #scope/🌱 

## 🪴 Water your Garden 🪴

### 🏡 Household

- #personal/🏡 

### 🍽 Cooking 

- #health/🍽 

### ⚕ Health

- #health/⚕ 

### 🐈 Freya

- #personal/😻 

### ♥ Julian

- #scope/💕  

### 💼 Vapology101

- #scope/💼  

### 🏫 School

- #school/✏️ 

### 🚫 Bad Habits

- #habits/ 

### 💄 Self-Care

- #personal/💅 

## 🫚 Deepen Thy Roots 🫚

### 🧬 Ancestry Research

- #scope/🧬 

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

###  🏗 New Projects

- #projects/

## 🌱 Plant a Seed 🌱

### 💰 Income

- #finance/💰 

### 💳 Spending

- #finance/💳  

### 🏦 Savings

- #finance/🏦  

### 📈 Debt

- #finance/📈 

### 🛒 Pending

- #shopping/🛒 

### 📦 Deliveries

- #shopping/📦  

## 🌲 Forest through the Trees 🌲

- #personal/📜 


## 🔗 Other Notes from Today

### Notes Created

```dataview
TABLE WITHOUT ID link(file.link, aliases) as "File", description as "Description", tags as "Tags"
WHERE file.cdate = <% date.format("YYYY-MM-DD") %>
SORT file.mtime DESC
```

### Notes Modified

```dataview
TABLE WITHOUT ID link(file.link, aliases) as "File", description as "Description", tags as "Tags"
WHERE file.mdate = <% date.format("YYYY-MM-DD") %>
SORT file.mtime DESC
```
