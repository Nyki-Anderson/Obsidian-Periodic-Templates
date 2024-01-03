---
<%*
// Sets date based on title of file
let date = moment(tp.file.title, "[Day ] DDD, dddd MMMM Do, YYYY");

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
obsidianEditingMode: live
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

## :mag_right: At a Glance :mag:

### 👟 Just Do It!

```tasks
due today
```
### 🐢 It Can Wait...

```tasks
due after today and before next week
not done
```
### 💩 Shit Just Got Real ...

```tasks
due before today 
not done
```


## ⏳ Quick Additions ⌛

### 🖊 Jot it Down

### 👥 Appointments

### 🎁 This Shit is Eventful

### 🔼 Let Me Upgrade You


## 🪴 Water your Garden 🪴

### 🏡 Household

### 🍽 Cooking 

### ⚕ Health

### 🐈 Freya

### ♥ Julian

### 💼 Vapology101

### 🏫 School

### 🚫 Bad Habits

### 💄 Beauty

## 🫚 Deepen Thy Roots 🫚

### 🧬 Ancestry Research

### 🪲 Hacking

### 🎓 Docker Tutorial

### 💻 Other Coding

### 🧵 Stitching

### 🎨 Coloring

### 🛋️ Refurbishing/Organizing

### 📓 Miscellaneous



## 🌱 Plant a Seed 🌱

### 💰 Income

### 💳 Spending

### 🏦 Savings

### 📈 Debt

### 🛒 Pending

### 📦 Deliveries

## 🌲 Forest through the Trees 🌲
