---
title: C3293 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3293
dev_langs:
- C++
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b195a91825b0f20445b29e330f67810329584db7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257731"
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