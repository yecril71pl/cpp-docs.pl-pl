---
title: Analizowanie argumentów wiersza polecenia języka C
ms.date: 11/04/2016
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
ms.openlocfilehash: 8161d724dbd21297bb3beef2cf9406ddd2484ff1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522437"
---
# <a name="parsing-c-command-line-arguments"></a>Analizowanie argumentów wiersza polecenia języka C

**Microsoft Specific**

Kod uruchamiający Microsoft C używa następujących reguł interpretując argumenty podane w wierszu polecenia systemu operacyjnego:

- Argumenty są rozdzielone biały znak, który jest spacja lub tabulator.

- W ciąg ujęty w znaki podwójnego cudzysłowu jest interpretowana jako jeden argument, niezależnie od tego, biały znak zawarty w. Ciąg w cudzysłowach można osadzać w argumencie. Należy pamiętać, że karetki (**^**) nie jest rozpoznawany jako znak ucieczki lub ogranicznik.

- Podwójny cudzysłów poprzedzony znakiem ukośnika odwrotnego  **\\"**, jest interpretowany jako literał podwójny cudzysłów (**"**).

- Ukośników odwrotnych jest interpretowany dosłownie, chyba że bezpośrednio poprzedzać znak podwójnego cudzysłowu.

- Jeśli parzysta liczba ukośników odwrotnych następuje podwójny cudzysłów, a następnie jednej kreski ułamkowej odwróconej (**\\**) jest umieszczany w `argv` tablicy dla każdej pary ukośniki odwrotne (**\\ \\**) i podwójnego cudzysłowu (**"**) jest interpretowany jako ogranicznik ciągu.

- Jeśli nieparzysta liczba ukośników odwrotnych następuje podwójny cudzysłów, a następnie jednej kreski ułamkowej odwróconej (**\\**) jest umieszczany w `argv` tablicy dla każdej pary ukośniki odwrotne (**\\ \\**) i podwójnego cudzysłowu jest interpretowany jako sekwencja unikowa przez pozostałe ukośnik odwrotny powoduje literał podwójny cudzysłów (**"**) mają być umieszczone w `argv`.

Ta lista ilustruje reguły powyżej, pokazując interpretowanych wynik przekazany do `argv` kilka przykładów dotyczących argumenty wiersza polecenia. Dane wyjściowe są wyświetlane w drugim, trzeci, a czwarty kolumn jest argumenty. Program C, który następuje po liście.

|Dane wejściowe wiersza polecenia|ARGV [1]|ARGV [2]|ARGV [3]|
|-------------------------|---------------|---------------|---------------|
|`"a b c" d e`|`a b c`|`d`|`e`|
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```
// Parsing_C_Commandline_args.c
// ARGS.C illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
//

#include <stdio.h>

int main( int argc, // Number of strings in array argv
char *argv[],      // Array of command-line argument strings
char **envp )      // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf_s( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf_s( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf_s( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf_s( "  %s\n", *(envp++) );

    return;
}
```

## <a name="comments"></a>Komentarze

Przykład danych wyjściowych z tego programu jest:

```
Command-line arguments:
  argv[0]   C:\MSC\TEST.EXE

Environment variables:
  COMSPEC=C:\NT\SYSTEM32\CMD.EXE

  PATH=c:\nt;c:\binb;c:\binr;c:\nt\system32;c:\word;c:\help;c:\msc;c:\;
  PROMPT=[$p]
  TEMP=c:\tmp
  TMP=c:\tmp
  EDITORS=c:\binr
  WINDIR=c:\nt
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)