---
layout: post
title: "S3 fun in Ruby - count S3 bucket size"
description: 
category: 
tags: [Ruby] [AWS] [S3]
---

I love Ruby and I always will. It was the very first language I learnt after academic struggle with pure ANSI C and (para-)objective programming classes in C++. 


There is a really decent 's3' gem. This tiny sctipt takes all files from your S3 bucket and sums up their sizes to diplay you total amount of disk space on S3, that your bucket takes:

```
require "s3"
# Make sure that you create separate AWS user
# which has at least read-only access to your S3 bucket(s)
service = S3::Service.new(:access_key_id => "AKKMYIDTOAWSSERVICESAKK",
     			  :secret_access_key => "qwertyqwertyqwertyqwerty")

bucket = service.buckets.find("my-bucket-name")

total_size = 0
bucket.objects.each do | build |
 total_size += build.size.to_i
end

puts total_size
``` 

The result will be diplayed in Bytes, so tremendously looking 52609580 in my case turned out to be ~50 Megs :)

{% include JB/setup %}
