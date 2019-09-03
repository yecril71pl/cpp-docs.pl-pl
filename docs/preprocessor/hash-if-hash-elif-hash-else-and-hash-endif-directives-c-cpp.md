---
title: '#if, #elif, #else i #endif, dyrektywy (C/C++)'
ms.date: 08/29/2019
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
ms.openlocfilehash: 2b7ed4733dcafda793b9a945c3f40739b52e040a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220340"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>dyrektywy #if, #elif, #else i #endif (C/C++)

Dyrektywa **#if** , z dyrektywami **#elif**, **#else**i **#endif** , kontroluje kompilację fragmentów pliku źródłowego. Jeśli wyrażenie zapisane (po **#if**) ma wartość różną od zera, grupa wierszy zaraz po dyrektywie **#if** jest przechowywana w jednostce translacji.

## <a name="grammar"></a>Gramatyka

*warunkowo* : \
&nbsp;&nbsp;&nbsp;&nbsp;*elif-część* <sub>wybór</sub> *else-część* <sub>wybór</sub> *endif-line*

*if-Part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*tekst w wierszu*

*if-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *wyrażenie stałe*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *Identyfikator*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *Identyfikator*

*elif — części* : \
&nbsp;&nbsp;&nbsp;&nbsp;*elif — tekst wiersza*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-części elif — tekst wiersza*

*elif-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *wyrażenia stałego*

*else-część* : \
&nbsp;&nbsp;&nbsp;&nbsp;*tekst wiersza else*

*else-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

## <a name="remarks"></a>Uwagi

Każda dyrektywa **#if** w pliku źródłowym musi być zgodna z zamykającą **#endif** dyrektywą. Dowolna liczba dyrektyw **#elif** może występować między dyrektywami **#if** i **#endif** , ale co najmniej jedna dyrektywa **#else** jest dozwolona. Dyrektywa **#else** , jeśli istnieje, musi być ostatnią dyrektywą przed **#endif**.

Dyrektywy **#if**, **#elif**, **#else**i **#endif** mogą być zagnieżdżane w częściach *tekstowych* innych dyrektyw **#if** . Każdy zagnieżdżony **#else**, **#elif**lub **#endif** dyrektywy należy do najbliższej poprzedniej dyrektywy **#if** .

Wszystkie dyrektywy kompilacji warunkowej, takie jak **#if** i **#ifdef**, muszą być zgodne z zamykającą dyrektywą **#endif** przed końcem pliku. W przeciwnym razie zostanie wygenerowany komunikat o błędzie. Gdy dyrektywy kompilacji warunkowej są zawarte w plikach dołączanych, muszą spełniać te same warunki: Na końcu dołączonego pliku nie mogą istnieć żadne niezgodne dyrektywy kompilacji warunkowej.

Zastępowanie makr jest wykonywane w obrębie części wiersza, która następuje po poleceniu **#elif** , więc wywołanie makra może być używane w *wyrażeniu stałym*.

Preprocesor wybiera jedno z wystąpień *tekstu* do dalszej obróbki. Blok określony w *tekście* może być dowolną sekwencją tekstu. Może zajmować więcej niż jeden wiersz. Zwykle *tekst* jest tekstem programu, który ma znaczenie dla kompilatora lub preprocesora.

Preprocesor przetwarza zaznaczony *tekst* i przekazuje go do kompilatora. Jeśli *tekst* zawiera dyrektywy preprocesora, preprocesor wykonuje te dyrektywy. Kompilowane są tylko bloki tekstu wybrane przez preprocesor.

Preprocesor wybiera pojedynczy element *tekstowy* , oceniając wyrażenie stałe po każdej **#if** lub **#elif** dyrektywie, dopóki nie zostanie znalezione wyrażenie stałe o wartości true (niezerowej). Zaznacza cały tekst ( **#** łącznie z innymi dyrektywami preprocesora, zaczynającymi się od) do skojarzonych **#elif**, **#else**lub **#endif**.

Jeśli wszystkie wystąpienia *wyrażenia stałego* mają wartość false lub jeśli nie pojawiają się **#elif** dyrektywy, preprocesor wybiera blok tekstu po klauzuli **#else** . Gdy nie ma klauzuli **#else** , a wszystkie wystąpienia *wyrażenia stałej* w bloku **#if** mają wartość false, nie jest zaznaczony żaden blok tekstu.

