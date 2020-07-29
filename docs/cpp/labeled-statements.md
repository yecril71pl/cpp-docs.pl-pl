---
title: Labeled — instrukcje
ms.date: 11/04/2016
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
ms.openlocfilehash: a10d071e46c79f49abf7e3eba498fae0487ccdc7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213362"
---
# <a name="labeled-statements"></a>Labeled — instrukcje

Etykiety służą do transferowania kontroli programu bezpośrednio do określonej instrukcji.

```
identifier :  statement
case constant-expression :  statement
default :  statement
```

Zakresem etykiety jest cała funkcja, w której jest zadeklarowana.

## <a name="remarks"></a>Uwagi

Istnieją trzy typy instrukcji z etykietami. Wszystkie Użyj dwukropka do oddzielenia pewnego typu etykiety od instrukcji. Etykiety case i default są specyficzne dla instrukcji case.

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

**Instrukcja goto**

Wygląd etykiety *identyfikatora* w programie źródłowym deklaruje etykietę. Tylko instrukcja [goto](../cpp/goto-statement-cpp.md) może przetransferować kontrolę do etykiety *identyfikatora* . Poniższy fragment kodu ilustruje użycie **`goto`** instrukcji i etykiety *identyfikatora* :

Etykieta nie może występować sama przez siebie, ale musi być zawsze dołączona do instrukcji. Jeśli etykieta jest konieczna, umieść instrukcję o wartości null po etykiecie.

Etykieta ma zakres funkcji i nie może zostać ponownie zadeklarowana w obrębie funkcji. Jednak taka sama nazwa może być używana jako etykieta w różnych funkcjach.

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

**Instrukcja Case**

Etykiety, które pojawiają się po **`case`** słowie kluczowym nie mogą występować także poza **`switch`** instrukcją. (To ograniczenie dotyczy również **`default`** słowa kluczowego). Poniższy fragment kodu przedstawia poprawne użycie **`case`** etykiet:

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

## <a name="labels-in-the-case-statement"></a>Etykiety w instrukcji case

Etykiety, które pojawiają się po **`case`** słowie kluczowym nie mogą występować także poza **`switch`** instrukcją. (To ograniczenie dotyczy również **`default`** słowa kluczowego). Poniższy fragment kodu przedstawia poprawne użycie **`case`** etykiet:

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

## <a name="labels-in-the-goto-statement"></a>Etykiety w instrukcji goto

Wygląd etykiety *identyfikatora* w programie źródłowym deklaruje etykietę. Tylko instrukcja [goto](../cpp/goto-statement-cpp.md) może przetransferować kontrolę do etykiety *identyfikatora* . Poniższy fragment kodu ilustruje użycie **`goto`** instrukcji i etykiety *identyfikatora* :

Etykieta nie może występować sama przez siebie, ale musi być zawsze dołączona do instrukcji. Jeśli etykieta jest konieczna, umieść instrukcję o wartości null po etykiecie.

Etykieta ma zakres funkcji i nie może zostać ponownie zadeklarowana w obrębie funkcji. Jednak taka sama nazwa może być używana jako etykieta w różnych funkcjach.

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

## <a name="see-also"></a>Zobacz także

[Omówienie instrukcji języka C++](../cpp/overview-of-cpp-statements.md)<br/>
[switch — instrukcja (C++)](../cpp/switch-statement-cpp.md)
