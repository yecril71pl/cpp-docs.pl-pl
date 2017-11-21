---
title: "Porady: wyświetlanie obrazów za pomocą programu .NET Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], displaying images
- graphics [C++], displaying images
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 23e8445e5a407e71061a971bccfb77d6b4170a35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-display-images-with-the-net-framework"></a>Porady: wyświetlanie obrazów za pomocą programu .NET Framework
Poniższy przykład kodu modyfikuje pobrać wskaźnika do obsługi zdarzeń OnPaint <xref:System.Drawing.Graphics> obiekt dla tego formularza. <xref:System.Windows.Forms.Form.OnPaint%2A> Funkcji jest przeznaczony dla aplikacji formularzy systemu Windows, najprawdopodobniej utworzone za pomocą Kreatora aplikacji Visual Studio.  
  
 Obraz jest reprezentowana przez <xref:System.Drawing.Image> klasy. Dane obrazu są ładowane z pliku jpg przy użyciu <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> metody. Przed narysowaniem obrazu do formularza, rozmiarów formularza do pomieszczenia obrazu. Rysowanie obrazu jest wykonywane z <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> metody.  
  
 <xref:System.Drawing.Graphics> i <xref:System.Drawing.Image> klasy znajdują się w <xref:System.Drawing?displayProperty=fullName> przestrzeni nazw.  
  
> [!NOTE]
>  GDI + jest dołączony do systemu Windows XP i jest dostępny jako pakiet redystrybucyjny systemu Windows NT 4.0 SP 6, Windows 2000, Windows 98 i systemu Windows. Aby pobrać najnowszy pakiet redystrybucyjny programu, zobacz [http://go.microsoft.com/fwlink/?linkid=11232](http://go.microsoft.com/fwlink/?linkid=11232).   
  
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
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)