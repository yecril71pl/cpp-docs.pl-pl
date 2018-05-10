---
title: Okno dialogowe Nowy zasób paska narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newtoolbarresource
dev_langs:
- C++
helpviewer_keywords:
- New Toolbar Resource dialog box
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6662fcfab3c9bb1d805e39147bd2838e6bbce5b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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

