---
title: Definicje argumentu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4bb50f4471aed2af6de0ae20e2e3c85ab0cb5d9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="argument-definitions"></a>Definicje argumentu
Argumenty w prototypie  
  
```  
  
int main( int  
argc[ ,char*argv[] [,char*envp[] ] ] );intwmain(intargc[ ,wchar_t*argv[] [,wchar_t*envp[] ] ] );  
```  
  
 umożliwiają wygodne przetwarzanie argumentów z poziomu wiersza polecenia oraz, opcjonalnie, dostęp do zmiennych środowiskowych. Definicje argumentów są następujące:  
  
 `argc`  
 Liczba całkowita, która zawiera liczbę argumentów następujących w `argv`. Parametr `argc` jest zawsze większy lub równy 1.  
  
 `argv`  
 Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Według konwencji `argv` **[0]** polecenia, z którym program zostanie wywołany, `argv` **[1]** jest pierwszy argument wiersza polecenia i tak dalej, aż do `argv`  **[**`argc`**]**, która jest zawsze **NULL**. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) uzyskać informacji o pomijanie przetwarzania w wierszu polecenia.  
  
 Pierwszy argument wiersza polecenia jest zawsze `argv` **[1]** i jest ostatni z nich `argv` **[** `argc` - 1**]**.  
  
> [!NOTE]
>  Według konwencji `argv` **[0]** polecenia, z którym program jest wywoływany.  Jednak jest możliwe zduplikować procesu przy użyciu [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) i użycie pierwszy i drugi argument (`lpApplicationName` i `lpCommandLine`), `argv` **[0]** nie może być Nazwa pliku wykonywalnego; Użyj [Funkcja GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) można pobrać nazwy pliku wykonywalnego, a jego w pełni kwalifikowaną ścieżkę.  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `envp`  
 Tablica `envp`, która jest typowym rozszerzeniem w wielu systemach Unix, jest używana w języku Microsoft C++. Jest to tablica ciągów reprezentujących zestaw zmiennych w środowisku użytkownika. Ta tablica jest został przerwany przez **NULL** wpisu. Mogą być deklarowane jako tablicy wskaźników do **char (char** \*[envp —**)** lub jako wskaźnik do wskaźników do **char (char** \* \* envp —**)**. Jeśli używany przez program **wmain** zamiast **głównego**, użyj `wchar_t` zamiast typów danych `char`. Blok środowiska przekazany do **głównego** i **wmain** jest "zablokowane" kopię bieżącego środowiska. Jeśli użytkownik zmieni środowiska przez wywołanie **putenv —** lub `_wputenv`, czy bieżące środowisko (zwrócony przez `getenv` / `_wgetenv` i `_environ` /  `_wenviron` zmiennej) będzie zmiany, ale blok wskazywana przez envp — nie zmieni się. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) uzyskać informacji o pomijanie przetwarzania w środowisku. Ten argument jest zgodny ze standardem ANSI w języku C, ale nie w języku C++.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `argc`, `argv`, i `envp` argumenty **głównego**:  
  
```  
// argument_definitions.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
int main( int argc, char *argv[], char *envp[] ) {  
    int iNumberLines = 0;    // Default is no line numbers.  
  
    // If /n is passed to the .exe, display numbered listing  
    // of environment variables.  
  
    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )  
         iNumberLines = 1;  
  
    // Walk through list of strings until a NULL is encountered.  
    for( int i = 0; envp[i] != NULL; ++i ) {  
        if( iNumberLines )  
            cout << i << ": " << envp[i] << "\n";  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [main: uruchamianie programu](../cpp/main-program-startup.md)