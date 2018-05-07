---
title: Błąd cxx0030 programu Expression Evaluator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 669c585c637129c1fb6a480d91b31e5a1264fd22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0030"></a>Błąd CXX0030 programu Expression Evaluator
Wyrażenie nie evaluatable  
  
 Ewaluator wyrażeń debugera nie można uzyskać wartości dla wyrażenia, jak podano. Jeden prawdopodobną przyczyną jest to, że wyrażenie odwołuje się do pamięci, która znajduje się poza przestrzeni adresowej programu (dereferencji pustego wskaźnika jest jednym z przykładów). System Windows nie zezwala na dostęp do pamięci, która znajduje się poza przestrzeni adresowej programu.  
  
 Można zmodyfikować za pomocą nawiasów kontrolować kolejność oceniania w wyrażeniu.  
  
 Ten błąd jest taki sam jak CAN0030.