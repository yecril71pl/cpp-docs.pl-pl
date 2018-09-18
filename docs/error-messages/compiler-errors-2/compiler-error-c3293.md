---
title: Błąd kompilatora C3293 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8d45f342528b1ee6297ee6c11a01a0eceb710595
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050336"
---
# <a name="compiler-error-c3293"></a>Błąd kompilatora C3293

"Metoda dostępu": umożliwia dostęp do domyślnej właściwości (indeksator) dla klasy "type" "default"

Właściwość indeksowana uzyskano niepoprawnie.  Zobacz [porady: użycie właściwości w języku C + +/ interfejsu wiersza polecenia](../../dotnet/how-to-use-properties-in-cpp-cli.md) Aby uzyskać więcej informacji.

**Visual Studio 2017 i nowszym**: W programie Visual Studio 2015 i starsze kompilatora w niektórych przypadkach misidentified domyślnej właściwości jako indeksatora domyślne. Było możliwe obejść ten problem za pomocą identyfikatora "domyślne" na dostęp do właściwości. Obejście się stało się problematyczne po domyślne została wprowadzona jako słowo kluczowe w C ++ 11. W związku z tym w programie Visual Studio 2017 zostały rozwiązane błędy, które wymagały obejście, a kompilator teraz zgłasza błąd, gdy umożliwia dostęp do domyślnej właściwości dla klasy "default".

## <a name="example"></a>Przykład

Poniższy przykład generuje C3293 w programie Visual Studio 2015 i starszych wersji.

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