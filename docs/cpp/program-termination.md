---
title: Zakończenie programu C++
description: 'Opisuje sposoby programowania w :::no-loc(exit)::: języku C++.'
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- :::no-loc(exit):::ing applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- ':::no-loc(exit):::'
- ':::no-loc(abort):::'
- ':::no-loc(return):::'
- ':::no-loc(main):::'
- ':::no-loc(atexit):::'
- ':::no-loc(void):::'
ms.openlocfilehash: 216aef5dbe8d110f9d75d43b5009b89fc5bfda51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227182"
---
# <a name="c-program-termination"></a>Zakończenie programu C++

W języku C++ można :::no-loc(exit)::: w następujący sposób:

- Wywołaj [:::no-loc(exit):::](:::no-loc(exit):::-function.md) funkcję.
- Wywołaj [:::no-loc(abort):::](:::no-loc(abort):::-function.md) funkcję.
- Wykonaj [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) instrukcję z `:::no-loc(main):::` .

## <a name="no-locexit-function"></a>Funkcja :::no-loc(exit):::

[:::no-loc(exit):::](../c-runtime-library/reference/:::no-loc(exit):::-:::no-loc(exit):::-:::no-loc(exit):::.md)Funkcja zadeklarowana w \<stdlib.h> , kończy program języka C++. Wartość dostarczona jako argument do `:::no-loc(exit):::` :::no-loc(return)::: systemu operacyjnego jako :::no-loc(return)::: kod lub :::no-loc(exit)::: kod programu. Zgodnie z Konwencją, :::no-loc(return)::: kod zero oznacza, że program został ukończony pomyślnie. Możesz użyć stałych EXIT_FAILURE i EXIT_SUCCESS, zdefiniowanych również w \<stdlib.h> , aby wskazać powodzenie lub niepowodzenie programu.

Wygenerowanie **`:::no-loc(return):::`** instrukcji z `:::no-loc(main):::` funkcji jest równoznaczne z wywołaniem `:::no-loc(exit):::` funkcji z :::no-loc(return)::: wartością jako argumentem.

## <a name="no-locabort-function"></a>Funkcja :::no-loc(abort):::

[:::no-loc(abort):::](../c-runtime-library/reference/:::no-loc(abort):::.md)Funkcja, zadeklarowana również w standardowym pliku dołączania \<stdlib.h> , kończy program języka C++. Różnica między `:::no-loc(exit):::` i `:::no-loc(abort):::` polega na tym, że `:::no-loc(exit):::` zezwala na przetwarzanie zakończenia w czasie wykonywania C++ (globalne destruktory obiektów zostaną wywołane), podczas gdy `:::no-loc(abort):::` natychmiast kończy działanie programu. `:::no-loc(abort):::`Funkcja pomija proces normalnego niszczenia dla zainicjowanych globalnych obiektów statycznych. Pomija również specjalne przetwarzanie, które zostało określone za pomocą [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) funkcji.

## <a name="no-locatexit-function"></a>Funkcja :::no-loc(atexit):::

Użyj [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) funkcji, aby określić akcje wykonywane przed zakończeniem działania programu. Nie zainicjowano globalnych obiektów statycznych przed wywołaniem w celu **:::no-loc(atexit):::** zniszczenia przed wykonaniem :::no-loc(exit)::: funkcji przetwarzania.

## <a name="no-locreturn-statement-in-no-locmain"></a>:::no-loc(return):::Instrukcja w:::no-loc(main):::

Wygenerowanie [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) instrukcji from `:::no-loc(main):::` jest funkcjonalnie równoważnej wywołania `:::no-loc(exit):::` funkcji. Rozpatrzmy następujący przykład:

```cpp
// :::no-loc(return):::_statement.cpp
#include <stdlib.h>
int :::no-loc(main):::()
{
    :::no-loc(exit):::( 3 );
    :::no-loc(return)::: 3;
}
```

`:::no-loc(exit):::`Instrukcje i **`:::no-loc(return):::`** w powyższym przykładzie są funkcjonalnie identyczne. Jednak C++ wymaga, aby funkcje, które mają :::no-loc(return)::: typy inne niż **`:::no-loc(void):::`** :::no-loc(return)::: wartość. **`:::no-loc(return):::`** Instrukcja pozwala na :::no-loc(return)::: wartość z `:::no-loc(main):::` .

## <a name="destruction-of-static-objects"></a>Niszczenie obiektów statycznych

Po wywołaniu `:::no-loc(exit):::` lub wykonaniu **`:::no-loc(return):::`** instrukcji z programu `:::no-loc(main):::` obiekty statyczne są niszczone w odwrotnej kolejności inicjalizacji (po wywołaniu do `:::no-loc(atexit):::` Jeśli taka istnieje). Poniższy przykład pokazuje, jak działa takie inicjowanie i oczyszczanie.

### <a name="example"></a>Przykład

W poniższym przykładzie obiekty statyczne `sd1` i `sd2` są tworzone i inicjowane przed wpisem do `:::no-loc(main):::` . Po zakończeniu działania tego programu przy użyciu **`:::no-loc(return):::`** instrukcji, najpierw `sd2` zostaje zniszczony, a następnie `sd1` . Destruktor dla `ShowData` klasy zamyka pliki skojarzone z tymi obiektami statycznymi.

```cpp
// using_:::no-loc(exit):::_or_:::no-loc(return):::1.cpp
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
   :::no-loc(void)::: Disp( char *szData ) {
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

int :::no-loc(main):::() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

Innym sposobem zapisu tego kodu jest zadeklarowanie `ShowData` obiektów z zakresem bloku, umożliwiając ich zniszczenie, gdy wykraczają poza zakres:

```cpp
int :::no-loc(main):::() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Zobacz także

[:::no-loc(main):::argumenty funkcji i wiersza polecenia](:::no-loc(main):::-function-command-line-args.md)
