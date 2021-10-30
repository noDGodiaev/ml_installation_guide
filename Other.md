## Jupyter

Добавление нового окружения в jupyter
~~~
pip install --user ipykernel
python -m ipykernel install --user --name=<my_env_name>
~~~

Удаление ядра (kernel) из jupyter
~~~
jupyter kernelspec uninstall your_env
~~~

Запуск jupyter в другой директории. Войдите в свойства ярлыка jupyter-> объект -> замените "%USERPROFILE%/" на требуемую директорию. Например
~~~
"D:\PROJECTS\python"
~~~

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