---
title: "Porady: obracanie obrazów za pomocą programu .NET Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], rotating images
- graphics [C++], rotating images
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5b337186f67758d56dbc0bae06b6886f43f7435
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-rotate-images-with-the-net-framework"></a>Porady: obracanie obrazów za pomocą programu .NET Framework
Poniższy przykład kodu pokazuje użycie <xref:System.Drawing.Image?displayProperty=fullName> klasę, aby załadować obrazu z dysku, jego obrót o 90 stopni i zapisać go jako nowy plik jpg.  
  
> [!NOTE]
>  GDI + jest dołączony do systemu Windows XP i jest dostępny jako pakiet redystrybucyjny systemu Windows NT 4.0 SP 6, Windows 2000, Windows 98 i Windows Millennium Edition. Aby pobrać najnowszy pakiet redystrybucyjny programu, zobacz [http://go.microsoft.com/fwlink/?linkid=11232](http://go.microsoft.com/fwlink/?linkid=11232). 
  
## <a name="example"></a>Przykład  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
  
int main()  
{  
   Image^ image = Image::FromFile("SampleImage.jpg");  
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );  
   image->Save("SampleImage_rotated.jpg");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)