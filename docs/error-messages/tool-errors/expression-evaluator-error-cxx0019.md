---
title: Błąd cxx0019 programu Expression Evaluator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52e1679374e105ab06ce245ba68cfe92706689e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302493"
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