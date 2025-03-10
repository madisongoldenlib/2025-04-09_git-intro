---
layout: page
title: Customizing Your Workshop's Website
permalink: /customization/index.html
---

## Table of Content

* TOC
{:toc}

## Configuration File `_config.yml`

You should edit the `_config.yml` configuration file in the root directory of your workshop to
configure some site-wide variables and make the site function correctly:

* `carpentry` - to tell us which carpentry workshop this is. Possible values are:
    - `"swc"` for Software Carpentry workshops,
    - `"dc"` for Data Carpentry workshops,
    - `"lc"` for Library Carpentry workshops, and
    - `"cp"` for general Carpentries events such as instructor trainings (for which you should use
      <https://github.com/carpentries/training-template> as the website template).
    - `"incubator"` for workshops teaching a lesson in The Carpentries Incubator.
* `curriculum` - to tell us which curriculum is being taught.
  At the moment, applicable to Software and Data Carpentry workshops only.
  Possible values are:
    - `"dc-astronomy"`, `"dc-ecology"`, `"dc-genomics"`, `"dc-socsci"`, `"dc-geospatial"`, or `"dc-image"` for Data Carpentry
      workshops
    - `"swc-inflammation"` or `"swc-gapminder"` for Software Carpentry workshops.
* `flavor` - `"r"` or `"python"` depending on which lessons are being taught at the workshop
  (currently only for Data Carpentry and Software Carpentry workshops).
* `pilot` - set this to `true` if the workshop will be a lesson pilot
  (of a new official lesson or a lesson in The Carpentries Incubator).
* `title` - overall title for the workshop. If set (i.e., different from "Workshop Title" or empty),
  it will appear in the "jumbotron" (the gray box at the top of the page). This variable is also
  used for the title of the extra pages. The README contains [more information about extra pages](https://github.com/carpentries/workshop-template#creating-extra-pages).

For workshops teaching lessons in The Carpentries Incubator,
i.e. where `carpentry` is set to `incubator`,
you should uncomment the following three fields in
`_config.yml`:

* `incubator_lesson_site` - the URL of the lesson pages that will be taught at the workshop.
* `incubator_pre_survey` - the URL of the pre-workshop survey you have prepared for the pilot workshop. (The standard Carpentries pre- and post-workshop surveys should not be used for Incubator workshops.)
* `incubator_post_survey` - the URL of the post-workshop survey you have prepared for the pilot workshop.

## Site URL

GitHub Pages sites are formatted as `https://GITHUB_USERNAME.github.io/REPOSITORY_NAME`.
For example, if the URL for your repository is `https://github.com/gvwilson/2015-07-01-oomza`,
the URL for its website will be `http://gvwilson.github.io/2015-07-01-oomza`.

You should not need to modify any of the other variable values in `_config.yml`.

## Home Page (`index.md`): data in the YAML header

Your workshop's home page lives in `index.md`,
which must define the values below in its header.
If your workshop is taught online, see the
[online workshops section](#for-online-workshops) for customization
options.

*   `layout` must be `workshop`.

*   `venue` is the short name of the institution or group hosting the
    workshop, like "Euphoric State University".  It should *not*
    include the address or other details, since this value is
    displayed in a table on websites (e.g.,
    <https://carpentries.org/upcoming_workshops/>). See section
    below for value to use for online workshops.

*   `address` is the workshop's address (including details like the
    room number). The address should be all on one line.
    See section below for value to use for online workshops.

*   `country` must be a two-letter ISO-3166 code for the country in
    which the workshop is going to take place, such as "fr" (for
    France) or "nz" (for New Zealand) - see [ISO-3166 codes on Wikipedia](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements)
    for a complete list. See section below for value to use for
    online workshops.

*   `language` is the language that will be used in the workshop.
    It must be an [ISO 639-1 code](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes).
    Note that two-letter codes mean different things for countries
    and languages: "ar" is Arabic when used for a language, but
    Argentina when used for a country.

*   `latitude` and `longitude` are the latitude and longitude of the workshop
    site (so we can put a pin on our map). You can use
    [LatLong.net](https://www.latlong.net/) to find these values.
    See section below for value to use for online workshops.

*  `humandate` is the human-friendly start and end date for the
    workshop.  Please use three-letter month names and abbreviations
    (e.g., `Jul` instead of `July`), since these values are displayed
    in a table on our websites.  (Strictly speaking this information
    is redundant, since we require a machine-readable `startdate` and
    `enddate`, but reliably translating those into human-readable
    dates is an interesting challenge...)

*   `humantime` is the human-friendly start and end time for each day of
    the workshop, e.g., "09:00 am - 4:00 pm" or "09:00-16:00".  (We
    recognize that we ought to allow different start or end times on
    different days, but going down that path leads eventually to
    embedding iCal date/time specifications in our headers, which in
    turn leads to madness...)

*   `startdate` is the workshop's starting date in YYYY-MM-DD format,
    such as `2015-07-01`.  You must use four digits for the year and
    two each for the month and day.

*   `enddate` is the workshop's ending date in the same format.  If your
    workshop is only one day long, the `enddate` field should be deleted.
    If your workshop has a more complicated schedule (e.g., a half day a
    week for four weeks), please delete the `enddate` field and only tell
    us its start date.

*   `instructor` is a comma-separated list of instructor names.  The
    list must be enclosed in square brackets, and each name must be in
    double quotes, as in `["Alan Turing","Grace Hopper"]`.  Do not
    include other information (such as the word "instructor") in these
    values.

*   `helper` is a comma-separated list of helper names formatted in the
    same way as the instructor names.  If there are no helpers, use an
    empty list `[]`.

*   `contact` is the contact email address to use for your workshop.
    If you do not provide a contact email address, your website will
    display the address for the workshop coordinators (who probably
    won't be able to answer questions about the specific details of
    your workshop).

The header may optionally define the following:

*   `collaborative_notes` is the URL for the Etherpad for your workshop.
    If you are not using an Etherpad, you can delete this line. You can
    [create a carpentries etherpad here](https://pad.carpentries.org/).

*   `eventbrite` is the multi-digit Eventbrite registration key.  If you
    are using Eventbrite, the Carpentries Regional Coordinators will
    give this to you.  If you are using something else, you may delete
    this line.  Note: this value must be given as a string in double
    quotes, rather than as a number.

### For online workshops

If the workshop is online, follow the same instructions as above with the
following modifications:

* `venue`: Use the name of the institution that organizes the workshop and do
  not include a mention that it is an online workshop.
* `address`: If you can safely share the URL for the videoconferencing, you may
  list it here (it must start with `http` or `https`); if you cannot or prefer
  to not share the videoconferencing information, use the value `online`.
* `country`: Please use the country associated with the host institution for the
  workshop.
* `latitude` and `longitude`: if it makes sense, use the coordinates for the
  host institution. If it does not, use `0` for both the latitude and the
  longitude.

By default, the Setup Instructions will list the installation instructions for the
videoconferencing service Zoom.
If you use a different videoconferencing service,
you can edit the file in `_includes/install_instructions/videoconferencing.html`
to include the relevant installation instructions.

## Home Page: Schedule

By default, the template displays the typical schedule for your workshop based on
the values of the variables set in the `_config.yml`. If you need to  make
minor modifications to this schedule, you can edit the `schedule.html` file
found in the sub-folder of the `_includes` folder that matches the type of
workshop you will be teaching  (`dc`, `lc`, or `swc`).

If you wish to create your own custom schedule, an empty template is available in
`_includes/custom-schedule.html`. In this file, we provide the structure for a
4-day workshop as it is often used for online workshops. To use this custom
schedule instead of the one provided by default in the template, delete the
block of code found under the "Schedule" header in the `index.md` file and
replace it with`{% raw %}{% include custom-schedule.html %}{% endraw %}`.

The schedule is formatted using a table. If you would like to learn more about
how to write tables in HTML, here is an [HTML table overview from
Mozilla](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table) and
the [HTML tables chapter from w3schools](https://www.w3schools.com/html/html_tables.asp).

For pilot workshops, some placeholder text including a link to the lesson homepage
will be displayed instead of a schedule table.
The lesson homepage will contain estimated timings for teaching the lesson.
Use the approach described above for `_includes/custome-schedule.html`
if you would like to create a schedule table to replace this text.

## Home Page: Setup Instructions

If you need assistance with customizing the setup instructions for your website,
feel free to ask your questions in the Carpentries
[Instructors Slack channel](https://carpentries.slack.com/archives/C08BVNU00)
([join The Carpentries Slack workspace](https://slack-invite.carpentries.org/)).

### Software Carpentry workshops

#### Default settings

For Software Carpentry workshops,
setting the `flavor` variable in `_config.yml` to `r` or `python`
will include the respective installation instructions for these tools.
Additionally, by default, the installation instructions for
a text editor, the Bash shell, and Git are included.

#### If you need to remove tools

If you need to remove any of the instructions for the default
set of tools,
you can delete lines that include these instructions in
the `_includes/swc/setup.html` file.

#### If you need to add tools

If you need to add installation instructions for other tools,
we provide installation instructions for SQL and OpenRefine.
To make them appear on your workshop website,
you can move the `{% raw %}{% include %}{% endraw %}` statements outside the comment
block in `_includes/swc/setup.html`.

If you need to add installation instructions for other tools,
you will need to write your own. You can use installation instructions
for other tools located in the `_includes/install_instructions/` folder
as examples.

### Data Carpentry workshops

For Data Carpentry workshops,
installation instructions live on the workshop overview page for each curriculum.
Instead of including installation instructions in the workshop template,
the workshop template includes links to these instructions.
The correct link will be displyed
when using the appropriate combination of values
for the `curriculum`  and `flavor` variables
in the `_config.yml` file.

### Library Carpentry workshops

By default, Library Carpentry workshop websites
include installation instructions for the Bash shell and Git.

You may need to add installation instructions for additional tools
you will be using during your workshop
by editing the `_includes/lc/setup.html` file.
You can either write your own instructions using the ones
provided in `_includes/lc/setup.html` as an example,
or, if you are using tools that already have installation instructions
provided for Software Carpentry,
you can add `{% raw %}{% include install_instructions/<filename.html> %}{% endraw %}`
where `<filename.html>` needs to be replaced by one of the files
in the `_includes/install_instructions` folder.

## Homepage: who can attend?

If you want to specify who can attend the workshop you are advertising,
there is a commented-out section in `index.md` that you can use to
inform workshop website visitors of who can attend the event.
You may want to specify that only members of your university,
department, etc. can attend or that the event is open to the public.
We don't provide templated text for this as each situation is different.
We do provide a section, called "Who can attend?" for you to specify this
information.

To use it, move the {% raw %}{% endcomment %}{% endraw %} line above the
`<p>` tag marking the beginning of this section and edit the paragraph
to reflect the attendance policy for your workshop.

## Updating the repository

If for some reason,
such as the installation instructions having become disconnected
with the current lesson material,
you need to get changes from this repository
into the clone of it with your workshop page,
please follow the steps bellow:

1. Add the workshop-template repository as upstream:
    ~~~
    $ git remote add upstream https://github.com/carpentries/workshop-template.git
    ~~~
    {: .language-bash}

2. Fetch the data from upstream repository (also know as the workshop-template
    repository):
    ~~~
    $ git pull upstream
    ~~~
    {: .language-bash}

3. Address possible merge conflicts, and
    ~~~
    $ git commit -a
    ~~~
    {: .language-bash}

4. Push the changes to your repository on GitHub:
    ~~~
    $ git push origin gh-pages
    ~~~
    {: .language-bash}


{% include links.md %}
