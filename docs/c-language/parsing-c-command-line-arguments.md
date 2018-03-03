---
title: "Analizowanie argumentów wiersza polecenia C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e3db47ca48e52babc03923dfba7b1dcb8173cc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="parsing-c-command-line-arguments"></a>Analizowanie argumentów wiersza polecenia języka C
**Dotyczące firmy Microsoft**  
  
 Kod uruchomienia Microsoft C stosowane są następujące reguły przy interpretowaniu argumenty podane w wierszu polecenia systemu operacyjnego:  
  
-   Argumenty są rozdzielone biały znak, który jest spację lub tabulator.  
  
-   Ciąg ujęta w znaki podwójnego cudzysłowu jest interpretowana jako jeden argument, niezależnie od biały znak zawartych w. Ciąg w cudzysłowie, można ją osadzić w argumencie. Należy pamiętać, że karetkę (**^**) nie został rozpoznany jako znak ucieczki lub ogranicznika.  
  
-   Podwójny cudzysłów poprzedzony ukośnikiem,  **\\"**, jest interpretowany jako literału podwójny cudzysłów (**"**).  
  
-   Używanie ukośników odwrotnych będą interpretowane jako literału, chyba że bezpośrednio poprzedzać podwójny cudzysłów.  
  
-   Jeśli parzystą liczbą ukośników odwrotnych następuje podwójny cudzysłów, a następnie co ukośnik odwrotny (**\\**) znajduje się w `argv` tablicy dla każdej pary ukośników odwrotnych ( **\\ \\** ) i podwójnego cudzysłowu (**"**) jest interpretowana jako ogranicznik ciągu.  
  
-   Jeśli nieparzystą liczbę ukośników odwrotnych następuje podwójny cudzysłów, a następnie co ukośnik odwrotny (**\\**) znajduje się w `argv` tablicy dla każdej pary ukośników odwrotnych ( **\\ \\** ) i podwójnego cudzysłowu jest interpretowana jako — sekwencja specjalna przez pozostałe ukośnik odwrotny, powodując literału podwójny cudzysłów (**"**) należy umieścić w `argv`.  
  
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