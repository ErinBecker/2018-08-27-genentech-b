---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "dc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc")
venue: "Genentech"        # brief name of host site without address (e.g., "Euphoric State University")
address: "SSF-82-14E Union Square Training Room"      # street address of workshop (e.g., "123 Forth Street, Blimingen, Euphoria")
country: "us"      # country (lowercase two-letter ISO code such as "fr" - see https://en.wikipedia.org/wiki/ISO_3166-1)
language: "en"     # language (lowercase two-letter ISO code such as "fr" - see https://en.wikipedia.org/wiki/ISO_639-1)
latlng: "37.656330,-122.379270"       # fractional latitude and longitude (e.g., "41.7901128,-87.6007318"; you can use http://www.latlong.net/)
humandate: "August 27-28, 2018"    # human-readable date (e.g., "Feb 17-18, 2020")  
humantime: "9:00 am - 5:00 pm"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2018-08-27      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2018-08-28        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Erin Becker", "Kelly Rowland"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Aleksandra Taranov", "Marinella Callow", "Sarah Headland", "Jennifer Giltnane", "Altaf Kassam"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["ebecker@carpentries.org"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes: https://pad.carpentries.org/2018-08-27-genentech           # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
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
  EVENTBRITE

  This block includes the Eventbrite registration widget if
  'eventbrite' has been set in the header.  You can delete it if you
  are not using Eventbrite, or leave it in, since it will not be
  displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
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
{% if page.carpentry == "swc" %}
  {% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/intro.html %}
{% endif %}

{% comment %}
  AUDIENCE

  Explain who your audience is.  (In particular, tell readers if the
  workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  LOCATION

  This block displays the address and links to maps showing directions
  if the latitude and longitude of the workshop have been set.  You
  can use https://itouchmap.com/latlong.html to find the lat/long of an
  address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
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
  <strong>Requirements:</strong> Participants must bring a laptop with a
  Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges
  on. They should have a few specific software packages installed (listed
  <a href="#setup">below</a>). They are also required to abide by
  {% if page.carpentry == "swc" %}
  Software Carpentry's
  {% elsif page.carpentry == "dc" %}
  Data Carpentry's
  {% elsif page.carpentry == "lc" %}
  Library Carpentry's
  {% endif %}
  <a href="{{site.swc_site}}/conduct.html">Code of Conduct</a>.
</p>

{% comment %}
  ACCESSIBILITY

  Modify the block below if there are any barriers to accessibility or
  special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong> We are committed to making this workshop
  accessible to everybody.
  The workshop organizers have checked that:
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

{% comment %}
  CONTACT EMAIL ADDRESS

  Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
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

<hr/>

{% comment %} 
 SURVEYS - DO NOT EDIT SURVEY LINKS 
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
{% if site.carpentry == "swc" %} 
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif site.carpentry == "dc" %}
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif site.carpentry == "lc" %}
<p><a href="{{ site.lc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.lc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>

<h2 id="schedule">Schedule</h2>

