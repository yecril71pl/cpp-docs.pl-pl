---
title: Użycie exit lub return
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
- return keyword [C++], using for program termination
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
ms.openlocfilehash: d60084c0d07d3eeb3f49a1fea53de04d150a701b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152725"
---
# <a name="using-exit-or-return"></a>Użycie exit lub return

Gdy wywołujesz **wyjść** lub wykonania **zwracają** instrukcji z `main`, statyczne obiekty są niszczone w odwrotnej kolejności ich inicjowania. Poniższy kod przedstawia sposób działania takich inicjowanie i oczyszczanie.

## <a name="example"></a>Przykład

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

W powyższym przykładzie obiektów statycznych `sd1` i `sd2` są tworzone i inicjowane przed wejściem do `main`. Po ten program kończy się za pomocą **zwracają** instrukcji, pierwsza `sd2` jest niszczony, a następnie `sd1`. Destruktor dla `ShowData` klasy zamyka pliki skojarzone z tych obiektów statycznych.

Innym sposobem na napisać ten kod jest do deklarowania `ShowData` obiektów o zakresie bloku, umożliwiając im niszczone, gdy wykraczają poza zakres:

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Zobacz także

[Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)