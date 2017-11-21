---
title: "C3162 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3162
dev_langs: C++
helpviewer_keywords: C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8bfde260ef0efe58ed70469a80a8bf7316eefa46
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3162"></a>C3162 błąd kompilatora
'type': Typ referencyjny, który posiada destruktor nie może służyć jako typ elementu członkowskiego danych statycznych "członek"  
  
 Środowisko uruchomieniowe języka wspólnego nie wiedzieć, kiedy uruchomić destruktor zdefiniowany przez użytkownika, gdy klasa zawiera także statycznej funkcji członkowskiej.  
  
 Destruktor nigdy nie zostanie uruchomiony, chyba że jawnie usunąć obiektu.  
  
 Aby uzyskać więcej informacji, zobacz,  
  
-   [/ CLR (kompilacja języka wspólnego środowiska wykonawczego)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Typowe problemy przy migracji 64-bitowe języka Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3162.  
  
```  
// C3162.cpp  
// compile with: /clr /c  
ref struct A {  
   ~A() { System::Console::WriteLine("in destructor"); }  
   static A i;   // C3162  
   static A^ a = gcnew A;   // OK  
};  
  
int main() {  
   A ^ a = gcnew A;  
   delete a;  
}  
```