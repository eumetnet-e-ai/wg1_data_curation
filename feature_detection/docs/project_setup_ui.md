See [Label Studio documentation](https://labelstud.io/guide/setup_project) for more information on project setup. 

**Use the [conventions](project_naming_conventions.md)
![](images/ls-project-ui-2.png) to set up your project name and description.**

1. Create a new project in Label Studio.
![](images/ls-project-ui-1.png)

2. Give it a name and description according to the [conventions](project_naming_conventions.md)
![](images/ls-project-ui-2.png)

3. Set up the labeling interface according to the [Label Studio documentation](https://labelstud.io/guide/setup). You can skip the *Data Import* step. 
<br><br>
Select the *Labeling Interface* tab and choose the appropriate interface for your project. You can choose one of the ready templates (most typically mask, BBOX, or polygon, depending on your ML method) or create a custom interface based on [ready templates](labeling_interface_templates.md).
![](images/ls-project-ui-3.png)

4. After selecting the template, you get a configuration for adding labels. Note that in order to use e.g. SAM2 model in your projects, you shall require custom label configuration. See [Adding model integration](adding_model_integration.md) for more.
![](images/ls-project-ui-4.png)
(You typicall want to enable controls to zoom in and out.)

5. Import data following [Copying data to Label Studio](copying_data_to_labelstudio.md).

6. Add model integration following [Adding model integration](adding_model_integration.md).

