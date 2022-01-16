## Jupyter
Установка Jupyter в Conda окружение [Jupyter Project](https://jupyter.org/install)
```
conda install -c conda-forge notebook
```
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

В случае, если вы используете IDE [DataSpell](https://www.jetbrains.com/ru-ru/dataspell/) от JetBrains,
 операции о добавлению нового окружения и ядра также необходимы, чтобы в IDE корректо отображались доступные окружения.
