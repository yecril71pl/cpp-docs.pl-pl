---
title: Wpisz Conversions (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e06da627d18fa643cb64fda870c986264c573641
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="type-conversions-c"></a>Konwersje typu (C)
Konwersje typów są zależne od określonego operatora i typu argumentu lub operatorów. Konwersje typów są wykonywane w następujących przypadkach:  
  
-   Wartości typu jeden jest przypisany do zmiennej innego typu lub operator konwertuje typ jej argument operacji lub argumentów operacji przed wykonaniem operacji  
  
-   Gdy wartość jednego typu jawnie jest rzutowane na inny typ  
  
-   Jeśli wartość jest przekazywany jako argument do funkcji lub typem zostanie zwrócona przez funkcję  
  
 Znak, krótki liczbą całkowitą lub pola bitowego całkowitą wszystkie podpisana lub nie, lub obiektu typu wyliczenia, można użyć w wyrażeniu wszędzie tam, gdzie można liczbą całkowitą. Jeśli `int` może reprezentować wartości oryginalny typ, a następnie przekonwertować wartości na `int`; w przeciwnym razie jest konwertowana na `unsigned int`. Ten proces jest nazywany "promocję typu całkowitego." Promocje typów całkowitych zachować wartość. Oznacza to, że wartość po promocji gwarantuje to taka sama, jak przed podwyższeniem. Zobacz [popularne konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia i przydziały](../c-language/expressions-and-assignments.md)