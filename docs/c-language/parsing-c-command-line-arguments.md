---
title: Analizowanie argumentów wiersza polecenia C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53b61bae046e73c4e49bbcaeb095b7bf230e95dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388604"
---
# <a name="parsing-c-command-line-arguments"></a>Analizowanie argumentów wiersza polecenia języka C
**Microsoft Specific**  
  
 Kod uruchomienia Microsoft C stosowane są następujące reguły przy interpretowaniu argumenty podane w wierszu polecenia systemu operacyjnego:  
  
-   Argumenty są rozdzielone biały znak, który jest spację lub tabulator.  
  
-   Ciąg ujęta w znaki podwójnego cudzysłowu jest interpretowana jako jeden argument, niezależnie od biały znak zawartych w. Ciąg w cudzysłowie, można ją osadzić w argumencie. Należy pamiętać, że karetkę (**^**) nie został rozpoznany jako znak ucieczki lub ogranicznika.  
  
-   Podwójny cudzysłów poprzedzony ukośnikiem,  **\\"**, jest interpretowany jako literału podwójny cudzysłów (**"**).  
  
-   Używanie ukośników odwrotnych będą interpretowane jako literału, chyba że bezpośrednio poprzedzać podwójny cudzysłów.  
  
-   Jeśli parzystą liczbą ukośników odwrotnych następuje podwójny cudzysłów, a następnie co ukośnik odwrotny (**\\**) znajduje się w `argv` tablicy dla każdej pary ukośników odwrotnych (**\\ \\**) i podwójnego cudzysłowu (**"**) jest interpretowana jako ogranicznik ciągu.  
  
-   Jeśli nieparzystą liczbę ukośników odwrotnych następuje podwójny cudzysłów, a następnie co ukośnik odwrotny (**\\**) znajduje się w `argv` tablicy dla każdej pary ukośników odwrotnych (**\\ \\**) i podwójnego cudzysłowu jest interpretowana jako — sekwencja specjalna przez pozostałe ukośnik odwrotny, powodując literału podwójny cudzysłów (**"**) należy umieścić w `argv`.  
  
 Ta lista przedstawia reguły powyżej wyświetlając wynik interpretowany przekazany do `argv` kilka przykładów argumentów wiersza polecenia. Dane wyjściowe wymienione w ciągu sekundy trzecie, a czwarta kolumn jest Argumentów. Program C, znajdujący się na liście.  
  
|Dane wejściowe wiersza polecenia|ARGV — [1]|ARGV — [2]|ARGV — [3]|  
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
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)