---
title: C++zakończenie programu
description: Opisuje sposoby exit programu w C++języku.
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: f83c9d5da5b0a1127603a97fd7946e9cca43a7a5
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123958"
---
# <a name="c-program-termination"></a>C++zakończenie programu

W C++programie można exit program w następujący sposób:

- Wywołaj funkcję [exit](exit-function.md) .
- Wywołaj funkcję [abort](abort-function.md) .
- Wykonaj instrukcję [return](return-statement-cpp.md) z `main`.

## <a name="opno-locexit-function"></a>Funkcja exit

Funkcja [exit](../c-runtime-library/reference/exit-exit-exit.md) zadeklarowana w \<STDLIB. h > kończy C++ program. Wartość podana jako argument `exit` jest zwracana do systemu operacyjnego jako kod return programu lub kod exit. Zgodnie z Konwencją, return kod zero oznacza, że program został ukończony pomyślnie. Możesz użyć stałych EXIT_FAILURE i EXIT_SUCCESS, również zdefiniowanych w \<STDLIB. h >, aby wskazać powodzenie lub niepowodzenie programu.

Wygenerowanie instrukcji **return** z funkcji `main` jest równoważne wywołaniu funkcji `exit` z wartością return jako argumentem.

## <a name="opno-locabort-function"></a>Funkcja abort

Funkcja [abort](../c-runtime-library/reference/abort.md) , zadeklarowana również w standardowym pliku dołączanym \<STDLIB. h >, kończy C++ program. Różnica między `exit` i `abort` polega na tym, że `exit` C++ pozwala na przetwarzanie zakończenia w czasie wykonywania (globalne destruktory obiektów zostaną wywołane), natomiast `abort` natychmiast kończy działanie programu. Funkcja `abort` pomija proces normalnego niszczenia dla zainicjowanych globalnych obiektów statycznych. Pomija również specjalne przetwarzanie, które zostało określone przy użyciu funkcji [atexit](../c-runtime-library/reference/atexit.md) .

## <a name="opno-locatexit-function"></a>Funkcja atexit

Użyj funkcji [atexit](../c-runtime-library/reference/atexit.md) , aby określić akcje wykonywane przed zakończeniem działania programu. Nie zainicjowano globalnych obiektów statycznych przed wywołaniem do **atexit** są niszczone przed wykonaniem funkcji przetwarzania exit.

## <a name="opno-locreturn-statement-in-opno-locmain"></a>Instrukcja return w main

Wygenerowanie instrukcji [return](return-statement-cpp.md) z `main` jest funkcjonalnie równoważne z wywołaniem funkcji `exit`. Rozważmy następujący przykład:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Instrukcje `exit` i **return** w powyższym przykładzie są funkcjonalnie identyczne. Jednak program C++ wymaga, aby funkcje, które mają return typy inne niż **void** return wartości. Instrukcja **return** pozwala return wartość z `main`.

## <a name="destruction-of-static-objects"></a>Niszczenie obiektów statycznych

Po wywołaniu `exit` lub wykonaniu instrukcji **return** z `main`obiekty statyczne są niszczone w odwrotnej kolejności inicjalizacji (po wywołaniu do `atexit`, jeśli istnieje). Poniższy przykład pokazuje, jak działa takie inicjowanie i oczyszczanie.

### <a name="example"></a>Przykład

W poniższym przykładzie obiekty statyczne `sd1` i `sd2` są tworzone i inicjowane przed wpisem do `main`. Po zakończeniu działania tego programu przy użyciu instrukcji **return** pierwsze `sd2` jest niszczone, a następnie `sd1`. Destruktor dla klasy `ShowData` zamyka pliki skojarzone z tymi obiektami statycznymi.

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

Innym sposobem zapisu tego kodu jest zadeklarowanie obiektów `ShowData` z zakresem bloku, umożliwiając ich zniszczenie, gdy wykraczają poza zakres:

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Zobacz także

[main funkcje i argumenty wiersza polecenia](main-function-command-line-args.md)
