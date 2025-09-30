Following examples help to define your own custom template for the labeling interface in Label Studio.

Tropical storm masks using Dvorak categories with SAM2 integration.

```
<View>
  <Image name="image" value="$image" zoom="true" zoomControl="true"/>
  <BrushLabels name="tag" toName="image">    
  	<Label value="dvorak_0" background="#FFA39E"/>
    <Label value="dvorak_1" background="#D4380D"/>
    <Label value="dvorak_2" background="#FFC069"/>
    <Label value="dvorak_3" background="#AD8B00"/>
    <Label value="dvorak_4" background="#D3F261"/>
    <Label value="dvorak_5" background="#389E0D"/>
    <Label value="dvorak_6" background="#5CDBD3"/>
    <Label value="dvorak_7" background="#096DD9"/>
    <Label value="dvorak_8" background="#ADC6FF"/>
  </BrushLabels>
  
   <KeyPointLabels name="tag2" toName="image" smart="true">
    <Label value="dvorak_0" smart="true" background="#FFA39E" showInline="true"/>
    <Label value="dvorak_1" smart="true" background="#D4380D" showInline="true"/>
    <Label value="dvorak_2" smart="true" background="#D4380D" showInline="true"/>
    <Label value="dvorak_3" smart="true" background="#AD8B00" showInline="true"/>
    <Label value="dvorak_4" smart="true" background="#D3F261" showInline="true"/>
    <Label value="dvorak_5" smart="true" background="#389E0D" showInline="true"/>
    <Label value="dvorak_6" smart="true" background="#5CDBD3" showInline="true"/>
    <Label value="dvorak_7" smart="true" background="#096DD9" showInline="true"/>
    <Label value="dvorak_8" smart="true" background="#ADC6FF" showInline="true"/>
  </KeyPointLabels>
</View>
```

