---
title: Kompilator C4700 ostrzegawcze (poziom 1 i 4) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4700
dev_langs: C++
helpviewer_keywords: C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f41e519a9dbcff3cc5ad4b718003e5964bfc3e85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Ostrzeżenie C4700 kompilatora (poziom 1 i 4)
niezainicjowanej zmiennej lokalnej "name" używane  
  
 Użyto zmiennej lokalnej *nazwa* bez pierwsze przypisanie wartości, która może spowodować nieoczekiwane wyniki.  
  
 Poniższy przykład generuje C4700:  
  
```  
// C4700.cpp  
// compile with: /W1  
int main() {  
   int i;  
   return i;   // C4700  
}  
```  
  
 W obszarze [/CLR: Safe](../../build/reference/clr-common-language-runtime-compilation.md) to ostrzeżenie poziom 4.  Poniższy przykład generuje C4700:  
  
```  
// C4700b.cpp  
// compile with: /W4 /clr:safe /c  
using namespace System;  
int main() {  
   Int32^ bi;  
   return *bi;   // C4700  
}  
```