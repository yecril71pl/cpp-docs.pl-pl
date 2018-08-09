---
title: Tworzenie obrazu urządzenia (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
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
- icons [C++], creating
- display devices
- display devices, creating image
- images [C++], creating for display devices
- icons [C++], inserting
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bbdc52cca73d568cb365deb345ec6465488e3b40
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641346"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Tworzenie obrazu urządzenia (Edytor obrazów dla ikon)
Podczas tworzenia nowej ikony lub zasobu kursora **obraz** edytora najpierw tworzy obraz w określonym stylu (32 x 32, 16 kolorów dla ikony oraz 32 × 32, monochromatyczny liczby kursorów). Można dodać obrazy w różnych rozmiarach i style do początkowego ikony lub kursor i edytowania każdego dodatkowego obrazu zgodnie z potrzebami dla różnych ekranów. Można również edytować obraz, za pomocą operacji kopiowania i wklejania z istniejącego typu obrazu lub mapy bitowej utworzonej w programie graficznym.  
  
 Po otwarciu ikony zasobu w [edytora obrazów](../windows/image-editor-for-icons.md), obraz, większość ściśle dopasowując bieżące urządzenie wyświetlające jest domyślnie otwierany.  
  
### <a name="to-create-a-new-icon-or-cursor"></a>Aby utworzyć nową ikonę lub kursora  
  
1.  W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasobów** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, użytkownik może po prostu kliknij prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz opcję **ikonę** lub **kursora** i kliknij przycisk **New**. Dla ikon spowoduje to utworzenie zasobu ikony z 32 x 32, ikona 16 kolorów. Dla kursorów, 32 x 32, tworzony jest monochromatyczny obrazu (w kolorze 2).  
  
     Jeśli znak plus (**+**) pojawia się obok typ zasobu obrazu w **Wstaw zasobów** okno dialogowe, oznacza to, narzędzi szablony są dostępne. Kliknij znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie kliknij przycisk **New**.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)