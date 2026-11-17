# AWS Certified Cloud Practitioner (CLF-C02) study vault

An [Obsidian](https://obsidian.md) vault for passing the AWS Certified Cloud Practitioner exam: study notes for every exam guide objective, a reference entry for every in-scope service, cheat sheets, spaced-repetition flashcards, and three full mock exams.

It is organized around the official [CLF-C02 exam guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf), and every external reference links to an AWS page.

## What's inside

| Folder | Contents |
| --- | --- |
| `00 - Start Here.md` | Home note: exam facts, domain weights, and links to everything |
| `01 - Study Plan (14 Days).md` | A day-by-day plan with checkboxes |
| `Domain 1` to `Domain 4` | One study note per task statement (19 in total), each with the verbatim objective, key concepts, exam traps, a self-check, and AWS references |
| `Services/` | All 134 in-scope services across the 19 exam guide categories: what each does, when to choose it, key facts, look-alikes, and its AWS doc link |
| `Cheat Sheets/` | 16 one-page summaries, such as Shared Responsibility Model, Support Plans, S3 Storage Classes, EC2 Purchasing Options, and Commonly Confused Services |
| `Flashcards/` | 812 cards in 9 decks for the Spaced Repetition plugin |
| `Practice Questions/` | 100 domain practice questions and three 65-question mock exams weighted like the real exam, all with explained answers |

## Setup

### 1. Install Obsidian

Download it free from [obsidian.md/download](https://obsidian.md/download) (Windows, macOS, Linux, iOS, Android).

### 2. Download this vault

With Git:

```bash
git clone https://github.com/tberndt5/aws-cloud-practitioner.git
```

Without Git: on the repository page choose **Code → Download ZIP**, then unzip it.

### 3. Open it in Obsidian

1. Open Obsidian.
2. Choose **Open folder as vault** (from the vault switcher in the bottom-left corner, or **File → Open vault**).
3. Select the `aws-cloud-practitioner` folder.
4. If Obsidian asks whether you trust the author of this vault, choose to trust it so plugins can run.

### 4. Install the Spaced Repetition plugin

The flashcards need the community plugin **Spaced Repetition** by Stephen Mwangi ([documentation](https://stephenmwangi.com/obsidian-spaced-repetition/), [source](https://github.com/st3v3nmw/obsidian-spaced-repetition)). It is not bundled with this repository.

1. Open **Settings** (the gear icon in the bottom-left corner).
2. Go to **Community plugins** and choose **Turn on community plugins**.
3. Choose **Browse**, search for `Spaced Repetition`, and open the result by Stephen Mwangi.
4. Choose **Install**, then **Enable**.

The default plugin settings work with this vault. The decks are found through the `flashcards/...` tag at the top of each file in `Flashcards/`.

## How to use it

### Follow the plan

Open `00 - Start Here`, then work through `01 - Study Plan (14 Days)`. Each day lists the notes to read, the deck to start, and the practice set to take. Tick the checkboxes as you go. The dates in the plan are examples; shift them to end the day before your exam.

Internal links such as `[[2.1 Shared Responsibility Model]]` are clickable in Obsidian. Hold Ctrl (Cmd on macOS) and hover over a link to preview the note.

### Review flashcards

1. Click the **Review flashcards** card icon in the left ribbon, or open the command palette (Ctrl/Cmd + P) and run **Spaced Repetition: Review flashcards from all notes**.
2. Choose a deck. Decks are grouped under `flashcards`: `domain-1` to `domain-4`, `services`, and `confused`.
3. Read the question, answer it from memory, and choose **Show answer**.
4. Grade yourself **Hard**, **Good**, or **Easy**. The plugin schedules the card's next showing from your grade, so cards you find hard come back sooner.
5. Review the due cards every day. The status bar shows how many are due.

The plugin stores each card's schedule as a small comment next to the card in the flashcard file, so your progress travels with the vault. To start over, choose a card's **Reset** option during review, or delete the `<!--SR:...-->` comments.

Cards use the plugin's single-line format, `Question::Answer`. You can add your own in any note that has a `flashcards/...` tag.

### Take practice questions and mock exams

Each question has its answer in a collapsed **Answer** callout directly below it. Click the callout to expand it. Every answer explains why the correct option is right, why each other option is wrong, and links to the note to review.

For a mock exam, allow 90 minutes, work closed-book, and write your answers down before expanding any callout. The scoring table at the end of each mock maps every question to its domain and task statement so you can total a score per domain.

## About the exam

| Item | Fact |
| --- | --- |
| Questions | 65 (50 scored, 15 unscored) |
| Time | 90 minutes |
| Passing score | 700 on a scale of 100 to 1,000 |
| Domains | Cloud Concepts 24%, Security and Compliance 30%, Cloud Technology and Services 34%, Billing, Pricing, and Support 12% |

Official exam page: [AWS Certified Cloud Practitioner](https://aws.amazon.com/certification/certified-cloud-practitioner/)

## Accuracy and scope

- The notes teach what CLF-C02 tests, using the service and support plan names in the exam guide. Where AWS has since renamed, retired, or changed something, a `Current status:` line follows the exam-relevant content.
- AWS changes often. Check the linked AWS documentation for anything you rely on, and please open an issue if you find an error.
- All practice and mock questions are original and written for this vault. None are taken from the real exam or from any practice exam provider.

## Disclaimer

This is an unofficial study aid. It is not affiliated with, endorsed by, or sponsored by Amazon Web Services. AWS and related marks are trademarks of Amazon.com, Inc. or its affiliates.
