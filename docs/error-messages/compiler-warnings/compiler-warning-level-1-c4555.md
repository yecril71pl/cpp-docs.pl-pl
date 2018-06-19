---
title: Kompilatora (poziom 1) ostrzeżenie C4555 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4555
dev_langs:
- C++
helpviewer_keywords:
- C4555
ms.assetid: 50b286c1-f7bf-4292-b1fa-baaac9538611
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 019423685bb92ddb4b9d4bafc58bb4ba4eb2d708
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278912"
---
# <a name="compiler-warning-level-1-c4555"></a>Kompilator C4555 ostrzegawcze (poziom 1)
wyrażenie nie przynosi efektu; oczekiwane wyrażenie, który przynosi efekt  
  
 To ostrzeżenie informuje o tym, gdy wyrażenie nie ma wpływu.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Na przykład:  
  
```  
// C4555.cpp  
// compile with: /W1  
#pragma warning(default:4555)  
  
void func1()  
{  
   1;   // C4555  
}  
  
void func2()  
{  
   int x;  
   x;   // C4555  
}  
  
int main()  
{  
}  
```