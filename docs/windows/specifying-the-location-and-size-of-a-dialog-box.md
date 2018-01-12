---
title: "Określanie lokalizacji i rozmiaru okna dialogowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes, size
- dialog boxes, positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03c4c6d6afb13a0e4ed8801838356ff0d1e851f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-the-location-and-size-of-a-dialog-box"></a>Określanie lokalizacji i rozmiaru okna dialogowego
Lokalizacja i rozmiar okno dialogowe, jak również lokalizacja i rozmiar kontrolki, to są mierzone w jednostkach okna dialogowego. Wartości dla poszczególnych formantów i w oknie dialogowym są wyświetlane w prawej dolnej części paska po wybraniu ich stanu programu Visual Studio.  
  
 Istnieją trzy właściwości, które można ustawić w [okna właściwości](/visualstudio/ide/reference/properties-window) do określenia, gdzie zostaną wyświetlone na ekranie okno dialogowe. Właściwość Centrum jest logiczną; Jeśli wartość jest ustawiona na wartość True, okno dialogowe zawsze będą wyświetlane w Centrum ekranu. Jeśli zostanie ustawiona na wartość False, można następnie ustawić właściwości Pozycja_x i Pozycja_y, aby jawnie zdefiniuj w przypadku, gdy na ekranie, zostanie wyświetlone okno dialogowe. Właściwości pozycji są wartości przesunięcia z lewym górnym rogu obszaru wyświetlania, która jest zdefiniowana jako {X = 0, Y = 0}. Pozycja również jest oparta na **wyrównanie bezwzględne** właściwości: w przypadku wartości PRAWDA współrzędne są podawane względem ekranu; w przypadku wartości FAŁSZ współrzędne są podawane względem okno właściciela okna dialogowego.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)

