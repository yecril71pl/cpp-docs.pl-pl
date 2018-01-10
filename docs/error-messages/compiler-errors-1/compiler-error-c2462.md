---
title: "C2462 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2462
dev_langs: C++
helpviewer_keywords: C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af4b7e303a67ed1eae3d217964818d1b4cd05b96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2462"></a>C2462 błąd kompilatora
'Identyfikator': nie można zdefiniować typu w "nowe wyrażenie"  
  
 Nie można zdefiniować typu w polu operand `new` operatora. Definicja typu należy umieścić w osobnych instrukcji.  
  
 Poniższy przykład generuje C2462:  
  
```  
// C2462.cpp  
int main() {  
   new struct S { int i; };   // C2462  
}  
```