# AttackForge ReportGen
Welcome to the community for AttackForge ReportGen!

AttackForge ReportGen is a free tool to help penetration testers create powerful and robust automated pentest reports.

It works by combining a DOCX template with an AttackForge project JSON file, and outputs a DOCX report.

For AttackForge Core and Enterprise users - you can upload your templates into your tenant for on-demand reports.

## Tutorial
If you are a first time user, we recommend watching this tutorial video: https://youtu.be/W3nKWOQBJGU

## Getting Started
Download ReportGen from your AttackForge product, or use the online version at https://attackforge.com/reportgen.html

When you open ReportGen in your browser - start by selecting your AttackForge product (Community / Core / Enterprise) then select DOCX.

<img width="2039" alt="image" src="https://github.com/AttackForge/ReportGen/assets/131424301/2620630e-5ea9-4643-bf35-a90633ee2c5d">

On the ReportGen homepage, you will find links to the following:
- Tags
  - This is where all of the reporting tags are located, which can help you to see some of the data which you can use in your reports.
  - Tags represent data fields that you will use in your templates, for example {projectName}.
- Templates
  - This is where you can download and modify existing templates to get started fast.
- Options
  - This is where you can find options you can include in your templates.
- Functions
  - Functions help to provide powerful ways to create logic in your templates.
- Filters
  - Filters help to get the right data that you need, or to transform or style it.
- Tables
  - Examples how to create tables in your templates.
- Custom Fields
  - Examples how to include custom tags and custom fields (set in your AttackForge product) in your templates.
- Charts
  - Examples how to use and configure charts in your templates
  
ReportGen includes many templates which are great for intermediate and advanced users, and might be tempting to start with. However we recommend first getting used to how the tool works and understanding the basics. After that, you can add your logic, styling and advanced features like charts and tables.

<img width="2038" alt="image" src="https://github.com/AttackForge/ReportGen/assets/131424301/54b18d03-1ed7-4e32-91b2-fb52f0fdc787">

Take the following template as an example:
```
{#vulnerabilities}
{title}
{/}
```
This template will:
- loop through every unique vulnerability
- print the "title" of the vulnerability on a new line

Using the [test AttackForge project JSON export file](https://attackforge.com/attackforge-core-enterprise/report-templates/af-project-test-data.json) - the output DOCX report will include:
```
Unrestricted Upload of File with Dangerous Type
PHP Unsupported Version Detection
Inconsistent Access Control
Relative Path Traversal
Reflected Cross Site Scripting
Blind SQL Injection
etc.
```
If you wanted every vulnerability title to appear on one line, you could do the following:
```
{#vulnerabilities}{title}, {/}
```
This would output:
```
Unrestricted Upload of File with Dangerous Type, PHP Unsupported Version Detection, Inconsistent Access Control, Relative Path Traversal, ...
```
ReportGen works by *inherting the style and formatting applied to the tags inside your DOCX template using Word.*
Therefore, if you wanted the title of the vulnerability to be **bold** in your report, you would simply apply the bold formatting to the tag {title} - the same way you would usually bold text in Word. ReportGen will also inherit every line break between your tags.

Now that you know how to print the title of each vulnerability in your report, you can start to add more data to your report.

Take the following template as an example:
```
{$help[All Report Data]["%()"]}
```
This template will print all of the available data - in your ReportGen browser console:

<img width="2055" alt="All report data" src="https://github.com/AttackForge/ReportGen/assets/131424301/da821234-a3c6-4115-85fd-72a26eb8e5c3">

If you wanted to print the available data for every unique vulnerability as you are looping through each one, you can add the helper function inside the loop as follows:
```
{#vulnerabilities}
{$help[Vulnerability]["%()"]}
{/}
```
Now you will get a help printout in your ReportGen browser console for every interation of the loop on unique vulnerabilities. Here you can see the data structure for every vulnerability:

<img width="2054" alt="vulns" src="https://github.com/AttackForge/ReportGen/assets/131424301/ae63e707-e4a8-4a0e-a7d8-d324d4800cd4">

Head over to [Issues](https://github.com/AttackForge/ReportGen/issues) for more examples, to request a feature, raise a bug, or ask for help.

:heart:
Team AttackForge
