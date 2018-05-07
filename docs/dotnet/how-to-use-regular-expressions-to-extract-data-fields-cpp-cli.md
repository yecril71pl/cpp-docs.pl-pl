---
title: 'Porady: Używanie wyrażeń regularnych do wyodrębniania pól danych (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
ms.assetid: b581d9b6-630e-48fa-94fe-20b0f7b89b06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 20e1139ccee0c3cc1533f42fb1b9e1eafaca3afd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-regular-expressions-to-extract-data-fields-ccli"></a>Porady: używanie wyrażeń regularnych do wyodrębniania pól danych (C++/CLI)
Poniższy przykład kodu pokazuje używanie wyrażeń regularnych do wyodrębniania danych z ciąg formatowania. Poniższy przykład kodu wykorzystuje <xref:System.Text.RegularExpressions.Regex> klasę, aby określić wzorzec, który odpowiada adresowi e-mail. Ten wzorzec zawiera identyfikatory pola, które mogą służyć do pobierania użytkownika i nazwę hosta części każdy adres e-mail. <xref:System.Text.RegularExpressions.Match> Klasa jest używana do realizacji dopasowania do wzorca rzeczywistych. Jeśli adres e-mail podany jest prawidłowy, nazwy hosta i nazwa użytkownika są wyodrębniane i wyświetlane.  
  
## <a name="example"></a>Przykład  
  
```  
// Regex_extract.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main()  
{  
    array<String^>^ address=  
    {  
        "jay@southridgevideo.com",  
        "barry@adatum.com",  
        "treyresearch.net",  
        "karen@proseware.com"  
    };  
  
    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");  
  
    for (int i=0; i<address->Length; i++)  
    {  
        Match^ m = emailregex->Match( address[i] );  
        Console::Write("\n{0,25}", address[i]);  
  
        if ( m->Success )   
        {  
            Console::Write("   User='{0}'",   
            m->Groups["user"]->Value);  
            Console::Write("   Host='{0}'",   
            m->Groups["host"]->Value);  
        }  
        else   
            Console::Write("   (invalid email address)");  
        }  
  
    Console::WriteLine("");  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [.NET framework — nieprawidłowe wyrażenia](/dotnet/standard/base-types/regular-expressions)   
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)