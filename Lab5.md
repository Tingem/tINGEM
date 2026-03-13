
# Лабораторна робота №5
## Тема: Знайомство з командами навігації по файловій системі та керування файлами та каталогами

## **Мета роботи:**
1. Отримання практичних навиків роботи з командною оболонкою Bash.
2. Знайомство з базовими командами навігації по файловій системі.
3. Знайомство з базовими командами для керування файлами та каталогами.

---

## Матеріальне забезпечення
* ЕОМ типу IBM PC.
* ОС сімейства Windows та віртуальна машина Virtual Box (Oracle).
* ОС GNU/Linux (Arch).
* Сайт мережевої академії Cisco netacad.com та його онлайн курси по Linux

---

## 1. Завдання для попередньої підготовки

### 1.1 — Словник (Dictionary)

| Term | Explanation |
|-----|-----|
| Directory | A folder used to store files and other folders |
| Root directory | The highest level of the Linux file structure, represented by `/` |
| Filesystem | A hierarchical structure used by an operating system to manage stored data |
| CLI | A text-based environment where users interact with the system by typing commands |
| Path | A sequence that shows the location of a file or folder in the system |
| Relative path | Location defined in relation to the current working folder |
| Absolute path | Full location that begins from the system root `/` |
| Glob | Pattern used by the shell to match multiple filenames |
| Wildcard | Special symbol that replaces one or more characters in a pattern |
| Recursive | Action performed on a folder and all items inside it |
| Hidden files | System or configuration items not shown in normal directory listings |

### 1.2 — Відповіді на питання

#### 1.2.1 — Порівняння файлових структур Windows та Linux

Файлові структури операційних систем Windows і Linux організовані за різними принципами.

У Windows структура починається з розділу **«My Computer / This PC»**, де кожен фізичний накопичувач має власне позначення у вигляді літери, наприклад **C:, D:, E:**. Файли та папки зберігаються окремо в межах кожного з цих дисків.

