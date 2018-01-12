---
title: "Porady: konwertowanie formatów plików obrazów za pomocą programu .NET Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: 5d5384b0-b9b7-4262-b9ad-c4cb95f75ee4
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dc2b84063c509cd870b5d02fa0a209b511d8a0f3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-convert-image-file-formats-with-the-net-framework"></a>Porady: konwertowanie formatów plików obrazów za pomocą programu .NET Framework
Poniższy przykład kodu pokazuje <xref:System.Drawing.Image?displayProperty=fullName> klasy i <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> wyliczenie używany do konwersji i zapisywania plików obrazów. Poniższy kod ładuje obraz z pliku jpg i zapisuje go w formatach plików GIF jak również bmp.  
  
> [!NOTE]
>  GDI + jest dołączony do systemu Windows XP, Windows Server 2003 i Windows Vista i jest dostępny jako pakiet redystrybucyjny systemu Windows 2000. Aby pobrać najnowszy pakiet redystrybucyjny programu, zobacz [http://go.microsoft.com/fwlink/p/?linkid=11232](http://go.microsoft.com/fwlink/p/?linkid=11232).   
  
## <a name="example"></a>Przykład  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
using namespace System::Drawing::Imaging;  
  
int main()  
{  
   Image^ image = Image::FromFile("SampleImage.jpg");  
   image->Save("SampleImage.png", ImageFormat::Png);  
   image->Save("SampleImage.bmp", ImageFormat::Bmp);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing>   
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)