---
title: Błąd cxx0017 programu Expression Evaluator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7540dc701ffa6e0acb3d2661e1196e5f4552d2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300751"
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