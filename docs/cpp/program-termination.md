---
title: C++zakończenie programu
ms.date: 12/10/2019
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
ms.openlocfilehash: a0e86cacd951327d39296a183be5ee4fbc36fd15
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301343"
---
# <a name="c-program-termination"></a>C++zakończenie programu

W C++programie można wyjść z programu w następujący sposób:

- Wywołaj funkcję [Exit](exit-function.md) .
- Wywołaj funkcję [Abort](abort-function.md) .
- Wykonaj instrukcję [Return](return-statement-cpp.md) z `main`.

## <a name="exit-function"></a>exit, funkcja

Funkcja [Exit](../c-runtime-library/reference/exit-exit-exit.md) zadeklarowana w \<STDLIB. h >, kończy C++ program. Wartość podana jako argument `exit` jest zwracana do systemu operacyjnego jako kod powrotny programu lub kod zakończenia. Zgodnie z Konwencją, zwracany kod zero oznacza, że program został ukończony pomyślnie. Możesz użyć stałych EXIT_FAILURE i EXIT_SUCCESS, również zdefiniowanych w \<STDLIB. h >, aby wskazać powodzenie lub niepowodzenie programu.

Wygenerowanie instrukcji **Return** z funkcji `main` jest równoważne wywołaniu funkcji `exit` z wartością zwracaną jako argument.

## <a name="abort-function"></a>abort — Funkcja

Funkcja [Abort](../c-runtime-library/reference/abort.md) , zadeklarowana również w standardowym pliku dołączanym \<STDLIB. h >, kończy C++ program. Różnica między `exit` i `abort` polega na tym, że `exit` C++ pozwala na przetwarzanie zakończenia w czasie wykonywania (globalne destruktory obiektów zostaną wywołane), natomiast `abort` natychmiast kończy działanie programu. Funkcja `abort` pomija proces normalnego niszczenia dla zainicjowanych globalnych obiektów statycznych. Pomija również specjalne przetwarzanie, które zostało określone przy użyciu funkcji [atexit —](../c-runtime-library/reference/atexit.md) .

## <a name="atexit-function"></a>atexit — Funkcja

Użyj funkcji [atexit —](../c-runtime-library/reference/atexit.md) , aby określić akcje wykonywane przed zakończeniem działania programu. Nie zainicjowano globalnych obiektów statycznych przed wywołaniem do **atexit —** przed wykonaniem funkcji przetwarzania wyjścia.

## <a name="return-statement-in-main"></a>Return — Instrukcja w głównym

Wygenerowanie instrukcji [Return](return-statement-cpp.md) z `main` jest funkcjonalnie równoważne z wywołaniem funkcji `exit`. Rozważmy następujący przykład:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Instrukcje `exit` i **Return** w powyższym przykładzie są funkcjonalnie identyczne. Jednak C++ wymaga, aby funkcje, które mają zwracane typy inne niż **void** zwracają wartość. Instrukcja **Return** umożliwia zwrócenie wartości z `main`.

## <a name="destruction-of-static-objects"></a>Niszczenie obiektów statycznych

Po wywołaniu `exit` lub wykonaniu instrukcji **Return** z `main`, obiekty statyczne są niszczone w odwrotnej kolejności inicjalizacji (po wywołaniu do `atexit` jeśli taka istnieje). Poniższy przykład pokazuje, jak działa takie inicjowanie i oczyszczanie.

### <a name="example"></a>Przykład

W poniższym przykładzie obiekty statyczne `sd1` i `sd2` są tworzone i inicjowane przed wpisem do `main`. Po zakończeniu działania tego programu przy użyciu instrukcji **Return** pierwszy `sd2` jest niszczony, a następnie `sd1`. Destruktor dla klasy `ShowData` zamyka pliki skojarzone z tymi obiektami statycznymi.

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

[main: uruchamianie programu](main-program-startup.md)