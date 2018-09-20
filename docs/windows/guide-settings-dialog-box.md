---
title: Przewodnik dotyczący ustawienia, okno dialogowe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLUs (dialog units)
- Dialog Editor [C++], snap to guides
- grid spacing
- guides, settings
- dialog units (DLUs)
- layout grid in Dialog Editor
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9ebc7828916b0c5809563a8f1e153d5e59a1ad7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382030"
---
# <a name="guide-settings-dialog-box-c"></a>Okno dialogowe Ustawienia prowadnic (C++)

## <a name="layout-guides"></a>Układ prowadnic

Wyświetla ustawienia prowadnic układu.

### <a name="none"></a>Brak

Ukrywa narzędzia układu.

### <a name="rulers-and-guides"></a>Linijki i prowadnice

Po włączeniu narzędzia układ; dodaje linijki linie pomocnicze można umieścić w linijki. Przewodniki domyślne są marginesy, które można przenosić, przeciągając. Kliknij linijki umieścić przewodnik. Formanty "przyciągana" do przewodników po przeniesieniu kontroli nad lub obok nich. Formanty również przechodzić z przewodnikiem po podłączeniu do niego. Formant jest dołączony do przewodnika po każdej stronie, gdy wskazówki są przenoszone, zmieni się rozmiar kontrolki.

### <a name="grid"></a>Siatka

Tworzy siatki układu. Nowe kontrolki automatycznie zostaną wyrównane do siatki.

## <a name="grid-spacing"></a>Odstępy między liniami siatki

Wyświetla ustawienia odstępy między liniami siatki w jednostkach pola okna dialogowego (Dlu).

### <a name="width-dlus"></a>Szerokość: Dlu

Ustawia szerokość siatki układu w Dlu. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez cztery.

### <a name="height-dlus"></a>Wysokość: Dlu

Określa wysokość siatki układu w Dlu. DLU pionowe jest średnią wysokość czcionka pola okna dialogowego podzielić przez 8.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Modyfikowanie siatki układu](../windows/modifying-the-layout-grid.md)<br/>
[Stany dla Edytora okien dialogowych (prowadnice i siatki)](../windows/dialog-editor-states-guides-and-grids.md)