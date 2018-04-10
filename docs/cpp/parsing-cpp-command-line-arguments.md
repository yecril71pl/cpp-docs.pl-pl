---
title: Analizowanie argumentów wiersza polecenia języka C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58db951b2c9459eb9511e0a354e1daec4b29b53d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="parsing-c-command-line-arguments"></a>Analizowanie argumentów wiersza polecenia języka C++
**Dotyczące firmy Microsoft**  
  
 Kod uruchomienia Microsoft C/C++ stosowane są następujące reguły przy interpretowaniu argumenty podane w wierszu polecenia systemu operacyjnego:  
  
-   Argumenty są rozdzielone biały znak, który jest spację lub tabulator.  
  
-   Znak daszek (^) nie został rozpoznany jako znak ucieczki lub ogranicznika. Znak jest obsługiwany w całkowicie przez analizator składni wiersza polecenia w systemie operacyjnym przed przesłaniem do `argv` tablicy w programie.  
  
-   Ciąg ujęta w znaki podwójnego cudzysłowu ("*ciąg*") jest interpretowana jako jeden argument, niezależnie od biały znak zawartych w. Ciąg w cudzysłowie, można ją osadzić w argumencie.  
  
-   Podwójny cudzysłów poprzedzony ukośnikiem (\\") jest interpretowany jako znak literału podwójnego cudzysłowu (").  
  
-   Używanie ukośników odwrotnych będą interpretowane jako literału, chyba że bezpośrednio poprzedzać podwójny cudzysłów.  
  
-   Jeśli parzystą liczbą ukośników odwrotnych następuje podwójny cudzysłów, jeden ukośnik odwrotny jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych i podwójny cudzysłów jest interpretowana jako ogranicznik ciągu.  
  
-   Jeśli nieparzystą liczbę ukośników odwrotnych następuje podwójny cudzysłów, jeden ukośnik odwrotny jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych i podwójny cudzysłów jest "wpisywany" z pozostałych ukośnik odwrotny, powodując literału podwójny cudzysłów (" ) należy umieścić w `argv`.  
  
## <a name="example"></a>Przykład  
 Następujący program przedstawiono argumenty jak wiersza polecenia są przekazywane:  
  
```  
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
  
 W poniższej tabeli przedstawiono przykładowe dane wejściowe i oczekiwane dane wyjściowe prezentacja reguły z powyższej listy.  
  
### <a name="results-of-parsing-command-lines"></a>Wyniki analizy wiersze poleceń  
  
|Dane wejściowe wiersza polecenia|ARGV — [1]|ARGV — [2]|ARGV — [3]|  
|-------------------------|---------------|---------------|---------------|  
|`"abc" d e`|`abc`|`d`|`e`|  
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [main: uruchamianie programu](../cpp/main-program-startup.md)