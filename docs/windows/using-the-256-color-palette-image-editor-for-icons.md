---
title: Korzystanie z palety 256 kolorów (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 256-color palette
- colors [C++], icons and cursors
- cursors [C++], color
- color palettes, 256-color
- palettes, 256-color
- icons, color
ms.assetid: 1506ed00-669b-4a21-b1a4-39b6a84a78bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9a8952ccdf4477f263a2fb960020e7abba19546
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418154"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>Korzystanie z palety 256 kolorów (Edytor obrazów dla ikon)

Aby narysować przy zaznaczeniem z palety 256 kolorów, musisz wybrać kolory z **kolory** palety w [okno kolorów](../windows/colors-window-image-editor-for-icons.md).

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Aby wybrać kolor z palety 256 kolorów dla dużych ikon

1. Wybierz kursor lub duże ikony, lub Utwórz nową ikonę dużych lub kursor.

2. Wybierz kolor z 256 kolorów, które są wyświetlane w **kolory** palety w **kolory** okna.

   Kolor wybrany staną się bieżący kolor w **kolory** palety w **kolory** okna.

   > [!NOTE]
   > Pasuje do początkowej palety 256 kolorów obrazów palety zwracany przez `CreateHalftonePalette` interfejsu Windows API. Wszystkie ikony przeznaczone dla powłoki Windows należy używać tej palety, aby zapobiec migotania podczas realizacji palety.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Tworzenie ikony 256 kolorów](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)<br/>
[Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)