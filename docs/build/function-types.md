---
title: Typy funkcji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d43daef2095fb63bd79644c940627754e00e199b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="function-types"></a>Typy funkcji
Istnieją dwa typy funkcji. Funkcja, która wymaga ramki stosu jest wywoływana funkcja ramki. Funkcja, która nie wymaga ramki stosu jest wywoływana funkcja typu liść.  
  
 Funkcja ramki jest funkcja, która przydziela miejsce na stosie, wywołuje inne funkcje, zapisuje nieulotnej rejestrów lub korzysta z obsługi wyjątków. Wymagany jest również wpisu tabeli funkcji. Funkcja ramki wymaga prolog i epilog. Funkcja ramki można dynamicznie przydzielić miejsca na stosie i mogą stosować wskaźnika ramki. Funkcja ramki ma pełnego zestawu funkcji to wywołanie standardowe dyspozycji.  
  
 Jeśli funkcja ramki nie wywołuje innej funkcji, nie jest wymagane, aby były wyrównane stosu (mowa w [alokacji stosu](../build/stack-allocation.md)).  
  
 Funkcja liścia to taki, który nie wymaga wpisu tabeli funkcji. Nie można go wprowadzić zmian w nieulotnej rejestrów, w tym źródło, co oznacza, że nie wywołaniem dowolnej funkcji lub przydzielenie miejsca na stosie. Może on być pozostaw niewyrównany stosu podczas wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykorzystanie stosu](../build/stack-usage.md)
