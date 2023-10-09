---
layout: post
title: how to make line between two points
date: 2023-09-23
description:  # Add post description (optional)
img: i-rest.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Qgis,经济地理]
---

# DrawLine

```
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

![Final Results]({{site.baseurl}}/assets/img/img-for-makeline-eg.jpg)

# change

```
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
