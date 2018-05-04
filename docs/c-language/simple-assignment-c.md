---
title: Proste Assignment (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31914118283c9d0c5c502e3426ba12e86d7c7680
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="simple-assignment-c"></a>Przypisanie proste (C)
Operator przypisania prostego przypisuje jej prawy operand operand po lewej stronie. Wartość prawy operand jest konwertowana na typ wyrażenia przypisania i zastępuje do wartości przechowywanej w obiekcie wskazywany przez argument po lewej stronie. Zastosuj reguły konwersji dla przypisania (zobacz [konwersje przypisań](../c-language/assignment-conversions.md)).  
  
```  
double x;  
int y;  
  
x = y;  
```  
  
 W tym przykładzie wartość `y` jest konwertowana na typ **podwójne** i przypisane do `x`.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory przypisania w języku C](../c-language/c-assignment-operators.md)