---
title: Przy użyciu wyjść ani zwracać | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
- return keyword [C++], using for program termination
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45885cc6dbac50a693bb84abb797469d8aff93a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="using-exit-or-return"></a>Użycie exit lub return
Podczas wywoływania **zakończyć** lub wykonać `return` instrukcji z **głównego**, statyczne obiekty zostaną zniszczone w odwrotnej kolejności ich inicjowania. W poniższym przykładzie przedstawiono sposób działania takich inicjowanie i oczyszczanie.  
  
## <a name="example"></a>Przykład  
  
```  
// using_exit_or_return1.cpp  
#include <stdio.h>  
class ShowData {  
public:  
   // Constructor opens a file.  
   ShowData( const char *szDev ) {  
   errno_t err;  
      err = fopen_s(&OutputDev, szDev, "w" );  
   }  
  
   // Destructor closes the file.  
   ~ShowData() { fclose( OutputDev ); }  
  
   // Disp function shows a string on the output device.  
   void Disp( char *szData ) {   
      fputs( szData, OutputDev );  
   }  
private:  
   FILE *OutputDev;  
};  
  
//  Define a static object of type ShowData. The output device  
//   selected is "CON" -- the standard output device.  
ShowData sd1 = "CON";  
  
//  Define another static object of type ShowData. The output  
//   is directed to a file called "HELLO.DAT"  
ShowData sd2 = "hello.dat";  
  
int main() {  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
 W powyższym przykładzie statycznych obiektów `sd1` i `sd2` są tworzone i zainicjowany przed wejściem do `main`. Po ten program zakończy przy użyciu `return` instrukcji, pierwsza `sd2` jest niszczony, a następnie `sd1`. Destruktor dla elementu `ShowData` klasy zamyka plików skojarzonych z tymi obiektami statycznych.   
  
 Jest napisać ten kod w inny sposób, aby zadeklarować `ShowData` obiektów o zakresie bloku, dzięki czemu mogą zostać zniszczone, gdy przejdą poza zakresem:  
  
```  
int main() {  
   ShowData sd1, sd2( "hello.dat" );  
  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)