---
title: '#Jeśli, #elif, #else i #endif — dyrektywy (C/C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9d4f941298159b8a3ea1aa3fe37efd1e6dc68ab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846652"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if, #elif, #else i #endif — dyrektywy (C/C++)
`#if` Dyrektywy z `#elif`, `#else`, i `#endif` dyrektywy, kompilacja formanty części pliku źródłowego. Jeśli wyrażenie (po `#if`) ma wartość różną od zera, grupa wiersza od razu po `#if` dyrektywy są przechowywane w jednostce tłumaczenia.  
  
## <a name="grammar"></a>Gramatyka  
 *warunkowe* :  
 *Jeśli część elif części*opt*część else*opt*endif wiersza*  
  
 *Jeśli część* :  
 *Jeśli wiersz tekstu*  
  
 *Jeśli wiersz* :  
 **#if***wyrażenie stałej*   
  
 **#ifdef***identyfikator*  
  
 **#ifndef***identyfikator*  
  
 *elif części* :  
 *elif wiersza tekstu*  
  
 *elif części elif wiersza tekstu*  
  
 *elif — wiersz* :  
 **#elif**  *constant-expression*  
  
 *część else* :  
 *else wiersza tekstu*  
  
 *else wiersza* :  
 `#else`  
  
 *ENDIF-line* :  
 `#endif`  
  
 Każdy `#if` dyrektywy w pliku źródłowym muszą być zgodne przez zamknięcia `#endif` dyrektywy. Dowolną liczbę `#elif` dyrektywy może wystąpić między `#if` i `#endif` dyrektywy, ale co najwyżej jeden `#else` dyrektywa jest dozwolone. `#else` Dyrektywy, jeśli jest obecny, musi być ostatnim dyrektywy przed `#endif`.  
  
 `#if`, `#elif`, `#else`, I `#endif` dyrektywy można zagnieżdżać w innych części tekstu `#if` dyrektywy. Każdy zagnieżdżone `#else`, `#elif`, lub `#endif` dyrektywy należy do najbliższego poprzedzających `#if` dyrektywy.  
  
 Wszystkie dyrektywy kompilacja warunkowa, takich jak `#if` i **#ifdef**, muszą być zgodne z zamknięcia `#endif` dyrektywy przed końcem pliku; w przeciwnym razie zostanie wygenerowany komunikat o błędzie. Gdy kompilacja warunkowa dyrektywy są zawarte w plików dołączanych, muszą spełniać warunki tego samego: nie może być nie niedopasowane dyrektywy kompilacja warunkowa na końcu pliku dołączanego.  
  
 Zastąpienia makro jest wykonywane w część wiersza polecenia, który następuje `#elif` polecenia dzięki wywołanie makra mogą być używane w *wyrażenia*.  
  
 Preprocesora wybierze jeden z danego wystąpienia *tekst* dla dalszego przetwarzania. Określona w bloku *tekst* może być dowolną sekwencją tekstu. Można go zajmują więcej niż jeden wiersz. Zazwyczaj *tekst* jest tekst program, który ma znaczenie kompilatora lub preprocesora.  
  
 Preprocesora przetwarza wybranego *tekst* i przekazuje je do kompilatora. Jeśli *tekst* zawiera dyrektywy preprocesora preprocesora wykonuje te dyrektywy. Tylko bloki tekstu wybranych przez preprocesora są kompilowane.  
  
 Preprocesora wybiera jeden *tekst* elementu przez obliczenie wyrażenia stałej po każdym `#if` lub `#elif` dyrektywy aż do znalezienia true wyrażenie stałe (różną od zera). Go zaznacza cały tekst (w tym dyrektyw preprocesora, począwszy od **#**) do jego skojarzony `#elif`, `#else`, lub `#endif`.  
  
 Jeśli wszystkie wystąpienia *wyrażenia* są ma wartość FAŁSZ, lub jeśli nie `#elif` dyrektywy wyświetlana, preprocesora wybiera bloku tekstu po `#else` klauzuli. Jeśli `#else` pominięcia klauzuli i wszystkie wystąpienia *wyrażenia* w `#if` bloku są false, nie bloku tekstu jest zaznaczone.  
  
 *Wyrażenia* jest liczba całkowita stałego wyrażenia z te dodatkowe ograniczenia:  
  
-   Wyrażenia musi mieć typ całkowitoliczbowy i może zawierać tylko stałe całkowite, stałe znakowe i **zdefiniowane** operatora.  
  
-   Nie można użyć wyrażenia `sizeof` lub operator rzutowanie typu.  
  
-   Środowisko docelowe nie można reprezentować wszystkie zakresy liczb całkowitych.  
  
-   Tłumaczenie reprezentuje typ `int` taki sam jak typ **długi**, i `unsigned int` taki sam jak `unsigned long`.  
  
-   Translator może dokonywać translacji stałe znakowe do zestawu wartości kodów innego zestawu dla środowiska docelowego. Aby określić właściwości środowiska docelowego, należy sprawdzić wartości makra z limitów. H w aplikacji utworzonej dla środowiska docelowego.  
  
-   Wyrażenie nie musi wykonywać wszelkie zapytania środowiska i musi być izolowane od szczegóły implementacji na komputerze docelowym.  

## <a name="defined"></a>zdefiniowane  
 Operator preprocesora **zdefiniowane** mogą być używane w specjalne wyrażenia stałe, jak pokazano przy użyciu następującej składni:  
  
 Definicja ( `identifier` )  
  
 Definicja `identifier`  
  
 To wyrażenie stałej jest traktowane jako wartość true (różną od zera), jeśli *identyfikator* jest obecnie zdefiniowana; w przeciwnym razie wynikiem warunku jest FAŁSZ (0). Identyfikator zdefiniowany jako pusty tekst jest uznawane za zdefiniowane. **Zdefiniowane** dyrektywy mogą być używane w `#if` i `#elif` dyrektywa, ale nigdzie else.  
  
 W poniższym przykładzie `#if` i `#endif` dyrektywy sterowania kompilacji jednego z trzech wywołania funkcji:  
  
```  
#if defined(CREDIT)  
    credit();  
#elif defined(DEBIT)  
    debit();  
#else  
    printerror();  
#endif  
```  
  
 Wywołanie funkcji `credit` jest kompilowana, jeśli identyfikator `CREDIT` jest zdefiniowany. Jeśli identyfikator `DEBIT` jest zdefiniowany, wywołanie funkcji `debit` ma być kompilowana. Jeśli identyfikator nie jest zdefiniowany, wywołanie `printerror` ma być kompilowana. Należy pamiętać, że `CREDIT` i `credit` są unikatowych identyfikatorów C i C++, ponieważ ich przypadków są różne.  
  
 Instrukcje kompilacja warunkowa w poniższym przykładzie założono wcześniej zdefiniowaną stałą symboliczne o nazwie `DLEVEL`.  
  
```  
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
  
 Pierwszy `#if` blok zawiera dwa zestawy zagnieżdżonych `#if`, `#else`, i `#endif` dyrektywy. Pierwszy zestaw dyrektyw jest przetwarzany tylko wtedy, gdy `DLEVEL > 5` ma wartość true. W przeciwnym razie instrukcje po #**else** są przetwarzane.  
  
 `#elif` i `#else` dyrektywy w drugim przykładzie służą do jednej z czterech opcji, na podstawie wartości z `DLEVEL`. Stała `STACK` ma ustawioną wartość 0, 100 lub wartość 200, w zależności od definicji `DLEVEL`. Jeśli `DLEVEL` jest większa niż 5, a następnie instrukcji  
  
```  
#elif DLEVEL > 5  
display(debugptr);  
```  
  
 jest skompilowany i `STACK` nie jest zdefiniowany.  
  
 Użycia kompilacja warunkowa jest zapobiec wielu dołączenia tego samego pliku nagłówka. W języku C++, gdzie klasy często są zdefiniowane w pliki nagłówkowe, można zapobiegające wiele definicji konstrukcji podobne do poniższych:  
  
```  
/*  EXAMPLE.H - Example header file  */  
#if !defined( EXAMPLE_H )  
#define EXAMPLE_H  
  
class Example  
{  
...  
};  
  
#endif // !defined( EXAMPLE_H )  
```  
  
 Poprzedni kod sprawdza, czy symboliczne stała `EXAMPLE_H` jest zdefiniowany. Jeśli tak, plik został już dołączony i nie muszą być ponownie przetwarzany. Jeśli nie, stała `EXAMPLE_H` jest zdefiniowana na przykład oznaczyć. H tak już przetworzony.  

## <a name="hasinclude"></a>__has_include
**Visual Studio 2017 wersji 15.3 i nowszych**: Określa, czy nagłówek biblioteki są dostępne do włączenia:  

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
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)