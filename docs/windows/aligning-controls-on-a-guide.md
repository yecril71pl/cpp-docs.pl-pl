---
title: Dopasowanie kontrolek do prowadnicy
ms.date: 11/04/2016
helpviewer_keywords:
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
ms.openlocfilehash: 182cae288f4882611ec3d535357b93bf6d6ea9c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491094"
---
# <a name="aligning-controls-on-a-guide"></a>Dopasowanie kontrolek do prowadnicy

Uchwyty zmiany rozmiaru kontrolek przyciąganie do prowadnic formanty są przenoszone, gdy przewodniki przyciąganie do kontrolek (Jeśli nie ma żadnych formantów wcześniej przypięty do przewodnika). Po przeniesieniu przewodnik również przenieść formantów, które są wyrównywane do niego. Formanty wyrównywane do więcej niż jeden podręcznik zmieniany jest rozmiar po przeniesieniu jeden z przewodników.

Znaczniki w linijki, określające odstępów przewodniki i formanty są definiowane przez jednostki okna dialogowego (Dlu). DLU opiera się na rozmiar czcionki okno dialogowe, zwykle 8-punktowy MS Shell Dlg. Poziomy DLU jest średniej szerokości czcionki okno dialogowe podzielona przez cztery. DLU pionowe jest średnią wysokość czcionki podzielić przez 8.

### <a name="to-size-a-group-of-controls-with-guides"></a>Rozmiar grupy formantów z liniami

1. Przyciągaj obok kontrolki (lub formantów) do przewodnika.

2. Przeciągnij przewodnika po drugiej stronie kontrolki (lub kontrolki).

   Jeśli to konieczne z wieloma formantami, rozmiar każdego przyciągane do prowadnicy drugiego.

3. Przenieś albo przewodnika, aby rozmiar kontrolki (lub kontrolki).

### <a name="to-change-the-intervals-of-the-tick-marks"></a>Aby zmienić interwałów znaczników

1. Z **Format** menu, wybierz **ustawienia prowadnic**.

2. W [okno dialogowe Ustawienia prowadnic](../windows/guide-settings-dialog-box.md)w **odstępy między liniami siatki** określ nową wysokość i szerokość w Dlu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Stany dla Edytora okien dialogowych (prowadnice i siatki)](../windows/dialog-editor-states-guides-and-grids.md)<br/>
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)