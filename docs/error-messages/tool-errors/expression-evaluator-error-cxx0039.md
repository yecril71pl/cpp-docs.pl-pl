---
title: Błąd cxx0039 programu Expression Evaluator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8681d73d2889433516b205a47c500193bbeabdb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0039"></a>Błąd CXX0039 programu Expression Evaluator
symbol jest niejednoznaczny  
  
 Ewaluator wyrażeń C nie można ustalić które wystąpienie symbolu do użycia w wyrażeniu. Symbol występuje więcej niż raz w drzewa dziedziczenia.  
  
 Należy użyć operator rozpoznawania zakresów (`::`) Aby jawnie określić wystąpienie do użycia w wyrażeniu.  
  
 Ten błąd jest taki sam jak CAN0039.