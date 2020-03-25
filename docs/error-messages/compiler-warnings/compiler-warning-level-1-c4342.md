---
title: Ostrzeżenie kompilatora (poziom 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 8ac00d3d57f8cf7d6c85f3106dbe9b8c3cb9adf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162923"
---
# <a name="compiler-warning-level-1-c4342"></a>Ostrzeżenie kompilatora (poziom 1) C4342

zmiana zachowania: wywołano*funkcję "Function*", ale operator składowej został wywołany w poprzednich wersjach

W wersjach wizualizacji C++ przed visual Studio 2002, element członkowski został wywołany, ale to zachowanie zostało zmienione i kompilator znalazł teraz najlepsze dopasowanie w zakresie przestrzeni nazw.

Jeśli zostanie znaleziony operator elementu członkowskiego, kompilator nie uwzględni wcześniej operatorów zakresu przestrzeni nazw. W przypadku lepszego dopasowania w zakresie przestrzeni nazw, bieżący kompilator prawidłowo wywołuje go, podczas gdy poprzedni kompilator nie uważa go.

To ostrzeżenie powinno być wyłączone po pomyślnym przejściu kodu do bieżącej wersji.  Kompilator może dać fałszywe pozytywne wartości, generując to ostrzeżenie dla kodu, w którym nie ma żadnych zmian w zachowaniu.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy przykład generuje C4342:

```cpp
// C4342.cpp
// compile with: /EHsc /W1
#include <fstream>
#pragma warning(default: 4342)
using namespace std;
struct X : public ofstream {
   X();
};

X::X() {
   open( "ofs_bug_ev.txt." );
   if ( is_open() ) {
      *this << "Text" << "<-should be text" << endl;   // C4342
      *this << ' ' << "<-should be space symbol" << endl;   // C4342
   }
}

int main() {
   X b;
   b << "Text" << "<-should be text" << endl;
   b << ' ' << "<-should be space symbol" << endl;
}
```
