---
title: Operator obliczania sekwencyjnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ed58e141dd811d95fe43ed2d587a2de17b3d656
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388490"
---
# <a name="sequential-evaluation-operator"></a>Operator obliczania sekwencyjnego
Operator obliczania sekwencyjnego, nazywane również "operatora przecinka" oblicza dwóch argumentów sekwencyjnie od lewej do prawej.  
  
## <a name="syntax"></a>Składnia  
 *wyrażenie*:  
 *assignment-expression*  
  
 *wyrażenie***,***wyrażenia przypisania*   
  
 Lewy operand operator obliczania sekwencyjnego jest szacowana jako `void` wyrażenia. Wynik operacji ma taką samą wartość i typ jako argument operacji po prawej. Każdy argument może być dowolnego typu. Operator obliczania sekwencyjnego nie przeprowadza konwersjach typów między swoich argumentów, a nie przekazuje on wartością l-value. Po pierwszym argumentem, co oznacza, że wszystkie efekty uboczne z wersji ewaluacyjnej lewy operand zostały zakończone przed rozpoczęciem oceny prawy operand jest punktu sekwencji. Zobacz [punkty sekwencji](../c-language/c-sequence-points.md) Aby uzyskać więcej informacji.  
  
 Operator obliczania sekwencyjnego jest zwykle używane do analizowania wyrażenia w kontekstach, których jest dozwolone tylko jedno wyrażenie.  
  
 Jako separatorów w niektórych kontekstach należy używać przecinków. Jednak należy uważać, aby nie należy mylić użycie przecinka jako separatora z jako operatora; używa dwóch różnią się całkowicie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono operator obliczania sekwencyjnego:  
  
```  
for ( i = j = 1; i + j < 20; i += i, j-- );  
```  
  
 W tym przykładzie każdy argument operacji **dla** niezależnie Obliczanie wyrażenia trzeci w instrukcji. Lewy argument operacji `i += i` jest obliczane pierwszy; a następnie prawy operand `j--`, oceny.  
  
```  
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 W funkcji wywołanie `func_one`, trzech argumentów rozdzielonych przecinkami, są przekazywane: `x`, `y + 2`, i `z`. W funkcji wywołanie `func_two`, kompilator, aby zinterpretować przecinkiem jako operator obliczania sekwencyjnego wymusić nawiasów. Wywołanie tej funkcji przekazuje dwa argumenty do `func_two`. Pierwszy argument jest wynik operacji obliczania sekwencyjnego `(x--, y + 2)`, która zawiera wartości i typ wyrażenia `y + 2`; drugi argument jest `z`.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator przecinkowy: ,](../cpp/comma-operator.md)