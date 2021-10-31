## Прочее

~~~
import tarfile
tar = tarfile.open("test.tar", "r")
tar.extractall()
~~~

## Conda-forge

~~~
conda install -c conda-forge ffmpeg-python
~~~

## Полезные ссылки
[Гайд от Rubbix](https://rubrix.readthedocs.io/en/master/tutorials/01-labeling-finetuning.html) по дообучению модели Bert
 в качестве текстового классификатора на их датасете с помощью высокоуровнего API от [Transformers](https://huggingface.co/transformers/index.html)