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
ms.openlocfilehash: ed9682492eedc915919758d42d5594560cb4a83a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129752"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Porady: dostęp do znaków w obiekcie System::String
Dostęp można uzyskać znaki <xref:System.String> obiektu dla wywołań wysokiej wydajności w niezarządzanych funkcji, które trwają `wchar_t*` ciągów. Metoda zwraca wskaźnik wewnętrzny do pierwszego znaku <xref:System.String> obiektu. This, wskaźnik można manipulować bezpośrednio lub przypięty i przekazany do funkcji, oczekiwano zwykłego `wchar_t` ciągu.  
  
## <a name="example"></a>Przykład  
 `PtrToStringChars` Zwraca <xref:System.Char>, która jest wskaźnik wewnętrzny (znanej także jako `byref`). W efekcie go podlega wyrzucanie elementów bezużytecznych. Nie masz przypiąć ten wskaźnik, chyba że użytkownik chce go przekazać do funkcji macierzystej.  
  
 Rozważmy poniższy kod.  Przypinanie nie jest potrzebna, ponieważ `ppchar` jest wskaźnik wewnętrzny i jeśli moduł zbierający elementy bezużyteczne przenosi ciąg wskazuje, również spowoduje zaktualizowanie `ppchar`. Bez [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md), kod będzie działać i nie ma potencjalnych trafień wydajności spowodowany przez przypinanie.  
  
 W przypadku przekazania `ppchar` funkcji macierzystej, następnie należy ją przypiętego wskaźnika; moduł zbierający elementy bezużyteczne nie będzie mógł zaktualizować wszystkie wskaźniki w ramce stosu niezarządzane.  
  
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
 Przykładzie pokazano, gdzie jest potrzebna przypinania.  
  
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
 Wskaźnik wewnętrzny ma wszystkie właściwości wskaźnik natywny C++. Na przykład umożliwia ona szczegółowe struktury połączonych danych i do wstawienia i usunięcia za pomocą tylko jednego wskaźnika:  
  
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