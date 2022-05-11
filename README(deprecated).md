### Installation guides

Репозиторий содержит краткие заметки об установке различных фреймворков
 для глубокого машинного обучения, настройке их для работы на GPU,
а также ссылки на полезные статьи и материалы по работе с ними.

Короткий алгоритм начала работы с любым фреймворком:
```
-> Anaconda
-> Установка CUDA
-> Фреймворк и дполнительные библиотеки, необходимые для работы
-> Проверка обнаружения фреймворком доступного GPU
-> Восхищение своей выдержкой и силой воли
```
Анаконда в отличие от других сред виртуализации обладает мультиплатформенностью
и возможностью установки CUDA непосредственно внутрь конкретной среды,
хотя она и является довольно тяжелым пакетом.

### Локальная установка в окружение
**для windows и linux**

Предпочтительный метод установки CUDA для работы на python. Установка  в окружение
позволяет использовать одновременно несколько версий CUDA. Подробно установка описана [тут](https://towardsdatascience.com/setting-up-tensorflow-gpu-with-cuda-and-anaconda-onwindows-2ee9c39b5c44)

~~~
activate env
conda install -c anaconda cudatoolkit=10.1
~~~

### Глобальная установка в PATH
**для windows**

Более трудоемкий способ установки. Позволяет использовать только одну 
установленную версию CUDA.
Если вы не работаете с пакетом Anaconda или область видимости CUDA должна 
быть глобальной, выполните следующие действия
1) установите Microsoft Visual Studio 2017,2019
2) установите Cuda Toolkit нужной версии
3) скачайте CuDNN и переместите его в директорию C:\tools
4) добавьте в переменную среду пользователя PATH следующие пути

~~~
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\bin
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\extras\CUPTI\lib64
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.0\include
C:\tools\cuda\bin
~~~

Подробно установка Cuda для TensorFlow
описана [тут](https://www.tensorflow.org/install/gpu?hl=ur)

## TensorFlow

[Таблица](https://www.tensorflow.org/install/source#gpu) совместимости версий tensroflow 
и CUDA

Тестовый код для проверки работы TensorFlow-gpu и CUDA
~~~
import tensorflow as tf  # 2.x
tf.compat.v1.disable_eager_execution() # need to disable eager in TF2.x
# Build a graph.
a = tf.constant(5.0)
b = tf.constant(6.0)
c = a * b

# Launch the graph in a session.
sess = tf.compat.v1.Session()

# Evaluate the tensor `c`.
print(sess.run(c)) # prints 30.0
~~~

Проверка видимости видеокарты
~~~
from tensorflow.python.client import device_lib

print(device_lib.list_local_devices())
print("Num GPUs Available: ", len(tf.config.list_physical_devices('GPU')))
~~~

Создание ограничения для Tensorflow на заполнение всей видеопамяти видеокарты
~~~
gpus = tf.config.list_physical_devices('GPU')
tf.config.experimental.set_memory_growth(gpus[0], True)
~~~

## PyTorch

Проверка видимости видеокарты
~~~
import torch

print(torch.cuda.is_available())     # Returns a bool indicating if CUDA is currently available.
print(torch.cuda.current_device())   # Returns the index of a currently selected device.
print(torch.cuda.device(0))          # Context-manager that changes the selected device.
print(torch.cuda.device_count())     # Returns the number of GPUs available.
print(torch.cuda.get_device_name(0)) # Gets the name of a device.
~~~
Отключение cuda девайсов
~~~
torch.cuda.is_available = lambda : False
~~~

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

Ошибки

1) ERROR 101 - нужно запускать ярлык или среду разраотки от имени адинистратора. По умолчанию ide от JetBrains не имеют
уровень доступа администратор

## Инференс моделей

Инференс [Yolo](https://github.com/ArmageddonReloadedDK/video_stream) на CPU и GPU

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

