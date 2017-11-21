---
title: "Błąd cxx0024 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0024
dev_langs: C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 386e04d8aa1655896b77f8492d7929778edd6109
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0024"></a>Błąd CXX0024 programu Expression Evaluator
Operacja musi l wartość  
  
 Wyrażenie, które nie zostało oszacowane jako l wartość została określona dla danej operacji, która wymaga wartości l.  
  
 L wartość (tzw. ponieważ wydaje się po lewej stronie instrukcji przypisania) jest wyrażenie, które odwołuje się do lokalizacji w pamięci.  
  
 Na przykład `buffer[count]` jest prawidłową wartością l, ponieważ wskazuje lokalizację pamięci. Porównanie logicznej `zed != 0` nie jest prawidłową wartością l, ponieważ jej wartość PRAWDA lub FAŁSZ, nie daje w wyniku adres pamięci.  
  
 Ten błąd jest taki sam jak CAN0024.