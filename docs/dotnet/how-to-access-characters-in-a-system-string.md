---
title: 'Porady: dostęp do znaków w obiekcie System::String | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6c5c4c6032330a58a6f1ea9fb85d3da57c28a177
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416191"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Porady: dostęp do znaków w obiekcie System::String

Możesz uzyskać dostęp znaków <xref:System.String> obiektu dla połączeń o wysokiej wydajności do niezarządzanych funkcji o `wchar_t*` ciągów. Metoda daje posługiwanie się nimi wskaźnik do pierwszego znaku <xref:System.String> obiektu. Tego wskaźnika można modyfikować bezpośrednio lub przypięty i przekazany do funkcji, oczekiwano zwykłej `wchar_t` ciągu.

## <a name="example"></a>Przykład

`PtrToStringChars` Zwraca <xref:System.Char>, czyli wskaźnika wewnętrznego (znany także jako `byref`). W efekcie podlega wyrzucania elementów bezużytecznych. Nie masz przypiąć ten wskaźnik, chyba że zamierzasz przekazać go do funkcji macierzystej.

Rozważmy poniższy kod.  Przypinanie nie jest potrzebna, ponieważ `ppchar` jest wskaźnika wewnętrznego, a jeśli moduł odśmiecania pamięci przenosi ciąg wskazuje on, również spowoduje zaktualizowanie `ppchar`. Bez [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md), ten kod będzie działać i nie ma potencjalnych wpływający na wydajność powodowane przez przypinanie.

W przypadku przekazania `ppchar` funkcji macierzystej, następnie musi być przypiętego wskaźnika; moduł odśmiecania pamięci nie będzie można zaktualizować wszystkie wskaźniki w ramce stosu w niezarządzanym.

```
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

Przykładzie pokazano, gdy potrzebne są przypinania.

```
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

Wskaźnika wewnętrznego ma wszystkie właściwości wskaźnika natywnego języka C++. Na przykład umożliwia on zaprezentuje struktury połączonych danych, a następnie wykonaj wstawienia i usunięcia przy użyciu tylko jednego wskaźnika:

```
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

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)