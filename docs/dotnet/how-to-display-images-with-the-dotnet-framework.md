---
title: 'Porady: wyświetlanie obrazów za pomocą programu .NET Framework | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++], displaying images
- graphics [C++], displaying images
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a7f3ed2d8fe90501b5ef3d0ae5028890fe5290e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-images-with-the-net-framework"></a>Porady: wyświetlanie obrazów za pomocą programu .NET Framework
Poniższy przykład kodu modyfikuje pobrać wskaźnika do obsługi zdarzeń OnPaint <xref:System.Drawing.Graphics> obiekt dla tego formularza. <xref:System.Windows.Forms.Form.OnPaint%2A> Funkcji jest przeznaczony dla aplikacji formularzy systemu Windows, najprawdopodobniej utworzone za pomocą Kreatora aplikacji Visual Studio.  
  
 Obraz jest reprezentowana przez <xref:System.Drawing.Image> klasy. Dane obrazu są ładowane z pliku jpg przy użyciu <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> metody. Przed narysowaniem obrazu do formularza, rozmiarów formularza do pomieszczenia obrazu. Rysowanie obrazu jest wykonywane z <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> metody.  
  
 <xref:System.Drawing.Graphics> i <xref:System.Drawing.Image> klasy znajdują się w <xref:System.Drawing?displayProperty=fullName> przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
  
protected:  
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override  
{  
    Graphics^ g = pe->Graphics;  
    Image^ image = Image::FromFile("SampleImage.jpg");  
    Form::ClientSize = image->Size;  
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing?displayProperty=fullName>   
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)