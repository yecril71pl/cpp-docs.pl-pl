---
title: Błąd cxx0064 programu Expression Evaluator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7964eac628fa89695d1757cff8b7b329fd7fe713
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0064"></a>Błąd CXX0064 programu Expression Evaluator
Nie można ustawić punktu przerwania na powiązanej wirtualnej funkcji członkowskiej  
  
 Punkt przerwania został ustawiony wirtualną funkcją członkowską za pomocą wskaźnika do obiektu, takie jak:  
  
```  
pClass->vfunc( int );  
```  
  
 Punkt przerwania można ustawić dla wirtualnej funkcji wprowadzając klasy, takich jak:  
  
```  
Class::vfunc( int );  
```  
  
 Ten błąd jest taki sam jak CAN0064.