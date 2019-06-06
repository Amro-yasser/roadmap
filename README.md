# roadmap
Python backend developer roadmap.

## Table of contents

[General](#general)

- Git and Gitflow
- [Terminal](#terminal)
  - [Basics](#basics)
  - [Manipulating files](#manipulating-files)
  - [Inspecting files](#inspecting-files)
  - [Directories](#directories)
- [SOLID, KISS, YAGNI](#solid-kiss-yagni)
- Design Patterns
- [SSH](#ssh)
- [TCP/IP, HTTP, HTTPS and APIs](#network-communication-and-security-protocols)
- [Regular Expressions](#regular-expressions)
- Semantic versioning
- Character Encodings
- Licenses
- Data structures and algorithms
- [How Browsers Work](https://www.html5rocks.com/ru/tutorials/internals/howbrowserswork/)

[Backend](#backend)

- [Python](#python) (standards and best practices)
- [Virtual environments and pip](#virtual-environments-and-pip)
- Relational DB and SQL (Postgresql)
- Django
  - Models and databases
    - Models
    - Making queries
    - Aggregation
    - Search
    - Managers
    - Performing raw SQL queries
    - Database transactions
    - Multiple databases
    - Tablespaces
    - Database access optimization
    - Database instrumentation
    - Examples
- NoSQL DB (MongoDB)
- Caching
- REST API
- Authentication/Authorization methodologies
- Message Brokers
- Search Engine
- Docker
- Web servers
- Web sockets

## General

### Terminal

Great resource for beginners - https://www.learnenough.com/command-line-tutorial/basics
Additional recources:

- [Conquering the Command Line by Mark Bates](http://conqueringthecommandline.com/book/frontmatter)


Key points:

- use `man`! Stands for _manual_.
- xdg-open <file_name/directory_name>
- `!command` or call previous command `!!`
- `cd -` change to previos directory
- `less`
- piping `|`
- redirect `>`
- append `>>`
- get `<`

#### Basics

<div id="table-man_echo" data-tralics-id="uid59" data-number="1.2" class="table">
<table class="tabular">
<tbody>
<tr class="bottom_border">
<td class="align_left"><strong>Command</strong></td>
<td class="align_left"><strong>Description</strong></td>
<td class="align_left"><strong>Example</strong></td>
</tr>
<tr>
<td class="align_left"><code class="tt">echo &lt;string&gt;</code></td>
<td class="align_left">Print string to screen</td>
<td class="align_left"><code>$ echo hello</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">man &lt;command&gt;</code></td>
<td class="align_left">Display manual page for command</td>
<td class="align_left"><code>$ man echo</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">⌃C</code></td>
<td class="align_left">Get out of trouble</td>
<td class="align_left"><code>$ tail ⌃C</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">⌃A</code></td>
<td class="align_left">Move to beginning of line</td>
<td class="align_left"></td>
</tr>
<tr>
<td class="align_left"><code class="tt">⌃E</code></td>
<td class="align_left">Move to end of line</td>
<td class="align_left"></td>
</tr>
<tr>
<td class="align_left"><code class="tt">⌃U</code></td>
<td class="align_left">Delete to beginning of line</td>
<td class="align_left"></td>
</tr>
<tr>
<td class="align_left">Option-click</td>
<td class="align_left">Move cursor to location clicked</td>
<td class="align_left"></td>
</tr>
<tr>
<td class="align_left">Up &amp; down arrow</td>
<td class="align_left">Scroll through previous commands</td>
<td class="align_left"></td>
</tr>
<tr>
<td class="align_left">
<code class="tt">clear</code> or <code class="tt">⌃L</code>
</td>
<td class="align_left">Clear screen</td>
<td class="align_left"><code>$ clear</code></td>
</tr>
<tr>
<td class="align_left">
<code class="tt">exit</code> or <code class="tt">⌃D</code>
</td>
<td class="align_left">Exit terminal</td>
<td class="align_left"><code>$ exit</code></td>
</tr>
</tbody>
</table>
</div>

#### Manipulating files

<table class="tabular">
<tbody>
<tr class="bottom_border">
<td class="align_left"><strong>Command</strong></td>
<td class="align_left"><strong>Description</strong></td>
<td class="align_left"><strong>Example</strong></td>
</tr>
<tr>
<td class="align_left"><code class="tt">&gt;</code></td>
<td class="align_left">Redirect output to filename</td>
<td class="align_left"><code>$ echo foo &gt; foo.txt</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">&gt;&gt;</code></td>
<td class="align_left">Append output to filename</td>
<td class="align_left"><code>$ echo bar &gt;&gt; foo.txt</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">cat &lt;file&gt;</code></td>
<td class="align_left">Print contents of file to screen</td>
<td class="align_left"><code>$ cat hello.txt</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">diff &lt;f1&gt; &lt;f2&gt;</code></td>
<td class="align_left">Diff files 1 &amp; 2</td>
<td class="align_left"><code>$ diff foo.txt bar.txt</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">ls</code></td>
<td class="align_left">List directory or file</td>
<td class="align_left"><code>$ ls hello.txt</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">ls -l</code></td>
<td class="align_left">List long form</td>
<td class="align_left"><code>$ ls -l hello.txt</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">ls -rtl</code></td>
<td class="align_left">Long by reverse modification time</td>
<td class="align_left"><code>$ ls -rtl</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">ls -a</code></td>
<td class="align_left">List all (including hidden)</td>
<td class="align_left"><code>$ ls -a</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">touch &lt;file&gt;</code></td>
<td class="align_left">Create an empty file</td>
<td class="align_left"><code>$ touch foo</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">mv &lt;old&gt; &lt;new&gt;</code></td>
<td class="align_left">Rename (move) from old to new</td>
<td class="align_left"><code>$ mv foo bar</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">cp &lt;old&gt; &lt;new&gt;</code></td>
<td class="align_left">Copy old to new</td>
<td class="align_left"><code>$ cp foo bar</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">rm &lt;file&gt;</code></td>
<td class="align_left">Remove (delete) file</td>
<td class="align_left"><code>$ rm foo</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">rm -f &lt;file&gt;</code></td>
<td class="align_left">Force-remove file</td>
<td class="align_left"><code>$ rm -f bar</code></td>
</tr>
</tbody>
</table>

#### Inspecting files

<table class="tabular">
<tbody>
<tr class="bottom_border">
<td class="align_left"><strong>Command</strong></td>
<td class="align_left"><strong>Description</strong></td>
<td class="align_left"><strong>Example</strong></td>
</tr>
<tr>
<td class="align_left"><code class="tt">curl</code></td>
<td class="align_left">Interact with URLs</td>
<td class="align_left"><code>$ curl -O https://example.com</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">which</code></td>
<td class="align_left">Locate a program on the path</td>
<td class="align_left"><code>$ which curl</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">head &lt;file&gt;</code></td>
<td class="align_left">Display first part of file</td>
<td class="align_left"><code>$ head foo</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">tail &lt;file&gt;</code></td>
<td class="align_left">Display last part of file</td>
<td class="align_left"><code>$ tail bar</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">wc &lt;file&gt;</code></td>
<td class="align_left">Count lines, words, bytes</td>
<td class="align_left"><code>$ wc foo</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">cmd1 | cmd2</code></td>
<td class="align_left">Pipe <code class="tt">cmd1</code> to <code class="tt">cmd2</code>
</td>
<td class="align_left"><code>$ head foo | wc</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">ping &lt;url&gt;</code></td>
<td class="align_left">Ping a server URL</td>
<td class="align_left"><code>$ ping google.com</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">less &lt;file&gt;</code></td>
<td class="align_left">View file contents interactively</td>
<td class="align_left"><code>$ less foo</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">grep &lt;string&gt; &lt;file&gt;</code></td>
<td class="align_left">Find string in file</td>
<td class="align_left"><code>$ grep foo bar.txt</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">grep -i &lt;string&gt; &lt;file&gt;</code></td>
<td class="align_left">Find case-insensitively</td>
<td class="align_left"><code>$ grep -i foo bar.txt</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">ps</code></td>
<td class="align_left">Show processes</td>
<td class="align_left"><code>$ ps aux</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">top</code></td>
<td class="align_left">Show processes (sorted)</td>
<td class="align_left"><code>$ top</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">kill -&lt;level&gt; &lt;pid&gt;</code></td>
<td class="align_left">Kill a process</td>
<td class="align_left"><code>$ kill -15 24601</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">pkill -&lt;level&gt; -f &lt;name&gt;</code></td>
<td class="align_left">Kill matching processes</td>
<td class="align_left"><code>$ pkill -15 -f spring</code></td>
</tr>
</tbody>
</table>

#### Directories

<table class="tabular">
<tbody>
<tr class="bottom_border">
<td class="align_left"><strong>Command</strong></td>
<td class="align_left"><strong>Description</strong></td>
<td class="align_left"><strong>Example</strong></td>
</tr>
<tr>
<td class="align_left"><code class="tt">mkdir &lt;name&gt;</code></td>
<td class="align_left">Make directory with name</td>
<td class="align_left"><code>$ mkdir foo</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">pwd</code></td>
<td class="align_left">Print working directory</td>
<td class="align_left"><code>$ pwd</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">cd &lt;dir&gt;</code></td>
<td class="align_left">Change to &lt;dir&gt;</td>
<td class="align_left"><code>$ cd foo/</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">cd ~/&lt;dir&gt;</code></td>
<td class="align_left">cd relative to home</td>
<td class="align_left"><code>$ cd ~/foo/</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">cd</code></td>
<td class="align_left">Change to home directory</td>
<td class="align_left"><code>$ cd</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">cd -</code></td>
<td class="align_left">Change to previous directory</td>
<td class="align_left"><code>$ cd &amp;&amp; pwd &amp;&amp; cd -</code></td>
</tr>
<tr>
<td class="align_left">
<code class="tt">.</code><span class="intersentencespace"></span>
</td>
<td class="align_left">The current directory</td>
<td class="align_left">
<code>$ cp ~/foo.txt .</code><span class="intersentencespace"></span>
</td>
</tr>
<tr>
<td class="align_left">
<code class="tt">..</code><span class="intersentencespace"></span>
</td>
<td class="align_left">One directory up</td>
<td class="align_left"><code>$ cd ..</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">find</code></td>
<td class="align_left">Find files &amp; directories</td>
<td class="align_left"><code>$ find . -name foo*.*</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">cp -r &lt;old&gt; &lt;new&gt;</code></td>
<td class="align_left">Copy recursively</td>
<td class="align_left">
<code>$ cp -r ~/foo .</code><span class="intersentencespace"></span>
</td>
</tr>
<tr>
<td class="align_left"><code class="tt">rmdir &lt;dir&gt;</code></td>
<td class="align_left">Remove (empty) dir</td>
<td class="align_left"><code>$ rmdir foo/</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">rm -rf &lt;dir&gt;</code></td>
<td class="align_left">Remove dir &amp; contents</td>
<td class="align_left"><code>$ rm -rf foo/</code></td>
</tr>
<tr>
<td class="align_left"><code class="tt">grep -ri &lt;string&gt; &lt;dir&gt;</code></td>
<td class="align_left">Grep recursively (case-insensitive)</td>
<td class="align_left"><code>$ grep -ri foo bar/</code></td>
</tr>
</tbody>
</table>

### SOLID, KISS, YAGNI

**SOLID**

- S - SRP - Принцип единственной ответственности (The Single Responsibility Principle), каждый класс выполняет лишь одну задачу.
- O - OCP - Принцип открытости-закрытости (The Open-Closed Principle), "программмные сущности должны быть открыты для расширений...но закрыты для модификаций. Поведение сущности может быть расширено путём создания новых типов сущностей.
В результате расширения поведения сущности, не должны вноситься изменения в код, который эти сущности использует.
- L - LSP- Принцип подстановки Барбары Лисков (The Liskov Substitution Principle), "объекты в программе должны быть заменяемыми на экземпляры их подтипов без изменения правильности выполнения программы". Наследующий класс должен дополнять базовый, а не изменять его.
- I - ISP - Принцип разделения интерфейса (The Interface Segregation Principle), много интерфейсов, специально предназначенных для клиента лучше, чем один интерфейс общего назначения.
- D - DIP - Принцип инверсии зависимостей (The Dependency Inverse Principle), "Зависимость на абстракциях. Нет зависимости на что-то конкретное".

**KISS** - keep it simple, stupid

Принцип KISS утверждает, что большинство систем работают лучше всего, если они остаются простыми, а не усложняются. Поэтому в области проектирования простота должна быть одной из ключевых целей, и следует избегать ненужной сложности.

**YAGNI** - you aren't gonna need it

Процесс и принцип проектирования ПО, при котором в качестве основной цели и/или ценности декларируется отказ от избыточной функциональности, — то есть отказ добавления функциональности, в которой нет непосредственной надобности.

- Разбивайте задачи на подзадачи которые не должны по вашему мнению длиться более 4-12 часов написания кода
- Разбивайте задачу на множество более маленьких задач, каждая задача должна решаться одним или парой классов
- Сохраняйте ваши методы маленькими. Каждый метод должен состоять не более чем из 30-40 строк. Каждый метод должен решать одну маленькую задачу, а не множество случаев. Если в вашем методе множество условий, разбейте его на несколько. Это повысит читаемость, позволит легче поддерживать код и быстрее находить ошибки в нём. Вы полюбите улучшать код.
- Сохраняйте ваши классы маленькими. Здесь применяется та же техника что и с методами.
- Придумайте решение задачи сначала, потом напишите код. Никогда не поступайте иначе. Многие разработчики придумывают решение задачи во время написания кода и в этом нет ничего плохого. Вы можете делать так и при этом придерживаться выше обозначенного правила. Если вы можете в уме разбивать задачу на более мелкие части, когда вы пишете код, делайте это любыми способами. И не бойтесь переписывать код ещё и ещё и ещё… В счёт не идёт число строк, до тех пор пока вы считаете что можно ещё меньше/ещё лучше.
- Не бойтесь избавляться от кода. Изменение старого кода и написание нового решения два очень важных момента. Если вы столкнулись с новыми требованиями, или не были оповещены о них ранее, тогда порой лучше придумать новое более изящное решение решающее и старые и новые задачи.



### SSH

**ssh** - защищённый протокол удалённого доступа к компьютерам.

Ссылки:

- [Что такое SSH](https://guides.hexlet.io/ssh/)
- [Connecting to Github with SSH](https://help.github.com/en/articles/connecting-to-github-with-ssh)


### Network communication and security protocols

#### TCP/IP

Сетевая модель передачи данных. Состоит из четырёх уровней. 

- Канальный уровень (link layer / network access). Определяются правила использования физического уровня узлами сети. Передаёт данные узлам, находящимся в одном сегменте локальной сети. Примеры: **Ethernet, Point-to-Point Protocol, HDLC и ADCCP**. 

- Сетевой уровень (internet layer). Предназначает для определения пути передачи данных. Например, протокол **IP**.

- Транспортный уровень (transport layer). Решают проблему негарантированной доставки сообщений, а также обеспечивают правильную последовательность прихода данных. Примеры: **TCP, UDP, SCTP, DCCP**

- Прикладной уровень (application layer). На прикладном уровне работают большинство сетевых приложений. Является пограничным между прикладной программой и другими уровнями, обеспечивая удобный интерфейс связи для сетевых программ пользователя.

> **HTTP** протокол для веб-браузера; **SMTP** для почтовых программ; **FTP** для ftp-клиента; и многие другие. 

> **80** и **8080** порты для **HTTP**; **FTP** на 20 и 21; **SSH** на 22; **DNS** на порт UDP 53;

#### HTTP

> Протокол передачи гипертекста - (HyperText Transfer Protocol) - это протокол прикладного уровня для передачи гипертекстовых документов, таких как HTML. Создан для связи межеду веб-серверами и веб-браузерами, хотя в принципе может использоваться и для других целей.

[Больше информации тут.](https://developer.mozilla.org/ru/docs/Web/HTTP)

"HTTP as an application layer protocol, on top of TCP (transport layer) and IP (network layer) and below the presentation layer.

<img alt="HTTP as an application layer protocol, on top of TCP (transport layer) and IP (network layer) and below the presentation layer." src="https://mdn.mozillademos.org/files/13673/HTTP%20&amp;%20layers.png" style="float: left; height: 299px; padding-bottom: 15px; padding-right: 20px; width: 418px;">


HTML-сообщения бывают двух видов:

Запросы от клиента (обычно, GET или POST):
- HTTP-метод, обычно глагол подобно GET, POST или существительное, как OPTIONS или HEAD, определяющее операцию, которую клиент хочет выполнить. Обычно, клиент хочет получить ресурс (используя GET) или передать значения HTML-формы (используя POST), хотя другие операция могут быть необходимы в других случаях.
- Путь к ресурсу: URL ресурсы лишены элементов, которые очевидны из контекста, например без protocol (http://), domain (здесь developer.mozilla.org), или TCP port (здесь 80).
- Версию HTTP-протокола.
- Заголовки  (опционально), предоставляюшие дополнительную информацию для сервера.
- Или тело, для некоторых методов, таких как POST, которое содержит отправленный ресурс.

Пример:

<img alt="A basic HTTP request" src="https://mdn.mozillademos.org/files/13687/HTTP_Request.png" style="height: 336px; width: 693px;">

Ответы от сервера:
- Версию HTTP-протокола.
- HTTP код состояния, сообщающий об успешности запроса или причине неудачи.
- Сообщение состояния -- краткое описание кода состояния.
- HTTP заголовки, подобно заголовкам в запросах.
- Опционально: тело, содержащее пересылаемый ресурс.

Пример:

<img alt="" src="https://mdn.mozillademos.org/files/13691/HTTP_Response.png" style="height: 494px; width: 758px;">


HTTP коды состояния делятся на пять групп:

- Информационные сообщения (начинаются с числа 100)
- Сообщения о том, что операция прошла успешно (начинаются с числа 200)
- Перенаправления (начинаются с числа 300)
- Ошибки на стороне клиента (начинаются с числа 400)
- Ошибки сервера (начинаются с числа 500)

[Ссылка.](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

Основные HTTP методы:

- GET - служит для получения какой-то информации с сервера.
- HEAD - тоже самое, что и GET, но сервер в ответ на такой запрос не возвращает response body.
- POST - служит для отравки данных на сервер.
- PUT - тоже самое, что и POST. Разница между ними заключается в том, что многократные вызовы PUT будут приносить один и тот же результат, без side effect.

### Regular Expressions

Online builder - https://regex101.com/

## Backend


### Python

### Virtual environments and pip

Creating virtual environments:

`$ python3 -m venv ~/.virtualenvs/my-env`

Activating a virtual environment:

`$ source ~/.virtualenvs/my-env/bin/activate`

Deactivating a virtual environment:

`$ deactivate`

Searching packages:

`$ pip search **package_name**`

or simply go to [<pypi.org>](pypi.org)

Installing a package:

`$ pip install **package_name**`

Installing a specific version of a package:

`$ pip install **package_name**==1.2`

Upgraging a package:

`$ pip install --upgrade **package_name**`

Show an information about a particular package:

`$ pip show **package_name**`

Display all packages installed in the virtual environment:

`$ pip list`

Save list of packages in a txt file:

`$ pip freeze > requirements.txt`

Installing packages from a txt file:

`$ pip install -r requirements.txt`

More about `pip`: https://docs.python.org/3/installing/index.html#installing-index

