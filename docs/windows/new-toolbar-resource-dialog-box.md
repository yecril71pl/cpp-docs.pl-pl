---
title: "Okno dialogowe Nowy zasób paska narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.newtoolbarresource
dev_langs:
- C++
helpviewer_keywords:
- New Toolbar Resource dialog box
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c30301b8887013d72e7ae2ab2d70650de7d7f0e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="new-toolbar-resource-dialog-box"></a>Okno dialogowe Nowy zasób paska narzędzi
Okno dialogowe Nowy zasób paska narzędzi umożliwia określenie szerokości i wysokości przycisków dodawanego do zasobu paska narzędzi. Wartość domyślna to 16 x 15 pikseli.  
  
 Mapa bitowa, który służy do tworzenia paska narzędzi ma maksymalną szerokość 2048. Dlatego jeśli ustawisz **szerokość przycisku** do 512, może być tylko czterech przycisków. Ustaw szerokość 513, może mieć tylko trzy przyciski.  
  
 **Szerokość przycisku**  
 Miejsce na wpisanie szerokości przycisków paska narzędzi, który ma zostać zmieniony z zasobu mapy bitowej do zasobu paska narzędzi. Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane do użycia standardowe kolory paska narzędzi (16 kolorów).  
  
 **Wysokość przycisku**  
 Miejsce na wpisanie wysokość przycisków paska narzędzi, który ma zostać zmieniony z zasobu mapy bitowej do zasobu paska narzędzi. Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane do użycia standardowe kolory paska narzędzi (16 kolorów).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 MFC i ATL  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości przycisku paska narzędzi](../windows/toolbar-button-properties.md)   
 [Konwertowanie map bitowych na paski narzędzi](../windows/converting-bitmaps-to-toolbars.md)   
 [Edytor paska narzędzi](../windows/toolbar-editor.md)

