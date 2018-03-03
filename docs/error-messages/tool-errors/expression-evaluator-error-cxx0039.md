---
title: "Błąd cxx0039 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6edef73f821030f8e8163c10b66efb64649e002f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0039"></a>Błąd CXX0039 programu Expression Evaluator
symbol jest niejednoznaczny  
  
 Ewaluator wyrażeń C nie można ustalić które wystąpienie symbolu do użycia w wyrażeniu. Symbol występuje więcej niż raz w drzewa dziedziczenia.  
  
 Należy użyć operator rozpoznawania zakresów (`::`) Aby jawnie określić wystąpienie do użycia w wyrażeniu.  
  
 Ten błąd jest taki sam jak CAN0039.