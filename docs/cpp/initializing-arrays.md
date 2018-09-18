---
title: Inicjowanie tablic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- initializing arrays [C++]
- arrays [C++], initializing
ms.assetid: 41efe5f0-15b5-4f49-9196-c4902f8fc705
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94f13ca235091c730f81eefb5c36f388bf3dee38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103298"
---
# <a name="initializing-arrays"></a>Inicjowanie tablic

Jeśli klasa ma Konstruktor, tablice tej klasy są inicjowane przez konstruktora. W przypadku mniej elementów niż elementów w tablicy na liście inicjatora, domyślny konstruktor jest używany dla pozostałych elementów. Jeśli nie zdefiniowano domyślnego konstruktora dla klasy, na liście inicjatora muszą być kompletne — oznacza to, musi istnieć jeden inicjator dla każdego elementu w tablicy.

Należy wziąć pod uwagę `Point` klasę, która definiuje dwa konstruktory:

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

Pierwszy element `aPoint` jest tworzony przy użyciu konstruktora `Point( int, int )`; pozostałe dwa elementy są konstruowane przy użyciu domyślnego konstruktora.

Tablice statyczny element członkowski (czy **const** lub nie) mogą być inicjowane w ich definicji (poza deklaracją klasy). Na przykład:

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```