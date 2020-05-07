---
title: Deklaracje tablicy
ms.date: 11/04/2016
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
ms.openlocfilehash: 4bc75e86601da77758490544cc5b02c485dcee46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313548"
---
# <a name="array-declarations"></a>Deklaracje tablicy

"Deklaracja tablicowa" nazywa tablicę i określa typ jej elementów. Może również definiować liczbę elementów w tablicy. Zmienna typu Array jest uważana za wskaźnik na typ elementów tablicy.

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracje-specyfikatory* *init-deklarator-list*<sub>opt</sub> **;**

*init-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator-list*  **,**  *init-deklarator*

*init-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *inicjator* deklarator

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*Direct-deklarator*:/\* A funkcja deklarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator***[***wybór wyrażenia stałego*<sub>opt</sub> **]**    

Ze względu na to, że *wyrażenie stałe* jest opcjonalne, składnia ma dwa formy:

- Pierwszy formularz definiuje zmienną tablicową. Argument *stałej wartości* w nawiasach określa liczbę elementów w tablicy. *Wyrażenie stałe*, jeśli istnieje, musi mieć typ całkowity i wartość większą od zera. Każdy element ma typ określony przez *specyfikator typu*, który może być dowolnego typu z wyjątkiem `void`. Element tablicy nie może być typem funkcji.

- Druga forma deklaruje zmienną, która została zdefiniowana w innym miejscu. Pomija argument *wyrażenia stałej* w nawiasach, ale nie nawiasów. Tego formularza można używać tylko wtedy, gdy wcześniej zainicjowano tablicę, zadeklarowano ją jako parametr lub zadeklarowano ją jako odwołanie do tablicy jawnie zdefiniowanej w innym miejscu w programie.

W obu formularzach, *Direct-deklarator* nazywa zmienną i może modyfikować typ zmiennej. Nawiasy kwadratowe (**[]**) są następujące: *deklarator* Modify deklarator do typu tablicy.

Kwalifikatory typu mogą występować w deklaracji obiektu typu Array, ale kwalifikatory stosują się do elementów, a nie do tablicy.

Można zadeklarować tablicę tablic (tablicę wielowymiarową), używając tablicy deklarator z listą wyrażeń stałych w nawiasach w tej postaci:

> *Typ-specyfikator* *deklarator* **[** *wyrażenie stałe* **]** **[** *wyrażenie stałe* **]** ...

Każde *wyrażenie stałe* w nawiasach definiuje liczbę elementów w danym wymiarze: tablice dwuwymiarowe mają dwa wyrażenia z nawiasami, trzy wielowymiarowe tablice mają trzy itd. Możesz pominąć pierwsze wyrażenie stałe, jeśli została zainicjowana tablica, zadeklarowana jako parametr lub zadeklarowana jako odwołanie do tablicy jawnie zdefiniowanej w innym miejscu w programie.

Można definiować tablice wskaźników do różnych typów obiektów przy użyciu złożonych deklaratory, zgodnie z opisem w [interpretacji bardziej złożonej Deklaratory](../c-language/interpreting-more-complex-declarators.md).

Tablice są przechowywane w wierszu. Na przykład następująca tablica składa się z dwóch wierszy z trzema kolumnami:

```C
char A[2][3];
```

Trzy kolumny pierwszego wiersza są przechowywane jako pierwsze, a następnie trzy kolumny drugiego wiersza. Oznacza to, że ostatni indeks dolny różni się najbardziej szybko.

Aby odwołać się do pojedynczego elementu tablicy, użyj wyrażenia indeksu dolnego, zgodnie z opisem w [Operatory przyrostkowe](../c-language/postfix-operators.md).

## <a name="examples"></a>Przykłady

Przykłady ilustrują deklaracje tablic:

```C
float matrix[10][15];
```

Tablica dwuwymiarowa o nazwie `matrix` zawiera 150 elementów, każdy z typem **zmiennoprzecinkowym** .

```C
struct {
    float x, y;
} complex[100];
```

Jest to Deklaracja tablicy struktur. Ta tablica zawiera 100 elementów; Każdy element jest strukturą zawierającą dwóch członków.

```C
extern char *name[];
```

Ta instrukcja deklaruje typ i nazwę tablicy wskaźników do `char`. Rzeczywista definicja `name` występuje w innym miejscu.

**Specyficzne dla firmy Microsoft**

Typ liczby całkowitej wymaganej do przechowywania maksymalnego rozmiaru tablicy jest rozmiarem **size_t**. Zdefiniowane w pliku nagłówka STDDEF. H, **size_t** jest `unsigned int` z zakresem od 0x00000000 do 0x7CFFFFFF.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md)
