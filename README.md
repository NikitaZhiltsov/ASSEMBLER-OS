# ASSEMBLER-OS 
Ближе, еще ближе...

GNU AT&T

Инструкции

movq <src>, <dst> // общий синтаксис
  movq %RAX, %RDX // перекладываем значение из одного регистра в другой
  movq (%RAX), %RАX // () - операция разименования. Обращение к регистру, извлечение 8-байтного значения и запись в тот же регистр
  movq $42, %RАX // запись значения в регистр
  movq 42, %RАX // обращение к регистру 42, извлечение 8-байтного значения и запись в регистр RAX
  movq %value, %RАX // обращение к регистру по имени без разъименования
  movq value, %RАX // обращение по имени к регитстру и извлечение значения
  
addq <src>, <dst> // общий синтаксис сложения в регистрах
  addq %RAX, %RDX // прибавить значение из первого регистра ко второму и записать во второй результат
  addq %RAX, value // прибавить значение из первого регистра ко второму и записать во второй результат (ко второму обращаемся по имени)
  addq %42, %RDX // прибавить значение 42 к значению, хранящемуся в регистре записать результат
sub <src>, <dst> // общий синтаксис вычитания в регистрах
  
incq <op> // общий синтаксис инкремента в регистрах +1
  incq %RAX // вычесть 1 из значения, записанного в регистр RAX
decq <op> // общий синтаксис декремента в регистрах -1
  
mulq <op> // общий синтаксис умножения в регистрах
  RAX = (<op> * RAX) // множитель всегда в RAX, поэтому нужен только 1 аргумент. Результат сохранится в RAX - первые 64 бита. Оставшиеся                        // 64 бита - в RDX.
divq <op> // общий синтаксис деления в регистрах
                    // делимое всегда RAX, поэтому аргумент является делителем. Частное целое сохранится  в RAX, остаток от деления в RDX.

pushq <src>         // общий синтаксис помещения в стек. Регистр стека - всегда RSP. Этот регистр указывает на последнюю запись.
  e.g. pushq $42    // отнять 8 бит, взять значение 42, поместить в стек - lower. Теперь последняя запись в стеке - эта.
  e.g. pushq %RAX   // все то же самое, что и в примере выше, только теперь обращаемся к записанному в регистре.
popq <dst>          // общий синтаксис удаления из стека. Регистр стека - всегда RSP. Этот регистр указывает на последнюю запись.
  e.g. popq %RAX    // удалить последннее значение из стека и переместить в регистр RAX. Стек становится меньше на одну запись. Стек                           // становится higher
  
