---
title: "Kompilatora (poziom 1) ostrzeżenie C4005 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4005
dev_langs: C++
helpviewer_keywords: C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf0c5777cecf89bb0723b30c87dc4c856de0a016
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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