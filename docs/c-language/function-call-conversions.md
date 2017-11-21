---
title: "Konwersje wywołania funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f45a7b3b4aecfd25d1973e1e95ec787e958025e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="function-call-conversions"></a>Konwersje wywołania funkcji
Typ konwersji w argumentów w wywołaniu funkcji zależy od obecności prototypu funkcji (deklaracja przekazująca dalej) z typami argumentów zadeklarowany dla funkcji o nazwie.  
  
 Jeśli prototyp funkcji jest dostępny i zawiera typy argumentów zadeklarowane, kompilator wykonuje sprawdzanie typu (zobacz [funkcje](../c-language/functions-c.md)).  
  
 Jeśli występuje bez prototypu funkcji tylko popularne konwersje arytmetyczne są wykonywane na argumentów w wywołaniu funkcji. Konwersje te są wykonywane niezależnie na każdy argument w wywołaniu. Oznacza to, że **float** wartość jest konwertowana na **podwójne**; `char` lub **krótki** wartość jest konwertowana na `int`; i `unsigned char` lub **niepodpisane krótko** jest konwertowana na `unsigned int`.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje typów](../c-language/type-conversions-c.md)