---
title: Wielowymiarowe Arrays (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3b067db3812fbe7e5db1d367635eedc5362527
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="multidimensional-arrays-c"></a>Tablice wielowymiarowe (C)
Wyrażenie indeksu dolnego może mieć wiele indeksów dolnych, jak pokazano poniżej:  
  
```  
  
expression1  
[  
expression2  
] [  
expression3  
]...  
```  
  
 Wyrażenia indeksu dolnego są skojarzone od lewej do prawej. Po lewej stronie wyrażenia indeksu * wyrażenie1***[***wyrażenie2 ***]**, jest szacowana jako pierwsza. Adres, który jest wynikiem Dodawanie *wyrażenie1* i *wyrażenie2* formularzy wyrażenia wskaźnika; następnie *expression3* zostanie dodany do tego wyrażenia wskaźnika do utworzenia nowego wyrażenia wskaźnika, i tak dalej, aż ostatniego wyrażenia indeksu został dodany. Operator pośredni (**\***) są stosowane po ostatnim jako wyrażenie jest obliczane, chyba że wpisz adresy wartość końcowego wskaźnika do tablicy (Zobacz przykłady poniżej).  
  
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
  
1.  Pierwszy indeks dolny `2` jest mnożony przez rozmiar tablicy typu `int` o wymiarach 4 na 6 i dodawany do wartości wskaźnika tablicy `prop`. Wynik wskazuje na trzecią tablicę `prop` o wymiarach 4 na 6.  
  
2.  Drugi indeks dolny `1` jest mnożony przez rozmiar 6-elementowej tablicy typu `int` i dodawany do adresu reprezentowanego przez `prop[2]`.  
  
3.  Każdy element 6-elementowej tablicy jest wartością typu `int`, więc końcowy indeks dolny `3` jest mnożony przez rozmiar typu `int`, zanim zostanie dodany do `prop[2][1]`. Wskaźnik wynikowy adresuje czwarty element 6-elementowej tablicy.  
  
4.  Operator pośredni jest stosowany do wartości wskaźnika. Wynik jest elementem typu `int` pod tym adresem.  
  
 W dwóch następnych przykładach pokazano przypadki, w których nie jest stosowany operator pośredni.  
  
```  
ip = prop[2][1];  
  
ipp = prop[2];  
```  
  
 W pierwszej z tych instrukcji wyrażenie `prop[2][1]` jest prawidłowym odwołaniem do trójwymiarowej tablicy `prop`; odwołuje się ono do 6-elementowej tablicy (zadeklarowanej powyżej). Ponieważ wartość wskaźnika adresuje tablicę, operator pośredni nie jest stosowany.  
  
 Podobnie, wynik wyrażenia `prop[2]` w drugiej instrukcji `ipp = prop[2];` jest wartością wskaźnika adresującą tablicę dwuwymiarową.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator indeksu dolnego:](../cpp/subscript-operator.md)