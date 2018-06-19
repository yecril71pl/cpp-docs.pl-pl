---
title: 'Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], creating
- image resources, display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices, creating icons for
- cursors [C++], hot spots
- icons [C++], types
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a977629cbae140afa1463a7765f193a7519e1f68
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881913"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons"></a>Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach (Edytor obrazów dla ikon)
Ikony i kursory są zasobów graficznych, które mogą zawierać wiele obrazów w różnych rozmiarach i schematów kolorów dla różnych typów urządzeń wyświetlających. Ponadto kursor ma "punkt aktywny," Lokalizacja, którą system Windows używa do śledzenia położenia. Zarówno ikony i kursory są tworzone i edytować za pomocą edytora obrazów jako mapy bitowe i inne obrazy.  
  
 Tworząc nową ikonę lub kursora, edytor obrazów najpierw tworzy obraz typu standardowego. Obraz jest wstępnie wypełniony kolorem (przezroczyste) ekranu. Jeśli obraz jest kursora, punkt aktywny jest początkowo lewym górnym rogu (współrzędne 0,0).  
  
 Domyślnie edytor obrazów obsługuje tworzenie obrazów dodatkowych urządzeń pokazano w poniższej tabeli. Można utworzyć obrazy w przypadku innych urządzeń, wpisując parametrów szerokości, wysokości i liczba kolorów w [okno dialogowe obrazu niestandardowego](custom-image-dialog-box-image-editor-for-icons.md).  
  
> [!NOTE]
>  Korzystając z edytora obrazów, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.  
  
|Kolor|Szerokość (w pikselach)|Wysokość (w pikselach)|  
|-----------|----------------------|-----------------------|  
|W skali odcieni szarości|16|16|  
|W skali odcieni szarości|32|32|  
|W skali odcieni szarości|48|48|  
|W skali odcieni szarości|64|64|  
|W skali odcieni szarości|96|96|  
|16|16|16|  
|16|32|32|  
|16|64|64|  
|16|48|48|  
|16|96|96|  
|256|16|16|  
|256|32|32|  
|256|48|48|  
|256|64|64|  
|256|96|96|  
  
-   [Tworzenie nowego obrazu urządzenia (ikony lub kursora)](../windows/creating-a-device-image-image-editor-for-icons.md)  
  
-   [Dodawanie obrazu dla innego ekranu urządzenia](../windows/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)  
  
-   [Kopiowanie obrazu urządzenia](../windows/copying-a-device-image-image-editor-for-icons.md)  
  
-   [Usuwanie obrazu urządzenia](../windows/deleting-a-device-image-image-editor-for-icons.md)  
  
-   [Tworzenie obszarów przezroczystych lub odwróconych w obrazach urządzeń](../windows/creating-transparent-or-inverse-regions-in-device-images.md)  
  
-   [Tworzenie ikony 256 kolorów](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
  
-   [Ustawianie aktywnego punktu kursora](../windows/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)   
 [Ikony](http://msdn.microsoft.com/library/windows/desktop/ms646973)   
 [Kursory](http://msdn.microsoft.com/library/windows/desktop/ms646970)

