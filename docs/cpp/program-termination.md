---
title: Zakończenie programu C++
description: Opisuje sposoby programowania w exit języku C++.
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
ms.openlocfilehash: fd0c7699ae032b5551f4fbc37eb3b7fa999a168f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352924"
---
# <a name="c-program-termination"></a>Zakończenie programu C++

W języku C++ można exit w następujący sposób:

- Wywołaj [exit](../c-runtime-library/reference/exit-exit-exit.md) funkcję.
- Wywołaj [abort](../c-runtime-library/reference/abort.md) funkcję.
- Wykonaj [return](return-statement-cpp.md) instrukcję z `main` .

## <a name="no-locexit-function"></a>Funkcja exit

[exit](../c-runtime-library/reference/exit-exit-exit.md)Funkcja zadeklarowana w \<stdlib.h> , kończy program języka C++. Wartość dostarczona jako argument do `exit` return systemu operacyjnego jako return kod lub exit kod programu. Zgodnie z Konwencją, return kod zero oznacza, że program został ukończony pomyślnie. Możesz użyć stałych EXIT_FAILURE i EXIT_SUCCESS, zdefiniowanych również w \<stdlib.h> , aby wskazać powodzenie lub niepowodzenie programu.

Wygenerowanie **`return`** instrukcji z `main` funkcji jest równoznaczne z wywołaniem `exit` funkcji z return wartością jako argumentem.

## <a name="no-locabort-function"></a>Funkcja abort

[abort](../c-runtime-library/reference/abort.md)Funkcja, zadeklarowana również w standardowym pliku dołączania \<stdlib.h> , kończy program języka C++. Różnica między `exit` i `abort` polega na tym, że `exit` zezwala na przetwarzanie zakończenia w czasie wykonywania C++ (globalne destruktory obiektów zostaną wywołane), podczas gdy `abort` natychmiast kończy działanie programu. `abort`Funkcja pomija proces normalnego niszczenia dla zainicjowanych globalnych obiektów statycznych. Pomija również specjalne przetwarzanie, które zostało określone za pomocą [atexit](../c-runtime-library/reference/atexit.md) funkcji.

## <a name="no-locatexit-function"></a>Funkcja atexit

Użyj [atexit](../c-runtime-library/reference/atexit.md) funkcji, aby określić akcje wykonywane przed zakończeniem działania programu. Nie zainicjowano globalnych obiektów statycznych przed wywołaniem w celu **atexit** zniszczenia przed wykonaniem exit funkcji przetwarzania.

## <a name="no-locreturn-statement-in-no-locmain"></a>return Instrukcja w main

Wygenerowanie [return](return-statement-cpp.md) instrukcji from `main` jest funkcjonalnie równoważnej wywołania `exit` funkcji. Rozpatrzmy następujący przykład:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

`exit`Instrukcje i **`return`** w powyższym przykładzie są funkcjonalnie identyczne. Jednak C++ wymaga, aby funkcje, które mają return typy inne niż **`void`** return wartość. **`return`** Instrukcja pozwala na return wartość z `main` .

## <a name="destruction-of-static-objects"></a>Niszczenie obiektów statycznych

Po wywołaniu `exit` lub wykonaniu **`return`** instrukcji z programu `main` obiekty statyczne są niszczone w odwrotnej kolejności inicjalizacji (po wywołaniu do `atexit` Jeśli taka istnieje). Poniższy przykład pokazuje, jak działa takie inicjowanie i oczyszczanie.

### <a name="example"></a>Przykład

W poniższym przykładzie obiekty statyczne `sd1` i `sd2` są tworzone i inicjowane przed wpisem do `main` . Po zakończeniu działania tego programu przy użyciu **`return`** instrukcji, najpierw `sd2` zostaje zniszczony, a następnie `sd1` . Destruktor dla `ShowData` klasy zamyka pliki skojarzone z tymi obiektami statycznymi.

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

Innym sposobem zapisu tego kodu jest zadeklarowanie `ShowData` obiektów z zakresem bloku, umożliwiając ich zniszczenie, gdy wykraczają poza zakres:

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Zobacz też

[main argumenty funkcji i wiersza polecenia](main-function-command-line-args.md)
