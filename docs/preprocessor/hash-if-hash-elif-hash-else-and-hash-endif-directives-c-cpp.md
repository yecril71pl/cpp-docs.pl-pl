---
title: '#IF, #elif, #else i #endif, dyrektywy (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
ms.openlocfilehash: 90fbab45c6408c30198c2a52a42545718002cc11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409892"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if, #elif, #else i #endif — dyrektywy (C/C++)

**#If** dyrektywy, za pomocą **#elif**, **#else**, i **#endif** dyrektyw, formanty kompilację części pliku źródłowego. Jeśli wyrażenie (po **#if**) ma wartość różną od zera, grupa linii następująca bezpośrednio **#if** dyrektywa jest zachowywana w jednostce translacji.

## <a name="grammar"></a>Gramatyka

*warunkowe* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*część IF części elif*<sub>zoptymalizowany pod kątem</sub> *część else*<sub>zoptymalizowany pod kątem</sub> *linia endif*

*część IF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*tekst z wierszem z operatorem IF*

*wiersz z operatorem IF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *wyrażenia stałego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identyfikator*

*części elif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*tekst linii elif*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*tekst linii elif części elif*

*Linia elif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *wyrażenia stałego*

*część else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*tekst linii else*

*else linii* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*Linia ENDIF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

Każdy **#if** dyrektywy w pliku źródłowym musi towarzyszyć zamykający **#endif** dyrektywy. Dowolną liczbę **#elif** dyrektyw może pojawić się między **#if** i **#endif** dyrektyw, ale co najwyżej jeden **#else** dyrektywa jest dozwolone. **#Else** dyrektywy, jeśli jest obecna, musi być ostatnią dyrektywą przed **#endif**.

**#If**, **#elif**, **#else**, i **#endif** dyrektywy można zagnieździć w części tekstowej innych **#if**dyrektywy. Każda zagnieżdżona **#else**, **#elif**, lub **#endif** dyrektywa należy do najbliższej poprzedzającej **#if** dyrektywy.

Wszystkie dyrektywy kompilacji warunkowej, takie jak **#if** i **#ifdef**, muszą się zgadzać z zamknięciem **#endif** dyrektyw przed końcem pliku; w przeciwnym razie błąd komunikat jest generowany. Gdy dyrektywy kompilacji warunkowej są zawarte w plików dołączanych, muszą spełniać te same warunki: Musi istnieć nie niedopasowane dyrektywy kompilacji warunkowej na końcu pliku dyrektywy include.

Wymiana makra jest wykonywana w części wiersza polecenia, który następuje po **#elif** poleceń, więc wywołanie makra mogą być używane w *wyrażenie_stałe*.

Preprocesor wybiera jedno z wystąpień danego *tekst* do dalszego przetwarzania. Określona w bloku *tekstu* może być dowolną sekwencją tekstu. Może zajmować więcej niż jeden wiersz. Zazwyczaj *tekstu* to tekst programu, który ma znaczenie dla kompilatora lub preprocesora.

Preprocesor przetwarza wybrany *tekst* i przekazuje go do kompilatora. Jeśli *tekstu* zawiera dyrektywy preprocesora, preprocesor wykonuje te dyrektywy. Tylko bloki tekstu wybrane przez preprocesor są kompilowane.

Preprocesor wybiera pojedynczy *tekstu* element oceniając wyrażenie stałej następujące po każdym **#if** lub **#elif** dyrektywy do momentu znalezienia prawdziwe (niezerowe) — stała wyrażenie. Go powoduje zaznaczenie całego tekstu (włączając inne dyrektywy preprocesora, począwszy od **#** ) do związanych z nią **#elif**, **#else**, lub **#endif** .

Jeśli wszystkie wystąpienia *wyrażenie_stałe* są fałszywe lub jeśli nie **#elif** dyrektywy pojawia się, preprocesor wybiera blok tekstu po **#else** klauzuli. Jeśli **#else** pominięcia klauzuli i wszystkie wystąpienia *wyrażenie_stałe* w **#if** bloku są fałszywe, jest zaznaczony żaden blok tekstu.

