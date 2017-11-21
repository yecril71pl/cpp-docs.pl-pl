---
title: "Używanie wyrażeń regularnych do walidacji formatowania (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 225775c3-3efc-4734-bde2-1fdf73e3d397
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: db15abf9aca532b8c0fb712733c4e87350b58747
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-regular-expressions-to-validate-data-formatting-ccli"></a>Porady: używanie wyrażeń regularnych do walidacji formatowania danych (C++/CLI)
Poniższy przykład kodu pokazuje użycie wyrażenia regularnego, aby upewnić się, formatowania ciągu. W poniższym przykładzie kodu powinien on zawierać prawidłowy numer telefonu. Poniższy przykład kodu wykorzystuje ciąg "\d{3}-\d{3}-\d{4}", aby wskazać, że każde pole reprezentuje prawidłowy numer telefonu. W ciągu "d" oznacza cyfrę, a argument po każdym "d" wskazuje liczbę miejsc po przecinku, które muszą być obecne. W takim przypadku numer będzie musiał być oddzielone kreskami.  
  
## <a name="example"></a>Przykład  
  
```  
// regex_validate.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ number =   
   {  
      "123-456-7890",   
      "444-234-22450",   
      "690-203-6578",   
      "146-893-232",  
      "146-839-2322",  
      "4007-295-1111",   
      "407-295-1111",   
      "407-2-5555",   
   };  
  
   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";  
  
   for ( int i = 0; i < number->Length; i++ )  
   {  
      Console::Write( "{0,14}", number[i] );  
  
      if ( Regex::IsMatch( number[i], regStr ) )  
         Console::WriteLine(" - valid");  
      else  
         Console::WriteLine(" - invalid");  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [.NET framework — nieprawidłowe wyrażenia](/dotnet/standard/base-types/regular-expressions)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)