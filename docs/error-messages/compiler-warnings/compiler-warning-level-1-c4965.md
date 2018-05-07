---
title: Kompilatora (poziom 1) ostrzeżenie C4965 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4965
dev_langs:
- C++
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b731393471097fd3ba02979a48cd59513eaea9fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4965"></a>Kompilator C4965 ostrzegawcze (poziom 1)
niejawne rzutowanie liczby całkowitej 0; Użyj nullptr lub jawnego rzutowania  
  
 Visual C++ funkcjami niejawna konwersja boxing typów wartości. Instrukcji, które spowodowały przypisanie wartości null, przy użyciu rozszerzeń zarządzanych dla języka C++ teraz staje się przypisanie do opakowanego int.  
  
 Aby uzyskać więcej informacji, zobacz [Boxing](../../windows/boxing-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4965.  
  
```  
// C4965.cpp  
// compile with: /clr /W1  
int main() {  
   System::Object ^o = 0;   // C4965  
  
   // the previous line is the same as the following line  
   // using Managed Extensions for C++  
   // System::Object *o = __box(0);  
  
   // OK  
   System::Object ^o2 = nullptr;  
   System::Object ^o3 = safe_cast<System::Object^>(0);  
}  
```