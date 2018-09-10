---
title: Praca z kolorem (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 200c71b6d2196251c8db3542b2b1b2ce88fdff85
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315538"
---
# <a name="working-with-color-image-editor-for-icons"></a>Praca z kolorem (Edytor obrazów dla ikon)

**Edytora obrazów** zawiera wiele funkcji, które w szczególności obsługiwać i dostosowywanie kolorów. Można ustawić kolor pierwszego planu i tła, wypełnij obszary ograniczonego kolorem lub wybierz kolor obrazu do użycia jako bieżący kolor pierwszego planu i tła. Możesz użyć narzędzi na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) wraz z palety kolorów w [okno kolorów](../windows/colors-window-image-editor-for-icons.md) do tworzenia obrazów.

Wszystkie kolory monochromatyczny i 16 kolorów obrazów są wyświetlane w **kolory** palety w **kolory** okna. Oprócz 16 kolory standardowe można utworzyć własne niestandardowe kolory. Dowolne kolory z palety natychmiast zmiana będzie odpowiedni kolor na obrazie.

Podczas pracy z ikony 256 kolorów i obrazy kursora **kolory** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window) jest używany. Aby uzyskać więcej informacji, zobacz [Tworzenie ikony 256 kolorów](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).

> [!NOTE]
> Za pomocą **edytora obrazów**, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.

Można również tworzyć obrazy True color. Jednak true koloru próbek nie są wyświetlane w palecie pełnego w **kolory** okna; pojawiają się tylko w obszarze wskaźnik kolor pierwszego planu i tła. Wartość true, kolory są tworzone przy użyciu [okno dialogowe selektora kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Aby uzyskać więcej informacji, zobacz [Dostosowywanie lub zmiana kolorów](../windows/customizing-or-changing-colors-image-editor-for-icons.md).

Można zapisać palety kolorów niestandardowych na dysku i ponownie załaduj je stosownie do potrzeb. Palety kolorów, ostatnio używane jest zapisywane w rejestrze i ładowane automatycznie przy następnym uruchomieniu programu Visual Studio.

- [Ustawianie pierwszego planu lub kolorów tła](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)

- [Wypełnianie ograniczonego obszaru obrazu za pomocą koloru](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)

- [Pobieranie koloru z obrazu do użycia w innym miejscu](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)

- [Wybieranie tła przezroczystego lub nieprzezroczystego](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)

- [Odwracanie kolorów w wyborze](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)

- [Dostosowywanie lub zmiana kolorów](../windows/customizing-or-changing-colors-image-editor-for-icons.md)

- [Zapisywanie i ładowanie różnych palet kolorów](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)

- [Okno kolory](../windows/colors-window-image-editor-for-icons.md)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)  