---
title: Kompilatora (poziom 1) ostrzeżenie C4342 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4342
dev_langs:
- C++
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1df710912338aa540dd2a29f859fc4533445b09b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281290"
---
# <a name="compiler-warning-level-1-c4342"></a>Kompilator C4342 ostrzegawcze (poziom 1)
Zmiana zachowania: "*funkcja*" o nazwie, ale operator elementu członkowskiego został wywołany w poprzednich wersjach  
  
 W wersjach programu Visual C++ przed Visual Studio 2002, Wywołano element członkowski, ale to zachowanie została zmieniona i kompilator teraz znajduje najlepsze dopasowanie w zakresie przestrzeni nazw.  
  
 Jeśli znaleziono operator elementu członkowskiego, kompilator będzie wcześniej nie należy wziąć pod uwagę przestrzeni nazw operatorów zakresu. Jeśli istnieje lepsze dopasowanie w zakresie przestrzeni nazw, bieżącego kompilatora prawidłowo wywołuje, natomiast poprzedniej kompilatory nie uważają, że.  
  
 Po pomyślnie portu kodu do wersji bieżącej, należy wyłączyć to ostrzeżenie.  Kompilator może dać wyniki fałszywie dodatnie, generowanie tego ostrzeżenia dla kodu w przypadku, gdy nie ma żadnej zmiany zachowania.  
  
 To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
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