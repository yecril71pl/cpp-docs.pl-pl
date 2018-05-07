---
title: 'Porady: Używanie wyrażeń regularnych do zmiany rozmieszczenia danych (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular expressions [C++], rearranging data
- data [C++], rearranging
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 72c72721aa68417ff13905fdf96f8d2a48b310cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-regular-expressions-to-rearrange-data-ccli"></a>Porady: używanie wyrażeń regularnych do zmiany rozmieszczenia danych (C++/CLI)
W poniższym przykładzie kodu pokazano, jak obsługa wyrażeń regularnych programu .NET Framework może służyć do zmiany rozmieszczenia ani formatowania danych. Poniższy przykład kodu wykorzystuje <xref:System.Text.RegularExpressions.Regex> i <xref:System.Text.RegularExpressions.Match> klasy, aby wyodrębnić imiona i nazwiska z ciągu, a następnie wyświetlenia tych elementów nazwy w odwrotnej kolejności.  
  
 <xref:System.Text.RegularExpressions.Regex> Klasy jest używany do tworzenia wyrażenia regularnego, który opisuje bieżącego formatu danych. Obie nazwy muszą być oddzielone przecinkami i może używać dowolną liczbę spacji wokół przecinkiem. <xref:System.Text.RegularExpressions.Match> Metody są następnie używane do analizowania każdy ciąg. W przypadku powodzenia imiona i nazwiska są pobierane z <xref:System.Text.RegularExpressions.Match> obiektu i wyświetlane.  
  
## <a name="example"></a>Przykład  
  
```  
// regex_reorder.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ name =   
   {  
      "Abolrous, Sam",   
      "Berg,Matt",   
      "Berry , Jo",  
      "www.contoso.com"  
   };  
  
   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");  
  
   for ( int i=0; i < name->Length; i++ )  
   {  
      Console::Write( "{0,-20}", name[i] );  
      Match^ m = reg->Match( name[i] );  
      if ( m->Success )  
      {  
         String^ first = m->Groups["first"]->Value;  
         String^ last = m->Groups["last"]->Value;  
         Console::WriteLine("{0} {1}", first, last);  
      }  
      else  
         Console::WriteLine("(invalid)");  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [.NET framework — nieprawidłowe wyrażenia](/dotnet/standard/base-types/regular-expressions)   
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)