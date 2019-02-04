---
title: Korzystanie z palety 256 kolorów (Edytor obrazów dla ikon)
ms.date: 11/04/2016
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
ms.openlocfilehash: 4e2f2c9ce58799756137bb47db42e52c97a43d39
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702898"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>Korzystanie z palety 256 kolorów (Edytor obrazów dla ikon)

Za pomocą **obraz** edytora, ikon i kursorów można wielkości dużych (64 × 64) z palety 256 kolorów do wyboru. Po utworzeniu zasobu stylu obrazu urządzenia jest zaznaczone.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-256-color-icon-or-cursor"></a>Tworzenie ikony 256 kolorów lub kursora

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasobów** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, możesz kliknąć prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz opcję **ikonę** lub **kursora** i wybierz polecenie **New**.

1. Na **obraz** menu, wybierz opcję **nowy obraz urządzenia**.

1. Wybierz żądany styl obrazu 256 kolorów.

## <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Aby wybrać kolor z palety 256 kolorów dla dużych ikon

Aby narysować przy zaznaczeniem z palety 256 kolorów, musisz wybrać kolory z **kolory** palety w [okno kolorów](../windows/colors-window-image-editor-for-icons.md).

1. Wybierz kursor lub duże ikony, lub Utwórz nową ikonę dużych lub kursor.

1. Wybierz kolor z 256 kolorów, które są wyświetlane w **kolory** palety w **kolory** okna.

   Kolor wybrany staną się bieżący kolor w **kolory** palety w **kolory** okna.

   > [!NOTE]
   > Pasuje do początkowej palety 256 kolorów obrazów palety zwracany przez `CreateHalftonePalette` interfejsu Windows API. Wszystkie ikony przeznaczone dla powłoki Windows należy używać tej palety, aby zapobiec migotania podczas realizacji palety.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Ikony i kursory: Zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
