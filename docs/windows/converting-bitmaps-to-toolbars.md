---
title: Konwertowanie map bitowych na paski narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor, converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e80bee7ef9bfe52abf63ac959475c5d8dbcf0ece
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872630"
---
# <a name="converting-bitmaps-to-toolbars"></a>Konwertowanie map bitowych na paski narzędzi
Konwertowanie map bitowych można utworzyć nowego paska narzędzi. Grafika z mapy bitowej konwertuje obrazy dla przycisków paska narzędzi. Zazwyczaj mapy bitowej zawiera kilka obrazów przycisk na jednym mapy bitowej, za pomocą jednego obrazu dla każdego przycisku. Obrazy może być dowolnym rozmiarze; Wartość domyślna to 16 pikseli szerokości i wysokości obrazu. Można określić rozmiaru obrazy dla przycisków w [okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md) po wybraniu Edytor paska narzędzi z **obrazu** menu znajduje się w edytorze obrazów.  
  
### <a name="to-convert-bitmaps-to-a-toolbar"></a>Aby przekonwertować bitmap do paska narzędzi  
  
1.  Otwórz istniejący zasób mapy bitowej w [edytor obrazów](../windows/image-editor-for-icons.md). (Jeśli mapy bitowej nie jest już w pliku .rc, kliknij prawym przyciskiem myszy plik .rc, wybierz **importu** z menu skrótów, przejdź do mapy bitowej, które chcesz dodać do pliku .rc, a następnie kliknij przycisk **Otwórz**.)  
  
2.  Z **obrazu** menu, wybierz **paska narzędzi edytora**.  
  
     [Okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md) pojawi się. Można zmienić szerokość i wysokość obrazów ikony do dopasowania mapy bitowej. Obraz paska narzędzi jest wyświetlone w edytorze paska narzędzi.  
  
3.  Aby zakończyć konwersję, zmienić polecenie **identyfikator** użycia przycisk [okna właściwości](/visualstudio/ide/reference/properties-window). Wpisz nowy **identyfikator** lub wybierz **identyfikator** z listy rozwijanej.  
  
    > [!TIP]
    >  Okno właściwości zawiera przycisk pinezki na pasku tytułu. Kliknięcie tego przycisku Włącza lub wyłącza automatyczne ukrywanie okna. Aby szybko przejść przez wszystkie właściwości przycisku paska narzędzi bez konieczności ponownie poszczególnych właściwości systemu windows, wyłącz automatyczne ukrywanie tak w oknie właściwości pozostaje nieruchomy.  
  
 Identyfikatory poleceń przycisków na pasku narzędzi nowej można również zmienić przy użyciu [okna właściwości](/visualstudio/ide/reference/properties-window). Informacje dotyczące nowych narzędzi edycji znajdują się w temacie [tworzenie, przenoszenie i edytowanie przycisków paska narzędzi](../windows/creating-moving-and-editing-toolbar-buttons.md).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 MFC i ATL  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie nowych pasków narzędzi](../windows/creating-new-toolbars.md)   
 [Edytor paska narzędzi](../windows/toolbar-editor.md)

