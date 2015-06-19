---
layout: post
title: "Debugging Celery task queue"
description: ""
category: 
tags: [python]  [celery] [debug]
---

Having process like fired up like this (just to give you analogy):
```
celery worker -B --workdir src -A myapp -n celery --concurrency=$CELERY_CONCURRENCY
```

Couple of ways to figure out what has stepped out of control:

First thing, for sure:
```
celery worker --workdir src -A myapp --concurrency=1 -l DEBUG
```

However, the most helpful and interesting commands are `celery status` - which show worker processes statuses - and really powerful `celery inspect` command. These two examples helped me a lot with figuring out what has been happening in my cluster:

```
celery inspect active --workdir src -A myapp  	# Dumps active tasks
celery inspect stats --workdir src -A myapp	# Dumps worker statistics
```

{% include JB/setup %}