<div class="row">
  <div class="col-md-6">

    <h3>Monday, August 27</h3>
    <table class="table table-striped">
        <tr> <td>9 - 10:15am</td>  <td><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/">Data Organization in Spreadsheets</a></td> </tr>
        <tr> <td>10:15 - 10:30am</td> <td>Coffee Break</td></tr>
        <tr> <td>10:30 - 12</td> <td><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/">Data Cleaning with OpenRefine</a></td> </tr>
        <tr> <td>12 - 1pm</td> <td>Lunch</td> </tr>
        <tr> <td>1 - 1:45pm</td> <td><a href="http://www.datacarpentry.org/R-ecology-lesson/00-before-we-start.html">Getting Started with R</a></td> </tr>
        <tr> <td>1:45 - 3:15pm</td> <td><a href="http://www.datacarpentry.org/R-ecology-lesson/01-intro-to-r.html">Introduction to R</a></td> </tr>
        <tr> <td>3:15 - 3:30pm</td> <td>Coffee Break</td></tr>
        <tr> <td>3:30 - 4:15pm</td> <td><a href="http://www.datacarpentry.org/R-ecology-lesson/01-intro-to-r.html">Introduction to R (cont)</a></td> </tr>
        <tr> <td>4:15 - 5pm</td> <td><a href="http://www.datacarpentry.org/R-ecology-lesson/02-starting-with-data.html">Starting with Data in R</a></td> </tr>
    </table>
 
 
    <h3>Tuesday, August 28</h3>
    <table class="table table-striped">
        <tr> <td>9 - 10:30am</td> <td><a href="http://www.datacarpentry.org/R-ecology-lesson/03-dplyr.html">Manipulating Data in R</a></td> </tr>
        <tr> <td>10:30 - 10:45am</td> <td>Coffee Break</td></tr>
        <tr> <td>10:45 - 12:00pm</td> <td><a href="http://www.datacarpentry.org/R-ecology-lesson/04-visualization-ggplot2.html">Visualizing Data in R</a></td> </tr>
        <tr> <td>12 - 1pm</td> <td>Lunch</td> </tr>
        <tr> <td>1 - 1:30pm</td> <td><a href="http://www.datacarpentry.org/R-ecology-lesson/04-visualization-ggplot2.html">Visualizing Data in R (cont)</a></td> </tr>
        <tr> <td>1:30 - 3pm</td> <td>Capstone: Working with Tabular Genomics Data in R</td> </tr>
        <tr> <td>3 - 3:15pm</td> <td>Coffee Break</td></tr>
        <tr> <td>3:15 - 5pm</td> <td>Capstone: Working with Tabular Genomics Data in R (cont)</td> </tr>
    </table>
 </div>
</div>

{% comment %}
  Collaborative Notes

  If you want to use an Etherpad, go to

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  where 'YYYY-MM-DD-site' is the identifier for your workshop,
  e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
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
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  Data Carpentry
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to the software described below.
  In addition, you will need an up-to-date web browser.
</p>
<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

<div id="r"> {% comment %} Start of 'R' section. {% endcomment %}
  <h3>R</h3>

  <p>
    <a href="https://www.r-project.org">R</a> is a programming language
    that is especially powerful for data exploration, visualization, and
    statistical analysis. To interact with R, we use
    <a href="https://www.rstudio.com/">RStudio</a>.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="r-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=q0PjTAylwoU">Video Tutorial</a>
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
    </div>
    <div class="col-md-4">
      <h4 id="r-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=5-ly3kyxwEg">Video Tutorial</a>
      <p>
        Install R by downloading and running
        <a href="https://cran.r-project.org/bin/macosx/R-latest.pkg">this .pkg file</a>
        from <a href="https://cran.r-project.org/index.html">CRAN</a>.
        Also, please install the
        <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-linux">Linux</h4>
      <p>
        You can download the binary files for your distribution
        from <a href="https://cran.r-project.org/index.html">CRAN</a>. Or
        you can use your package manager (e.g. for Debian/Ubuntu
        run <code>sudo apt-get install r-base</code> and for Fedora run
        <code>sudo dnf install R</code>).  Also, please install the
        <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio IDE</a>.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'R' section. {% endcomment %}

<div id="openrefine"> {% comment %} Start of 'OpenRefine' section. {% endcomment %}
  <h3>OpenRefine</h3>
  <p>
    For this lesson you will need <em>OpenRefine</em> and a
    web browser. <em>Note:</em> this is a Java program that runs on your machine (not in the cloud).
    It runs inside a web browser, but no web connection is needed.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="openrefine-windows">Windows</h4>
      <p>
        Check that you have either the Firefox or the Chrome browser installed and set as your default browser.
        <strong>OpenRefine runs in your default browser.</strong>
        It will not run correctly in Internet Explorer.
      </p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a></p>
      <p>Create a new directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory by right-clicking and selecting "Extract ...". </p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by clicking <code>google-refine.exe</code> (this will launch a command prompt window, but you can ignore that - just wait for OpenRefine to open in the browser).</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-mac">Mac</h4>
      <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong> It may not run correctly in Safari.</p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Create a new directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory by double-clicking it.</p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by dragging the icon into the Applications folder.</p>
      <p>Use <code>Ctrl-click/Open ... </code> to launch it.</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-linux">Linux</h4>
      <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong></p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Make a directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory.</p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by entering <code>./refine</code> into the terminal within the OpenRefine directory.</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
  </div>
</div> {% comment %} End of 'OpenRefine' section. {% endcomment %}
