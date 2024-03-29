.. _config_accelerators:

Конфигурация ускорителей
========================

Архитектура конфигурации
------------------------

Старт конфигурации начинается с 
`руководства администратора по аппаратам <./data/varian/TrueBeam_Administrators_Guide.pdf>`_.

Конфигурация собственно аппарата осуществляется с помощью консольного компьютера в трех местах:

- в **Major Mode menu -> System Administration**,
- в **Major Mode menu -> Service**,
- в **Imager Calibration mode** (*PVA Settings in System Administration*)

На этом этапе создается описание терапевтического оборудования,
которое в дальнейшем используется и в конфигурации Eclipse.
Логика Varian такова, что конфигурация оборудования относится 
к глобальной настройке комплекса ассоциируемой с настройкой информационной системы ARIA.
Eclipse часть параметров может настраивать под себя выдавая сбивающие с толку предупреждения.
Детали этой логики будут рассматриваться в конфигурации Eclipse, 
та как это следует рассматривать как его проблему.

.. note:: Конфигурация аппарата большая и выполняется при инсталляции сервисными инженерами.
          Пользователям в нее влезать не следует за исключением изучения предмета для понимания
          и в некоторых случаях для изменения политики использования некоторых процедур
          типа авотпозиционирования и других, связанных с безопасность пациента.
          Поэтому в данном руководстве рассматриваться не будет.
          Фотографии экрана с частями пользовательского интерфейса для TrueBeam STX
          содержатся в `папке <./data/varian/Pictures/STX_admin/>`_.

.. note:: В документации присутствует понятие **Customer HASP Authentication**
          (Hardware Against Software Piracy (**HASP**) key) опция.
          Она предоставляет доступ к документации и некоторым инструментам.

          **Q:** От чего зависит наличие этого ключа. 
          Почему его нет у нас и можем ли мы его как-то получить?

.. todo::
    
  #. Выяснить, где хранится конфигурация радиотерапевтической установки.
     Хранится ли она на компьютере самой установки или на сервере.
     Почему при отсутствии соединения с сервером TrueBeam отказывается 
     принимать логин пользователя и не работает, а Halcyon при этом позволяет работать? 

Конфигурация **CBCT**
---------------------

Конфигурация протоколов сканирования **CBCT** осуществляется в сервисном режиме в закладке **CBCT Mode Editor**.

.. todo::
    
  #. К визиту аппликаторов подготовить собственный проект протоколов сканирования.
     Утрясти детали на основании обсуждения с ними.
  #. Провести дозиметрию лучевых нагрузок в предопределенных режимах сканирования
     для понимания масштаба бедствия и понимания к чему стремиться.
  #. Для тех же протоколов провести сканирование фантома Calphan 
     для понимания качества изображений в связи с измеренными дозами.
  #. Получить изображения фантома **IBA** для планарных рентгеновских снимках и 
     определиться с качеством изображений и интеграции фантома и метода в систему качества.
  #. Разобраться в возможности позиционирования пациента по паре снимков чисто рентгеновских и 
     в комбинации с портальным для позиционирования пациента вместо CBCT. 
     Учесть дозы, время, ресурс оборудования.
  #. Прокачать вопрос выбора угла сканирования CBCT.
     Доклад Питерцев на Онкорадиологии указывает на то, что можно сэкономить серьезно в скорости навигации.
     Проверить, если возможность выравнивания интенсивности изображения 
     при малом угле сканирования (у Питерцев это было ужасно). 
     Разобраться попутно с вопросом положения стола при CBCT.
     В РОНЦ было требование помещения стола по латерали в 0 и смещать после сканирования.
     Нельзя ли, сажем при молочной железе сканировать в узком секторе тангенциальных направлений?
  #. Проверить работу **4D CBCT** задействовав простейший фантом для гейтинга, или, лучше, 
     совместить разбирательство нашей платформы для гейтинга в сочетании с нормальным фантомом.

Конфигурация портальной системы
-------------------------------

Настройки условий работы с портальной системой находятся в разделе **PVA** системных настроек.

.. todo::
    
  #. Разобраться внимательнее с возможными настройками в PVA.
  #. Выработать свою политику условий получения изображений.
  #. Понять возможности автосовмещения изображений на предмет использования в навигации.
  #. Получить изображение мегавольтного фантома **IBA** и определиться с 
  
Конфигурация ускорителя для дальнейшего изучения по мере необходимости
----------------------------------------------------------------------

Из-за большого объема и отсутствия реальной необходимости 
погружения в конфигурацию тема подробно не рассматривается.
Однако, такая потребность может возникнуть в будущем.
Поэтому далее следуют вопросы и возможности, знание о существовании
которых может помочь в решении практических задач по  мере возникновения.

#. Вопрос генерации информации о лучевых нагрузках при CBCT.
   На старте эта функция отключена.
