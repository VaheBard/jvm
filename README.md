# JVM. Организация памяти, сборщики мусора, VisualVM

На первой строке кода вызывается загрузчик классов - ClassLoader.  
Appliaction ClassLoader с перва проверяет у себя, есть ли такие классы как в коде, при нахождении загружает,    
иначе передает эстафету родителю Platform ClassLoader, тот если не находит передает BootStrap ClassLoader.  
После загрузки идет проверка Verify - нет ли синтаксических ошибок...   
Потом идет процесс подготовки Prepare - выделяется память под этот класс...   
Далее идет разрешение символьных ссылок Resolve - все поля которые являются не статическими   
а динамичными превращаютс на указатели на реальные объекты в области памяти...  

На третей строке запускается метод main, и в этот момент в стэке образуется специальный фрейм(кадр)   
под этот метод, который будет хранить всю информацию которая будет собираться в нем.  
На четвертой строке выполнения кода, в стэк заносится информация о том что появился примитив i который равно 1.   
На пятой строке создается объект new Object(), под него в куче выделяется память, а указатель(ссылка) этого объекта    
"o" заносится в стэк.   
На шестой строке также в куче выделяется память для объекта Integer со значением 2, а переменная ii указывающая    
на этот объект заносится в стэк.   
На седьмой строке появляется новый фрейм, так как при вызове какого нибудь метода появляется новый фрейм.   
Программа переходит на 11 строку, аргументы метода будут копироваться от i = 1, и ссылки от выше указанных ссылок.   
Далее на 12 строке в куче выделяется память под Integer со значением 700, указатель которого useLessVar заносится в стэк.   
На 13 строке создается еще один фрейм, так как вызывается метод println. В нем создается еще фрейм в который заносится   
вычисление метода o.toString(). После чего фрейм printAll закрывается и программа возвращается на 8 строку.   
На 8 строке также появляется фрейм метода println, в нем создается переменная "finished", которая выводится на экран.   
Программа завершается!


