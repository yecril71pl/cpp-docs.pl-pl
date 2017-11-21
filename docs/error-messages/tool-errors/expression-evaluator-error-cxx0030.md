---
title: "Błąd cxx0030 programu Expression Evaluator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0030
dev_langs: C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffa1dd85419943ede6a13d61cb82924c32b5e80a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0030"></a>Błąd CXX0030 programu Expression Evaluator
Wyrażenie nie evaluatable  
  
 Ewaluator wyrażeń debugera nie można uzyskać wartości dla wyrażenia, jak podano. Jeden prawdopodobną przyczyną jest to, że wyrażenie odwołuje się do pamięci, która znajduje się poza przestrzeni adresowej programu (dereferencji pustego wskaźnika jest jednym z przykładów). System Windows nie zezwala na dostęp do pamięci, która znajduje się poza przestrzeni adresowej programu.  
  
 Można zmodyfikować za pomocą nawiasów kontrolować kolejność oceniania w wyrażeniu.  
  
 Ten błąd jest taki sam jak CAN0030.