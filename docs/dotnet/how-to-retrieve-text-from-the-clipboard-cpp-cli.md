---
title: 'Porady: pobieranie tekstu ze Schowka (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- text, retrieving from Clipboard
- Clipboard, retrieving text
ms.assetid: 99e77ba0-8573-4030-92d8-de8aa7623ee4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6517b367e8c3d59538a4e36839ccc7f93d8b1817
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-retrieve-text-from-the-clipboard-ccli"></a>Porady: pobieranie tekstu ze schowka (C++/CLI)
Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> funkcja zwraca wskaźnik do elementu członkowskiego <xref:System.Windows.Forms.IDataObject> interfejsu. Ten interfejs może następnie zapytanie dotyczące formatu danych i używane do pobierania danych rzeczywistych.  
  
## <a name="example"></a>Przykład  
  
```  
// read_clipboard.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.Drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main( )  
{  
   IDataObject^ data = Clipboard::GetDataObject( );  
  
   if (data)  
   {  
      if (data->GetDataPresent(DataFormats::Text))   
      {  
         String^ text = static_cast<String^>  
           (data->GetData(DataFormats::Text));  
         Console::WriteLine(text);   
      }  
      else  
         Console::WriteLine("Nontext data is in the Clipboard.");  
   }  
   else   
   {  
      Console::WriteLine("No data was found in the Clipboard.");  
   }  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje w systemie Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)