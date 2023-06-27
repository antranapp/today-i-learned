---
title: How to create thumbnail image for all images inside a folder using Imagick?
createdAt: 2023-06-27T16:56:57Z
---

# How to create thumbnail image for all images inside a folder using Imagick?

```shell
for file in ./*; do output_file="./$(basename "$file" | cut -d. -f1).jpg"; convert "$file" -resize 200x200^ -gravity center -extent 200x200 "$output_file.thumbnail.jpg"; done
```