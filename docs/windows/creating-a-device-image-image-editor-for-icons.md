---
title: "Tworzenie obrazu urządzenia (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d68a9d35471e43296cade829700fc6c5b311ce2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Tworzenie obrazu urządzenia (Edytor obrazów dla ikon)
Podczas tworzenia nowego zasobu ikony, obraz edytora najpierw tworzy obraz w określonym stylu (32 x 32, 16 kolorów dla ikony oraz 32 × 32 dla kursory w skali odcieni szarości). Można dodać obrazy w różnych rozmiarach i style do początkowej ikony lub kursor i edytować każdy dodatkowego obrazu w razie potrzeby dla różnych ekranów. Można również edytować obrazu za pomocą operacji kopiowania i wklejania z istniejącym typem obrazu lub mapy bitowej utworzonej w programie grafiki.  
  
 Po otwarciu zasobu ikony w [edytor obrazów](../windows/image-editor-for-icons.md), większość ściśle dopasowania bieżące urządzenie wyświetlające jest domyślnie otwierany obrazu.  
  
### <a name="to-create-a-new-icon-or-cursor"></a>Aby utworzyć nową ikonę lub kursora  
  
1.  W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasób** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, użytkownik może po prostu kliknij prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz pozycję **ikona** lub **kursora** i kliknij przycisk **nowy**. Ikony spowoduje to utworzenie zasobu ikony z 32 × 32, ikona 16 kolorów. Dla kursorów, 32 × 32, tworzony jest monochromatyczny obrazu (w kolorze 2).  
  
     Jeśli znak plus (**+**) widoczna obok typ zasobu obrazu w **Wstaw zasób** okno dialogowe, oznacza to, że szablony narzędzi są dostępne. Kliknij znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie kliknij przycisk **nowy**.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Wymagania**  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
