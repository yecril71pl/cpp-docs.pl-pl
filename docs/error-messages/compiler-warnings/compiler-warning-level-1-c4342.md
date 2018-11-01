---
title: Kompilator ostrzeżenie (poziom 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 439c4976f25688fd9220c3f58ceb933266b5f15c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447342"
---
# <a name="compiler-warning-level-1-c4342"></a>Kompilator ostrzeżenie (poziom 1) C4342

Zmiana zachowania: "*funkcja*" o nazwie, ale operator składowej został wywołany w poprzednich wersjach

W wersjach programu Visual C++ przed Visual Studio 2002, element członkowski został wywołany, ale to zachowanie została zmieniona i kompilator znajdzie teraz najlepsze dopasowanie w zakresie przestrzeni nazw.

Jeśli operator składowej został znaleziony, kompilator będzie wcześniej nie należy wziąć pod uwagę dowolnego obszaru nazw operatorów zakresu. W przypadku będący lepszym dopasowaniem w zakresie przestrzeni nazw, bieżącego kompilator poprawnie wywołuje, natomiast poprzedniego kompilatory nie należy wziąć pod uwagę jej.

To ostrzeżenie powinna być wyłączona po przeniesiesz kod do bieżącej wersji.  Kompilator może stanowić fałszywych alarmów, generuje to ostrzeżenie dla kodu w przypadku, gdy nastąpiła żadna zmiana zachowania.

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Poniższy przykład spowoduje wygenerowanie C4342:

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