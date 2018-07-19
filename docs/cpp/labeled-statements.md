---
title: Instrukcje oznaczone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b54eb2757f4f58acd0339a058c8bee999b4c8b7
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947744"
---
# <a name="labeled-statements"></a>Labeled — instrukcje
Etykiety są używane do program kontrola jest przekazywana bezpośrednio do określonej instrukcji.  
  
```  
identifier :  statement  
case constant-expression :  statement  
default :  statement  
```  
  
 Zakres etykiety jest całą funkcję, w którym jest zdeklarowana.  
  
## <a name="remarks"></a>Uwagi  
 Istnieją trzy typy labeled — instrukcje. Wszystkie Użyj dwukropka do oddzielenia pewien rodzaj etykiety z instrukcji. Wielkość liter i domyślne etykiety są specyficzne dla instrukcji case.  
  
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
  
 Wygląd *identyfikator* etykieta w programie źródłowym deklaruje etykietę. Tylko [goto](../cpp/goto-statement-cpp.md) instrukcji można przekazać sterowanie do *identyfikator* etykiety. Poniższy fragment kodu przedstawia sposób używania metody **goto** instrukcji i *identyfikator* etykiety:  
  
 Etykiety nie może występować samodzielnie, ale zawsze musi być dołączony do instrukcji. Jeśli etykieta jest potrzebny samodzielnie, należy umieścić instrukcja o wartości null po etykiecie.  
  
 Etykieta ma zakres funkcji i nie może być ponownie zadeklarowany wewnątrz funkcji. Jednak takiej samej nazwie może służyć jako etykieta w różnych funkcji.  
  
```cpp 
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
  
 Etykiety, które pojawiają się po **przypadek** — słowo kluczowe także nie może występować poza **Przełącz** instrukcji. (To ograniczenie dotyczy także **domyślne** — słowo kluczowe.) Poniższy fragment kodu przedstawia poprawnego użycia **przypadek** etykiety:  
  
```cpp 
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
  
## <a name="labels-in-the-case-statement"></a>Etykiet w instrukcji case  
 Etykiety, które pojawiają się po **przypadek** — słowo kluczowe także nie może występować poza **Przełącz** instrukcji. (To ograniczenie dotyczy także **domyślne** — słowo kluczowe.) Poniższy fragment kodu przedstawia poprawnego użycia **przypadek** etykiety:  
  
```cpp 
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
 Wygląd *identyfikator* etykieta w programie źródłowym deklaruje etykietę. Tylko [goto](../cpp/goto-statement-cpp.md) instrukcji można przekazać sterowanie do *identyfikator* etykiety. Poniższy fragment kodu przedstawia sposób używania metody **goto** instrukcji i *identyfikator* etykiety:  
  
 Etykiety nie może występować samodzielnie, ale zawsze musi być dołączony do instrukcji. Jeśli etykieta jest potrzebny samodzielnie, należy umieścić instrukcja o wartości null po etykiecie.  
  
 Etykieta ma zakres funkcji i nie może być ponownie zadeklarowany wewnątrz funkcji. Jednak takiej samej nazwie może służyć jako etykieta w różnych funkcji.  
  
```cpp 
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
 [switch, instrukcja (C++)](../cpp/switch-statement-cpp.md)