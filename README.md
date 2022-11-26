# Проект распознавания визитных карточек с использованием библиотек OpenCV, Tesseract и предобученной GOOGLE Bert модели с сайта HuggingFace.
Веб-сайт используемой модели: https://huggingface.co/dslim/bert-large-NER

## Структура проекта
project_ML_console/ </br>
├── __init__.py  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;                             Файл инициализации модуля </br>
├── app.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;&nbsp;                          Главный файл приложения </br>
├── bert_model.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;                           Файл загрузки BERT модели </br>
├── card_recognizer.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Распознаватель контура </br>
├── contact_recognizer.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;&nbsp;Распознаватель контактного лица</br>
├── contact.py  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;                                          Класс описания сущности контактного лица</br>
├── data/   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;                                               Папка с дополнительными данными</br>
&emsp;└── jobs  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;                                  Текстовый файл с перечнем профессий</br>
├── README.md     &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;                                         Файл описания проекта </br>
├── requirements.txt  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;                                     Файл,содержащий список необходимых библиотек </br>
├── text_recognizer &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;            Распознаватель текста на базе Tesseract OCR</br>
├── test_data/   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;                                                      Папка с тестовыми изображениями визитных карточек </br>
&emsp;└── card.jpg &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;                                         Тестовый файл изображения визитной карточки </br>
└── token_recognizers/ &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;                                   Папка, содержащая распознаватели отдельных сущностей </br>
&emsp;├── __init__.py  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;&nbsp;                                         Файл инициализации модуля </br>
&emsp;├── email_recognizer.py  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;              Распознаватель email адресов </br>
&emsp;├── job_recognizer.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;                                 Распознаватель должности </br>
&emsp;├── loc_recognizer.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;                     Распознаватель дреса (использует BERT) </br>
&emsp;├── name_recognizer.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;                    Распознаватель имени и фамилии (использует BERT) </br>
&emsp;├── org_recognizer.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;                         Распознаватель организации (использует BERT) </br>
&emsp;├── phone_recognizer.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;                        Распознаватель телефонных номеров </br>
&emsp;└── website_recognizer.py &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;                                 Распознаватель веб-сайтов </br>

## Описание программы, установка и запуск
1. Программа представляет собой web приложение на фреймворке Streamlit. Приложение запускается из папки приложения следующей командой:
```
streamlit run app.py
```
Приложение по умолчанию разворачивается на локальном хосте localhost:8051.

2. Изображение должно иметь формат .jpg или .png и иметь достаточно высокое разрешение, изображение низкого качетсва будет распознано неверно. Внимание, программа распознает визитные карточки только на английском языке!

3. Перед запуском приложения необходимо установить движок оптического распознавания символов Tesseract OCR, используя следующие команды (все нижеприведенные команды представлены для MacOS и Linux, для Windows они могут отличаться):

Для Linux:
```
apt install tesseract-ocr
apt install libtesseract-dev
```
Для MacOS:
```
brew install tesseract
```

После установки движка Tesseract возможно придется также поменять путь к движку Tesseract, задаваемому в файле text_recognizer.py:

Для Linux:
```
pytesseract.pytesseract.tesseract_cmd = ( r'/usr/bin/tesseract' )
```

Для MacOS:
```
pytesseract.pytesseract.tesseract_cmd = ( r'/usr/local/bin/tesseract' )
```

На вашей системе путь может отличаться. Чтобы узнать корректный путь к движку на вашей системе, воспользуйтесь командой which в терминале:
```
which tesseract
```
4. После установки Tesseract неоходимо установить дополнительные библиотеки Python командой: 
```
pip install -r requirements.txt
```

5. Для тестирования приложения используйте изображение card.jpg из папки test_data.

6. Первичная загрузка модели BERT может занять значительное время, так как размер скачиваемых файлов занимает около 1.33 Гб, так что запаситесь терпением и чашечкой кофе! ☕️ 🍪 ☺️
