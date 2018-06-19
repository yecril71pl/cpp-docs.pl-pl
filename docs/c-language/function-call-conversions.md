---
title: Konwersje wywołania funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71b0fc4468ea98f04c87c8389021f2e12d9cae69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384499"
---
# <a name="function-call-conversions"></a>Konwersje wywołania funkcji
Typ konwersji w argumentów w wywołaniu funkcji zależy od obecności prototypu funkcji (deklaracja przekazująca dalej) z typami argumentów zadeklarowany dla funkcji o nazwie.  
  
 Jeśli prototyp funkcji jest dostępny i zawiera typy argumentów zadeklarowane, kompilator wykonuje sprawdzanie typu (zobacz [funkcje](../c-language/functions-c.md)).  
  
 Jeśli występuje bez prototypu funkcji tylko popularne konwersje arytmetyczne są wykonywane na argumentów w wywołaniu funkcji. Konwersje te są wykonywane niezależnie na każdy argument w wywołaniu. Oznacza to, że **float** wartość jest konwertowana na **podwójne**; `char` lub **krótki** wartość jest konwertowana na `int`; i `unsigned char` lub **niepodpisane krótko** jest konwertowana na `unsigned int`.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje typów](../c-language/type-conversions-c.md)