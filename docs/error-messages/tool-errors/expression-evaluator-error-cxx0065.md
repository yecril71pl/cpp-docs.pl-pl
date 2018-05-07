---
title: Błąd cxx0065 programu Expression Evaluator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78c25c9c6bde27219f10e4047dc7a6ab416f55d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0065"></a>Błąd CXX0065 programu Expression Evaluator
Zmienna wymaga ramki stosu  
  
 Wyrażenie zawierał zmiennej, która istnieje w bieżącym zakresie, ale nie został jeszcze utworzony.  
  
 Ten błąd może wystąpić, gdy mają przeprowadził w prologu funkcji, ale nie została jeszcze — Konfiguracja ramki stosu funkcji lub mieć przeprowadził do kodu zakończenia dla funkcji.  
  
 Kod prologu poszczególnych kroków do momentu ramki stosu nie został skonfigurowany przed obliczenie wyrażenia.  
  
 Ten błąd jest taki sam jak CAN0065.