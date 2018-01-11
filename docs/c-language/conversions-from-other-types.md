---
title: "Konwersje z innych typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8dbf2d3d269f5df3a028a5c416f8adca015be6dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="conversions-from-other-types"></a>Konwersje z innych typów
Ponieważ `enum` wartość jest `int` wartości zgodnie z definicją konwersje do i z `enum` wartości są takie same jak te dotyczące `int` typu. Dla kompilatora Microsoft C całkowitą jest taka sama jak **długi**.  
  
 **Dotyczące firmy Microsoft**  
  
 Nie konwersji między typami struktura lub związek są dozwolone.  
  
 Każda wartość może zostać przekonwertowana na typ `void`, ale wynik takich konwersji może być używana wyłącznie w kontekście, gdzie wartość wyrażenia jest usuwane, takie jak instrukcja wyrażenia.  
  
 `void` Typ nie ma wartości, zgodnie z definicją. W związku z tym nie można przekonwertować żadnego innego typu, i innych typów nie można przekonwertować na `void` przez przypisanie. Jednak jawnie rzutowania wartości na typ `void`, zgodnie z opisem w [konwersje rzutowania typów](../c-language/type-cast-conversions.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje przypisań](../c-language/assignment-conversions.md)