---
title: Właściwości przycisku paska narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons (in Toolbar editor), setting properties
- Toolbar editor, toolbar button properties
- status bars, active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e61ba7e8720c755ce26408826c56a5c1fc9d51e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890690"
---
# <a name="toolbar-button-properties"></a>Właściwości przycisku paska narzędzi
Właściwości przycisku paska narzędzi są:  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**ID**|Określa identyfikator przycisku. Listy rozwijanej udostępnia typowe **identyfikator** nazwy.|  
|**Szerokość**|Ustawia szerokość przycisku. Zaleca się 16 pikseli.|  
|**Wysokość**|Określa wysokość przycisku. Należy pamiętać, że wysokość jeden przycisk zmieni wysokość wszystkich przycisków na pasku narzędzi. Zaleca się 15 pikseli.|  
|**wiersz**|Określa komunikat wyświetlany w pasku stanu. Dodawanie \n i nazwę dodaje etykietkę narzędzia do tego przycisku paska narzędzi. Aby uzyskać więcej informacji, zobacz [tworzenie etykietka narzędzia](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|  
  
 **Szerokość** i **wysokość** dotyczą wszystkich przycisków. Mapa bitowa, który służy do tworzenia paska narzędzi ma maksymalną szerokość 2048. Dlatego jeśli szerokość przycisku równa 512, może mieć tylko czterech przycisków i jeśli ustawisz szerokość 513 trzy przyciski może mieć tylko.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 MFC i ATL  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiana właściwości przycisku paska narzędzi](../windows/changing-the-properties-of-a-toolbar-button.md)   
 [Edytor paska narzędzi](../windows/toolbar-editor.md)

