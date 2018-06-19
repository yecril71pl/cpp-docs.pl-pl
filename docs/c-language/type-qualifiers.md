---
title: Kwalifikatory typu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74f51dfe3b0b45fb08bc30f9b0d158275112bcf9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389988"
---
# <a name="type-qualifiers"></a>Kwalifikatory typów
Kwalifikatory typu podać jedną z dwóch właściwości do identyfikatora. **Const** kwalifikator typu deklaruje obiektu jako niemodyfikowalnymi. `volatile` Kwalifikator typu deklaruje element, którego wartość legalnie może zostać zmieniona przez coś poza kontrolą programu, w którym zostanie wyświetlona, takich jak współbieżnie wykonywanego wątku.  
  
 Kwalifikatory, wpisz dwa **const** i `volatile`, może wystąpić tylko raz w deklaracji. Kwalifikatory typu może być pokazywana z dowolnym specyfikatora typu; jednak nie może występować po przecinku pierwszy w wielu deklaracji elementu. Na przykład następujące deklaracje są:  
  
```  
typedef volatile int VI;  
const int ci;  
```  
  
 Deklaracje te są niedozwolone:  
  
```  
typedef int *i, volatile *vi;  
float f, const cf;     
```  
  
 Kwalifikatory typu mają zastosowanie tylko wtedy, gdy dostęp do identyfikatorów jako l wartości w wyrażeniach. Zobacz [wartości L i r wyrażenia](../c-language/l-value-and-r-value-expressions.md) informacji o wartości l i wyrażenia.  
  
## <a name="syntax"></a>Składnia  
 *Kwalifikator typu*:  
 **constvolatile**  
  
 Poniżej przedstawiono prawne **const** i `volatile` deklaracje:  
  
```  
int const *p_ci;       /* Pointer to constant int */  
int const (*p_ci);     /* Pointer to constant int */  
int *const cp_i;       /* Constant pointer to int */  
int (*const cp_i);     /* Constant pointer to int */  
int volatile vint;     /* Volatile integer        */  
```  
  
 Jeśli specyfikacja typu tablicowego zawiera kwalifikatory typu, elementu jest kwalifikowana, nie typem tablicy. Jeśli specyfikacja typu funkcji zawiera kwalifikatory, zachowanie jest niezdefiniowany. Ani `volatile` ani **const** ma wpływ na zakres wartości lub arytmetyczne właściwości obiektu.  
  
 Ta lista zawiera opis używania **const** i `volatile`.  
  
-   **Const** — słowo kluczowe może służyć do modyfikowania dowolnego typu podstawowych lub zbiorczej lub wskaźnik do obiektu dowolnego typu lub `typedef`. Jeśli element jest zadeklarowany za pomocą tylko **const** kwalifikator typu jego typ przyjmuje się **const int**. A **const** można zainicjować zmiennej, lub można umieścić w regionie tylko do odczytu z magazynu. **Const** — słowo kluczowe jest przydatne w przypadku deklarowanie wskaźniki do **const** , ponieważ wymaga to funkcja, nie należy zmieniać wskaźnika w dowolny sposób.  
  
-   Kompilator przy założeniu, że, w dowolnym momencie w programie `volatile` zmiennej są dostępne dla nieznanych procesu, który używa lub modyfikuje jej wartość. W związku z tym niezależnie od optymalizacji określony w poleceniu wiersz kodu dla poszczególnych przydziałów lub odniesienie do `volatile` zmienna musi zostać wygenerowany, nawet jeśli wygląda na to, aby nie mają żadnego skutku.  
  
     Jeśli `volatile` jest używana samodzielnie, `int` zakłada, że. `volatile` Specyfikatora typu może służyć do zapewnienia niezawodny dostęp do lokalizacji pamięci specjalnych. Użyj `volatile` z obiektów danych, które mogą być dostępne lub zmieniony przez obsługę sygnału, jednocześnie wykonywania programów lub specjalnego sprzętu, takich jak mapowanych na pamięć we/wy rejestry sterowania. Można zadeklarować zmiennej jako `volatile` dla swojego okresu istnienia, lub można rzutować jednego odwołania do `volatile`.  
  
-   Element może być jednocześnie **const** i `volatile`, w tym przypadku nie można zmodyfikować legalnie przez własny program elementu, ale mogły zostać zmodyfikowane przez niektóre proces asynchroniczny.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i typy](../c-language/declarations-and-types.md)