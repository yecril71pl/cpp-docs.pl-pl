---
title: C2528 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2528
dev_langs:
- C++
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 347330600e9b912d50522532f0c64e789e385520
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2528"></a>C2528 błąd kompilatora
"Nazwa": wskaźnik do odwołania jest niedozwolony  
  
 Nie można zadeklarować wskaźnik do odwołania. Przed zadeklarowaniem wskaźnik do niego, należy usunąć odwołania do zmiennej.  
  
 Poniższy przykład generuje C2528:  
  
```  
// C2528.cpp  
int i;  
int &ir = i;  
int & (*irptr) = ir;    // C2528  
```