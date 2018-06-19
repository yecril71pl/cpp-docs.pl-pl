---
title: C2462 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2462
dev_langs:
- C++
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4ce82ed15bdb8844f69abc260446c1af2fd4a0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198563"
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