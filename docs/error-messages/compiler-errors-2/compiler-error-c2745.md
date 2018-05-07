---
title: C2745 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2745
dev_langs:
- C++
helpviewer_keywords:
- C2745
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11f371629c3811821d9c7dce56cc44137534058c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2745"></a>C2745 błąd kompilatora
"token": ten token nie można przekonwertować na identyfikator  
  
 Identyfikatory musi składać się z dozwolonych znaków.  
  
 Poniższy przykład generuje C2745:  
  
```  
// C2745.cpp  
// compile with: /clr  
int main() {  
   int __identifier([));   // C2745  
}  
```