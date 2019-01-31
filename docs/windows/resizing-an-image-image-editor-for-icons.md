---
title: Zmiana rozmiaru obrazu (Edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
ms.openlocfilehash: d88a4cccff5b9b7b6303329782b7367cb953b13d
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484971"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Zmiana rozmiaru obrazu (Edytor obrazów dla ikon)

Zachowanie **obraz** edytora podczas zmiany rozmiaru obrazu zależy od tego, czy masz [wybranego](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) całego obrazu lub jego część.

Jeśli zaznaczenie obejmuje tylko część obrazu, **obraz** edytora zmniejsza zaznaczenie przy usuwaniu wierszy lub kolumn pikseli i wypełniania opuszczonych regionów z bieżącym kolorem tła. Można również rozciągać zaznaczenie zduplikowane wiersze lub kolumny w pikselach.

Jeśli zaznaczenie obejmuje cały obraz **obraz** edytora albo zmniejsza rozciąga obrazu, lub przycina i rozszerza je.

Istnieją dwa mechanizmy do zmiany rozmiaru obrazu: uchwytów zmiany rozmiaru i [okno właściwości](/visualstudio/ide/reference/properties-window). Przeciągnij uchwyty zmiany rozmiaru, aby zmienić rozmiar wszystkich lub część obrazu. Uchwyty zmiany rozmiaru, które można przeciągać są wypełnione. Nie można przeciągnąć uchwyty, które są puste. Użyj **właściwości** okna, aby zmienić rozmiar całego tylko obraz nie jest częścią wybrane.

![Uchwytów na mapę bitową](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Uchwyty zmiany rozmiaru

> [!NOTE]
> Jeśli masz **Kafelek siatki** opcji wybranej w [okno dialogowe Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md), następnie zmiany rozmiaru przyciąganie do następnego wiersza siatki kafelka. Jeśli tylko **siatkę pikseli** opcja jest zaznaczone (ustawienie domyślne), zmiana rozmiaru przyciąganie do następnego dostępne pikseli.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-resize-an-entire-image-using-the-properties-window"></a>Zmiana rozmiaru całego obrazu w oknie właściwości

1. Otwórz obraz, którego właściwości chcesz zmienić.

1. W **szerokość** i **wysokość** pola [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz wymiary, które mają.

   Jeśli masz zwiększenie rozmiaru obrazu, **obraz** edytora rozszerza obraz w prawo, dół, i / lub i wypełnia nowego regionu z bieżącym kolorem tła. Obraz, który nie jest rozciągana.

   Jeśli skrócić rozmiar obrazu, **obraz** edytora Przycina obraz w prawo lub dolnej krawędzi i / lub.

   > [!NOTE]
   > Możesz użyć **szerokość** i **wysokość** właściwości, aby zmienić rozmiar tylko całego obrazu, nie można zmienić rozmiar częściowy wybór.

## <a name="to-crop-or-extend-an-entire-image"></a>Przycinanie lub rozszerzanie całego obrazu

1. Wybierz obraz.

   Jeśli część obrazu jest aktualnie zaznaczona, a chcesz wybrać całego obrazu, wybierz dowolne miejsce dla obrazu spoza bieżącego zaznaczenia.

1. Przeciągnij uchwyt zmiany rozmiaru, do momentu zilustrowano wielkości.

Zwykle **obraz** edytora Przycina lub powiększenie obrazu przy zmianie rozmiaru przez przeniesienie uchwyt zmiany rozmiaru. Przytrzymanie **Shift** kluczy po przeniesieniu uchwyt zmiany rozmiaru **obraz** edytora zmniejsza lub obraz jest rozciągany tak.

## <a name="to-shrink-or-stretch-an-entire-image"></a>Aby zmniejszanie i rozciąganie całego obrazu

1. Wybierz obraz.

   Jeśli chcesz wybrać całego obrazu część obrazu jest aktualnie zaznaczona, wybierz dowolne miejsce dla obrazu spoza bieżącego zaznaczenia.

1. Naciśnij i przytrzymaj **Shift** klucza, a następnie przeciągnij uchwyt zmiany rozmiaru, do momentu zilustrowano wielkości.

## <a name="to-shrink-or-stretch-part-of-an-image"></a>Aby zmniejszanie i rozciąganie części obrazu

1. Wybierz część obrazu, który chcesz zmienić. Aby uzyskać więcej informacji, zobacz [Zaznaczanie obszaru obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Przeciągnij jeden z uchwytów zmiany rozmiaru, dopóki nie obowiązuje wielkości.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)