---
title: Kompilatora (poziom 1) ostrzeżenie C4129 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc095a32e5cb0d5a0bf240282e11c3fa3382ffe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4129"></a>Kompilator C4129 ostrzegawcze (poziom 1)
"znak": nierozpoznany znak sekwencji ucieczki  
  
 `character` Po ukośnik odwrotny (\\) znaków lub ciągu stała nie został rozpoznany jako prawidłowy sekwencja. Kreska ułamkowa odwrócona jest ignorowana, a nie wydrukować. Drukowania znaku po ukośniku odwrotnym.  
  
 Aby wydrukować pojedynczy ukośnik odwrotny, określ podwójny ukośnik odwrotny (\\\\).  
  
 Standard C++ w sekcji 2.13.2 omówiono sekwencje specjalne.  
  
 Poniższy przykład generuje C4129:  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```