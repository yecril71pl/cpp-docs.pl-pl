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
ms.openlocfilehash: 9b90337b48c46d335bfccf405b2ba7e0628b9f99
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209495"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons"></a>Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach (Edytor obrazów dla ikon)

Ikony i kursory są zasobów graficznych, które zawiera wiele obrazów o różnych wielkościach i schematów kolorów dla różnych rodzajów wyświetlania na urządzeniach. Ponadto kursor ma "punkt aktywny," w lokalizacji Windows używa do śledzenia jego położenie. Ikony i kursory są tworzone oraz edytowane za pomocą **obraz** edytora, jak mapy bitowe i inne obrazy.

Po utworzeniu kursor, lub Nowa ikona **obraz** edytora najpierw tworzy obraz standardowego typu. Obraz, który początkowo jest wypełniony kolorem ekranu (przezroczyste). Jeśli obraz kursora, punkt aktywny jest początkowo lewego górnego rogu (współrzędne 0,0).

Domyślnie **obraz** Edytor obsługuje tworzenie dodatkowych obrazów dla urządzeń z poniższą tabelą. Można utworzyć obrazy w przypadku innych urządzeń, wpisując parametrów szerokości, wysokości i liczba kolorów w [okno dialogowe obrazu niestandardowego](custom-image-dialog-box-image-editor-for-icons.md).

> [!NOTE]
> Za pomocą **edytora obrazów**, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.

|Kolor|Szerokość (w pikselach)|Wysokość (w pikselach)|
|-----------|----------------------|-----------------------|
|Monochromatyczny|16|16|
|Monochromatyczny|32|32|
|Monochromatyczny|48|48|
|Monochromatyczny|64|64|
|Monochromatyczny|96|96|
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

- [Tworzenie nowego obrazu urządzenia (kursor lub ikonę)](../windows/creating-a-device-image-image-editor-for-icons.md)

- [Dodawanie obrazu wyświetlania na różnych urządzeniach](../windows/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)

- [Kopiowanie obrazu urządzenia](../windows/copying-a-device-image-image-editor-for-icons.md)

- [Usuwanie obrazu urządzenia](../windows/deleting-a-device-image-image-editor-for-icons.md)

- [Tworzenie obszarów przezroczystych lub odwróconych w obrazach urządzeń](../windows/creating-transparent-or-inverse-regions-in-device-images.md)

- [Tworzenie ikony 256 kolorów](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)

- [Ustawianie aktywnego punktu kursora](../windows/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)  
[Ikony](https://msdn.microsoft.com/library/windows/desktop/ms646973)  
[Kursory](https://msdn.microsoft.com/library/windows/desktop/ms646970)