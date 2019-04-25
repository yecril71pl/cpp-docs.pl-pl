---
title: Tablice wielowymiarowe (C)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
ms.openlocfilehash: 34f5c60ba9ba5da869426ae4971808a5d75fee2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233366"
---
# <a name="multidimensional-arrays-c"></a>Tablice wielowymiarowe (C)

Wyrażenie indeksu dolnego może mieć wiele indeksów dolnych, jak pokazano poniżej:

```
expression1 [ expression2 ] [ expression3 ] ...
```

Wyrażenia indeksu dolnego są skojarzone od lewej do prawej. Skrajnie po lewej stronie wyrażenia indeksu dolnego, *wyrażenie1* **[** *wyrażenie2* **]**, jest stosowana jako pierwsza. Adres, który jest wynikiem dodawania *wyrażenie1* i *wyrażenie2* stanowi wyrażenie wskaźnika; następnie *expression3* jest dodawany do tego wyrażenia wskaźnika w celu utworzenia nowego wyrażenia wskaźnika, i tak dalej, aż ostatniego wyrażenia indeksu dolnego został dodany. Operator pośredni (<strong>\*</strong>) są stosowane po ostatnim indeksem wyrażenie jest obliczane, chyba że wskaźnik końcowej wartości typ tablicowy (Zobacz przykłady poniżej).

Wyrażenia zawierające wiele indeksów dolnych odwołują się do elementów „tablic wielowymiarowych”. Tablica wielowymiarowa jest tablicą, której elementy są tablicami. Na przykład, pierwszy element tablicy trójwymiarowej jest tablicą z dwoma wymiarami.

## <a name="examples"></a>Przykłady

W poniższych przykładach tablica o nazwie `prop` została zadeklarowana za pomocą trzech elementów, z których każdy jest tablicą o wymiarach 4 na 6, zawierającą wartości typu `int`.

```
int prop[3][4][6];
int i, *ip, (*ipp)[6];
```

Odwołanie do tablicy `prop` wygląda następująco:

```
i = prop[0][0][1];
```

W powyższym przykładzie pokazano, w jaki sposób odwołać się pojedynczo do drugiego elementu typu `int` w tablicy `prop`. Tablice są przechowywane wierszami, zatem ostatni indeks dolny zmienia się najszybciej; wyrażenie `prop[0][0][2]` odwołuje się do następnego (trzeciego) elementu tablicy, i tak dalej.

```
i = prop[2][1][3];
```

Ta instrukcja jest bardziej złożonym odwołaniem do pojedynczego elementu tablicy `prop`. Wyrażenie jest oceniane w następujący sposób:

1. Pierwszy indeks dolny `2` jest mnożony przez rozmiar tablicy typu `int` o wymiarach 4 na 6 i dodawany do wartości wskaźnika tablicy `prop`. Wynik wskazuje na trzecią tablicę `prop` o wymiarach 4 na 6.

1. Drugi indeks dolny `1` jest mnożony przez rozmiar 6-elementowej tablicy typu `int` i dodawany do adresu reprezentowanego przez `prop[2]`.

1. Każdy element 6-elementowej tablicy jest wartością typu `int`, więc końcowy indeks dolny `3` jest mnożony przez rozmiar typu `int`, zanim zostanie dodany do `prop[2][1]`. Wskaźnik wynikowy adresuje czwarty element 6-elementowej tablicy.

1. Operator pośredni jest stosowany do wartości wskaźnika. Wynik jest elementem typu `int` pod tym adresem.

W dwóch następnych przykładach pokazano przypadki, w których nie jest stosowany operator pośredni.

```
ip = prop[2][1];

ipp = prop[2];
```

W pierwszej z tych instrukcji wyrażenie `prop[2][1]` jest prawidłowym odwołaniem do trójwymiarowej tablicy `prop`; odwołuje się ono do 6-elementowej tablicy (zadeklarowanej powyżej). Ponieważ wartość wskaźnika adresuje tablicę, operator pośredni nie jest stosowany.

Podobnie, wynik wyrażenia `prop[2]` w drugiej instrukcji `ipp = prop[2];` jest wartością wskaźnika adresującą tablicę dwuwymiarową.

## <a name="see-also"></a>Zobacz także

[Operator indeksu dolnego:](../cpp/subscript-operator.md)
