---
title: C2460 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4220be654f93ecd79d196efc14657ca7346411f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197783"
---
# <a name="compiler-error-c2460"></a>C2460 błąd kompilatora
"identifier1": używa "identifier2", który jest definiowany  
  
 Klasy lub struktury (`identifier2`) jest zadeklarowana jako element członkowski (`identifier1`). Cykliczne definicje klas i struktur nie są dozwolone.  
  
 Poniższy przykład generuje C2460:  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 Zamiast tego użyj odwołanie wskaźnika w klasie.  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```