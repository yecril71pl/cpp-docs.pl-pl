---
title: "Kompilatora (poziom 1) ostrzeżenie C4965 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4965
dev_langs: C++
helpviewer_keywords: C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cde1b35dc183065461d1a2e59c77089256774ab4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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