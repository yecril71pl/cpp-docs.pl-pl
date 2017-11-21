---
title: "Etykietą instrukcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 79b60544b719eebcff44a7e9c6a4ee360a75315a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="labeled-statements"></a>Labeled — instrukcje
Etykiety są używane do przekazywania kontroli programu bezpośrednio do określonej instrukcji.  
  
```  
identifier :  statement  
case constant-expression :  statement  
default :  statement  
```  
  
 Zakres etykiety jest całą funkcję, w którym jest zadeklarowany.  
  
## <a name="remarks"></a>Uwagi  
 Istnieją trzy typy labeled — instrukcje. Dwukropek wszystkie służy do oddzielania pewien typ etykiety z instrukcji. Etykiety case i domyślne są specyficzne dla instrukcji case.  
  
```cpp  
#include <iostream>   
using namespace std;   
  
void test_label(int x) {  
  
    if (x == 1){  
        goto label1;  
    }  
    goto label2;  
  
label1:  
    cout << "in label1" << endl;  
    return;  
  
label2:  
    cout << "in label2" << endl;  
    return;  
}  
  
int main() {  
    test_label(1);  // in label1   
    test_label(2);  // in label2  
}  
  
```  
  
 **Goto — instrukcja**  
  
 Wygląd *identyfikator* etykiety w programie źródłowym deklaruje etykiety. Tylko [goto](../cpp/goto-statement-cpp.md) instrukcji można przenosić formant *identyfikator* etykiety. Poniższy fragment kodu przedstawia użycie `goto` instrukcji i *identyfikator* etykiety:  
  
 Etykiety nie może występować samodzielnie, ale zawsze musi być dołączony do instrukcji. Jeśli etykieta nie jest konieczne samodzielnie, umieść instrukcję null po etykiecie.  
  
 Etykieta ma zakres funkcji i nie można ponownie zadeklarować w funkcji. Jednak takiej samej nazwie może służyć jako etykieta w różnych funkcji.  
  
```  
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
}  
  
//Output: At Test2 label.  
```  
  
 **Case — instrukcja**  
  
 Po etykietach, które są wyświetlane po **przypadku** — słowo kluczowe także nie może występować poza `switch` instrukcji. (To ograniczenie ma również zastosowanie do **domyślne** — słowo kluczowe.) Poniższy fragment kodu przedstawia poprawnego używania **przypadku** etykiety:  
  
```  
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );   
      EndPaint( hWnd, &ps );  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## <a name="labels-in-the-case-statement"></a>Etykiety case — instrukcja  
 Po etykietach, które są wyświetlane po **przypadku** — słowo kluczowe także nie może występować poza `switch` instrukcji. (To ograniczenie ma również zastosowanie do **domyślne** — słowo kluczowe.) Poniższy fragment kodu przedstawia poprawnego używania **przypadku** etykiety:  
  
```  
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      // Obtain a handle to the device context.  
      // BeginPaint will send WM_ERASEBKGND if appropriate.  
  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );  
  
      // Inform Windows that painting is complete.  
  
      EndPaint( hWnd, &ps );  
      break;  
  
   case WM_CLOSE:  
      // Close this window and all child windows.  
  
      KillTimer( hWnd, TIMER1 );  
      DestroyWindow( hWnd );  
      if ( hWnd == hWndMain )  
         PostQuitMessage( 0 );  // Quit the application.  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## <a name="labels-in-the-goto-statement"></a>Etykiety instrukcji goto  
 Wygląd *identyfikator* etykiety w programie źródłowym deklaruje etykiety. Tylko [goto](../cpp/goto-statement-cpp.md) instrukcji można przenosić formant *identyfikator* etykiety. Poniższy fragment kodu przedstawia użycie `goto` instrukcji i *identyfikator* etykiety:  
  
 Etykiety nie może występować samodzielnie, ale zawsze musi być dołączony do instrukcji. Jeśli etykieta nie jest konieczne samodzielnie, umieść instrukcję null po etykiecie.  
  
 Etykieta ma zakres funkcji i nie można ponownie zadeklarować w funkcji. Jednak takiej samej nazwie może służyć jako etykieta w różnych funkcji.  
  
```  
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
// At Test2 label.  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)   
 [Switch — instrukcja (C++)](../cpp/switch-statement-cpp.md)