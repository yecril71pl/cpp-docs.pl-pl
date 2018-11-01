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
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
ms.openlocfilehash: 721a8f1de511c105df5d72bbe60685d210ad5a94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576101"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Zmiana rozmiaru obrazu (Edytor obrazów dla ikon)

Zachowanie **obraz** edytora podczas zmiany rozmiaru obrazu zależy od tego, czy masz [wybranego](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) całego obrazu lub jego część.

Jeśli zaznaczenie obejmuje tylko część obrazu, **obraz** edytora zmniejsza zaznaczenie przy usuwaniu wierszy lub kolumn pikseli i wypełniania opuszczonych regionów z bieżącym kolorem tła, lub jego rozciąga zaznaczenie o zduplikowane wiersze lub kolumny w pikselach.

Jeśli zaznaczenie obejmuje cały obraz **obraz** edytora albo zmniejsza rozciąga obrazu, lub przycina i rozszerza je.

Istnieją dwa mechanizmy do zmiany rozmiaru obrazu: uchwytów zmiany rozmiaru i [okno właściwości](/visualstudio/ide/reference/properties-window). Można przeciągnąć uchwyty zmiany rozmiaru, aby zmienić rozmiar wszystkich lub część obrazu. Uchwyty zmiany rozmiaru, które można przeciągać są wypełnione. Nie można przeciągnąć uchwyty, które są puste. Możesz użyć **właściwości** okna, aby zmienić rozmiar całego tylko obraz nie jest częścią wybrane.

![Uchwytów na mapę bitową](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Uchwyty zmiany rozmiaru

> [!NOTE]
> Jeśli masz **Kafelek siatki** opcji wybranej w [okno dialogowe Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md), następnie zmiany rozmiaru przyciąganie do następnego wiersza siatki kafelka. Jeśli tylko **siatkę pikseli** opcja jest zaznaczone (ustawienie domyślne), zmiana rozmiaru przyciąganie do następnego dostępne pikseli.

- [Zmiana rozmiaru całego obrazu](../windows/resizing-an-entire-image-image-editor-for-icons.md)

- [Przycinanie i rozszerzanie całego obrazu](cropping-or-extending-an-entire-image-image-editor-for-icons.md)

- [Zmniejszanie i rozciąganie całego obrazu](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)

- [Zmniejszanie i rozciąganie części obrazu](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)