#. В конфигурации аксессуаров и возможностей стоят флаги наличия для большого количества таких устройств, 
   которых у нас на самом деле нет. Это перегружает все прочие настройки. 
   Возможно с этим следует разбираться уже сейчас.
#. В руководстве администратора **Table 6** *Clinical General Preferences* перечислены
   параметры, которые влияют на клиническое использование. 
   Они могут быть критичными, потому что есть, например, флаг о том,
   проведена ли настройка динамических клиньев в системе планирования.
#. Группа параметров реконструкции **CBCT** позволяет регулировать работу с сырыми изображениями
   и отправку данных внешним системам. Где-то там же настройки потоков DICOM данных.
#. **PVA** секция содержит множество вопросов работы с навигационными изображениями, относящихся к разделу протоколов лечения. 
   Вероятно здесь придется разбираться в соответствующем контексте.
   Здесь же вопрос Workflow в смысле автоматизации процесса получения изображений и переходов между компонентами GUI.
   Еще Gating и Coaching (что-то связанное с VCD).
   **Получается PVA - это целый мир настроек, работу с которым нужно провести плотно в момент визита аппликаторов**.
#. В сервисном режиме можно регулировать пределы связанные с контролем столкновений.
   Следует проверить и, возможно отредактировать под себя.
   Там же регулировки **audio**.
#. Калибровка должна проводиться на регулярной основе.
   Нужно понять, является ли это обязанностью сервиса или мы должны это делать сами.
   В любом случае много внимания этому вопросу и нужно разобраться с техникой.

Калибровка систем ускорителя
----------------------------

Калибровка - это часть администрирования аппарата.
В руководстве администратора занимает четверть объема начиная со страницы 152.

Включает:

- Калибровка рентгеновской трубки (за исключением механики, находящейся в своем разделе)
- MLC Calibration. Именно в этом месте дозиметрически критичные калибровки. 
  Есть возможность калибровки центральной линии и зазора между лепестками.
  Строгое предупреждение, что это влияет на величину **DLG!**
- Калибровка стола
- Руки систем визуализации
- Калибровка средств визуализации включая темновые токи панелей, 
  профилей полей, нормировка дзы, калибровка по воздуху и HU.
- Калибровка изоцентра. Речь о калибровке изоцентра портальной системы и 
  привязка к нему аналогичного изоцентра рентгеновской системы.
- Калибровка CBCT - калибровка по воздуху и HU.
- Калибровка оптической камеры - калибровка блока гейтинга, привязка к фиксированной системе координат.
- kV Collimator - автокалибровка координат шторок, формы фильтра и оси.

Поддержание и контроль параметров
---------------------------------

Это уже задачи пользователя (?) поддержания оборудования в надлежащем состоянии.
Соответствующий раздел руководства администратора начиная со страницы 215
фактически описывает систему контроля качества аппарата на стороне пользователя.

Именно с этой задачей связан радел **MachineQA** в основном меню консоли.
Здесь предусмотрена загрузка стандартных планов для выполнения тестов механики и параметров пучка.

Тесты включают:

#. Диагностика МЛК
#. Юстировка пучка 
#. Тесты в процедурной в специальном режиме отключения излучения
#. Проверка качества изображений
#. Геометрические тесты
#. Вводные устройства (пульты)
#. Мониторинг питания
#. Мониторинг охлаждения
#. Мониторинг газа
#. Мониторинг вакуума
#. Уровень масла
#. Лазерная система контроля столкновений
#. Энкодеры стола

.. todo::

  #. Соотнести эту часть руководства администратора с выстраиваемой нами системы QA.

Файловая система
----------------

Varian широко использует разделяемы папки в работе комплекса.

Основным местом обмена данными с радиотерапевтическим оборудованием 
являются разделяемые основным сервером папки в следующем месте:

.. code-block:: none

    \\m66-vcom-01\va_transfer\TDS\<machineID>\*

Для каждого аппарата заведена большая файловая структура с относительно стандартной системой.
Смысл каждой папки понятен из контекста.
В частности аппараты сохраняют данные типа результатов тестирования, 
программы разного рода тестов, планы для верификации и т.д.
И просто обмен файлами по потребностям пользователя.
Именно здесь следует размещать файлы для поддержки системы качества.

.. todo::
    
  #. Проверить действительно ли вся конфигурация содержится в файловой системе
     или что-то хранится в базах данных SQL.
  #. Посмотреть файловую структуру разделяемых папок и составить мнение о содержании, 
     возможности использования и необходимого обслуживания.

Вопросы для осмысления и решения
--------------------------------

.. todo::

  #. На стр.48 говорится о **Radiation Dose Structured Report (RDSR) Storage Installation**.
     **RDSR** это некая система учета лучевой нагрузки от **CBCT**. 
     Ее конфигурация каким-то образом связана с конфигурацией сервисов **DICOM**.
     Вся эта тема - предмет для отдельного разбирательства.
  #. 

