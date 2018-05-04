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
ms.openlocfilehash: eacd447d27f3dd8bd2d2d88e6d975cdb29a82026
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="initializing-arrays"></a>Inicjowanie tablic
Jeśli klasa zawiera konstruktora, tablic tej klasy są inicjowane przez konstruktora. W przypadku mniejszej liczby elementów na liście inicjatora niż elementów w tablicy, domyślny konstruktor jest używany dla pozostałe elementy. Jeśli żaden konstruktor domyślny jest zdefiniowany w klasie, lista inicjatora musi być ukończone — to znaczy musi być jednego inicjatora dla każdego elementu w tablicy.  
  
 Należy wziąć pod uwagę `Point` klasy, który definiuje dwa konstruktory:  
  
```  
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
  
 Statyczny element członkowski tablic (czy **const** lub nie) mogą być inicjowane w ich definicje (poza deklaracją klasy). Na przykład:  
  
```  
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
  
