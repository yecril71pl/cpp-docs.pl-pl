---
title: "Kompilatora (poziom 1) ostrzeżenie C4288 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4288
dev_langs: C++
helpviewer_keywords: C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: abbc9ba0a41a4961c49cffca6c10ff9a4e4e1437
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4288"></a>Kompilator C4288 ostrzegawcze (poziom 1)
użyto niestandardowego rozszerzenia: "var": zmienna sterująca pętli zadeklarowana w pętli for użyta poza zakresem pętli; powoduje on konflikt z deklaracją w zewnętrznym zakresie  
  
 Podczas kompilowania za pomocą [/Ze](../../build/reference/za-ze-disable-language-extensions.md) i **/Zc:forscope-**, Zmienna zadeklarowana w **dla** pętli użyto po [dla](../../cpp/for-statement-cpp.md)-zakresu pętli. Ta zmienna ma pozostać w zakresie umożliwia rozszerzenie firmy Microsoft dla języka C++ i C4288 przypomina o tym, czy pierwszej deklaracji zmiennej nie jest używany.  
  
 Zobacz [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) informacji o sposobie określania rozszerzenia Microsoft **dla** pętli /Ze.  
  
 Poniższy przykład generuje C4288:  
  
```  
// C4288.cpp  
// compile with: /W1 /c /Zc:forScope-  
int main() {  
   int i = 0;    // not used in this program  
   for (int i = 0 ; ; ) ;  
   i++;   // C4288 using for-loop declaration of i  
}  
```