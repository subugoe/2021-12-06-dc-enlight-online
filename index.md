---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "SUB Göttingen"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "Germany"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "english"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "45"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-1"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "Oct 11-15, 2021"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: ""    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2021-10-11      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2021-10-15        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Britta Timmermann", "Timo Gnadt", "Hanna Varachkina", "Raisa Barthauer", "Julika Mimkes", "Péter Király"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Harald Kusch"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["varachkina@sub.uni-goettingen.de"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}


{% comment %}

{% endcomment %}


{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody.  For workshops at a physical location, the workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>
{% else %}
  We are dedicated to providing a positive and accessible learning environment for all. Please
  notify the instructors in advance of the workshop if you require any accommodations or if there is
  anything we can do to make this workshop more accessible to you.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
{% if site.carpentry == "pilot" %}
<p><a href="{{ site.pilot_pre_survey }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.pilot_post_survey }}">Post-workshop Survey</a></p>
{% elsif site.pilot_pre_survey or site.pilot_post_survey %}
<div class="alert alert-danger">
WARNING: you have defined custom pre- and/or post-survey links for
a workshop not configured as a lesson pilot
(the value of `site` is not set to `pilot` in `_config.yml`).
Please comment out the `pilot_pre_survey` and `pilot_post_survey` fields
in `_config.yml` or, if this workshop is a lesson pilot,
change the value of `carpentry` to `pilot`.
</div>
{% else %}
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">Schedule</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% elsif site.carpentry == "pilot" %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. If you would like to know the timing of these breaks in advance, please [contact the workshop organisers](#contact). For a list of lesson sections and estimated timings, [visit the lesson homepage]({{ site.lesson_site }}).
{% comment %}
Edit/replace the text above if you want to include a schedule table.
See the contents of the _includes/custom-schedule.html file for an example of
how one of these schedule tables is constructed.
{% endcomment %}
{% endif %}

<hr/>


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to software as described below.
  In addition, you will need an up-to-date web browser.
</p>
<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}
{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}


<h2 id="setup"Tools</h2>
These are the installation instructions for the tools used
during the workshop.

{% comment %}
{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% elsif site.carpentry == "pilot" %}
Please check the "Setup" page of
[the lesson site]({{ site.lesson_site }}) for instructions to follow
to obtain the software and data you will need to follow the lesson.
{% endif %}
{% endcomment %}
<div id="openrefine">
  <h3>OpenRefine</h3>
  <p>
    For this lesson you will need <em>OpenRefine</em> and a
    web browser. <em>Note:</em> this is a Java program that runs on your machine (not in the cloud).
    It runs inside a web browser, but no web connection is needed.
  </p>

  <div>
    <ul class="nav nav-tabs" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#openrefine-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#openrefine-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#openrefine-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="openrefine-windows">
        <ol>
          <li>
            Check that you have either the Firefox or the Chrome browser installed and set as your default browser.
            <strong>OpenRefine runs in your default browser.</strong>
            It will not run correctly in Internet Explorer.
          </li>
          <li>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a></li>
          <li>Create a new directory called OpenRefine.</li>
          <li>Unzip the downloaded file into the OpenRefine directory by right-clicking and selecting "Extract ...". </li>
          <li>Go to your newly created OpenRefine directory.</li>
          <li>Launch OpenRefine by clicking <code>openrefine.exe</code> (this will launch a command prompt window, but you can ignore that - just wait for OpenRefine to open in the browser).</li>
          <li>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</li>
        </ol>
      </article>
      <article role="tabpanel" class="tab-pane" id="openrefine-macos">
        <ol>
          <li>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong> It may not run correctly in Safari.</li>
          <li>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</li>
          <li>Create a new directory called OpenRefine.</li>
          <li>Unzip the downloaded file into the OpenRefine directory by double-clicking it.</li>
          <li>Go to your newly created OpenRefine directory.</li>
          <li>Launch OpenRefine by dragging the icon into the Applications folder.</li>
          <li>Use <kbd>Ctrl</kbd>-click/Open ... to launch it.</li>
          <li>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</li>
        </ol>
      </article>
      <article role="tabpanel" class="tab-pane" id="openrefine-linux">
        <ol>
          <li>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong></li>
          <li>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</li>
          <li>Make a directory called OpenRefine.</li>
          <li>Unzip the downloaded file into the OpenRefine directory.</li>
          <li>Go to your newly created OpenRefine directory.</li>
          <li>Launch OpenRefine by entering <code>./refine</code> into the terminal within the OpenRefine directory.</li>
          <li>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</li>
        </ol>
      </article>
    </div>
  </div>
</div>

