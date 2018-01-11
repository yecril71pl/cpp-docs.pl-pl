---
title: "Nazwy bez połączenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- functions [C++], parameters
- typedef names, linkage
- enumerators [C++], linkage
- names [C++], with no linkage
- function parameters [C++]
ms.assetid: 7174c500-12d2-4572-8c16-63c27c758fb1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13acb94022caf7ad9ddbf2fe94ad2fa95a70dc80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="names-with-no-linkage"></a>Nazwy bez połączenia
Tylko nazwy, które mają bez połączenia są:  
  
-   Parametry funkcji.  
  
-   Nazwy o zakresie bloku nie jest zadeklarowany jako `extern` lub **statycznych**.  
  
-   Moduły wyliczające.  
  
-   Zadeklarowane nazwy w `typedef` instrukcji. Wyjątek jest gdy `typedef` używana jest instrukcja o podanie nazwy dla typu klasy bez nazwy. Nazwa może być następnie połączenie zewnętrzne, jeśli klasa ma połączenie zewnętrzne. W poniższym przykładzie pokazano sytuację, w którym `typedef` nazwa ma połączenie zewnętrzne:  
  
    ```  
    // names_with_no_linkage.cpp  
    typedef struct  
    {  
       short x;  
       short y;  
    } POINT;  
  
    extern int MoveTo( POINT pt );  
  
    int main()  
    {  
    }  
    ```  
  
     `typedef` Nazwa `POINT`, staje się nazwa klasy dla struktury bez nazwy. Następnie służy do deklarowania funkcji z zewnętrznym powiązaniem.  
  
 Ponieważ `typedef` nazwy bez połączenia, należy ich definicje może się różnić między jednostki tłumaczenia. Ponieważ kompilacji została wykonana indywidualnie, nie istnieje sposób dla kompilatora wykryć te różnice. W związku z tym błędy tego typu nie są wykrywane czasu łącza. Rozważmy następujące:  
  
```  
// Translation unit 1  
typedef int INT  
  
INT myInt;  
...  
  
// Translation unit 2  
typedef short INT  
  
extern INT myInt;  
...  
```  
  
 Poprzedni kod generuje błąd "Nierozpoznany zewnętrzny" łączenia.  
  
## <a name="example"></a>Przykład  
 Funkcje języka C++ można zdefiniować tylko w zakresie pliku lub klasy. W poniższym przykładzie przedstawiono sposób definiowania funkcji i zawiera definicję błędne funkcji:  
  
```  
// function_definitions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void ShowChar( char ch );    // Declare function ShowChar.  
  
void ShowChar( char ch )     // Define function ShowChar.  
{                            // Function has file scope.  
   cout << ch;  
}  
  
struct Char                  // Define class Char.  
{  
    char Show();             // Declare Show function.  
    char Get();              // Declare Get function.  
    char ch;  
};  
  
char Char::Show()            // Define Show function  
{                            //  with class scope.  
    cout << ch;  
    return ch;  
}  
  
void GoodFuncDef( char ch )  // Define GoodFuncDef  
{                            //  with file scope.  
    int BadFuncDef( int i )  // C2601, Erroneous attempt to  
    {                        //  nest functions.  
        return i * 7;  
    }  
    for( int i = 0; i < BadFuncDef( 2 ); ++i )  
        cout << ch;  
    cout << "\n";  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Program i połączenie](../cpp/program-and-linkage-cpp.md)