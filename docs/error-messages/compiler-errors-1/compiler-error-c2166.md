---
title: "C2166 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2166
dev_langs: C++
helpviewer_keywords: C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bb177b3ffa86e543d55de5bb5e31c395f01a5e54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2166"></a>C2166 błąd kompilatora
wartość l Określa obiekt const  
  
 Kod próbuje zmodyfikować elementu zadeklarowane `const`.  
  
 Poniższy przykład generuje C2166:  
  
```  
// C2166.cpp  
int f();  
int main() {  
   ( (const int&) 1 ) = 5;   // C2166  
}  
```