---
title: "Błąd cxx0033 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 49f2b6221d385587fa5e62af51d37eb7d3b78872
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0033"></a>Błąd CXX0033 programu Expression Evaluator
błąd informacje o typie OMF  
  
 Plik wykonywalny nie ma formatu modułu prawidłowego obiektu (OMF) do debugowania.  
  
 Ten błąd jest taki sam jak CAN0033.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Plik wykonywalny nie została utworzona z konsolidator wydane w tej wersji programu Visual C++. Połącz ponownie przy użyciu bieżącej wersji programu LINK.exe kod obiektu.  
  
2.  Plik .exe może być uszkodzony. Ponowne skompilowanie i ponowne łączenie programu.