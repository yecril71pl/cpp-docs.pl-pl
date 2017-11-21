---
title: "C3699 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3699
dev_langs: C++
helpviewer_keywords: C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: caabe5d8d9e956081211ef23546f0d720ecdcbd6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3699"></a>C3699 błąd kompilatora
"operator": nie można użyć tego operatora pośredniego na typie 'type'  
  
 Podjęto próbę użycia operatora pośredniego, która nie jest dozwolona w `type`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3699.  
  
```  
// C3699.cpp  
// compile with: /clr /c  
using namespace System;  
int main() {  
   String * s;   // C3699  
   // try the following line instead  
   // String ^ s2;  
}  
```  
  
## <a name="example"></a>Przykład  
 Właściwość prosta nie może mieć typu referencyjnego. Zobacz [właściwości](../../windows/property-cpp-component-extensions.md) Aby uzyskać więcej informacji. Poniższy przykład generuje C3699.  
  
```  
// C3699_b.cpp  
// compile with: /clr /c  
ref struct C {  
   property System::String % x;   // C3699  
   property System::String ^ y;   // OK  
};  
```  
  
## <a name="example"></a>Przykład  
 Odpowiednik składni "wskaźnika do wskaźnika" jest dojścia do odwołaniem śledzącym. Poniższy przykład generuje C3699.  
  
```  
// C3699_c.cpp  
// compile with: /clr /c  
using namespace System;  
void Test(String ^^ i);   // C3699  
void Test2(String ^% i);  
```