[Label Sudio documentation](https://labelstud.io/guide/labeling) provides basic guidance for labeling. 

This guides does not try to be the comprehensive guide for labeling but insead show most common functions with tips and screenshots.

2. In order to start labeling, select the project and then select task from the list. Note that you can filter tasks without any labels adding *Annotations* < 1 to *filters* 
![](images/ls-project-label-ui-1.png)
3. Labeling view screenshot is below. This example contains both preannotations ('predictions') from IBtRACKS (see [example script for adding predcitions](./prepare_tasks_and_predictions_skeleton.py)) and SAM2 integration (see [adding_model_integration](./adding_model_integration.md))
![](images/ls-project-label-ui-2.png)
Following things are worth noting from the screenshot:
    1. Proceed to the next step by selecting the next task from the list (1)
    2. In order to add a manual annotation
        1. select the label from the top list (2) 
        2. tool from the right (5) 
        3. paint the area on the image (in case of masks)
    3. If you have a model integration and want to use the model
        1. enable the model (4)
        2. select the label from the bottom list (3)
        3. select the keypoint tool from right (6)
        4. click the center of the feature on the image 5. accept the proposal. <br>
    ![](images/ls-project-label-ui-3.png)
4. If you have pre-annotations ('predictions') added, you see the area and class on the image
    - You can click visibility of the pre-annotation using small view symbol (7) which appears when you hover the mouse over the pre-annotation
    - You can delete the pre-annotation by clicking its name (8) and then clicking the trash bin icon (9)
    - You can save the pre-annotation as annotation by clicking the submit button (10)
    - **Note that if you add your own annotation, and click Submit, also pre-annotations get saved**

