---
title: Tablice wielowymiarowe (C)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
ms.openlocfilehash: f94cdff03763f689edbdedffad4ac56abec5ee53
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218835"
---
# <a name="multidimensional-arrays-c"></a>Tablice wielowymiarowe (C)

Wyrażenie indeksu dolnego może mieć wiele indeksów dolnych, jak pokazano poniżej:

```
expression1 [ expression2 ] [ expression3 ] ...
```

Wyrażenia indeksu dolnego są skojarzone od lewej do prawej. Pierwszy wyrażenie indeksu dolnego, *wyrażenie1* **[** *wyrażenie2* **]**, jest oceniane jako pierwsze. Adres, który wynika z dodania elementu *wyrażenie1* i *wyrażenie2* tworzą wyrażenie wskaźnika; następnie *expression3* jest dodawany do tego wyrażenia wskaźnika, aby utworzyć nowe wyrażenie wskaźnika i tak dalej, aż do ostatniego wyrażenia indeksu dolnego. Operator pośredni ( <strong>\*</strong> ) jest stosowany po obliczeniu ostatniego wyrażenia indeksu dolnego, chyba że końcowa wartość wskaźnika odnosi się do typu tablicy (Zobacz przykłady poniżej).

Wyrażenia zawierające wiele indeksów dolnych odwołują się do elementów „tablic wielowymiarowych”. Tablica wielowymiarowa jest tablicą, której elementy są tablicami. Na przykład, pierwszy element tablicy trójwymiarowej jest tablicą z dwoma wymiarami.

## <a name="examples"></a>Przykłady

W poniższych przykładach tablica o nazwie `prop` jest zadeklarowana z trzema elementami, z których każdy jest tablicą o wartości 4 na 6 **`int`** .

```
int prop[3][4][6];
int i, *ip, (*ipp)[6];
```

Odwołanie do tablicy `prop` wygląda następująco:

```
i = prop[0][0][1];
```

Powyższy przykład pokazuje, jak odwołać się do drugiego pojedynczego **`int`** elementu `prop` . Tablice są przechowywane wierszami, zatem ostatni indeks dolny zmienia się najszybciej; wyrażenie `prop[0][0][2]` odwołuje się do następnego (trzeciego) elementu tablicy, i tak dalej.

```
i = prop[2][1][3];
```

Ta instrukcja jest bardziej złożonym odwołaniem do pojedynczego elementu tablicy `prop`. Wyrażenie jest oceniane w następujący sposób:

1. Pierwszy indeks dolny `2` jest mnożony przez rozmiar tablicy o wielkości 4 na 6 **`int`** i dodany do wartości wskaźnika `prop` . Wynik wskazuje na trzecią tablicę `prop` o wymiarach 4 na 6.

1. Drugi indeks dolny `1` jest mnożony przez rozmiar 6-elementowej **`int`** tablicy i dodawany do adresu reprezentowanego przez `prop[2]` .

1. Każdy element w 6-elementowej tablicy jest **`int`** wartością, więc końcowy indeks dolny `3` jest mnożony przez rozmiar **`int`** przed dodaniem do `prop[2][1]` . Wskaźnik wynikowy adresuje czwarty element 6-elementowej tablicy.

1. Operator pośredni jest stosowany do wartości wskaźnika. Wynikiem jest **`int`** element na tym adresie.

W dwóch następnych przykładach pokazano przypadki, w których nie jest stosowany operator pośredni.

```
ip = prop[2][1];

ipp = prop[2];
```

W pierwszej z tych instrukcji wyrażenie `prop[2][1]` jest prawidłowym odwołaniem do trójwymiarowej tablicy `prop`; odwołuje się ono do 6-elementowej tablicy (zadeklarowanej powyżej). Ponieważ wartość wskaźnika adresuje tablicę, operator pośredni nie jest stosowany.

Podobnie, wynik wyrażenia `prop[2]` w drugiej instrukcji `ipp = prop[2];` jest wartością wskaźnika adresującą tablicę dwuwymiarową.

## <a name="see-also"></a>Zobacz także

[Operator indeksu dolnego:](../cpp/subscript-operator.md)
