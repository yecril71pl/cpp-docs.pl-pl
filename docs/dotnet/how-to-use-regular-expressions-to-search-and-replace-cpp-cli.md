---
title: 'Porady: Używanie wyrażeń regularnych do wyszukiwania i zamieniania (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search and replace
- Replace method
- regular expressions [C++], search and replace
ms.assetid: 12fe3e18-fe10-4b25-a221-19dc5eab3821
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: feb64670accef1cdcc5eedf9aa2b081dc41615b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132417"
---
# <a name="how-to-use-regular-expressions-to-search-and-replace-ccli"></a>Porady: używanie wyrażeń regularnych do wyszukiwania i zamieniania (C++/CLI)
Poniższy przykład kodu pokazuje sposób klasy wyrażeń regularnych <xref:System.Text.RegularExpressions.Regex> może służyć do wykonywania wyszukiwania i zamiany. Jest to zrobić za pomocą <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody. Wersja użyta przyjmuje dwa ciągi jako dane wejściowe: ciąg, który ma być zmodyfikowana, a ciąg, który ma zostać wstawiony zamiast sekcje (jeśli istnieje) pasujących do wzorca <xref:System.Text.RegularExpressions.Regex> obiektu.  
  
 Ten kod zastępuje wszystkie cyfr w ciągu znaków podkreślenia (_) i zastąpi te za pomocą ciągu pustego, skutecznie usunięcie ich. Ten sam efekt można wykonywać w jednym kroku, ale w tym miejscu służą dwa kroki dla celów demonstracyjnych.  
  
## <a name="example"></a>Przykład  
  
```  
// regex_replace.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System::Text::RegularExpressions;  
using namespace System;  
  
int main()  
{  
   String^ before = "The q43uick bro254wn f0ox ju4mped";  
   Console::WriteLine("original  : {0}", before);  
  
   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");  
   String^ after = digitRegex->Replace(before, "_");  
   Console::WriteLine("1st regex : {0}", after);  
  
   Regex^ underbarRegex = gcnew Regex("_");  
   String^ after2 = underbarRegex->Replace(after, "");  
   Console::WriteLine("2nd regex : {0}", after2);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [.NET framework — nieprawidłowe wyrażenia](/dotnet/standard/base-types/regular-expressions)   
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)