---
title: Specyfikatory klasy magazynowania dla deklaracji na poziomie zewnętrznym (C)
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
ms.openlocfilehash: 6c30b8a12c0bf26bc35905872fb6fa527b367ef4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229470"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>Specyfikatory klasy magazynowania dla deklaracji na poziomie zewnętrznym (C)

Zmienne zewnętrzne są zmiennymi w zakresie pliku. Są zdefiniowane poza jakąkolwiek funkcją i są potencjalnie dostępne dla wielu funkcji. Funkcje mogą być definiowane tylko na poziomie zewnętrznym i dlatego nie mogą być zagnieżdżane. Domyślnie wszystkie odwołania do zmiennych zewnętrznych i funkcji o tej samej nazwie są odwołaniami do tego samego obiektu, co oznacza, że mają *zewnętrzne powiązania*. (Możesz użyć **`static`** słowa kluczowego, aby przesłonić to zachowanie).

Deklaracje zmiennych na poziomie zewnętrznym są definicjami zmiennych (*Definiowanie deklaracji*) lub odwołaniami do zmiennych zdefiniowanych w innym miejscu (*deklaracje odwołania*).

Zewnętrzna deklaracja zmiennej, która również inicjuje zmienną (jawnie lub niejawnie) jest deklaracją definiującą zmienną. Definicja na poziomie zewnętrznym może przybierać różne formy:

- Zmienna zadeklarowana ze **`static`** specyfikatorem klasy magazynu. Można jawnie zainicjować **`static`** zmienną za pomocą wyrażenia stałego, zgodnie z opisem w [inicjalizacji](../c-language/initialization.md). Jeżeli pominięto inicjator, zmienna jest inicjowana domyślnie na wartość 0. Na przykład, następujące dwie instrukcje są rozważane jako definicje zmiennej `k`.

    ```C
    static int k = 16;
    static int k;
    ```

- Zmienna jawnie zainicjowana na poziomie zewnętrznym. Na przykład, `int j = 3;` jest definicją zmiennej `j`.

W deklaracjach zmiennych na poziomie zewnętrznym (czyli poza wszystkimi funkcjami) można użyć **`static`** **`extern`** specyfikatora klasy magazynu lub lub całkowicie pominąć specyfikator klasy magazynowania. Nie można używać **`auto`** terminali i **`register`** *`storage-class-specifier`* na poziomie zewnętrznym.

Gdy zmienna jest zdefiniowana na poziomie zewnętrznym, jest widoczna w pozostałej części jednostki translacji. Zmienna nie jest widoczna przed jej deklaracją, w tym samym pliku źródłowym. Ponadto, nie jest widoczna w innych plikach źródłowych programu, chyba że deklaracja odwołaniowa sprawia, że staje się widoczna, jak opisano poniżej.

Reguły dotyczące programu **`static`** obejmują:

- Zmienne zadeklarowane poza wszystkimi blokami bez **`static`** słowa kluczowego zawsze zachowują swoje wartości w całym programie. Aby ograniczyć dostęp do określonej jednostki tłumaczenia, należy użyć **`static`** słowa kluczowego. Zapewnia to *wewnętrzne połączenie*. Aby uczynić je globalnymi w całym programie, należy pominąć jawną klasę magazynu lub użyć słowa kluczowego **`extern`** (patrz reguły na następnej liście). Zapewnia to *zewnętrzny związek*. Powiązanie wewnętrzne i zewnętrzne są również omówione w [połączeniu](../c-language/linkage.md).

- Można zdefiniować zmienną na poziomie zewnętrznym tylko raz w programie. Można zdefiniować inną zmienną o tej samej nazwie i **`static`** specyfikatorze klasy magazynu w innej jednostce translacji. Ponieważ każda **`static`** definicja jest widoczna tylko w ramach własnej jednostki tłumaczenia, nie występuje konflikt. Zapewnia to przydatny sposób ukrywania nazw identyfikatorów, które muszą być współużytkowane przez funkcje pojedynczej jednostki tłumaczenia, ale nie są widoczne dla innych jednostek tłumaczenia.

- **`static`** Specyfikator klasy magazynu może być również stosowany do funkcji. Jeśli deklarujesz funkcję **`static`** , jej nazwa jest niewidoczna poza plikiem, w którym jest zadeklarowana.

Zasady korzystania z programu **`extern`** to:

- **`extern`** Specyfikator klasy magazynu deklaruje odwołanie do zmiennej zdefiniowanej w innym miejscu. Można użyć **`extern`** deklaracji, aby utworzyć definicję w innym pliku źródłowym lub aby zmienna była widoczna przed jej definicją w tym samym pliku źródłowym. Po zadeklarowaniu odwołania do zmiennej na poziomie zewnętrznym zmienna jest widoczna w całej pozostałej części jednostki translacji, w której występuje zadeklarowane odwołanie.

- Aby **`extern`** odwołanie było prawidłowe, zmienna, do której się odwołuje, musi być zdefiniowana raz i tylko raz, na poziomie zewnętrznym. Ta definicja (bez **`extern`** klasy magazynu) może znajdować się w dowolnej jednostce translacji, która składa się z programu.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje deklaracje zewnętrzne:

```C
/******************************************************************
                      SOURCE FILE ONE
*******************************************************************/
#include <stdio.h>

extern int i;                // Reference to i, defined below
void next( void );           // Function prototype

int main()
{
    i++;
    printf_s( "%d\n", i );   // i equals 4
    next();
}

int i = 3;                  // Definition of i

void next( void )
{
    i++;
    printf_s( "%d\n", i );  // i equals 5
    other();
}

/******************************************************************
                      SOURCE FILE TWO
*******************************************************************/
#include <stdio.h>

extern int i;              // Reference to i in
                           // first source file
void other( void )
{
    i++;
    printf_s( "%d\n", i ); // i equals 6
}
```

Dwa pliki źródłowe w tym przykładzie zawierają łącznie trzy zewnętrzne deklaracje `i`. Tylko jedna deklaracja jest „deklaracją definiującą”. Deklaracja,

```C
int i = 3;
```

definiuje zmienną globalną `i` oraz inicjuje ją początkową wartością 3. Deklaracja "odwołanie" `i` w górnej części pierwszego pliku źródłowego przy użyciu **`extern`** sprawia, że zmienna globalna jest widoczna przed jej zdefiniowaną deklaracją w pliku. Deklaracja odwołaniowa `i` w drugim pliku źródłowym również sprawia, że zmienna jest widoczna w tym pliku źródłowym. Jeśli wystąpienie definiujące zmiennej nie jest dostarczone w jednostce tłumaczenia, kompilator zakłada deklarację odwołaniową

```C
extern int x;
```

deklaracja odwołaniowa i oraz odwołanie definiujące

```C
int x = 0;
```

pojawia się w innej jednostce translacji programu.

Wszystkie trzy funkcje `main`, `next` i `other`, wykonują to samo zadanie: zwiększają `i` oraz drukują. Drukowane są wartości 4, 5 i 6.

Jeśli zmienna `i` nie została zainicjowana, wartość zostanie ustawiona na 0 automatycznie. W tym przypadku byłyby wypisane wartości 1, 2 i 3. Zobacz [Inicjowanie](../c-language/initialization.md) informacji o inicjacji zmiennej.

## <a name="see-also"></a>Zobacz także

[Klasy magazynu w języku C](../c-language/c-storage-classes.md)
