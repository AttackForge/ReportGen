# AttackForge ReportGen
Welcome to the community for AttackForge ReportGen!

AttackForge ReportGen is a free tool to help security teams and penetration testers create powerful and robust automated custom reports.

It works by combining a DOCX template with an AttackForge project JSON file, and outputs a DOCX report.

You can upload your templates into your AttackForge tenant for on-demand custom reports.

# Tutorial
If you are a first time user, we recommend watching this tutorial video: https://youtu.be/W3nKWOQBJGU

# Getting Started
Download ReportGen from your AttackForge product, or use the online version at https://attackforge.com/reportgen.html

<img width="1915" height="992" alt="reportgen" src="https://github.com/user-attachments/assets/40064f85-d519-46ec-b817-8e3006987628" />

On the ReportGen homepage, you will find links to the following:
- **Templates**
  - This is where you can download and modify existing templates to get started fast.
- **Filters**
  - Filters help to get the right data that you need, or to transform or style it.
- **Functions**
  - Functions help to provide powerful ways to create logic in your templates.
- **Styles**
  - This is where you can find options to customize your rich-text fields with custom Word styles.
- **Tables**
  - Examples how to create tables in your templates.
- **Charts**
  - Examples how to use and configure charts in your templates.
- **Options**
  - This is where you can find options you can include in your templates.
- **Examples**
  - Find all sorts of examples on how to achieve use cases, such as using custom fields or adding custom logic.
- **Releases**
  - Check out the latest and greatest features we're adding to ReportGen and AttackForge.
- **CLI**
  - Download the ReportGen CLI tool for programmatic offline report generation.

ReportGen includes various templates which are great for intermediate and advanced users, and might be tempting to start with. However we recommend first getting used to how the tool works and understanding the basics. After that, you can add your logic, styling and advanced features like charts and tables.

<img width="1906" height="992" alt="templates" src="https://github.com/user-attachments/assets/ad8fd806-82d3-485e-9fda-f98dd2eacd20" />

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
{$help[Root Scope][scope]}
```
This template will print all of the available data - in your ReportGen browser console:

<img width="1919" height="992" alt="help-1" src="https://github.com/user-attachments/assets/dad85d8e-f8e8-40ad-806d-2eab96d37f30" />

If you wanted to print the available data for every unique vulnerability as you are looping through each one, you can add the helper function inside the loop as follows:
```
{#vulnerabilities}
{$help[Vuln Data][scope]}
{/}
```

<img width="1669" height="1245" alt="insert-help" src="https://github.com/user-attachments/assets/1322ebb9-2c98-4c84-8d80-e3f905d1a8ae" />

Now you will get a help printout in your ReportGen browser console for every interation of the loop on unique vulnerabilities. Here you can see the data structure for every vulnerability:

<img width="1917" height="991" alt="vulns-print" src="https://github.com/user-attachments/assets/08ebba5d-8dfe-44ad-bf3e-fe9deabe9ba2" />

# Creating Automated Reports

Looking to create automated reports in your existing code or scripts?

Try the [ReportGen Library](https://www.npmjs.com/package/@attackforge/reportgen-node) or [ReportGen CLI](https://www.npmjs.com/package/@attackforge/reportgen-cli) - available on [NPM](https://www.npmjs.com/search?q=attackforge)

<img width="2055" alt="1" src="https://github.com/AttackForge/ReportGen/assets/131424301/3ba93545-e116-43bb-aa01-22cee9b040e6">

Creating automated and programatic reports is easy using ReportGen Library or CLI, for example:

```
> npx @attackforge/reportgen-cli
Usage: reportgen [--output=output_file.docx] [--product=product] [--template=template_file.docx] [input_file.json]
Options:
--output=output_file.docx
--product=community|core|enterprise
--template=template_file.docx
```


Head over to [Issues](https://github.com/AttackForge/ReportGen/issues) for more examples, to request a feature, raise a bug, or ask for help.

:heart:
Team AttackForge
