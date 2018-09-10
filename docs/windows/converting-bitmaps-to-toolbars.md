---
title: Konwertowanie map bitowych na paski narzędzi (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed77f1df88bb3f3572c3ea819ffac5cb9a1f45b1
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317232"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>Konwertowanie map bitowych na paski narzędzi (C++)

Aby utworzyć nowy pasek narzędzi w projektu w języku C++, konwertowania mapy bitowej. Konwertuje grafiki z mapy bitowej obrazy przycisków na pasku narzędzi. Zazwyczaj mapy bitowej zawiera kilka obrazów przycisku w postaci bitmapy z jednego obrazu dla każdego przycisku. Obrazy mogą być dowolnego rozmiaru; Wartość domyślna to 16 pikseli szerokości i wysokości obrazu. Można określić rozmiar obrazów przycisku w [okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md) po wybraniu **Edytor paska narzędzi** z **obraz** menu znajduje się w edytorze obrazu.

### <a name="to-convert-bitmaps-to-a-toolbar"></a>Aby przekonwertować map bitowych paska narzędzi

1. Otwórz istniejący zasób mapy bitowej w [edytora obrazów](../windows/image-editor-for-icons.md). (Jeśli mapa bitowa nie jest już w pliku .rc, kliknij prawym przyciskiem myszy plik .rc, wybierz polecenie **importu** z menu skrótów, przejdź do mapy bitowej, które chcesz dodać do pliku .rc, a następnie kliknij przycisk **Otwórz**.)

2. Z **obraz** menu, wybierz **Edytor paska narzędzi**.

   [Okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md) pojawia się. Można zmienić szerokość i wysokość obrazy ikon, aby dopasować mapę bitową. Obraz paska narzędzi są następnie wyświetlane na pasku narzędzi edytora.

3. Aby zakończyć konwersję, zmień polecenie **identyfikator** za pomocą przycisku [okno właściwości](/visualstudio/ide/reference/properties-window). Wpisz nowy **identyfikator** lub wybierz **identyfikator** z listy rozwijanej.

   > [!TIP]
   > **Właściwości** okno zawiera przycisk pinezki na pasku tytułu. Kliknięcie tego przycisku Włącza lub wyłącza **Autoukrywanie** okna. Aby szybko przechodzić przez wszystkie właściwości przycisku paska narzędzi bez konieczności ponownie otworzyć windows pojedynczej właściwości, należy wyłączyć **Autoukrywanie** wyłączyć tak **właściwości** okna pozostaje stacjonarnych.

Możesz również zmienić identyfikatory poleceń przyciski na nowy pasek narzędzi, za pomocą [okno właściwości](/visualstudio/ide/reference/properties-window). Aby uzyskać informacje na temat edytowania nowy pasek narzędzi, zobacz [tworzenie, przenoszenie i edytowanie przycisków paska narzędzi](../windows/creating-moving-and-editing-toolbar-buttons.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Tworzenie nowych pasków narzędzi](../windows/creating-new-toolbars.md)  
[Edytor paska narzędzi](../windows/toolbar-editor.md)