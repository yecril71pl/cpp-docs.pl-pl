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
ms.workload: cplusplus
ms.openlocfilehash: a10a7573df5986ed20475b34208a1e0f301d9bb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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