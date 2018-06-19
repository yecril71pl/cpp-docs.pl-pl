---
title: Tworzenie obszarów przezroczystych lub odwróconych w obrazach urządzeń (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors, device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices, transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects, transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70fd2411eefba495478baaf5fb20fe7a27031001
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882553"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>Tworzenie obszarów przezroczystych lub odwróconych w obrazach urządzeń (Edytor obrazów dla ikon)
W [edytor obrazów](../windows/image-editor-for-icons.md), początkowej obrazu ikony ma atrybut przezroczysty. Mimo że obrazów ikony, jak i kursor jest prostokątny, wiele nie są wyświetlane, ponieważ części obrazu są niewidoczne; przedstawia podstawowy obraz na ekranie za pomocą ikony lub kursora. Przeciągnięcie ikony części obrazu może występować w kolorze odwrócony. Utwórz w tym celu przez ustawienie koloru ekranu i kolorów odwrotnych w [kolory — okno](../windows/colors-window-image-editor-for-icons.md).  
  
 Kolory ekranu i odwrotność zastosować ikony i kursory kształtu i kolor obrazu pochodnej albo wyznaczyć odwracanie regionów. Kolory wskazują części obrazu posiadających te atrybuty. Można zmienić kolory reprezentujących atrybuty ekranu odwrotność kolorach i edytowania. Te zmiany nie wpływają na wygląd ikony lub kursora w aplikacji.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-transparent-or-inverse-regions"></a>Aby utworzyć obszarów przezroczystych lub odwróconych  
  
1.  W **kolory** okna, kliknij przycisk **koloru ekranu** selektora lub **kolor odwrotność** selektora.  
  
2.  Zastosuj ekranu lub odwrotny kolor na przy użyciu narzędzia do rysowania obrazu. Aby uzyskać więcej informacji dotyczących narzędzi do rysowania, zobacz [przy użyciu narzędzia do rysowania](using-a-drawing-tool-image-editor-for-icons.md).  
  
### <a name="to-change-the-screen-or-inverse-color"></a>Aby zmienić kolor ekranu lub odwrotność  
  
1.  Wybierz opcję **koloru ekranu** selektora lub **kolor odwrotność** selektora.  
  
2.  Wybierz kolor z **kolory** palety w **kolory** okna.  
  
     Kolor dopełniający automatycznie wyznaczono innych selektora.  
  
    > [!TIP]
    >  Po dwukrotnym kliknięciu Selektor koloru ekranu lub kolor odwrotność [wybór koloru niestandardowego — okno dialogowe](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) pojawi się.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