*Wyrażenie stałe* jest wyrażeniem stałym całkowitym z następującymi dodatkowymi ograniczeniami:

- Wyrażenia muszą mieć typ całkowity i mogą zawierać tylko stałe całkowite, stałe znakowe i **zdefiniowany** operator.

- Wyrażenie nie może używać `sizeof` operatora rzutowania typu.

- Środowisko docelowe może nie reprezentować wszystkich zakresów liczb całkowitych.

- Tłumaczenie reprezentuje typ **int** w taki sam sposób jak typ **Long**i unsigned **int** tak samo jak **unsigned long**.

- Translator może przetłumaczyć stałe znaków na zestaw wartości kodu, które różnią się od zestawu dla środowiska docelowego. Aby określić właściwości środowiska docelowego, należy użyć aplikacji skompilowanej dla tego środowiska w celu sprawdzenia wartości *limitów. H* makra.

- Wyrażenie nie może wysyłać zapytań do środowiska i musi pozostać izolowane od szczegółów implementacji na komputerze docelowym.

## <a name="preprocessor-operators"></a>Operatory preprocesora

### <a name="defined"></a>zdefiniowane

**Zdefiniowany** operator preprocesora może być używany w specjalnych wyrażeniach stałych, jak pokazano w następującej składni:

> **zdefiniowane (** *Identyfikator* **)** \
> **zdefiniowane** *Identyfikator*

To wyrażenie stałe jest uznawane za prawdziwe (niezerowe), jeśli *Identyfikator* jest obecnie zdefiniowany. W przeciwnym razie warunek ma wartość false (0). Identyfikator zdefiniowany jako pusty tekst jest uznawany za zdefiniowany. **Zdefiniowanego** operatora można używać w **#if** i dyrektywie **#elif** , ale Nowhere else.

W poniższym przykładzie dyrektywy **#if** i **#endif** kontrolują kompilację jednego z trzech wywołań funkcji:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

Wywołanie `credit` funkcji jest kompilowane, jeśli identyfikator `CREDIT` jest zdefiniowany. Jeśli identyfikator `DEBIT` jest zdefiniowany, `debit` wywołanie funkcji jest kompilowane. Jeśli żaden z identyfikatorów nie jest zdefiniowany, wywołanie `printerror` jest kompilowane. Oba `CREDIT` i `credit` są unikatowymi identyfikatorami w C++ C i ponieważ ich przypadki są różne.

W instrukcjach kompilacji warunkowej w poniższym przykładzie przyjęto założenie, że `DLEVEL`wcześniej zdefiniowana stała symboliczna o nazwie.

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

Pierwszy blok **#if** przedstawia dwa zestawy zagnieżdżonych dyrektyw **#if**, **#else**i **#endif** . Pierwszy zestaw dyrektyw jest przetwarzany tylko wtedy, `DLEVEL > 5` gdy ma wartość true. W przeciwnym razie instrukcje po **#else** są przetwarzane.

Dyrektywy **#elif** i **#else** w drugim przykładzie służą do dokonania jednego z czterech opcji na podstawie wartości `DLEVEL`. Stała `STACK` jest ustawiona na 0, 100 lub 200, w zależności od `DLEVEL`definicji. Jeśli `DLEVEL` jest większa niż 5, instrukcja

```C
#elif DLEVEL > 5
display(debugptr);
```

jest kompilowany i `STACK` nie jest zdefiniowany.

Typowym zastosowaniem kompilacji warunkowej jest uniemożliwienie wielu dołączeń tego samego pliku nagłówkowego. W C++, gdzie klasy są często zdefiniowane w plikach nagłówkowych, konstrukcje takie jak te mogą służyć do zapobiegania wielu definicji:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

Poprzedni kod sprawdza, czy jest zdefiniowana stała `EXAMPLE_H` symboliczna. Jeśli tak, plik został już uwzględniony i nie wymaga ponownego przetworzenia. Jeśli nie, stała `EXAMPLE_H` jest zdefiniowana do oznaczania przykładu. H jako już przetworzony.

### <a name="__has_include"></a>__has_include

**Program Visual Studio 2017 w wersji 15,3 lub nowszej**:  Określa, czy nagłówek biblioteki jest dostępny do dołączenia:

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
