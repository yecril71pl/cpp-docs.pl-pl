---
title: Błąd cxx0033 programu Expression Evaluator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 720b1aec6c9be16879119bc0e8148a301507577a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299503"
---
# <a name="expression-evaluator-error-cxx0033"></a>Błąd CXX0033 programu Expression Evaluator
błąd informacje o typie OMF  
  
 Plik wykonywalny nie ma formatu modułu prawidłowego obiektu (OMF) do debugowania.  
  
 Ten błąd jest taki sam jak CAN0033.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Plik wykonywalny nie została utworzona z konsolidator wydane w tej wersji programu Visual C++. Połącz ponownie przy użyciu bieżącej wersji programu LINK.exe kod obiektu.  
  
2.  Plik .exe może być uszkodzony. Ponowne skompilowanie i ponowne łączenie programu.