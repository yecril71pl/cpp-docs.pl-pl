---
title: "C2675 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2675
dev_langs: C++
helpviewer_keywords: C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60bc86f87f6b1bd247d8f866b9d8bc7131f4898e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2675"></a>C2675 błąd kompilatora
Jednoargumentowy "operator": "type" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora  
  
 C2675 może również wystąpić, gdy przy użyciu operatora jednoargumentowego, a typ definiuje operator lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora. Użycie operatora, musi ona przeciążenia dla określonego typu lub zdefiniuj konwersji do typu, dla którego zdefiniowano operator.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2675.  
  
```  
// C2675.cpp  
struct C {   
   C(){}  
} c;  
  
struct D {   
   D(){}  
   void operator-(){}  
} d;  
  
int main() {  
   -c;   // C2675  
   -d;   // OK  
}  
```