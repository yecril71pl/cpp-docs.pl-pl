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
ms.openlocfilehash: 1efeca1e597af8e7f96b2854fcbcfc49b000009a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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