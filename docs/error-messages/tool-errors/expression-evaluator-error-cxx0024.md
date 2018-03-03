---
title: "Błąd cxx0024 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c96bd943719afb0d974a5c4386742bea24396fd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0024"></a>Błąd CXX0024 programu Expression Evaluator
Operacja musi l wartość  
  
 Wyrażenie, które nie zostało oszacowane jako l wartość została określona dla danej operacji, która wymaga wartości l.  
  
 L wartość (tzw. ponieważ wydaje się po lewej stronie instrukcji przypisania) jest wyrażenie, które odwołuje się do lokalizacji w pamięci.  
  
 Na przykład `buffer[count]` jest prawidłową wartością l, ponieważ wskazuje lokalizację pamięci. Porównanie logicznej `zed != 0` nie jest prawidłową wartością l, ponieważ jej wartość PRAWDA lub FAŁSZ, nie daje w wyniku adres pamięci.  
  
 Ten błąd jest taki sam jak CAN0024.