*Wyrażenie_stałe* to wyrażenie stałe liczby całkowitej z następującymi ograniczeniami dodatkowymi:

- Wyrażenia muszą mieć typ całkowity i mogą obejmować tylko stałe będące liczbami całkowitymi, stałe znaków i **zdefiniowane** operatora.

- Nie można użyć wyrażenia `sizeof` lub operatora typu rzutowania.

- Środowisko docelowe może nie być w stanie odtworzyć wszystkich zakresów liczb całkowitych.

- Tłumaczenie reprezentuje typ **int** taki sam jak typ **długie**, i **unsigned int** taka sama jak **unsigned long**.

- Tłumacz może przetłumaczyć stałe znaków na zestaw wartości kodu inny od zestawy środowiska docelowego. Aby określić właściwości środowiska docelowego, sprawdź wartości makr z limitów. H w aplikacji utworzonej dla środowiska docelowego.

- Wyrażenie nie musi wykonywać żadnych zapytań środowiska i musi być izolowane od szczegółów implementacji na komputerze docelowym.

## <a name="defined"></a>zdefiniowane

Operator preprocesora **zdefiniowane** mogą być używane w specjalnym wyrażeniu stałym, jak pokazano w następującej składni:

zdefiniowany ( `identifier` )

Definicja `identifier`

To wyrażenie stałej jest uważany za wartość true (niezerową), jeśli *identyfikator* jest obecnie zdefiniowany; w przeciwnym razie warunek jest fałszywy (0). Identyfikator zdefiniowany jako pusty tekst jest uważany za zdefiniowany. **Zdefiniowane** dyrektywa może być używana w **#if** i **#elif** dyrektywy, nigdzie indziej.

W poniższym przykładzie **#if** i **#endif** dyrektywy kontrolują kompilację jednego z trzech wywołań funkcji:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

Wywołanie funkcji `credit` jest kompilowana, jeśli identyfikator `CREDIT` jest zdefiniowany. Jeśli identyfikator `DEBIT` jest zdefiniowany, wywołanie funkcji `debit` jest kompilowany. Jeśli żaden identyfikator nie jest zdefiniowany, wywołania `printerror` jest kompilowany. Należy pamiętać, że `CREDIT` i `credit` są różnymi identyfikatorami w C i C++, ponieważ ich przypadki są różne.

Instrukcje kompilacji warunkowej w poniższym przykładzie zakładają wcześniej zdefiniowaną symboliczne stałą o nazwie `DLEVEL`.

```C
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```

Pierwszy **#if** blok zawiera dwa zestawy zagnieżdżonych **#if**, **#else**, i **#endif** dyrektywy. Pierwszy zestaw dyrektyw jest przetwarzany tylko wtedy, gdy `DLEVEL > 5` ma wartość true. W przeciwnym razie instrukcje po **#else** są przetwarzane.

**#Elif** i **#else** dyrektywy w drugim przykładzie są wykorzystywane do wytwarzania jednego z czterech wyborów, w oparciu o wartość `DLEVEL`. Stała `STACK` jest ustawiona na 0, 100 lub 200, w zależności od definicji `DLEVEL`. Jeśli `DLEVEL` jest większa niż 5, instrukcja

```C
#elif DLEVEL > 5
display(debugptr);
```

jest skompilowany i `STACK` nie został zdefiniowany.

Typowym zastosowaniem dla kompilacji warunkowej jest zapobieganie wielu dołączeniom tego samego pliku nagłówka. W języku C++, w którym klasy często są zdefiniowane w plikach nagłówkowych, następujące konstrukcje może służyć do zapobieżenia wielu definicjom:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
...
};

#endif // !defined( EXAMPLE_H )
```

Poprzedzający kod sprawdza, czy symboliczna stała `EXAMPLE_H` jest zdefiniowana. Jeśli tak, plik został już włączony i nie muszą być ponownie przetwarzany. Jeśli nie, stała `EXAMPLE_H` jest definiowana, aby oznaczyć PRZYKŁADU. H jako już przetworzone.

## <a name="hasinclude"></a>__has_include

**Visual Studio 2017 w wersji 15.3 lub nowszej**:  Określa, czy nagłówek biblioteki są dostępne do włączenia:

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)