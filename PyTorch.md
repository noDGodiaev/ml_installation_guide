## PyTorch

[Инструкция](https://pytorch.org/get-started/locally/)

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
