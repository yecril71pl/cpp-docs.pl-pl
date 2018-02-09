---
title: "Porady: Rysowanie kształtów za pomocą programu .NET Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
ms.assetid: ffad5ae7-6ef4-4550-8940-be3f209a101d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c5fc48eefb44049e4cff010b16c9567e443ba5db
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-draw-shapes-with-the-net-framework"></a>Porady: rysowanie kształtów za pomocą programu .NET Framework
Poniższy przykład kodu wykorzystuje <xref:System.Drawing.Graphics> klasę, aby zmodyfikować <xref:System.Windows.Forms.Form.OnPaint%2A> obsługi zdarzeń, aby pobrać wskaźnika do <xref:System.Drawing.Graphics> obiekt dla tego formularza. Ten wskaźnik jest następnie używany do kolor tła formularza i rysowanie linii i łuku przy użyciu <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> i <xref:System.Drawing.Graphics.DrawArc%2A> metody.  
  
## <a name="example"></a>Przykład  
  
```  
#using <system.drawing.dll>  
using namespace System;  
using namespace System::Drawing;  
// ...  
protected:   
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override  
{  
   Graphics^ g = pe->Graphics;  
   g->Clear(Color::AntiqueWhite);  
  
   Rectangle rect = Form::ClientRectangle;  
   Rectangle smallRect;  
   smallRect.X = rect.X + rect.Width / 4;  
   smallRect.Y = rect.Y + rect.Height / 4;  
   smallRect.Width = rect.Width / 2;  
   smallRect.Height = rect.Height / 2;  
  
   Pen^ redPen = gcnew Pen(Color::Red);  
   redPen->Width = 4;  
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);  
  
   Pen^ bluePen = gcnew Pen(Color::Blue);  
   bluePen->Width = 10;  
   g->DrawArc( bluePen, smallRect, 90, 270 );  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Przestrzeń nazw System::Drawing](https://msdn.microsoft.com/en-us/library/system.drawing.aspx)