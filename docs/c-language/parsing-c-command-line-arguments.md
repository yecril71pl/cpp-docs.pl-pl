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
ms.openlocfilehash: ace6d1b8295d0901ef22f3c354b32ad17e296e87
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299094"
---
# <a name="parsing-c-command-line-arguments"></a>Analizowanie argumentów wiersza polecenia języka C

**Microsoft Specific**

Kod uruchamiania języka Microsoft C używa następujących reguł podczas interpretacji argumentów podanych w wierszu polecenia systemu operacyjnego:

- Argumenty są rozdzielane znakami odstępu, który jest spacją lub tabulatorem.

- Ciąg ujęty w znaki podwójnego cudzysłowu jest interpretowany jako pojedynczy argument, bez względu na biały znak zawarty w. Ciąg w cudzysłowie może być osadzony w argumencie. Należy zauważyć, że karetka ( **^** ) nie jest rozpoznawana jako znak ucieczki ani ogranicznik.

- Podwójny cudzysłów poprzedzony ukośnikiem odwrotnym, **\\"** , jest interpretowany jako literał podwójnego cudzysłowu ( **"** ).

- Ukośniki odwrotne są interpretowane dosłownie, chyba że od razu poprzedzają podwójny cudzysłów.

- Jeśli parzysta liczba kresek ułamkowych jest poprzedzona znakiem podwójnego cudzysłowu, to jeden ukośnik odwrotny ( **\\** ) jest umieszczany w tablicy `argv` dla każdej pary ukośników odwrotnych ( **\\\\** ) i podwójny cudzysłów ( **"** ) jest interpretowany jako ogranicznik ciągu.

- Jeśli po parzystej liczbie ukośników odwrotnych następuje znak podwójnego cudzysłowu, to jeden ukośnik odwrotny ( **\\** ) jest umieszczany w tablicy `argv` dla każdej pary ukośników odwrotnych ( **\\\\** ) i podwójny cudzysłów jest interpretowany jako sekwencja ucieczki przez resztę ukośnika odwrotnego ("), co powoduje umieszczenie literału podwójnego cudzysłowu ( **"** ) w `argv`.

Na tej liście przedstawiono reguły opisane powyżej, pokazując interpretowany wynik przekazane do `argv` dla kilku przykładów argumentów wiersza polecenia. Dane wyjściowe wymienione w drugiej, trzeciej i czwartej kolumnie pochodzą z ARGUMENTÓW. Program C, który znajduje się na liście.

|Wprowadzanie w wierszu polecenia|argv [1]|argv [2]|argv [3]|
|-------------------------|---------------|---------------|---------------|
|`"a b c" d e`|`a b c`|`d`|`e`|
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```c
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

Przykładem danych wyjściowych z tego programu jest:

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)
