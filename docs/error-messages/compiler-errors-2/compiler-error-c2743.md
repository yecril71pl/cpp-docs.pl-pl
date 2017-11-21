---
title: "C2743 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2743
dev_langs: C++
helpviewer_keywords: C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f45e7617bbf162c23994897c42aab44abeacea88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2743"></a>C2743 błąd kompilatora
'type': nie można przechwycić natywnego typu destruktorem __clrcall lub konstruktorem kopiującym  
  
 Moduł skompilowany z **/CLR** próbował catch wyjątku typu macierzystego i których używa typu destruktorem lub konstruktorem kopiującym `__clrcall` konwencji wywoływania.  
  
 Gdy skompilowano z opcją **/CLR**, obsługa wyjątków oczekuje funkcji Członkowskich w typie natywnym jako [__cdecl](../../cpp/cdecl.md) i nie [__clrcall](../../cpp/clrcall.md). Typy natywne przy użyciu funkcji Członkowskich `__clrcall` konwencji wywoływania nie można przechwycić w module skompilowanym z **/CLR**.  
  
 Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2743.  
  
```  
// C2743.cpp  
// compile with: /clr  
public struct S {  
   __clrcall ~S() {}  
};  
  
public struct T {  
   ~T() {}  
};  
  
int main() {  
   try {}  
   catch(S) {}   // C2743  
   // try the following line instead  
   // catch(T) {}  
  
   try {}  
   catch(S*) {}   // OK  
}  
```