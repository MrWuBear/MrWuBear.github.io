---
layout: post
title: Useful Codes In QGIS
date: 2023-09-23
description:  # Add post description (optional)
img: i-rest.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Qgis]
---

# DrawLine

![Final Results]({{site.baseurl}}/assets/img/img-for-makeline-eg.jpg)

```python
make_line(
    @geometry ,
	with_variable(
		'index_',
		LinkedIndex,
		eval(
			'geometry(get_feature( 
			\'PointB\',
			\'Index\',
			' ||concat('\'',@index_,'\'') || '
			))'
		)
	)
)
```

# change
```python
make_line(
	start_point($geometry) ,
	translate(
		centroid($geometry),
		$length/10,
		$length/10
	),
	end_point($geometry)
)
```
