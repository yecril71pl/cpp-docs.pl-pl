---
title: "Porady: analizowanie ciągów za pomocą wyrażeń regularnych (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- strings [C++], parsing
ms.assetid: 5b0c7ca3-9bba-4389-a45c-6d373cff91b0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fed9fd05ed9916e4d285c64a398b48b82d99f884
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-parse-strings-using-regular-expressions-ccli"></a>Porady: analizowanie ciągów za pomocą wyrażeń regularnych (C++/CLI)
Poniższy przykład kodu pokazuje prostego ciągu analizy przy użyciu <xref:System.Text.RegularExpressions.Regex> klasy w <xref:System.Text.RegularExpressions?displayProperty=fullName> przestrzeni nazw. Ciąg zawierający wiele typów ukośników word jest tworzony. Ten ciąg jest następnie analizować przy użyciu <xref:System.Text.RegularExpressions.Regex> klasy w połączeniu z <xref:System.Text.RegularExpressions.Match> klasy. Następnie każdego wyrazu w zdaniu jest wyświetlany osobno.  
  
## <a name="example"></a>Przykład  
  
```  
// regex_parse.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main( )  
{  
   int words = 0;  
   String^ pattern = "[a-zA-Z]*";  
   Console::WriteLine( "pattern : '{0}'", pattern );  
   Regex^ regex = gcnew Regex( pattern );  
  
   String^ line = "one\ttwo three:four,five six  seven";     
   Console::WriteLine( "text : '{0}'", line );  
   for( Match^ match = regex->Match( line );   
        match->Success; match = match->NextMatch( ) )   
   {  
      if( match->Value->Length > 0 )  
      {  
         words++;  
         Console::WriteLine( "{0}", match->Value );  
      }  
   }  
   Console::WriteLine( "Number of Words : {0}", words );  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [.NET framework — nieprawidłowe wyrażenia](/dotnet/standard/base-types/regular-expressions)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)