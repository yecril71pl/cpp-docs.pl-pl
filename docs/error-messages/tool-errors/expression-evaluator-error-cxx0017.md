---
title: "Błąd cxx0017 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e769e9886168c9f19ad110c48d848a9b84ab8aac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0017"></a>Błąd CXX0017 programu Expression Evaluator
Nie odnaleziono symbolu  
  
 Nie można odnaleźć określonego w wyrażeniu symbolu.  
  
 Jedną z możliwych przyczyn tego błędu jest niezgodność wielkości liter w nazwie symbolu. Ponieważ C i C++ jest rozróżniana wielkość liter języków, należy podać nazwę symbolu w dokładnej zdefiniowane w źródle.  
  
 Ten błąd może wystąpić przy próbie rzutowanie typu zmienną, aby obejrzeć zmiennej podczas debugowania. `typedef` Deklaruje nazwę typu, ale nie definiuje nowego typu. Typecast nastąpiła w debugerze wymaga nazwy zdefiniowanego typu.  
  
 Ten błąd jest taki sam jak CAN0017.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Sprawdź, czy symbol jest już zadeklarowany w momencie, w którym jest używany program.  
  
2.  Użyj nazwy typu rzeczywistego można rzutować zmiennych w debugerze, zamiast `typedef`-zdefiniowaną nazwę.