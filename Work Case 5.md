
# Work Case №5

## 1. Робота з периферійними пристроями в Linux

### 1.1 — Механізм роботи ОС Linux з пристроями на прикладі флешки та принтера

У Linux всі пристрої розглядаються як файли, які знаходяться в каталозі `/dev`.

#### Флешка (USB-накопичувач)

При підключенні:
- Ядро Linux визначає пристрій (наприклад `/dev/sdb1`)
- Система може автоматично змонтувати його (через `udev` + `automount`)
- Або користувач монтує вручну

#### Принтер

Для роботи з принтером використовується система друку CUPS (Common UNIX Printing System).

Її взаємодія:
- Керує чергою друку
- Взаємодіє з драйверами
- Приймає завдання друку

### 1.2 — Що таке монтування

Це процес підключення файлової системи пристрою до дерева каталогів Linux.

Використовується для доступу до файлів на пристрої та роботи з USB, дисками, ISO-образами.

#### Як працює

1. Створення точки монтування:

```Bash
sudo mkdir /mnt/usb
```

2. Монтування:

```Bash
sudo mount /dev/sdb1 /mnt/usb
```

3. Відмонтування:

```Bash
sudo umount /mnt/usb
```

### 1.3 — Різниця Linux та Windows

| Характеристика | Linux | Windows |
| :--- | :--- | :--- |
| Робота з пристроями | Через файли (`/dev`) | Через букви дисків (`C:`, `D:`) |
| Монтування | Явне або авто | Автоматичне |
| Гнучкість | Дуже висока | Менша |
| Драйвери | Часто вбудовані | Часто потрібно встановлювати |
| Контроль | Повний контроль через термінал | Переважно через GUI |

Linux дає більше контролю, але вимагає більше знань.

---

## 2. Практична частина

### 2.1 — Підключення флешки до VirtualBox

#### Через надання прямого доступу до USB пристроїв

<h3>
  <details>
    <summary>Скріншоти</summary>
    <table>
      <tr>
        <td><img width="885" height="616" src="https://github.com/user-attachments/assets/c44a8fac-bcab-4f5b-afea-77409a6254f2"/></td>
        <td><img width="854" height="613" src="https://github.com/user-attachments/assets/20c6db07-1e8d-4158-b8c8-61d8316e9994" /></td>
      </tr>
    </table>
  </details>
</h3>

Флешка з'явилася безпосредньо в файловому менеджері та відображається в дереві блокових пристроїв через `lsblk`.

### 2.2 — Копіювання файлу (GUI)

Відкривши файловий менеджер, обираємо флешку та копіюємо в бажане місце.

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="854" height="616" src="https://github.com/user-attachments/assets/e6f98d04-0a6a-48d2-8a06-1d669eb1a911"/></td>
      </tr>
    </table>
  </details>
</h3>

### 2.3 — Копіювання через термінал

```Bash
cp /mnt/file.txt ~/
```

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="853" height="615" src="https://github.com/user-attachments/assets/58b79774-0ebc-4d4f-890a-2fee291aaf2b"/></td>
      </tr>
    </table>
  </details>
</h3>

### 2.4 — Підключення принтера через CUPS

#### Встановлення та запуск CUPS 

```Bash
sudo apt install cups
```

```Bash
sudo systemctl start cups
```

**[http://localhost:631](http://localhost:631)**

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="1535" height="622" src="https://github.com/user-attachments/assets/dd0b94e7-00b5-4c0a-9fc6-6300c1cf8d31"/></td>
      </tr>
    </table>
  </details>
</h3>


### 2.5 — Друк через GUI після налаштування CUPS

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="878" height="622" src="https://github.com/user-attachments/assets/57cb9e99-fc1f-4758-8094-afcdfea24cf5"/></td>
      </tr>
    </table>
  </details>
</h3>

### 2.6 — Друк через термінал

```Bash
lp filename
```

#### Або:

```Bash
lpr filename
```

<h3>
  <details>
    <summary>Скріншот</summary>
    <table>
      <tr>
        <td><img width="878" height="621" src="https://github.com/user-attachments/assets/e56d8476-222d-4be4-a052-0cdfdab00a53"/></td>
      </tr>
    </table>
  </details>
</h3>

---

## Словник (Vocabulary)

1.1. **Print Queue** — черга завдань на друк, які очікують своєї обробки системою друку.

2. **Block Device** — пристрій зберігання даних, який працює з інформацією у вигляді фіксованих блоків (наприклад, жорсткі диски або USB-накопичувачі) і доступ до нього здійснюється через вузли в `/dev`.

3. **CUPS (Common UNIX Printing System)** — підсистема друку в Unix-подібних ОС, яка відповідає за керування принтерами, чергами друку та обробку завдань.

4. **File System** — спосіб організації даних на носії інформації, який визначає структуру збереження файлів (наприклад, NTFS, ext4, FAT32).

5. **Filesystem Hierarchy** — ієрархічна структура каталогів у системі, де всі файли починаються від кореневого каталогу `/` і впорядковуються за певними правилами.

6. **Mounting** — процедура підключення файлової системи пристрою до певної точки в структурі каталогів ОС.

7. **Unmounting** — безпечне від’єднання файлової системи, під час якого завершуються всі операції запису та перевіряється відсутність активних процесів.

8. **Automount** — процес, за допомогою якого система самостійно підключає носій даних одразу після його під’єднання, без участі користувача.

9. **Driver** — програмне забезпечення, що забезпечує взаємодію операційної системи з апаратними компонентами, такими як принтери чи накопичувачі.

10. **Mount Point** — каталог у файловій системі Linux, до якого підключається зовнішній носій і через який він стає доступним для користувача.

---

## Висновок (Conclusion)

 This work explored how peripheral devices are connected and used in a Linux operating system, using a USB flash drive and a printer as examples. Particular emphasis was placed on the mounting mechanism, which enables external storage to be integrated into the file system so that users can access, read, and modify data on it.

The study also compared Linux and Windows in terms of device handling, noting that Linux offers greater flexibility and transparency, whereas Windows prioritizes automation and ease of use. Practical exercises demonstrated working with devices through both graphical tools and the command line, highlighting that Linux provides multiple ways to accomplish the same tasks and gives users a higher level of control over system operations.
---

## Team Contributions
- **Member 1 — [Tingem]([https://github.com/DimitriyArch](https://github.com/Tingem))**: Formatted the Markdown file and сompleted the practical part and did Conclusions, helped with work and writted Vocabulary.
