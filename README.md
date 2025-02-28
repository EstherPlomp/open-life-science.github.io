# Open Life Science

***Sharing. Connecting. Empowering***

Find all the information about our community and projects at
[https://open-life-science.github.io](https://open-life-science.github.io).

## Welcome!

First and foremost, Welcome! 🎉 Willkommen! 🎊 Bienvenue! 🙏 सुस्वागत (Suswagat)🎈🎈🎈

This document (the `README` file) is a hub to give you some information about the
project. Jump straight to one of the sections below, or just scroll down to find
out more.

## What are we doing?

We are working to create a mentoring program for individuals interested in becoming
ambassadors for Open Science practice, training and education in their communities.

Our outcome is to support early stage researchers and young leaders by sharing
Open Science skills, connecting them to others in the community,
and empowering them to become ambassadors for Open Science practice,
training and education in their communities.

## Who are we?

We are currently a team of 3 members who share a passion for Open Research and inclusiveness in Open Science.

As the graduates, mentors, and hosts of various Mozilla Open Leaders cohorts, we have gained expertise in the technical and culture track. Furthermore, we participate in a wide range of activities in different international communities of practice in the life sciences: ELIXIR (European bioinformatics network), Galaxy, The Carpentries, Software Sustainability Institute (SSI), Open Bioinformatics Foundation (OBF), and Mozilla.

## What do we need?

**You!** In whatever way you can help.

We need expertise in open-science, training, mentoring, communication. We'd love your feedback along the way, and of course.

## Get involved

If you think you can help in any of the areas listed above (and we bet you can)
or in any of the many areas that we haven't yet thought of (and here we're sure
you can) then please check out [our contributors' guidelines](CONTRIBUTING.md)
and our [roadmap](roadmap.md).

Please note that it's very important to us that we maintain a positive and
supportive environment for everyone who wants to participate. When you join us
we ask that you follow our [code of conduct](CODE_OF_CONDUCT.md) in all
interactions both on and offline.

## How can I generate the website locally?

You need a `ruby` environment (version >= 2.4). Either you have it installed and
you know how to install [Bundler](https://bundler.io/) and
[Jekyll](https://jekyllrb.com/) and then run Jekyll, or you use
(mini-)[conda](https://conda.io/docs/index.html), a package management system
that can install all these tools for you. You can install it by following the
instructions on this page: https://conda.io/docs/user-guide/install/index.html

In the sequel, we assume you use miniconda.

1. Open a terminal
2. Clone this GitHub repository:

   ```
   $ git clone https://github.com/open-life-science/open-life-science.github.io.git
   ```

3. Navigate to the `open-life-science.github.io/` folder with `cd`
4. Set up the conda environment:

   ```
   $ make create-env
   ```

5. Install the project's dependencies:

   ```
   $ make install
   ```

6. Start the website:

   ```
   $ make serve
   ```

7. Open the website in your favorite browser at:
   [http://127.0.0.1:4000/](http://127.0.0.1:4000/)

## Run the link checks

To avoid dead or wrong links, run the link checkers:

```
$ make check-html
```

## Create a new blog post

To create a new blog post:

1. Create a file in the folder `_posts` with a file named following the pattern `yyyy-mm-dd-name.md`
2. Add some metadata on the top of the file

    ```
    ---
    layout: post
    title: <title of the post>
    author: <github id of the author>
    image: images/yyyy-mm-dd-name.jpg
    ---
    ```

4. Add content of the post in the file in Markdown
3. Add images in `images/posts/`

## Add someone as mentor, expert or organizer

Add someone to the list of people:

1. Open the `_data/people.yaml` file
2. Create a new entry there (using the GitHub id, or firstname-lastname if no GitHub id) following the alphabetical order
3. Fill in information using the tags:
    - `first-name` (*mandatory*)
    - `last-name` (*mandatory*)
    - `twitter`
    - `email`
    - `website`
    - `gitter`
    - `orcid`
    - `affiliation`
    - `city`
    - `country` (*mandatory*)
    - `pronouns`
    - `expertise`
    - `bio`

Add the person to their corresponding list to be visible on the website:
- If they are a participant for a cohort, add their GitHub id with their project to `_data/ols-n-projects.yaml`
- If they are a potential mentor for a cohort, add their GitHub id in the `_data/ols-n-metadata.yaml`
- If they are an expert for a cohort, add their GitHub id in the `_data/ols-n-metadata.yaml`
- If they are a speaker for a cohort, add their GitHub id with their talk details in `_data/ols-n-schedule.yaml`

Add many people in a row to `_data/people.yaml`:

1. Create a CSV file with at least the following columns (named this way):
   - `First name`
   - `Last name`
   - `Email`
   - `Github username`
   - `Twitter username`
   - `Website`
   - `ORCID`
   - `Affiliation`
   - `City`
   - `Country`
   - `Pronouns`
   - `Areas of expertise (1 element per line)`
   - `Bio`

   A form like [this one](https://docs.google.com/forms/d/e/1FAIpQLScmsWw0VSvdytz3A1k6HnbfgOnsE4SiJcL9_qkMTs_Na6-l2Q/viewform?usp=pp_url) can be used to generate such csv

2. Get a copy of the CSV file at the root of this folder
3. Activate the conda environment

   ```
   $ source activate open-life-science-website
   ```

   Or alternatively, get locally:
   - Python 3.*
   - pyyaml
   - pandas

4. Run the script which extract information from the CSV file and add them to `_data/people.yaml`

   ```
   $ python bin/prepare_website_data.py extractpeople \
      -df <path to csv file with participants> OR -du <URL to csv file with participants>
   ```

## Add possible mentors and experts for a cohort

1. Create a CSV file with at least the following columns (named this way):
   - `First name`
   - `Last name`
   - `Email`
   - `Github username`
   - `Twitter username`
   - `Website`
   - `ORCID`
   - `Affiliation`
   - `City`
   - `Country`
   - `Pronouns`
   - `Areas of expertise (1 element per line)`
   - `Bio`

   A form like [this one](https://docs.google.com/forms/d/e/1FAIpQLScmsWw0VSvdytz3A1k6HnbfgOnsE4SiJcL9_qkMTs_Na6-l2Q/viewform?usp=pp_url) can be used to generate such csv

2. Activate the conda environment

   ```
   $ source activate open-life-science-website
   ```

   Or alternatively, get locally:
   - Python 3.*
   - pyyaml
   - pandas

4. Run the script which extract information from the CSV file and add them to `_data/people.yaml`

   ```
   $ python bin/prepare_website_data.py addmentorsexperts \
      -c <cohort id> \
      -t <mentors or experts> \
      -df <path to csv file with participants> OR -du <URL to csv file with participants>
   ```

## Add a partner/sponsor

1. Open the `_data/partners.yaml` file
2. Create a new entry there (using the name in lowercase, with spaces replaced by `-`) following an alphabetical order
3. Fill in information using the tags:
    - `name`
    - `website`
    - `description`
4. Add a logo (if possible) named as the entry in `images/partners` folder
5. Add the path to the logo in `_data/partners.yaml` using `logo` tag

## Update schedule for a cohort

The schedule displayed in a cohort page is automatically generated from a file `_data/ols-n-schedule.yaml`.

In this file, for each week, it is listed the timeframe and the different calls planned. For each call, several information are given:
- `type`: `Mentor-Mentee`, `Cohort`, `Mentors` or `Coworking`
- `duration` in min
- `title`
- `date` in the format `Month Day, Year`
- `time` in the format '14:00' and for Berlin time
- `calendar-event`: link to calendar event
- `agenda`: tldr
- `notes`: link to notes
- `recording`: link to recording
- `content` with details of the content written in Markdown
- `before` with tasks to do before as a list written in Markdown
- `after` with tasks to do after as a list written in Markdown
- `resources`: list of useful resources with for each of them:
   - `type`: `slides`, `document`, or `external-link`
   - `title`
   - `speaker`: username in `_data/people.yaml`, if slides
   - `link`

## Update schedule automatically

1. Create a spreadsheet or CSV with columns:
   - `Week`
   - `Start Date`
   - `Start Time`
   - `End Date`
   - `Duration`
   - `Title`
   - `Type`
   - `Learning objectives`
   - `Slides`
   - `Confirmed speaker`
   - `Note link`
   - `Recording`
   - `Hosts`
   - `Facilitators`
   - `Before`
   - `After`

2. Adapt the script in `bin/update_schedule.sh` with cohort id and link to CSV export of the spreadsheet

## Order experts and possible mentors by expertise areas

In metadata file for cohort, experts and possible mentors can be ordered by expertise area to be display in cohort page given these areas.

To order them:

1. Activate the conda environment

   ```
   $ source activate open-life-science-website
   ```

   Or alternatively, get locally:
   - Python 3.*
   - pyyaml
   - pandas

2. Run the script which sort expertise and save information in metadata file

   ```
   $ python bin/prepare_website_data.py sortexpertises -c <cohort id>
   ```

## Add projects

1. Create a CSV file with for each project the following information
   - `Title`
   - `Mentor 1`
   - `Authors`
   - `Project-description`
   - `Comment regarding review` (with `rejected` if needed)
   - `Keywords`

2. Create a CSV file with participant information (similar as the one needed to add new people) with an extra column with project name

3. Activate the conda environment

   ```
   $ source activate open-life-science-website
   ```

   Or alternatively, get locally:
   - Python 3.*
   - pyyaml
   - pandas

4. Run the script which extract project information from a CSV file and add them in project file

   ```
   $ python bin/prepare_website_data.py addprojects \
      -c <cohort id> \
      -pf <path to csv file with projects> OR -pu <URL to csv file with projects> \
      -df <path to csv file with participants> OR -du <URL to csv file with participants>
   ```

## Add events to Google calendar

1. Create CSV file with
   - `Week`
   - `Type`
   - `Optional`
   - `Subject`
   - `Start Date`
   - `Start Time`
   - `End Date`
   - `Duration`
   - `End Time`
   - `All Day Event`
   - `Note link`
   - `Description`

2. Add events to [Google calendar](https://support.google.com/calendar/answer/37118#advanced&zippy=%2Ccreate-or-edit-a-csv-file)

## Create files for a new cohort

1. Activate the conda environment

   ```
   $ source activate open-life-science-website
   ```

   Or alternatively, get locally:
   - Python 3.*
   - pyyaml
   - pandas

2. Run the script which create new cohort files

   ```
   $ python bin/prepare_website_data.py createcohort \
      -c <cohort id> \
   ```

3. Update `_config.yml` file to add new cohort in collection