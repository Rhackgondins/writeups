## Subliminal

```
I hid an image in this.
I really hope this triangle will haunt you in your sleep.
Author : iHuggsy
Format : Hero{}
```

<u>Programming language :</u> Python 🐍

This challenge leaves us with a short video of a dancing triangle in which each frame contains a small part of an image. There was a lot of strategies to solve it, but I decided to split each frame into PNG file to be able to recreate the original picture with a little script.

![Subliminal_Video](images/Subliminal_Video.png)



For the video conversion I use ffmeg.

![Subliminal_ffmpeg](images/Subliminal_ffmpeg.png)



And for the programming I firstly create an image with the same dimension as the video, which is 1080x720 and then, used the 'outXX.png' name of the PNG files to get the line number associate to their name.

```python
from PIL import Image

flag = Image.new('RGB', (1080, 720), color='white')
flag_pix = flag.load()

for i in range(1, 721):
  img = Image.open('out' + str(i) + '.png')
  pixels = img.load()

  for j in range(1080):
    flag_pix[j, i-1] = pixels[j, i-1]

flag.save('flag.png')
```



And this is the resulting image.

![Subliminal_Flag](images/Subliminal_Flag.png)