---
layout: "post"
title: "Image Down Sample"
date: "2020-03-06 19:17"
comments: true
tags: [Computer Vision]
categories: [Computer Vision]
toc: true

---

# Downsample

```matlab
% Downsample an image
img = imread('img/penny-farthing.png');
imshow(img);

img_d = downsample(img);    % 1/2 size
img_d = downsample(img_d);  % 1/4 size
img_d = downsample(img_d);  % 1/8 size

img_bd = blur_downsample(img);     % 1/2 size
img_bd = blur_downsample(img_bd);  % 1/4 size
img_bd = blur_downsample(img_bd);  % 1/8 size

imshow(imresize(img_d, size(img)));   % view downsampled image in original size
imshow(imresize(img_bd, size(img)));  % compare with blurred & downsampled

function img_d = downsample(img)
    img_d = img(1:2:end, 1:2:end); % selects rows, cols: 1,3,5, ....
end

function img_bd=blur_downsample(img)
    % TODO: img_bd = ? (blur by 5x5 gaussian, then downsample)
    img_bd = imfilter(img, fspecial('gaussian', [5 5]));
    img_bd = img_bd(1:2:end, 1:2:end);
end
```

Result after downsample:

![image-20200304110246285](/img/image-20200304110246285.png)

result of downsample after blur:

![image-20200304110319797](/img/image-20200304110319797.png)

# References

- Motion models, https://classroom.udacity.com/courses/ud810/lessons/3232568787/concepts/31898394400923
-
