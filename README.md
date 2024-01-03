# 🗓️ Obsidian-Periodic-Templates
This is a collection of my templates for periodic (scoped) journal templates including: daily, weekly, monthly, quarterly, and yearly notes. 

## 🎯 **Objectives**
I have spent a long time working out how exactly I want my periodic journal to operate. I have taken it as a personal challenge to configure my journal content so that it is adaptable to each day, measurable for long term goal and progress review, and automatable for obvious reasons. 

This repository will keep the various versions of templates I have derived personally and through extensive crowd-sourcing of others' methodologies. I will provide links to any inspiration that I used to develop my templates as well. 

## ✨ Features:
These templates:
- Use **Javascript**, **Dataview** queries, and **Templater** to provide a seamless and automated journaling experience that is directly integrated with both the **Calendar** and **Periodic Notes** plugins. 
- Contain a navigational menu to jump between periodic scopes.
- Dynamically create new periodic notes (at any scope-level) via the navigational links and use the corresponding template.
- Automatically move each note to the desired folder/subfolder and have unique names at the note-level so linking is simplified.
- Contain all necessary metadata to capture and later query entries in customizably meaningful ways.

# 🪑 Table of Contents

- [🗓️ Obsidian-Periodic-Templates](#️-obsidian-periodic-templates)
  - [🎯 **Objectives**](#-objectives)
  - [✨ Features:](#-features)
- [🪑 Table of Contents](#-table-of-contents)
- [🗺️ Walkthrough](#️-walkthrough)
  - [:toolbox: Community Plugins](#toolbox-community-plugins)
    - [Periodic Notes](#periodic-notes)
    - [Templater](#templater)
    - [Dataview](#dataview)
    - [Tasks](#tasks)
    - [*Optional*](#optional)
  - [🏗️ Vault Setup](#️-vault-setup)
  - [💻 Implementation](#-implementation)
    - [Dynamic Navigation](#dynamic-navigation)
    - [Daily Notes Template(s)](#daily-notes-templates)
    - [Weekly Summmary Template(s)](#weekly-summmary-templates)
    - [Monthly Overview Template(s)](#monthly-overview-templates)
    - [Quarterly Goals Template(s)](#quarterly-goals-templates)
    - [Yearly Progress Template(s)](#yearly-progress-templates)
- [📚 TL;DR](#-tldr)
- [🍎 Feedback \& Questions Welcome!](#-feedback--questions-welcome)
- [💙 Thank You](#-thank-you)

> ❗ **Tip**:
> 
> To get the most out of this repository, follow this `README.md` file like a tutorial. The configuration of this system spans several plugins and is nuanced at times... To customize it to your own naming conventions and such will require you understand how the whole system works together. 
>
> A [📚 TL;DR](#-tldr) can be found at the bottom of this `README.md` for those who wish to understand how the system was put together but not necessarily the implementation I describe in detail.

# 🗺️ Walkthrough
This walkthrough will go through the entire setup as is used in my personal vault. The directory structure of this vault is **NOT** reflected in the directory structure of this repository. 

## :toolbox: Community Plugins
I will include any Obsidian plugins I make use of and provide screenshots where helpful to describe configuration of these tools. 

### [Periodic Notes](https://github.com/liamcain/obsidian-periodic-notes)
The most important component of using these tutorials is the **Periodic Notes** plugin. It allows built-in integration with the **Calendar** plugin and allows you to granularly determine where each scoped-periodic note is stored in your folder directory.

Rather than show the configuration of these options here, look for them in the [💻 Implementation](#-implementation) section under each periodic scope.

The beauty of this plugin is that you only need to activate the peridioc scopes you want to use (i.e., Daily, Weekly, Monthly, Quarterly, and Yearly).

It is critical that you use the same naming conventions in this plugin's options as you use in the templates. This may become more clear in the [💻 Implementation](#-implementation) section.

### [Templater](https://github.com/SilentVoid13/Templater)
**Templater** is where the real magic happens. Be sure to activate the `Trigger Templater on New File Creation` option as it allows dynamic template activation depending on the folder. 

Notice, that only the designated scope directory need be designated here. The date-dependent directories will automatically populate when the notes are created. So to get the daily note for today to be stored in `The Journal/Daily/2024/January/Day 2, Tuesday January 2nd, 2024` you need only specify `The Journal/Daily` in the **Templater** options for the `DAILY.md` template. See screenshot below for clarification.

![Templater Folder Note Configuration](Screenshots/Templater%20Configuration.png)

Rather conveniently, this still allows you to use other templates for generic note creation. In my vault I use a frontmatter template to dynamically populate metadata properties and this does not conflict with my periodic note templates.

### [Dataview](https://github.com/blacksmithgu/obsidian-dataview)
The **Dataview** plugin is used more extensively in the broader scoped periodic templates. More on the logic behind such queries when I further develop the templates beyond DAILY.md and WEEKLY.md. 

### [Tasks](https://github.com/obsidian-tasks-group/obsidian-tasks)


### *Optional*
- [Linter](https://github.com/platers/obsidian-linter): In order to maintain definite style and formatting conventions throughout my vault, I use the plugin **Linter**. I lint on save in the rest of my vault but this would be destructive if my templates and other utilities were altered each time I instinctively press `Command-S`. So in the Linter options, I add the entire `The Utilities` folder to the `Folders to Ignore` list. 
- [Banners](https://github.com/noatpad/obsidian-banners): I use the **Banners** plugin to insert nice month-specific banners to each periodic note. This is done dyamically depending on the month of the note (requires that each note be named using a valid date format).

## 🏗️ Vault Setup

My personal vault is organized mainly into folderized **Scopes**. The two main-level folders that pertain to this project are `The Journal` and `The Utilities` folders. 

![The Journal Folder and Subfolder Conventions](Screenshots/The%20Journal%20Folder.png)

## 💻 Implementation
If you wish to implement your vault's periodic note templates exactly as I have, each scope and it's configuration are explained here. The template files themselves are also commented line-by-line for all JavaScript sections. 

### Dynamic Navigation
At the top of each periodic note will be a navbar that both allows you to quickly jump between scopes (past or present) as well as create new notes from said links. The logic is written in **JavaScript** and uses `moment.js` syntax to easily modify and manipulate dates forward and backward in time[^1].

### Daily Notes Template(s)
These notes are intended to capture the raw data of the day: tasks, events, musings, and personal objectives. I am playing around with adaptive formatting so that each day can unfold naturally throughout the note rather than have a list of designated prompts that must be filled, as this has not worked for me in the past. The scope of the daily note is anything and everything that has value at the moment and I am designing the structure to be able to handle the broadest scope while being streamlined and fun/playful at the same time. Each expansion in scope should be able to either quantify or query the various entries in the daily note in a meaningful way. Anything that does not satisfy this goal will be continually reworked until it does. 

![Periodic Plugin Options for Daily Template](Screenshots/Periodic%20Plugin%20Options%20(Daily).png)

### Weekly Summmary Template(s)
The goal of the weekly note is to gather and summarize the musings of the week at a glance but with easy integration back to the raw undistilled body of information when desired. Basically I want to be able to see everything visually or graphically upfront but be able to drill back into the original entry and even expand on them without leaving the weekly interface. I also want to track habits and progress toward more long-term projects and such but this may be better realized in later iterations. The weekly note should zoom me outward just enough to see the forest through the daily trees. 

![Periodic Plugin Options for Weekly Template](Screenshots/Periodic%20Plugin%20Options%20(Weekly).png)

### Monthly Overview Template(s)

![Periodic Plugin Options for Monthly Template](Screenshots/Periodic%20Plugin%20Options%20(Monthly).png)

### Quarterly Goals Template(s)

![Periodic Plugin Options for Quarterly Template](Screenshots/Periodic%20Plugin%20Options%20(Quarterly).png)

### Yearly Progress Template(s)

![Alt text](Screenshots/Periodic%20Plugin%20Options%20(Yearly).png)

# 📚 TL;DR
The system works as follows:
1. The **Periodic Notes** plugin allows integration with the **Calendar** plugin so that you can simply select a day to create a new daily note. To configure, simply activate the scope of note you wish to use, choose a unique identifier based on `moment.js` syntax, select a template to activate, and specify the folder to store new notes of this scope. 
2. The **Templater** plugin allows a template to be triggered when the **Periodic Notes** plugin activates. Configure using `Trigger Templater on new file creation` and specify each folder of your journal to trigger the corresponding template.
3. **JavaScript** is used in each template to designate the current periodic note's date and use this date to populate the links for naviagation, title/aliases, and specify any other features like adaptive banners for each month.`moment.js` syntax is used throughout to manipulate dates and provide smart link creation.
4. The **Dataview** and **Tasks** plugins allow you to query and manipulate the various entries in each note so that broadly scoped templates contain metrics, summarized lists, and general overviews that keep track of your progress throughout the year.

# 🍎 Feedback & Questions Welcome!
I love sharing what I learn so don't hesitate but I am no expert... Please provide feedback or ask questions for clarification and expect me to be responsive. I also would love to hear ways to improve what I've done -- criticisms are taken constructively!

# 💙 Thank You

[^1]: Navbar and dyanmic note creation from links: [Github: obsidian-periodic-notes-navbar](https://github.com/martenlienen/obsidian-periodic-notes-navbar) by [martenlienen](https://github.com/martenlienen)
