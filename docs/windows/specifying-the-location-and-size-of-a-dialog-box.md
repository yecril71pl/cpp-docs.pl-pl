---
title: Określanie lokalizacji i rozmiaru okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, size
- dialog boxes, positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3a3a9a629ec138659a7b0d2aba2460aced31fc74
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649006"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box"></a>Określanie lokalizacji i rozmiaru okna dialogowego
Lokalizacja i rozmiar, okno dialogowe, a także lokalizacji i rozmiaru formantów w nim, są mierzone w jednostkach okna dialogowego. Wartości dla poszczególnych formantów i w oknie dialogowym są wyświetlane w prawej dolnej części paska po ich wybraniu stanu programu Visual Studio.  
  
 Istnieją trzy właściwości, które można ustawić w [okno właściwości](/visualstudio/ide/reference/properties-window) do określenia, gdzie zostanie wyświetlone okno dialogowe na ekranie. Właściwość Centrum jest atrybut typu wartość logiczna; Jeśli wartość jest ustawiona na wartość True, okno dialogowe będzie zawsze pojawiają się w środku ekranu. Jeśli zostanie ustawiona na wartość False, następnie można ustawić właściwości Pozycja_x i Pozycja_y umożliwia jawne zdefiniowanie w przypadku, gdy na ekranie, zostanie wyświetlone okno dialogowe. Właściwości pozycji są wartości przesunięcia z lewym górnym rogu obszaru wyświetlania, która jest zdefiniowana jako {X = 0, Y = 0}. Pozycja również opiera się na **bezwzględnie Wyrównaj** właściwości: w przypadku opcji True współrzędne są podawane względem ekranu; w przypadku wartości FAŁSZ współrzędne są podawane względem okna dialogowego od właściciela tego okna.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)