---
title: 'Porady: wpisywanie tekstu do pliku (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++], text
- text files, writing in C++
ms.assetid: 39ecdba6-84e0-485c-a202-84cf6d7b8d4a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 080b4fcfb005d0d04c10ad5c0a6f4d1c7a49fe0e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-write-a-text-file-ccli"></a>Porady: wpisywanie tekstu do pliku tekstowego (C++/CLI)
Poniższy przykład kodu pokazuje, jak utworzyć plik tekstowy i zapisywanie tekstu do niej przy użyciu <xref:System.IO.StreamWriter> klasy, która jest zdefiniowana w <xref:System.IO> przestrzeni nazw. <xref:System.IO.StreamWriter> Konstruktora pobiera nazwę pliku, który ma zostać utworzony. Jeśli plik istnieje, zostanie zastąpiony (chyba że przekazujesz True jako drugi <xref:System.IO.StringWriter> argumentów konstruktora).  
  
 Plik jest dokonywane przy użyciu <xref:System.IO.StreamWriter.Write%2A> i <xref:System.IO.TextWriter.WriteLine%2A> funkcji.  
  
## <a name="example"></a>Przykład  
  
```  
// text_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "textfile.txt";  
  
   StreamWriter^ sw = gcnew StreamWriter(fileName);  
   sw->WriteLine("A text file is born!");  
   sw->Write("You can use WriteLine");  
   sw->WriteLine("...or just Write");  
   sw->WriteLine("and do {0} output too.", "formatted");  
   sw->WriteLine("You can also send non-text objects:");  
   sw->WriteLine(DateTime::Now);  
   sw->Close();  
   Console::WriteLine("a new file ('{0}') has been written", fileName);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Plik i strumienia I-O](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)