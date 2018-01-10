---
title: "Kompilatora (poziom 1) ostrzeżenie C4129 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4129
dev_langs: C++
helpviewer_keywords: C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6405c7c156f34b49ab892304ee51a6b996ac2595
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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