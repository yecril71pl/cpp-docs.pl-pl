---
title: Deklaracje tablicy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee1c3be0ecc06dd2ccfb28882b6dc99912d7e13
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762479"
---
# <a name="array-declarations"></a>Deklaracje tablicy

"Array deklaracji" nazwy tablicy i określa typ jej elementów. Można także zdefiniować liczbę elementów w tablicy. Zmienna typu tablicy jest traktowany jako wskaźnik do typu elementów tablicy.

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *init-declarator-list*<sub>zoptymalizowany pod kątem</sub> **;**

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list***,***init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator* **=** *inicjatora*

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*deklarator bezpośrednio*: /\* deklaratora funkcji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio***[***wyrażenie_stałe*<sub>zoptymalizowany pod kątem</sub> **]** 

Ponieważ *wyrażenie_stałe* jest opcjonalne, składnia ma dwie formy:

-   Pierwszy formularz definiuje zmienną tablicową. *Wyrażenie_stałe* argument w nawiasach kwadratowych określa liczbę elementów w tablicy. *Wyrażenie_stałe*, jeśli jest obecna, musi mieć typ całkowitoliczbowy i wartość większą od zera. Każdy element ma typu podanego przez *Specyfikator typu*, które mogą być dowolnego typu z wyjątkiem `void`. Do elementu tablicy nie może być typu funkcji.

-   Druga forma deklaruje zmienną, która została zdefiniowana w innym miejscu. Pomija *wyrażenie_stałe* argumentu w nawiasy kwadratowe, ale nie nawiasy kwadratowe. Można użyć tego formularza, tylko jeśli wcześniej zainicjowana Tablica zadeklarowana jako parametr, lub zadeklarowana jako odwołanie do tablicy jawnie definiowane w innym miejscu w programie.

W obu formach *deklaratora bezpośrednio* nazwy zmiennej i może modyfikować typ zmiennej. Nawiasy kwadratowe (**[**) następujących *deklaratora bezpośrednio* modyfikowania deklaratorów typ tablicy.

Kwalifikatory typów może występować w deklaracji obiektu typu tablicy, ale kwalifikatory dotyczą elementów, a nie samej tablicy.

Można zadeklarować tablicy tablic (tablicy "wielowymiarowej"), postępując zgodnie z deklarator tablicy z listą stałe wyrażenia w nawiasach kwadratowych w tym formularzu:

> *Specyfikator typu* *deklaratora* **[** *wyrażenie_stałe* **]** **[** *wyrażenie_stałe* **]** ...

Każdy *wyrażenie_stałe* w nawiasach definiuje liczbę elementów w określonym wymiarze: tablice dwuwymiarowe mieć dwóch wyrażeń w nawiasach kwadratowych, mają trzy tablic trójwymiarowych i tak dalej. Możesz pominąć pierwsze wyrażenie stałe, jeśli mają zainicjowany Tablica zadeklarowana jako parametr, lub zadeklarowana jako odwołanie do tablicy jawnie definiowane w innym miejscu w programie.

Można zdefiniować tablice wskaźników do różnych typów obiektów przy użyciu deklaratorów złożonych, zgodnie z opisem w [interpretowanie bardziej Deklaratorów złożonych](../c-language/interpreting-more-complex-declarators.md).

Tablice są przechowywane wierszami. Na przykład następującą tablicę składa się z dwóch wierszach z trzech kolumnach:

```C
char A[2][3];
```

Trzy kolumny pierwszego wiersza są przechowywane najpierw następuje trzy kolumny drugiego wiersza. Oznacza to, że ostatni indeks dolny zmienia się najszybciej.

Aby odwołać się do pojedynczego elementu tablicy, należy użyć wyrażenie indeksu dolnego, zgodnie z opisem w [przyrostkowe operatory](../c-language/postfix-operators.md).

## <a name="examples"></a>Przykłady
Te przykłady ilustrują deklaracje tablicy:

```C
float matrix[10][15];
```

Dwuwymiarową tablicę o nazwie `matrix` 150 elementami, każdy o **float** typu.

```C
struct {
    float x, y;
} complex[100];
```

To jest deklaracją tablicy struktur. Ta tablica ma 100 elementów; Każdy element jest strukturą zawierającą dwa elementy członkowskie.

```C
extern char *name[];
```

Ta instrukcja deklaruje typ i nazwę tablicę wskaźników do `char`. Rzeczywistą definicją `name` wystąpi w innych miejscach.

**Microsoft Specific**

Typ liczby całkowitej do przeprowadzenia maksymalny rozmiar tablicy jest rozmiar **size_t**. Zdefiniowane w pliku nagłówkowym STDDEF. Godz., **size_t** jest `unsigned int` z zakresem 0x00000000 do 0x7CFFFFFF.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)