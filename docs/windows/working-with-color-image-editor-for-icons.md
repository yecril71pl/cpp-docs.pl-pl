---
title: "Praca z kolorem (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.image.color
dev_langs: C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors, Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ad0c7df6804667c3bd243668193283ecee61c8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-color-image-editor-for-icons"></a>Praca z kolorem (Edytor obrazów dla ikon)
Edytor obrazów zawiera wiele funkcji, które w szczególności obsługiwać i dostosowywanie kolorów. Można ustawić kolor pierwszego planu i tła, wypełnianie kolorem ograniczonego obszarów lub wybrać kolor na obraz do użycia jako bieżący kolor pierwszego planu i tła. Możesz użyć narzędzia na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) wraz z palety kolorów w [kolory — okno](../windows/colors-window-image-editor-for-icons.md) do tworzenia obrazów.  
  
 Wszystkie kolory w skali odcieni szarości i 16 kolorów obrazów są wyświetlane w palety kolorów w oknie kolorów. Oprócz standardowych 16 kolorów można tworzyć kolory niestandardowe. Zmiana któregoś z kolorów w palecie natychmiast zmieni kolor odpowiedniego obrazu.  
  
 Podczas pracy z ikony 256 kolorów i kursora obrazy, właściwość kolorów w [okna właściwości](/visualstudio/ide/reference/properties-window) jest używany. Aby uzyskać więcej informacji, zobacz [Tworzenie ikony 256 kolorów](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).  
  
> [!NOTE]
>  Korzystając z edytora obrazów, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.  
  
 Można również tworzyć obrazy koloru wartość true. Jednak true kolorów nie są wyświetlane w palecie pełna w oknie kolorów. pojawią się one w obszarze wskaźnik kolor pierwszego planu i tła. Wartość true, kolory są tworzone przy użyciu [wybór koloru niestandardowego — okno dialogowe](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Aby uzyskać więcej informacji, zobacz [Dostosowywanie lub zmiana kolorów](../windows/customizing-or-changing-colors-image-editor-for-icons.md).  
  
 Można zapisać palety kolorów niestandardowych na dysku i ponownie załaduj je zgodnie z potrzebami. Palety kolorów, które niedawno używane jest zapisywane w rejestrze i ładowane automatycznie przy następnym uruchomieniu programu Visual Studio.  
  
-   [Ustawianie pierwszego planu lub kolorów tła](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)  
  
-   [Wypełnianie ograniczonego obszaru obrazu kolorem](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)  
  
-   [Pobieranie koloru z obrazu do użycia w innym miejscu](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)  
  
-   [Wybieranie tła przezroczystego lub nieprzezroczystego](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)  
  
-   [Odwracanie kolorów w wyborze](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)  
  
-   [Dostosowywanie lub zmiana kolorów](../windows/customizing-or-changing-colors-image-editor-for-icons.md)  
  
-   [Zapisywanie i ładowanie różnych palet kolorów](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)  
  
-   [Kolory — okno](../windows/colors-window-image-editor-for-icons.md)  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   

