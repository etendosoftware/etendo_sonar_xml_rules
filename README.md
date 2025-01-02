# Etendo Sonar XML Rules

Collect all XML rules used in Etendo

### Adding new XML rules

1. Log in to SonarQube as a quality profile administrator.
2. Go to the `Rules` page.
3. In the filters section, expand the Language filter category and select `XML`.
4. Expand the `Template` filter category and select `Show Templates Only`.
5. Look for the `Track breaches of an XPath rule` template.
6. Click on it to select it, then use the interface controls to create a new instance.
7. Fill in the form that pops up.
    * **Name**: the name for the new rule
    * **Key**: a key that will identify the new rule. Can be the name, replacing spaces with underscores. For example \
    _Name_: New Rule For XML \
    _Key_: New_Rule_For_XML
    * **Type**: There are three types of rules:
        * _Bug_: A coding mistake that can lead to an error or unexpected behavior at runtime.
        * _Vulnerability_: A point in the code that's open to attack.
        * _Code Smell_: A maintainability issue that makes the code confusing and difficult to maintain. \
        \
        For these types of rules, we tipically use Bug or Code Smell
    * **Description**: explain in detail the issue being checked by this rule, and why is it an issue in the first place. Use examples to show compliant and non-compliant code.
    * **File Pattern**: The files to be validated using Ant-style matching patterns. For example:
        * `**/src-db/tables/*.xml` - any XML file in the src-db/tables folder
        * `**/src-db/**/*.xml` - any XML file in the src-db folder
        * `**/AD_ELEMENT.xml` - XML files named AD_ELEMENT in any place
    * **Expression**: The XPath query that will match with the non-compliant code. To develop these types of expressions, the following tool will be useful: [Free Online XPath Tester / Evaluator](https://www.freeformatter.com/xpath-tester.html) \
    \
    With this tool, you can load an xml file that triggers the issue, and try to write an XPath expression that matches with the code triggering it. You can check for examples of XPath expressions in the other rules created from this template. 
    * **Message**: the text that will be shown on non-compliant code

    > [!TIP]
    > Sonar provides some [useful guidelines on writing new rules](https://docs.sonarsource.com/sonarqube/latest/extension-guide/adding-coding-rules/#guidelines-when-writing-rules-for-issues) that should be taken into account for these XML Rules
8. Once you've created your rule, you'll need to add it to a quality profile and run an analysis to see it in action.

### Exporting added XML rules

1. Log in to SonarQube as quality profile administrator
2. Go to the `Quality Profiles` page
3. Focus onto the desired XML profile to import
4. Click on the ⚙️ -> Back up. An xml file will be downloaded, containing all the profile's XML rules
5. Rename the downloaded file to `sonar_XML_rules_backup.xml`
6. Replace the backup present in this repository with the new backup
7. Upload the changes to this repository

### Importing backup to SonarQube server

1. Get the backup from this repository
2. Log in to SonarQube as quality profile administrator
3. Go to the `Quality Profiles` page
4. Click on `Restore` button
5. On the popup that appears, load the repository backup file and click on `Restore`
6. All backup rules will be loaded correctly