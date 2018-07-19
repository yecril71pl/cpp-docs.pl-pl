---
title: Definicje argumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a401caad212978372bcb02b412fa8a9648b7170
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37948255"
---
# <a name="argument-definitions"></a>Definicje argumentu
Argumenty w prototypie  
  
```cpp 
  
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);  
```  
  
 umożliwiają wygodne przetwarzanie argumentów z poziomu wiersza polecenia oraz, opcjonalnie, dostęp do zmiennych środowiskowych. Definicje argumentów są następujące:  
  
 *argc —*  
 Liczba całkowita, która zawiera liczbę argumentów, które należy wykonać w *argv*. *Argc —* parametru jest zawsze większa lub równa 1.  
  
 *ARGV*  
 Tablica ciągów zakończonych znakiem null, która reprezentuje argumenty wiersza polecenia wprowadzone przez użytkownika programu. Zgodnie z Konwencją `argv` **[0]** jest poleceniem, z którym wywoływany jest program `argv` **[1]** jest pierwszym argumentem wiersza polecenia i tak dalej, aż do `argv`  **[**`argc`**]**, która zawsze ma wartość NULL. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) uzyskać informacje dotyczące pomijania przetwarzania w wierszu polecenia.  
  
 Pierwszym argumentem wiersza polecenia jest zawsze `argv` **[1]** i jest ostatni z nich `argv` **[** `argc` - 1 **]**.  
  
> [!NOTE]
>  Zgodnie z Konwencją `argv` **[0]** jest poleceniem, z którym wywoływany jest program.  Jednak jest możliwe, aby utworzyć proces przy użyciu [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) i jeśli korzystasz z pierwszego i drugiego argumentu (`lpApplicationName` i `lpCommandLine`), `argv` **[0]** może nie być Nazwa pliku wykonywalnego; Użyj [Funkcja GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) można pobrać nazwy pliku wykonywalnego oraz jego w pełni kwalifikowanej ścieżki.  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 *envp*  
 *Envp* tablicy, która jest typowym rozszerzeniem w wielu systemach UNIX, jest używany w Microsoft C++. Jest to tablica ciągów reprezentujących zestaw zmiennych w środowisku użytkownika. Tablica jest zakończona wpisem o wartości NULL. Mogą być deklarowane jako tablica wskaźników do **char (char** \*envp []**)** lub jako wskaźnik do wskaźników do **char (char** \* \* envp **)**. Jeśli program używa **wmain** zamiast **głównego**, użyj **wchar_t** typu danych zamiast **char**. Blok środowiska przekazany do **głównego** i **wmain** jest "zamrożoną" kopią bieżącego środowiska. Jeśli następnie zmienisz środowisko przez wywołanie **putenv** lub `_wputenv`, bieżące środowisko (zwrócone przez `getenv` / `_wgetenv` i `_environ` /  `_wenviron` zmiennej) będzie zmieni się, ale blok wskazywany przez envp nie zmieni się. Zobacz [Dostosowywanie przetwarzania wiersza polecenia](../cpp/customizing-cpp-command-line-processing.md) uzyskać informacje dotyczące pomijania przetwarzania środowiska. Ten argument jest zgodny ze standardem ANSI w języku C, ale nie w języku C++.  
  
**END specyficzny dla Microsoft**  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać *argc —*, *argv*, i *envp* argumenty **głównego**:  
  
```cpp 
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