У Linux використовується єдина ієрархічна файлова система, що починається з кореневого каталогу **/**. Усі пристрої, диски та інші файлові системи підключаються до цієї структури у вигляді каталогів.


| Команда | Що робить |
|--------|-----------|
| touch | створює порожній файл |
| mkdir | створює нову папку (каталог) |
| mv | переносить файл або змінює його назву |
| cp | робить копію файлу |
| cp -r | копіює папку разом з усім її вмістом |
| rm | видаляє файл |
| rm -r | видаляє папку разом з файлами всередині |
| rmdir | видаляє папку, якщо вона порожня |
#### 1.2.2 — Поняття FHS

FHS (Filesystem Hierarchy Standard) — це стандарт, який визначає, як організована структура каталогів у Linux.

Він пояснює:

для чого призначені основні системні каталоги;

де повинні зберігатися системні файли;

у яких місцях розміщуються програми, бібліотеки та конфігураційні файли.

Каталог

| Каталог | Призначення |
|--------|-------------|
| /bin | Основні системні програми |
| /etc | Конфігураційні файли |
| /home | Домашні каталоги користувачів |
| /usr | Програми користувача |
| /var | Змінні дані (логи, кеш) |
| /tmp | Тимчасові файли |

Завдяки стандарту FHS різні дистрибутиви Linux мають схожу структуру файлової системи, що полегшує адміністрування.

#### 1.2.3 — Основні команди для роботи з файлами та каталогами

| Команда | Призначення |
| :--- | :--- |
| `touch` | Створення порожнього файлу |
| `mkdir` | Створення каталогу |
| `mv` | Переміщення або перейменування файлів |
| `cp` | Копіювання файлів |
| `cp -r` | Копіюваггя каталогів |
| `rm` | Видалення файлів |
| `rm -r` | Видалення каталогу разом із вмістом |
| `rmdir` | Видалення порожнього каталогу |

---

## 2. Хід роботи 

### 2.1 — Приклади команд з NDG Lab 7 & 8

| Команда | Призначення та функціональність |
| :--- | :--- |
| `pwd` | Показує поточну робочу директорію користувача (print working directory) |
| `cd Documents` | Перехід у каталог `Documents` або інший каталог, зазначений як аргумент |
| `echo` | Виводить текст або значення змінних у термінал; часто використовується для повідомлень або результатів скриптів |
| `ls` | Відображає список файлів і каталогів у поточній директорії |
| `ls -a` | Показує всі файли та каталоги, включаючи приховані (імена починаються з `.`) |
| `ls -l` | Виводить детальний список: права доступу, власник, розмір, дата зміни |
| `ls -R` | Рекурсивно відображає вміст усіх підкаталогів поточного каталогу |
| `ls -d` | Показує сам каталог як об'єкт, а не його вміст (зручно при роботі з шаблонами) |
| `cp` | Копіює файл або каталог з одного місця в інше |
| `cp -v` / `--verbose` | Копіює файли та відображає процес копіювання (які файли копіюються) |
| `cp -p` | Копіює файл із збереженням атрибутів: права доступу, власник, час створення |
| `cp -R` | Рекурсивно копіює каталоги разом із усіма файлами та підкаталогами |
| `rm` | Видаляє файли з файлової системи |
| `rm -r` | Рекурсивно видаляє каталог разом із усім його вмістом |
| `rmdir` | Видаляє порожній каталог |
| `mkdir` | Створює новий каталог |
| `touch premove` | Створює порожній файл `premove` або оновлює дату останньої зміни існуючого файлу |
| `mv premove postmove` | Перейменовує файл `premove` у `postmove` або переміщує його в інший каталог |
| `rm postmove` | Видаляє файл `postmove` з файлової системи |

  ---
  
### 2.3 — Опис дій команд `cd`

| Команда   | Опис дії |
|-----------|-----------|
| `cd /` | Перехід у кореневу директорію файлової системи |
| `cd /home` | Відкриває каталог `home` |
| `cd ~` | Переходить у домашню директорію поточного користувача |
| `cd` | Виконує перехід до домашнього каталогу користувача |
| `cd ..` | Піднімається на один рівень вище у структурі каталогів |
| `cd ../..` | Переходить на два рівні вище від поточної директорії |
| `cd -` | Повертає до попереднього відкритого каталогу |

---

## Відповіді на контрольні запитання

### 1. Перегляд шляху до домашньої директорії через `echo`

Використовуючи аргументи `$HOME` та `~`

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="166" height="195" src="https://github.com/user-attachments/assets/2a274db9-ac2c-4884-a35e-b325f9d025c9"/></td>
      </tr>
    </table>
  </details>
</h3>

### 2. Перегляд вміст кореневого каталогу, не переходячи до нього через `ls /`

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="400" height="386" src="https://github.com/user-attachments/assets/e104cd62-1241-425d-884e-c1a6eb83c523"/></td>
      </tr>
    </table>
  </details>
</h3>

### 3. Створення і додавання інформації у порожній файл через `echo`

<h3>
  <details>
    <summary>Скріншоти</summary>
    <table>
      <tr>
        <td><img width="259" height="146" src="https://github.com/user-attachments/assets/1d702fba-c951-46fa-b236-fc31dac5a8c0"/></td>
        <td><img width="163" height="140" src="https://github.com/user-attachments/assets/3a481dd9-e53d-4aca-aba5-2173be2c1af5"/></td>
      </tr>
    </table>
  </details>
</h3>

### 4. Cтворення, копіювання та видалення каталогу командами `mkdir`, `cp -r`, `rmdir`, `rm -r`

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="177" height="232" src="https://github.com/user-attachments/assets/6488a6cb-6294-4d83-aaa2-e9c201adc926"/></td>
      </tr>
    </table>
  </details>
</h3>

### 5. Аналіз команди `mv`

1. Переміщення файлу
2. Перейменування файлу
3. Переміщення та перейменування

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="591" height="188" src="https://github.com/user-attachments/assets/609e93c8-b715-46ab-9e10-03898c885add"/></td>
      </tr>
    </table>
  </details>
</h3>

---

## Висновок (Conclusion)

During the laboratory work, practical experience in using the Bash command-line interface in the Linux operating system was gained. The organization of the Linux file system and its main differences compared to the Windows file system were explored. In addition, the FHS (Filesystem Hierarchy Standard) was reviewed, which describes the structure and functions of the primary system directories.

Throughout the lab, essential commands for navigating the file system (`pwd`, `cd`, `ls`) as well as commands for file and directory management (`touch`, `mkdir`, `cp`, `mv`, `rm`, `rmdir`) were analyzed. Hands-on practice included creating, copying, moving, renaming, and removing files and directories using the terminal.

The knowledge obtained during this work enables more confident use of the Linux command line and provides a foundation for further learning related to system administration and working with Linux-based operating systems.


---

## Team Contributions

- **Member 1 — [Tingem](https://github.com/Tingem)**
