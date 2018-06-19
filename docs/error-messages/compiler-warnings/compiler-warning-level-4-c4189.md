---
title: Kompilatora (poziom 4) ostrzeżenie C4189 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4189
dev_langs:
- C++
helpviewer_keywords:
- C4189
ms.assetid: 7ad9242c-228e-4054-8244-5e914b618ef3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f15efc139f9f09b86f77569349065719bace677
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293172"
---
# <a name="compiler-warning-level-4-c4189"></a>Kompilator C4189 ostrzegawcze (poziom 4)
'Identyfikator': lokalna zmienna jest zainicjowana, ale nie odwołuje się do  
  
 Zmienna jest zadeklarowana i zainicjowana, ale nie używane.  
  
 Poniższy przykład generuje C4189:  
  
```  
// C4189.cpp  
// compile with: /W4  
int main() {  
   int a = 1;   // C4189, remove declaration to resolve  
}  
```