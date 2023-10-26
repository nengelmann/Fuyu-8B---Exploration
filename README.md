# Fuyu-8B---Exploration
Exploration of the multi modal fuyu-8b model of Adept. 🤓 🔍


Try yourself in colab! \
<a href="https://colab.research.google.com/github/nengelmann/Fuyu-8B---Exploration/blob/main/Fuyu_8B_Exploration.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>


# Info

The colab uses the original [model](https://huggingface.co/adept/fuyu-8b) from Adept and a modified (sharded) [model](https://huggingface.co/ybelkada/fuyu-8b-sharded), both via huggingface integration. \
The original blog post about fuyu-8b can be found [here](https://www.adept.ai/blog/fuyu-8b).

# Examples

## Meme

**Prompt** (original model): \
_Perform OCR to extract text contained within the image. The extracted text in combination with the image represent a joke or funny situation. Explain why it is funny.\n_

<img src="https://api.memegen.link/images/facepalm/_/I_can't_even.png" height="400">

**Model output**: \
_The image features a bald man sitting with his hands covering his face, seemingly covering his eyes. The caption below him reads "I CAN'T EVEN," which is a common expression that is often used to **imply a sense of disbelief** or surprise. This combination of the man's facial expression and the words "I CAN'T EVEN" creates an amusing and lighthearted scene, making the scene particularly funny and entertaining._

**Disclaimer**: \
This **is** a **cherry-picked** example.

**Opinion**: \
However, I think it's pretty good and it shows the models potential. It has not been explicitly trained to evaluate memes, you could fine-tune on memes and the quality of this cherry-picked example might be in reach (_not tried yet_). 


## Chart

**Prompt** (original model): \
_Perform OCR to extract text contained within the chart. Based on the extracted text and the chart itself, describe what you see and point out relations and interesting interconnections.\n_

<img src="https://upload.wikimedia.org/wikipedia/commons/5/55/Composition_of_38th_Parliament.png" height="400">

**Model output**: \
_The graph depicts the distribution of the "NDP" and "Vacant" positions in Canada as of May 19, 2005. The "NDP" positions are represented by blue, red, and orange segments, while the "Vacant" positions are represented in blue, red, and orange segments. The "NDP" positions occupy 133, 138, and 139, respectively, while the "Vacant" positions occupy 134, 135, and 136_

**Disclaimer**: \
This is **not** a **cherry-picked** example. \
It is the first result by [searching](https://www.google.com/search?q=chart&tbm=isch&ved=2ahUKEwjCupmLiZOCAxWWoScCHc0FBw0Q2-cCegQIABAA&oq=chart&gs_lcp=CgNpbWcQAzIHCAAQigUQQzIFCAAQgAQyBwgAEIoFEEMyBQgAEIAEMgUIABCABDIHCAAQigUQQzIFCAAQgAQyBQgAEIAEMgUIABCABDIFCAAQgARQAFgAYKkGaABwAHgAgAFNiAFNkgEBMZgBAKoBC2d3cy13aXotaW1nwAEB&sclient=img&ei=KwU6ZYL5K5bDnsEPzYucaA&bih=909&biw=1850&client=ubuntu-sn&hs=AfI) for 'chart' in google images. Also the prompt has not been engineered but is the first shot.

**Result**: \
Fail case.

**Another Prompt** (original model): \
_What stake does the liberal party have and how does that relate to the conservative party?\n_

**Model output**: \
_The liberal party has a stake that consists of "conservative" values, such as "social egalitarianism" and "free market conservatism." This stake is represented by the graph, which divides the pie chart into red and blue segments. The conservative party, on the other hand, has a stake that consists of "social conservatism" and "traditional values." This stake is represented by the graph, which divides the pie chart into red and green segments. The conservative party's stake is represented by a smaller segment compared to the liberal party'_

**Opinion**: \
Mostly a fail case, as it is describing knowledge from the train data (liberal and conservative values) instead of the charts distribution. The last sentence is correct.

**Another Prompt** (original model): \
_Extract the text from the pie chart. Based on the pie chats distribution, explain how the liberal parties stake relates to the conservative parties stake.\n_

**Model output**: \
_The "Liberal" party stake is represented by 133, while the "Conservative" party stake is represented by 98. The "NDP" party stake is represented by 19, while the " Bloc Quebecois" party stake is represented by 34. The "Conservative" party stake is represented by 98, while the "NDP" party stake is represented by 19. The "Liberal" party stake is represented by 133, while the "Conservative" party stake is represented by_

**Opinion**: \
Much better than before but with a strange repetition. Also the relation is missing. \
However this suggests that there is more potential with some prompt engineering and a better understanding of the model.

## Graph

**Prompt** (original model): \
_Perform OCR to extract text contained within the chart. Based on the extracted text and the chart itself, describe what you see and point out relations and interesting interconnections.\n_

<img src="https://www.splashlearn.com/math-vocabulary/wp-content/uploads/2022/05/graphs-3-01.png" height="400">

**Model output**: \
_The graph displays various types of school supplies, including pencils, which are represented by green and pink bars, and other types of school supplies, such as erasers, represented by purple and yellow bars. The graph shows a sharp increase in pencil supplies, while other types of school supplies show a steady increase. The graph also displays a sharp decrease in the number of school supplies related to other types of supplies, such as pencils and erasers. This suggests that pencils and erasers are the primary subjects of interest, while other types of supplies have decreased over time._

**Disclaimer**: \
This is **not** a **cherry-picked** example. \
It is the first result by [searching](https://www.google.com/search?q=graphs&tbm=isch&ved=2ahUKEwjLj4v0kpOCAxVwmScCHf5yAkYQ2-cCegQIABAA&oq=graphs&gs_lcp=CgNpbWcQA1AAWABgAGgAcAB4AIABAIgBAJIBAJgBAKoBC2d3cy13aXotaW1n&sclient=img&ei=dw86ZYv4JPCynsEP_uWJsAQ&bih=909&biw=925&client=ubuntu-sn&hs=h3d) for 'graphs' in google images. Also the prompt has not been engineered but is the first shot.

**Opinion**: \
A few things are not correct (color, description, etc.), overall it is not too bad, considering that it is the same prompt as in the fail case example above.

**Another Prompt** (original model): \
_What is the number of supplies for type pen?\n_

**Model output**: \
_There are four supplies for the type of pen._

**Result**: \
Fail case.

## Relation Overview

**Prompt** (original model): \
_Perform OCR to extract text contained within the image. Describe what this image is about so that a 5 year old understands.\n_

<img src="https://www.chilimath.com/wp-content/uploads/2023/06/Ways-to-Write-or-Represent-Relations-1024x1024.png" height="400">

**Model output**: \
_The image features a graph that displays two intersecting circles. The graph's center is labeled "Relation in graph" and "1". The graph's outer circle is labeled "1-5". The graph's inner circle is labeled "2-5". The graph's outermost circle is labeled "1". The graph's innermost circle is labeled "3"._

**Disclaimer**: \
This is **not** a **cherry-picked** example. \
It is the first result by [searching](https://www.google.com/search?q=ralation&tbm=isch&ved=2ahUKEwjS_6zyjpOCAxXHsycCHfErD9kQ2-cCegQIABAA&oq=ralation&gs_lcp=CgNpbWcQAzIFCAAQgAQyBQgAEIAEMgUIABCABDIJCAAQGBCABBAKMgkIABAYEIAEEAoyCQgAEBgQgAQQCjIJCAAQGBCABBAKMgkIABAYEIAEEAoyCQgAEBgQgAQQCjIJCAAQGBCABBAKOgcIABCKBRBDUN0LWJIXYMMYaABwAHgAgAGtAYgBoQaSAQM4LjGYAQCgAQGqAQtnd3Mtd2l6LWltZ8ABAQ&sclient=img&ei=Qgs6ZdLWDcfnnsEP8de8yA0&bih=909&biw=1850&client=ubuntu-sn&hs=AfI) for 'relation' in google images. Also the prompt has not been engineered but it the first shot.

**Opinion**: \
Fail case.


## Synthetic Scene

**Prompt** (original model): \
_Explain what objects are in this image.\n_

<img src="https://learnopencv.com/wp-content/uploads/2021/04/image-15.png" height="400">

**Model output**: \
_In the image, there is a boat floating on the water, surrounded by waves. The boat is surrounded by an orange sun, which adds a vibrant and visually appealing touch to the scene. The waves in the ocean create a dynamic and lively atmosphere, while the sun's orange hue adds a pop of color to the scene._

**Disclaimer**: \
This is **not** a **cherry-picked** example. \

**Opinion**: \
Fair enough, actually I'd have expected more the objects side (cloud, sun, ship).

