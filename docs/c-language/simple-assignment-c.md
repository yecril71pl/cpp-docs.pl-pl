---
title: Proste Assignment (C) | Dokumentacja firmy Microsoft
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
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cf9c5675affb6dcaea78e0cabf2a4427ad03938
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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