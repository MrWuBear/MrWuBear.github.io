---
layout: post
title: Useful Codes In QGIS
date: 2023-09-23
description:  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Qgis]
---

# DrawLine
```Python
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