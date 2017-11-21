---
title: "C3289 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3289
dev_langs: C++
helpviewer_keywords: C3289
ms.assetid: 3c1c623b-7fcf-43ab-a89a-8722532a8d29
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 28e79ec1da42e2dab150a0b89cd8bc4d7ff87180
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3289"></a>C3289 błąd kompilatora
"właściwość": właściwość prosta nie może być indeksowany.  
  
 Właściwość została niepoprawnie zadeklarowany. Metody dostępu muszą być zdefiniowane dla właściwości indeksowanej. Zobacz [właściwości](../../windows/property-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3289.  
  
```  
// C3289.cpp  
// compile with: /clr  
public ref struct C {  
   // user-defined simple indexer  
   property int indexer1[int];   // C3289  
  
   // user-defined indexer  
   property int indexer2[int] {  
      int get(int i) { return 0; }  
      void set(int i, int j) {}  
   }  
};  
  
int main() {  
   C ^ MyC = gcnew C();  
   MyC->indexer2[0] = 1;  
}  
```