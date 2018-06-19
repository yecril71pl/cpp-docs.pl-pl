---
title: Kompilatora (poziom 4) ostrzeżenie C4289 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4289
dev_langs:
- C++
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f7f09bd85d3740d43b6e4b6a80ed562f8cc2261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292610"
---
# <a name="compiler-warning-level-4-c4289"></a>Kompilator C4289 ostrzegawcze (poziom 4)
użyte rozszerzenie niestandardowe: 'var' : zmienna sterowania pętlą zadeklarowana w pętli for jest używana poza zakresem pętli for  
  
 Podczas kompilowania za pomocą [/Ze](../../build/reference/za-ze-disable-language-extensions.md) i **/Zc:forScope-**, Zmienna zadeklarowana w [dla](../../cpp/for-statement-cpp.md) pętli użyto po **dla**-zakresu pętli.  
  
 Zobacz [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) informacji o sposobie określania standardowe zachowanie w **dla** pętli z **/Ze**.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4289:  
  
```  
// C4289.cpp  
// compile with: /W4 /Zc:forScope-  
#pragma warning(default:4289)  
int main() {  
   for (int i = 0 ; ; )   // C4289  
      break;  
   i++;  
}  
```