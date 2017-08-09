### EMOTIC Dataset
#### Structure description
#### The entire annotations (or ground truth) is stored inside a matlab structure file _Annotations_combined.mat_

Each structure entry has all the information (including the annotation) about a single person under consideration.   

    Annotations(1) = 
    
                      filename: '007eear5kx5qhbzewz.jpg'   
                        folder: 'emodb_small/images'    
                    image_size: [1x1 struct]    
       hasAnnotations_discrete: 'YES'    
     hasAnnotations_continuous: 'YES'    
             original_database: [1x1 struct]   
                        person: [1x2 struct]   

The person field above `[1x2 struct]` shows that the image has 2 persons and the details about each is stored in this field.  
For the first person, 
```
Annotations(1).person(1) =

                 body_bbox: [215 111 580 352]
                 head_bbox: [228 118 318 231]
    annotations_categories: [1x1 struct]
    annotations_continuous: [1x1 struct]
        annotations_gender: [1x1 struct]
           annotations_age: [1x1 struct]
            estimated_mask: []
            estimated_eyes: [0.6049 0.4196]
       estimated_head_bbox: [263 111 437 227]
            estimated_bbox: [294 167 580 384]
                confidence: 0.7692
```
Each bbox has the format `[x1 y1 x2 y2]` - the four co-ordinates of the bounding rectangle.   
`estimated_*` filed represents the bboxes that were obtained after running body ([link](https://arxiv.org/abs/1506.01497)) and face R-CNN ([link](https://arxiv.org/abs/1606.03473)) based detectors on each person.   

The confidence level with which the bboxes were estimated is given by   
```
Annotations(1).person(1).confidence = 0.9
``` 

The annotated categories (ground truth) of that person by a given worker is given by  
```
Annotations(1).person(1).annotations_categories = 
     
            worker_id: 'AHI8X7NP92DAV'
            work_time: 511
             batch_id: 2
           categories: {'Affection'  'Pleasure'  'Happiness'}
```
The continuous dimension annotations (ground truth) of a person by a given worker is shown by
```
Annotations(1).person(1).annotations_continuous = 

    worker_id: 'A3C8KN9HKGGZKG'
    work_time: 361
     batch_id: 128
      valence: 8
      arousal: 4
    dominance: 10
```
The gender of the person annotated by the worker is shown by
```
Annotations(1).person(1).annotations_gender = 

    worker_id: 'A3C8KN9HKGGZKG'
    work_time: 361
     batch_id: 128
       gender: 'Female'
```
The age of the person annotated by the worker is given by
``` 
Annotations(1).person(1).annotations_age 

    worker_id: 'A3C8KN9HKGGZKG'
    work_time: '361'
          age: 'Adult'
     batch_id: 128
```
     
