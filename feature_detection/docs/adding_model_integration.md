See Label Studio documentat at https://labelstud.io/guide/ml

To add model integration in Label Studio, follow these steps:

1. Go to the *Settings* tab of your project.
2. Choose *Model*
![](images/ls-project-model-ui-1.png)
3. Choose *Connect Model*
![](images/ls-project-model-ui-2.png)
4. Add following data:

    |  |  |
    |-------|-------|
    | Name  | (e.g. `SAM2`) |
    | URL   | `http://nuclio-sam2-ml-backend.annotation-tools.svc.cluster.local:8080` |
    | Authentication | `No Authentication` |
    | Extra parameters | - |
    | Interactive preannotations |  `Yes` |

5. Save your changes. Afterwards, do NOT select *Start model training on annotation submission*. The function is not implemented yet. 

6. Add necessary tags to your project configuration to tell the model which labels to use. 

   1. Go to the *Settings* tab of your project and select 'code'
    ![](images/ls-project-model-ui-3.png)

    2. Add the `<KeyPointLabels name="tag2" toName="image" smart="true">`**. Add the same labels you already have with `smart="true"` and `showInline` attributes under the `KeyPointLabels`.<br>
    <br>
    For example, if you have the following configuration:
        ```
        <BrushLabels name="tag" toName="image">    
            <Label value="dvorak_0" background="#FFA39E" />
        </BrushLabels>
        ```
         add the following configuration:    
        ```
        <KeyPointLabels name="tag2" toName="image" smart="true">
            <Label value="dvorak_0" smart="true" background="#FFA39E" showInline="true"/>
        </KeyPointLabels>
        ```

        See [labeling_interface templates](labeling_interface_templates.md) for more examples.

        ** (assuming that you have `image` tag in your configuration)
