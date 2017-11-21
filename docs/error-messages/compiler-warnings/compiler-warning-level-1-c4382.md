---
title: "Kompilatora (poziom 1) ostrzeżenie C4382 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4382
dev_langs: C++
helpviewer_keywords: C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 29c6636a2465f57b2e57be43cf00056265d46f34
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4382"></a>Kompilator C4382 ostrzegawcze (poziom 1)
wyrzucanie 'type': typ z destruktorem __clrcall lub konstruktorem kopiującym można tylko przechwycić w/CLR: pure modułu  
  
 **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015.  
  
 Podczas kompilacji za pomocą **/CLR** (nie **/CLR: pure**), obsługa wyjątków oczekuje funkcji Członkowskich w typie natywnym za [__cdecl](../../cpp/cdecl.md) i nie [__clrcall](../../cpp/clrcall.md). Typy natywne przy użyciu funkcji Członkowskich `__clrcall` konwencji wywoływania nie można przechwycić w module skompilowanym z **/CLR**.  
  
 Jeśli wyjątek zostanie przechwycony w module skompilowanym z **/CLR: pure**, możesz zignorować to ostrzeżenie.  
  
 Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4382.  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```