---
title: "C3293 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3293
dev_langs: C++
helpviewer_keywords: C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ccf6bd08b1ca540fcdf46d18631e0ab11c7fe4f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3293"></a>C3293 błąd kompilatora
"Metoda dostępu": "default" umożliwia dostęp do domyślnej właściwości (indeksator) dla klasy 'type'  
  
 Właściwość indeksowana uzyskano niepoprawnie.  Zobacz [porady: Użyj właściwości w języku C + +/ CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md) Aby uzyskać więcej informacji.  

 **Visual Studio 2017 i nowsze**: W programie Visual Studio 2015 i starsze wersje kompilatora w niektórych przypadkach misidentified właściwości domyślnej jako indeksatora domyślne. Było możliwe obejść ten problem za pomocą identyfikatora "domyślne" do dostępu do właściwości. Obejście się stało się problemy po domyślne wprowadzono słowo kluczowe języka C ++ 11. W związku z tym w programie Visual Studio 2017 usterki, które wymagane obejście zostały usunięte, a kompilator teraz zgłasza błąd, gdy umożliwia dostęp do właściwości domyślnej dla klasy "domyślny".
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3293 w Visual Studio 2015 lub starszym.  
  
```  
// C3293.cpp  
// compile with: /clr /c  
using namespace System;  
ref class IndexerClass {  
public:  
   // default indexer  
   property int default[int] {  
      int get(int index) { return 0; }  
      void set(int index, int value) {}  
   }  
};  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier
  
   String ^s = "Hello";  
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier  
   Console::WriteLine(wc2);  
}  
```