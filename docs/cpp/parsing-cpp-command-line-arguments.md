---
title: Analizowanie argumentów wiersza polecenia języka C++
ms.date: 11/04/2016
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
ms.openlocfilehash: 53873fa9340253ab5e8459eb442385641246f930
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396122"
---
# <a name="parsing-c-command-line-arguments"></a>Analizowanie argumentów wiersza polecenia języka C++

**Microsoft Specific**

Kod startowy w Microsoft C/C++ używa następujących reguł interpretując argumenty podane w wierszu polecenia systemu operacyjnego:

- Argumenty są rozdzielone biały znak, który jest spacja lub tabulator.

- Znak daszka (^) nie została rozpoznana jako znak ucieczki lub ogranicznik. Znak odbywa się całkowicie przez parser wiersza polecenia w systemie operacyjnym przed przesłaniem do `argv` tablicy w programie.

- W ciąg ujęty w znaki podwójnego cudzysłowu ("*ciąg*") jest interpretowany jako jeden argument, niezależnie od tego, biały znak zawarty w. Ciąg w cudzysłowach można osadzać w argumencie.

- Podwójny cudzysłów poprzedzone znakiem ukośnika odwrotnego (\\") jest interpretowany jako znak literału podwójny cudzysłów (").

- Ukośników odwrotnych jest interpretowany dosłownie, chyba że bezpośrednio poprzedzać znak podwójnego cudzysłowu.

- Jeśli parzysta liczba ukośników odwrotnych następuje podwójny cudzysłów, jednej kreski ułamkowej odwróconej jest umieszczana w `argv` tablicy dla każdej pary ukośników odwrotnych i podwójnego cudzysłowu jest interpretowany jako ogranicznik ciągu.

- Jeśli nieparzysta liczba ukośników odwrotnych następuje podwójny cudzysłów, jednej kreski ułamkowej odwróconej jest umieszczana w `argv` tablicy dla każdej pary ukośników odwrotnych i podwójnego cudzysłowu jest "poprzedzone znakiem zmiany znaczenia" przez pozostałe ukośnik odwrotny powoduje literał podwójny cudzysłów (" ) mają być umieszczone w `argv`.

## <a name="example"></a>Przykład

Następujący program pokazuje jak wiersza polecenia argumenty są przekazywane:

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

W poniższej tabeli przedstawiono przykładowe dane wejściowe i oczekiwanych danych wyjściowych, demonstrując reguły na powyższej liście.

### <a name="results-of-parsing-command-lines"></a>Wyniki analizy wiersze poleceń

|Dane wejściowe wiersza polecenia|ARGV [1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)