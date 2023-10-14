# SimpleParser
Задание для оболтусов из моей группы на ФФ НГУ.

## Мотивация:
Научиться писать парсеры и получить кучу баллов по курсу C++/Python.

## Цель:
Написать парсер, который бы "съедал" бы выражение на языке Lox (из книги [Crafting Interpreters](https://craftinginterpreters.com) за авторством Роберта Нистрома) и выдавал бы лист токенов. 

## Требования: 
Грамматика языка Lox выглядит следующим образом (за пояснениями проследуйте в главы 4-6 вышеуказанной книги):
expression     → literal
            | unary
            | binary
            | grouping ;

literal        → NUMBER | STRING | "true" | "false" | "nil" ;
grouping       → "(" expression ")" ;
unary          → ( "-" | "!" ) expression ;
binary         → expression operator expression ;
operator       → "==" | "!=" | "<" | "<=" | ">" | ">="
            | "+"  | "-"  | "*" | "/" ;

Вам нужно реализовать две функции:
* Одна считывает файл расширения .lox и выдаёт массив токенов
* Другая считывает из консоли введённую строку пишет массив токенов в консоль (запись типа TOKEN_NAME TOKEN Value).
Выглядит это примерно так
    Input: if (true == true) { a + 1 }
    Output:
    IF if null
    LEFT_PAREN ( null
    TRUE true null
    EQUAL_EQUAL == null
    TRUE true null
    RIGHT_PAREN ) null
    LEFT_BRACE { null
    IDENTIFIER a null
    PLUS + null
    NUMBER 1 1.0
    RIGHT_BRACE } null
    EOF  null

## Важно: 
* Ваш парсер должен улавливать простейшие синтаксические ошибки (непарная скобка и т.п) и выдавать сообщение о наличии ошибки.
* Вам **не нужно** исполнять команды языка. Вам нужно просто "прочитать" написанное.