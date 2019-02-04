---
title: Konwertowanie map bitowych na paski narzędzi (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
ms.openlocfilehash: 31b684ff72e970a6b09748b3925564b0b372d339
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702703"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>Konwertowanie map bitowych na paski narzędzi (C++)

Aby utworzyć nowy pasek narzędzi w projektu w języku C++, konwertowania mapy bitowej. Konwertuje grafiki z mapy bitowej obrazy przycisków na pasku narzędzi. Zazwyczaj mapy bitowej zawiera kilka obrazów przycisku w postaci bitmapy z jednego obrazu dla każdego przycisku. Obrazy mogą być dowolnego rozmiaru; Wartość domyślna to 16 pikseli szerokości i wysokości obrazu. Można określić rozmiar obrazów przycisku w **nowy zasób paska narzędzi** okno dialogowe, w przypadku wybrania **Edytor paska narzędzi** z **obraz** menu znajduje się w edytorze obrazu.

**Nowy zasób paska narzędzi** okno dialogowe umożliwia określenie szerokości i wysokości przyciski dodawania zasobu paska narzędzi w projekcie C++. Wartość domyślna to 16 x 15 pikseli.

Mapa bitowa, który jest używany do tworzenia paska narzędzi ma maksymalną szerokość 2048. Jeśli ustawisz **szerokość przycisku** do 512, możesz mieć tylko cztery przyciski. Ustaw szerokość 513, może mieć tylko trzy przyciski.

Okno dialogowe ma następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Szerokość przycisku.**|Miejsce na wprowadź szerokość przycisków paska narzędzi, które konwertowania zasób mapy bitowej do zasobu paska narzędzi. Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane by wykorzystywały standardowe kolory paska narzędzi (16 kolorów).|
|**Wysokość przycisku**|Miejsce na Wprowadź wysokość przycisków paska narzędzi, które konwertowania zasób mapy bitowej do zasobu paska narzędzi. Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane by wykorzystywały standardowe kolory paska narzędzi (16 kolorów).|

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-convert-bitmaps-to-a-toolbar"></a>Aby przekonwertować map bitowych paska narzędzi

1. Otwórz istniejący zasób mapy bitowej w [edytora obrazów](../windows/image-editor-for-icons.md). (Jeśli mapa bitowa nie jest już w pliku .rc, kliknij prawym przyciskiem myszy plik .rc, wybierz polecenie **importu** z menu skrótów, przejdź do mapy bitowej, które chcesz dodać do pliku .rc, a następnie wybierz **Otwórz**.)

1. Z **obraz** menu, wybierz **Edytor paska narzędzi**.

   **Nowy zasób paska narzędzi** pojawi się okno dialogowe. Można zmienić szerokość i wysokość obrazy ikon, aby dopasować mapę bitową. Obraz paska narzędzi są następnie wyświetlane na pasku narzędzi edytora.

1. Aby zakończyć konwersję, zmień polecenie **identyfikator** za pomocą przycisku [okno właściwości](/visualstudio/ide/reference/properties-window). Wpisz nowy **identyfikator** lub wybierz **identyfikator** z listy rozwijanej.

   > [!TIP]
   > **Właściwości** okno zawiera przycisk pinezki na pasku tytułu. Wybranie tego przycisku Włącza lub wyłącza **Autoukrywanie** okna. Aby szybko przechodzić przez wszystkie właściwości przycisku paska narzędzi bez konieczności ponownie otworzyć windows pojedynczej właściwości, należy wyłączyć **Autoukrywanie** wyłączyć tak **właściwości** okna pozostaje stacjonarnych.

Możesz również zmienić identyfikatory poleceń przyciski na nowy pasek narzędzi, za pomocą [okno właściwości](/visualstudio/ide/reference/properties-window). Aby uzyskać informacje na temat edytowania nowy pasek narzędzi, zobacz [tworzenie, przenoszenie i edytowanie przycisków paska narzędzi](../windows/creating-moving-and-editing-toolbar-buttons.md).

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Tworzenie nowych pasków narzędzi](../windows/creating-new-toolbars.md)<br/>
[Edytor paska narzędzi](../windows/toolbar-editor.md)<br/>
[Właściwości przycisku paska narzędzi](../windows/toolbar-button-properties.md)<br/>
