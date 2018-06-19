---
title: Kompilatora (poziom 1) ostrzeżenie C4005 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4005
dev_langs:
- C++
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a06ea88dab6ac7e89f7d53351b54593fd7bd232
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275379"
---
# <a name="compiler-warning-level-1-c4005"></a>Kompilator C4005 ostrzegawcze (poziom 1)
"identyfikator": zmiana definicji makra  
  
 Identyfikator makro została zdefiniowana dwukrotnie. Kompilator używa druga definicja makra.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Definiowanie makr w wierszu polecenia, a w kodzie z `#define` dyrektywy.  
  
2.  Makra zaimportowane z plików dołączanych.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Usuń jedną z definicji.  
  
2.  Użyj [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) dyrektywy przed druga definicja.  
  
 Poniższy przykład generuje C4005:  
  
```  
// C4005.cpp  
// compile with: /W1 /EHsc  
#include <iostream>  
using namespace std;  
  
#define TEST "test1"  
#define TEST "test2"   // C4005 delete or rename to resolve the warning  
  
int main() {  
   cout << TEST << endl;  
}  
```