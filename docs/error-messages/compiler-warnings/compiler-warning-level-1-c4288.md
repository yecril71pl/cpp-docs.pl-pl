---
title: Kompilatora (poziom 1) ostrzeżenie C4288 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2c51bdc201b364d76f1692db8ee14973c90923f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276633"
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