---
title: "Błąd cxx0065 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0065
dev_langs: C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db01baa10191df50c1f319bf8320263657088d75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0065"></a>Błąd CXX0065 programu Expression Evaluator
Zmienna wymaga ramki stosu  
  
 Wyrażenie zawierał zmiennej, która istnieje w bieżącym zakresie, ale nie został jeszcze utworzony.  
  
 Ten błąd może wystąpić, gdy mają przeprowadził w prologu funkcji, ale nie została jeszcze — Konfiguracja ramki stosu funkcji lub mieć przeprowadził do kodu zakończenia dla funkcji.  
  
 Kod prologu poszczególnych kroków do momentu ramki stosu nie został skonfigurowany przed obliczenie wyrażenia.  
  
 Ten błąd jest taki sam jak CAN0065.