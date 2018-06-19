---
title: C3699 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3699
dev_langs:
- C++
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ddbf6ac43b2a3d987faa86fab6d9862068fc0fe0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265032"
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