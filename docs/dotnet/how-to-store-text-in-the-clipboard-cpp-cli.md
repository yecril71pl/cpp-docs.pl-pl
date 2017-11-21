---
title: 'Porady: przechowywanie tekstu w Schowku (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- text, storing in Clipboard
- Clipboard, storing text
ms.assetid: 9996023f-b700-47ad-8ad9-1ba201eaa5a6
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 971d87da7045e079e62d2ab3274ddc35ddbffaea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-store-text-in-the-clipboard-ccli"></a>Porady: przechowywanie tekstu w schowku (C++/CLI)
Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.Clipboard> obiekt zdefiniowany w <xref:System.Windows.Forms> przestrzeni nazw do przechowywania ciągu. Ten obiekt zawiera dwie funkcje Członkowskie: <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> i <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Dane są przechowywane w Schowku, wysyłając każdy obiekt pochodzi od <xref:System.Object> do <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>.  
  
## <a name="example"></a>Przykład  
  
```  
// store_clipboard.cpp  
// compile with: /clr  
#using <System.dll>  
#using <System.Drawing.dll>  
#using <System.Windows.Forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main()  
{  
   String^ str = "This text is copied into the Clipboard.";  
  
   // Use 'true' as the second argument if  
   // the data is to remain in the clipboard  
   // after the program terminates.  
   Clipboard::SetDataObject(str, true);  
  
   Console::WriteLine("Added text to the Clipboard.");  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: pobieranie tekstu ze Schowka (C + +/ CLI)](../dotnet/how-to-retrieve-text-from-the-clipboard-cpp-cli.md)   
 [Operacje w systemie Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)