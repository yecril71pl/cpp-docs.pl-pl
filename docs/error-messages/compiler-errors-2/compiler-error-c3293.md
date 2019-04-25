---
title: Błąd kompilatora C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 84d539722474d5f5dfffe1f6fe121bb7349ba131
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222590"
---
# <a name="compiler-error-c3293"></a>Błąd kompilatora C3293

"Metoda dostępu": umożliwia dostęp do domyślnej właściwości (indeksator) dla klasy "type" "default"

Właściwość indeksowana uzyskano niepoprawnie.  Zobacz [jak: Korzystanie z właściwości w C++sposób niezamierzony](../../dotnet/how-to-use-properties-in-cpp-cli.md) Aby uzyskać więcej informacji.

**Visual Studio 2017 i nowszym**: W programie Visual Studio 2015 lub starszego kompilatora w niektórych przypadkach misidentified domyślna właściwość jako indeksatora domyślne. Było możliwe obejść ten problem za pomocą identyfikatora "domyślne" na dostęp do właściwości. Obejście się stało się problematyczne po domyślne została wprowadzona jako słowo kluczowe w C ++ 11. W związku z tym w programie Visual Studio 2017 zostały rozwiązane błędy, które wymagały obejście, a kompilator teraz zgłasza błąd, gdy umożliwia dostęp do domyślnej właściwości dla klasy "default".

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