<div id="sql">
  <h3>SQLite</h3>

  <p>
    SQL is a specialized programming language used with databases.  We
    use a database manager called
    <a href="https://www.sqlite.org/">SQLite</a> in our lessons.
  </p>

  <div>
    <ul class="nav nav-tabs" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#sql-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#sql-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#sql-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
      <li role="presentation"><a data-os="web" href="#sql-web" aria-controls="Web" role="tab" data-toggle="tab">Web</a></li>
    </ul>
    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="sql-windows">
        <ul>
          <li>Run "Git Bash" from the Start menu</li>
          <li>Copy the following <code>curl -fsSL  {{site.url}}{{site.baseurl}}/getsql.sh | bash</code></li>
          <li>Paste it into the window that Git Bash opened. If you're unsure, ask an instructor for help</li>
          <li>You should see something like <code>3.27.2 2019-02-25 16:06:06 ...</code></li>
        </ul>

          <p>If you want to do this manually, download <a href="https://www.sqlite.org/2019/sqlite-tools-win32-x86-3270200.zip">sqlite3</a>, make a bin directory in the user's home directory, unzip sqlite3, move it into the bin directory, and then add the bin directory to the path.</p>

      </article>
      <article role="tabpanel" class="tab-pane" id="sql-macos">
        <p>
          SQLite comes pre-installed on macOS.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane" id="sql-linux">
        <p>
          SQLite comes pre-installed on Linux.
        </p>
      </article>
      <article role="tabpanel" class="tab-pane" id="sql-web">
        <ul>
          <li>In case of problems: register for an account at <a href="https://www.pythonanywhere.com/">https://www.pythonanywhere.com</a></li>
          <li>Download <a href="http://swcarpentry.github.io/sql-novice-survey/files/survey.db">survey.db</a></li>
          <li>Click on files and upload survey.db</li>
          <li>Click on dashboard and Choose new console <code>bash</code></li>
        </ul>
      </article>
    </div>
  </div>

  <p><strong>If you installed Anaconda, it also has a copy of SQLite
      <a href="https://github.com/ContinuumIO/anaconda-issues/issues/307">without support to <code>readline</code></a>.
      Instructors will provide a workaround for it if needed.</strong></p>
</div>

<div id="r">
  <h3>R</h3>

  <p>
    <a href="https://www.r-project.org">R</a> is a programming language
    that is especially powerful for data exploration, visualization, and
    statistical analysis. To interact with R, we use
    <a href="https://www.rstudio.com/">RStudio</a>.
  </p>

  <div>
    <ul class="nav nav-tabs" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#rstats-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#rstats-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#rstats-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="rstats-windows">
        <p>
          Install R by downloading and running
          <a href="https://cran.r-project.org/bin/windows/base/release.htm">this .exe file</a>
          from <a href="https://cran.r-project.org/index.html">CRAN</a>.
          Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
          Note that if you have separate user and admin accounts, you should run the
          installers as administrator (right-click on .exe file and select "Run as
          administrator" instead of double-clicking). Otherwise problems may occur later,
          for example when installing R packages.
        </p>
        <h4>Video Tutorial</h4>
        <div class="yt-wrapper2">
        <div class="yt-wrapper">
        <iframe type="text/html" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" src="https://www.youtube-nocookie.com/embed/q0PjTAylwoU?modestbranding=1&playsinline=1&iv_load_policy=3&rel=0" class="yt-frame" allowfullscreen></iframe>
        </div>
        </div>
      </article>
      <article role="tabpanel" class="tab-pane" id="rstats-macos">
        <p>
          Install R by downloading and running
          <a href="https://cran.r-project.org/bin/macosx/R-latest.pkg">this .pkg file</a>
          from <a href="https://cran.r-project.org/index.html">CRAN</a>.
          Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
        </p>
        <h4>Video Tutorial</h4>
        <div class="yt-wrapper2">
        <div class="yt-wrapper">
        <iframe type="text/html" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" src="https://www.youtube-nocookie.com/embed/5-ly3kyxwEg?modestbranding=1&playsinline=1&iv_load_policy=3&rel=0" class="yt-frame" allowfullscreen></iframe>
        </div>
        </div>
      </article>
      <article role="tabpanel" class="tab-pane" id="rstats-linux">
        <p>
          Instructions for R installation on various Linux platforms (debian,
          fedora, redhat, and ubuntu) can be found at
          <https://cran.r-project.org/bin/linux/>. These will instruct you to
          use your package manager (e.g. for Fedora run
          <code>sudo dnf install R</code> and for Debian/Ubuntu, add a ppa
          repository and then run <code>sudo apt-get install r-base</code>).
          Also, please install the
          <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
        </p>
      </article>
    </div>
  </div>
</div>
