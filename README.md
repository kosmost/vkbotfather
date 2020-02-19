# vkbotfather

Данный проект позволяет облегчить создание ботов ВК.

### Установка

1. Установите Python версии не ниже 3.6. При установке убедитесь, что поставили галочку в пункте **Add Python 3.8 to PATH**. Если у вас установлен Python, то проверьте его работу через командную строку.

   ```bash
   python -h
   ```

   Если у вас выводит ошибку:

   ```bash
   python -h
   
   "python" не является внутренней или внешней командой, исполняемой программой или пакетом файлов.
   ```

   **То нужно добавить Python в PATH.** Для этого стоит сделать следующие:

   - Открыть свойства своего ПК.
   - В открывшейся окне перейти в "Дополнительные параметры системы"
   - Нажать на "Переменные среды"
   - Найти Path (или что-то подобное) и нажать, после этого нажать на "Изменить".
   - Нажать на "Добавить" и вставить путь к папке, где находится Python.
   - Повторить предыдущий пункт, но добавить путь к Python\Scripts.  

   **Теперь Python установлен и настроен на вашем ПК.**

2. [Скачайте](https://github.com/wultes/vkbotfather/archive/master.zip) данный репозиторий и распакуйте в любое удобное для вас место.

   Или вы можете его клонировать.

   ```bash
   git clone https://github.com/wultes/vkbotfather
   ```

3. Откройте командную строку и введите следующую команду:

   ```bash
   pip install -r requirements.txt --upgrade
   ```

4. Откройте файл ```config.toml``` любым текстовым редактором и укажите токен сообщества.

5. Для запуска бота введите команду:

   ```bash
   python main.py
   ```

    

### Получение токена сообщества

Для того, чтобы получить токен нужно перейти в настройки сообщества, которое вы создали или в котором является админом. Далее, перейти в "Работа с API" и создайте новый ключ с доступом к управлению и сообщениям сообщества.



### Использование

Запустив бота, вы можете его протестировать. Для этого отправьте сообщение в сообщество, к которому подключен ваш бот.

*Если после этого бот ничего не ответил, то посмотрите логи в командной строке.*



### Добавление плагинов

Для создания и добавления плагинов нужно сделать следующие шаги:

- Создать в папке ```plugins``` файл с названием самого плагина. Например, ```about.py```.

- Создать в этом файле класс.

  ```python
  class AboutBot:
  ```

- Создать в этом классе функции.

  ```python
  class AboutBot:
      
      @staticmethod
      def get_about():
          
          return "About"
  ```

  Название функции, которая будет возвращать значение боту, обязательно должно начинаться с ```get_название_функции``` и иметь ```@staticmethod```.

- Открываем файл ```settings.py``` и добавляем новый плагин в список плагинов.

  ```python
          self.plugins = (
              about.AboutBot(), #0
          )
  ```

- После этого, переходим в файл ```bot.py``` и добавляем условие, при котором наша функция будет вызываться.

  ```python
      def message_analysic(self, message):
          if message == '/help':
              return self.plugins[0].get_about()
  ```

**Плагин успешно установлен и готов к использованию**

### Лицензия

Данный репозиторий использует лицензию [MIT](https://choosealicense.com/licenses/mit/)  
Copyright © 2020 [Wultes](https://github.com/wultes/). 
