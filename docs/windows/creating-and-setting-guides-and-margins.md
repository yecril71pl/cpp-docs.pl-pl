---
title: Tworzenie i Ustawianie prowadnic i marży | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- guides, clearing
- guides
- Dialog Editor [C++], guides and margins
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
ms.assetid: fafa4545-8f00-436f-b590-300e76601156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0083affb850f35941ca18709785c9bd5e4fc35e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378257"
---
# <a name="creating-and-setting-guides-and-margins"></a>Tworzenie i ustawianie prowadnic i marginesów

Czy przenosisz się formantów, dodawanie formantów, rozmieszczanie bieżący układ, przewodniki może pomóc można wyrównać formanty dokładnie w oknie dialogowym. Przewodniki są wyświetlane jako niebieskie linie dotted przez okno dialogowe wyświetlany w edytorze i odpowiednie strzałki w linijek (w górnej i lewej strony **okna dialogowego** edytora).

Kiedy tworzysz okno dialogowe, znajdują się cztery marginesy. Marginesy są przewodniki zmodyfikowane, pojawiają się jako niebieskie linie dotted.

### <a name="to-create-a-guide"></a>Aby utworzyć linię

1. Na linijce kliknij raz, aby utworzyć linię. (Jednym kliknięciem tworzy nowy przewodnik; dwukrotne kliknięcie powoduje uruchomienie [okno dialogowe Ustawienia prowadnic](../windows/guide-settings-dialog-box.md) określić ustawienia prowadnic.)

### <a name="to-set-a-guide"></a>Aby ustawić przewodnik

1. W oknie dialogowym kliknij przewodnika, a następnie przeciągnij go do nowej pozycji. (Możesz również kliknij strzałkę w linijkę, aby przeciągnąć skojarzonego przewodnika).

   Współrzędne przewodnika są wyświetlane na pasku stanu w dolnej części okna i linijki. Przesuń wskaźnik nad strzałką znajdującą się w linijkę, aby wyświetlić dokładnego położenia przewodnika.

### <a name="to-delete-a-guide"></a>Aby usunąć prowadnicę

1. Przeciągnij ją z okna dialogowego.

\- lub —

- Przeciągnij odpowiednie strzałkę z linijki.

### <a name="to-move-margins"></a>Aby przenieść marginesów

1. Przeciągnij margines do nowej pozycji.

   Aby margines zniknąć, należy przenieść margines do pozycji zero. Aby przywrócić margines, umieść wskaźnik na marginesie pozycji zero i przenieść margines w określonej pozycji.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Stany dla Edytora okien dialogowych (prowadnice i siatki)](../windows/dialog-editor-states-guides-and-grids.md)<br/>
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)