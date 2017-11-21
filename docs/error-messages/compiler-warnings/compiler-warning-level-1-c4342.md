---
title: "Kompilatora (poziom 1) ostrzeżenie C4342 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4342
dev_langs: C++
helpviewer_keywords: C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: faea23fcfa1e323ec28d81aa5abeb27f3c87cef1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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