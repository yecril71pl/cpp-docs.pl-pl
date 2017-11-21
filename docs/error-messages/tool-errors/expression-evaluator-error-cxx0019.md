---
title: "Błąd cxx0019 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0019
dev_langs: C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 67fbd43280ad6ffcecdf0532819cd80a0d44b479
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0019"></a>Błąd CXX0019 programu Expression Evaluator
Zły typ rzutowania  
  
 Ewaluator wyrażeń C nie można wykonać typu rzutowania zgodnie z zapisem.  
  
 Ten błąd jest taki sam jak CAN0019.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Określony typ jest nieznany.  
  
2.  Znaleziono zbyt wiele poziomów typów wskaźnika. Na przykład typ rzutowania  
  
    ```  
    (char **)h_message  
    ```  
  
     Nie można obliczyć przez Ewaluator wyrażeń C.