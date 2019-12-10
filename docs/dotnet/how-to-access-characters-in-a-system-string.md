---
title: 'Porady: dostęp do znaków w obiekcie System::String'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
ms.openlocfilehash: 3c44c5e7651bb1c5b4c28654b896cbe64bd5bec7
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988645"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Porady: dostęp do znaków w obiekcie System::String

Do funkcji niezarządzanych, które pobierają ciągi `wchar_t*`, można uzyskać dostęp do znaków obiektu <xref:System.String>. Metoda daje wskaźnik wewnętrzny do pierwszego znaku obiektu <xref:System.String>. Ten wskaźnik może być manipulowany bezpośrednio lub przypięty i przesłany do funkcji, oczekiwany jest zwykły ciąg `wchar_t`.

## <a name="example"></a>Przykład

`PtrToStringChars` zwraca <xref:System.Char>, który jest wskaźnikiem wnętrza (znanym także jako `byref`). W związku z tym podlega wyrzucaniu elementów bezużytecznych. Nie musisz przypinać tego wskaźnika, chyba że zamierzasz przekazać go do funkcji natywnej.

Rozważmy następujący kod.  Przypinanie nie jest potrzebne, ponieważ `ppchar` jest wskaźnikiem wnętrza, a jeśli moduł wyrzucania elementów bezużytecznych przenosi do niego ciąg, spowoduje również zaktualizowanie `ppchar`. Bez [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)kod będzie działał i nie zostanie osiągnięty potencjalny wpływ na wydajność spowodowany przez Przypinanie.

Jeśli przejdziesz `ppchar` do funkcji natywnej, musi to być przypięty wskaźnik; Moduł wyrzucania elementów bezużytecznych nie będzie mógł zaktualizować żadnych wskaźników w niezarządzanej ramce stosu.

```cpp
// PtrToStringChars.cpp
// compile with: /clr
#include<vcclr.h>
using namespace System;

int main() {
   String ^ mystring = "abcdefg";

   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );

   for ( ; *ppchar != L'\0'; ++ppchar )
      Console::Write(*ppchar);
}
```

```Output
abcdefg
```

## <a name="example"></a>Przykład

Ten przykład pokazuje, gdzie jest wymagany Przypinanie.

```cpp
// PtrToStringChars_2.cpp
// compile with: /clr
#include <string.h>
#include <vcclr.h>
// using namespace System;

size_t getlen(System::String ^ s) {
   // Since this is an outside string, we want to be secure.
   // To be secure, we need a maximum size.
   size_t maxsize = 256;
   // make sure it doesn't move during the unmanaged call
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);
   return wcsnlen(pinchars, maxsize);
};

int main() {
   System::Console::WriteLine(getlen("testing"));
}
```

```Output
7
```

## <a name="example"></a>Przykład

Wewnętrzny wskaźnik ma wszystkie właściwości wskaźnika natywnego C++ . Na przykład można użyć go do przeprowadzenia połączonej struktury danych i wykonania operacji wstawiania i usuwania przy użyciu tylko jednego wskaźnika:

```cpp
// PtrToStringChars_3.cpp
// compile with: /clr /LD
using namespace System;
ref struct ListNode {
   Int32 elem;
   ListNode ^ Next;
};

void deleteNode( ListNode ^ list, Int32 e ) {
   interior_ptr<ListNode ^> ptrToNext = &list;
   while (*ptrToNext != nullptr) {
      if ( (*ptrToNext) -> elem == e )
         *ptrToNext = (*ptrToNext) -> Next;   // delete node
      else
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node
   }
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
