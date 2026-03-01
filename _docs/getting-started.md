---
layout: docs
title: Quick Start Guide
description: Get your PitCrew site live and get oriented as a new team member.
permalink: /docs/getting-started/
parent: Getting Started
---

**On this page:** [Set Up Your Website](#set-up-your-website) · [Joining the Team](#joining-the-team) · [Subteams](#subteams) · [Resources](#resources)

---

## Set Up Your Website

The first thing to do as a new site maintainer is run the Setup Wizard. It configures your colors, team data, and site features — no coding needed.

### Using the Setup Wizard

**Visit `/wizard/`** on your site — or it launches automatically the first time anyone visits if `startup_wizard: true` is set in `_config.yml`.

**Estimated time: 2–3 hours.** Have this ready before you start:

| Category | What you need |
|---|---|
| Team Info | Team name, number, program (FTC/FRC/VEX/FLL), current season |
| Brand | Primary and secondary colors (hex codes, or use the picker) |
| Online | Instagram, GitHub, YouTube, Twitter URLs · contact email |
| People | Each member: name, role, grade, grad year, bio · Each mentor: name, role, org, bio |
| Season | Sponsors (name, tier, URL) · Awards (name, event, season) · Events (name, date, location, type) |

> **Photos and logos** are referenced by file path (e.g. `/assets/images/photo.jpg`). Upload the actual image files to your project separately. Fields left blank use a placeholder automatically.

**The wizard walks you through 11 steps:**

1. Team Identity — name, number, program, season
2. Brand Colors — primary and secondary, with a live preview
3. Features — toggle blog, docs, CAD viewer, search, and more on or off
4. Social Links — Instagram, GitHub, YouTube, Twitter, email
5. Navigation — page order and labels
6. Team Members — add, edit, remove
7. Mentors — add, edit, remove
8. Sponsors — add, edit, remove
9. Awards — add, edit, remove
10. Events — add, edit, remove
11. Review & Download

### Saving Progress

A **Save Progress** button is in the footer on every step. Use it if you need to stop partway through.

- Downloads `pitcrew-progress.zip` with all data entered so far
- Upload those files to your project and commit — your data is preserved
- When you return to `/wizard/`, it starts from Step 1, but all saved data is already in place

### Finishing Up

On the **Review & Download** step:

- Check the **"Skip wizard on startup"** box (recommended) so visitors aren't auto-redirected once you go live
- Click **Download pitcrew-config.zip**

Then deploy the changes:

```bash
# 1. Extract the zip and overwrite files in your project
# 2. Preview locally
bundle exec jekyll serve

# 3. Push to GitHub
git add -A
git commit -m "Initial site setup via wizard"
git push
```

### Manual Configuration (No Wizard)

Prefer editing files directly? Everything the wizard does maps to two places:

- **`_config.yml`** — colors, features, navigation, social links, team identity
- **`_data/*.yml`** — team.yml, mentors.yml, sponsors.yml, awards.yml, events.yml

See the [Site Configuration guide](/docs/site-setup/) for a full reference.

---

## Joining the Team

New to the robotics team? Here's how your first week typically goes.

### Your First Week

**Day 1 — Orientation**
- Meet the team and mentors
- Tour the workspace
- Review safety guidelines
- Get added to communication channels

**Days 2–3 — Training**
- Complete safety training (required before touching any tools)
- Learn basic tool and equipment usage
- Shadow experienced members
- Start a beginner task or project

**Days 4–5 — Integration**
- Join a subteam based on your interests
- Start contributing to real tasks
- Ask lots of questions — that's what this phase is for

---

## Subteams

Choose a subteam based on what excites you. Most members specialize in one or two areas.

### Mechanical
Build and maintain the robot's physical structure.
- **What you'll do:** Fabricate parts, assemble mechanisms, iterate on designs
- **Skills gained:** CAD, machining, 3D printing, hand tools
- **Tools:** Drills, saws, 3D printers, CNC machines

### Programming
Write the software that makes the robot move and think.
- **What you'll do:** Control systems, autonomous routines, driver assist features
- **Skills gained:** Java or Python, version control (Git), debugging, computer vision
- **Tools:** VS Code, GitHub, Android Studio (FTC)

### Electrical
Design and build the robot's wiring and electronics.
- **What you'll do:** Wire motors and sensors, manage power distribution, troubleshoot circuits
- **Skills gained:** Wiring, soldering, multimeter usage, circuit design
- **Tools:** Multimeter, crimping tools, wire strippers

### Business
Handle the behind-the-scenes work that keeps the team funded and recognized.
- **What you'll do:** Reach out to sponsors, write award submissions, run social media, organize outreach events
- **Skills gained:** Communication, writing, graphic design, project management
- **Tools:** Presentation software, Canva, social media platforms

---

## Resources

| Resource | Link |
|---|---|
| Team Calendar | [Link to calendar] |
| Communication (Slack/Discord) | [Link to channel] |
| Code Repository | [Link to GitHub] |
| Game Manual | [Link to current season manual] |

**Questions?** Every team member and mentor is here to help. If something isn't in the docs, just ask.
