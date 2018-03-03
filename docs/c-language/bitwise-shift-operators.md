---
title: "Operatory przesunięcia bitowego | Dokumentacja firmy Microsoft"
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
- operators [C++], bitwise
- shift operators, bitwise
- bitwise-shift operators
- operators [C++], shift
ms.assetid: d0485785-5c72-47e1-a7c0-0adde03ade23
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e13e65e42febf2256e11bcb428e98805cdd6550f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bitwise-shift-operators"></a>Operatory przesunięcia bitowego
Operatory przesunięcia przesunięcia w lewo ich pierwszy argument operacji (`<<`) lub w prawo (`>>`) przez liczbę pozycji określa drugi argument operacji.  
  
## <a name="syntax"></a>Składnia  
 *wyrażenie SHIFT*:  
 *wyrażenie dodatku*  
  
 *wyrażenie SHIFT*`<<`*wyrażenie dodatku shift-expression*`>>`*wyrażenie dodatku*   
  
 Oba argumenty muszą być wartości całkowite. Popularne konwersje arytmetyczne; wykonywania tych operatorów Typ wyniku jest typem lewego operandu po konwersji.  
  
 Do zmiany leftward vacated odpowiednich bitów są ustawione na 0. Dla zmian rightward vacated bitów po lewej stronie zostaną wypełnione oparte na typ pierwszego argumentu po konwersji. Jeśli typ jest `unsigned`, są ustawione na 0. W przeciwnym razie są wypełnione z kopiami bitu znaku. Dla operatory przesunięcia w lewo bez przepełnienia, instrukcja  
  
```  
expr1 << expr2   
```  
  
 jest odpowiednikiem mnożenia przez 2<sup>Wyr2</sup>. Operatory przesunięcia w prawo, aby uzyskać  
  
```  
expr1 >> expr2   
```  
  
 jest odpowiednikiem dzielenie przez 2<sup>Wyr2</sup> Jeśli `expr1` jest niepodpisany lub ma wartość nieujemną.  
  
 Zdefiniowano wynik operacji shift, jeśli drugi operand jest ujemny lub prawy operand jest większa niż lub równa szerokość w bitach awansowana Lewy argument operacji.  
  
 Ponieważ konwersja przez zmianę operatory nie zapewniają przepełnienia lub niedopełnienie warunków, informacje mogą zostać utracone, jeśli wynik operacji przesunięcia nie może być reprezentowany w typie pierwszy argument operacji po konwersji.  
  
```  
unsigned int x, y, z;  
  
x = 0x00AA;  
y = 0x5500;  
  
z = ( x << 8 ) + ( y >> 8 );  
```  
  
 W tym przykładzie `x` zostanie przesunięty w ośmiu pozycji w lewo i `y` jest przesuniętych prawo osiem pozycji. Przesuniętych wartości zostaną dodane, dając 0xAA55 i przypisane do `z`.  
  
 Przesunięcie w prawo wartości ujemnej daje połowa oryginalnej wartości, zaokrąglona w dół. Na przykład -253 (binarne 11111111 00000011) przesunięte daje prawo o jeden bit -127 (binarne 11111111 10000001). Dodatnią 253 zmian prawym przyciskiem myszy, aby wygenerować +126.  
  
 Przesunięcia w prawo zachować bitu znaku. Kiedy całkowita przewiduje się po prawej, najbardziej znaczącego bitu pozostaje ustawione. Gdy całkowitą bez znaku przewiduje się po prawej, najbardziej znaczącego bitu jest wyczyszczone.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory przesunięcia w lewo i w prawo (>> i <<)](../cpp/left-shift-and-right-shift-operators-input-and-output.md)