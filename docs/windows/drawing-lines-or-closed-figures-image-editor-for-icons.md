---
title: Linie rysunku lub zamkniętych figur (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- closed figures, drawing
- lines [C++], painting
- lines [C++], drawing
- Image editor [C++], drawing lines
- shapes, drawing
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d1eba17d961db9ec96e4250e49c10ecad5b75b4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590733"
---
# <a name="drawing-lines-or-closed-figures-image-editor-for-icons"></a>Linie rysunku lub zamkniętych figur (Edytor obrazów dla ikon)

Edytor obrazów narzędzi do rysowania linii i zamkniętych figur wszystkie działają tak samo jak: Umieść punkt wstawiania w jednym punkcie i przeciągnij pola do innego. W przypadku wierszy te punkty są punkty końcowe. W przypadku zamkniętych figur te punkty są przeciwny narożników prostokąta blokujących na rysunku.

Wiersze są rysowane w szerokości ustalany na podstawie bieżącego zaznaczenia pędzla, a ramce rysunki są rysowane w szerokości ustalany na podstawie bieżącego zaznaczenia szerokość. Linie i wszystkie dane, zarówno w ramce, jak i wypełnione, są rysowane w bieżącym kolorem po naciśnięciu lewego przycisku myszy, lub w bieżącym kolorem tła po naciśnięciu prawego przycisku myszy.

### <a name="to-draw-a-line"></a>Aby narysować linię

1. Na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) (lub **obraz** menu **narzędzia** polecenie), kliknij przycisk **wiersza** narzędzia.

2. Jeśli to konieczne, wybierz kolory i pędzla:

   - W [paleta kolorów](../windows/colors-window-image-editor-for-icons.md), kliknij przycisk myszy po lewej stronie, aby wybrać kolor pierwszego planu lub prawego przycisku myszy, aby zmienić kolor tła.

   - W [Selektor opcji](../windows/toolbar-image-editor-for-icons.md), kliknij kształt reprezentujący pędzla, którego chcesz użyć.

3. Umieść wskaźnik myszy na punkt początkowy dla wiersza.

4. Przeciągnij do endpoint dla wiersza.

### <a name="to-draw-a-closed-figure"></a>Aby narysować figurę zamkniętą

1. Na **edytora obrazów** narzędzi (lub z **obrazu** menu **narzędzia** polecenie), kliknij przycisk **rysunek rysunek zamknięte** narzędzia.

   **Rysunek rysunek zamknięte** narzędzia Tworzenie figur zgodnie z informacjami zawartymi w ich odpowiednich przycisków.

2. Jeśli to konieczne, zaznacz kolorów i szerokości linii.

3. Przesuń wskaźnik do jednego rogu prostokątny obszar, w którym chcesz rysować na rysunku.

4. Przeciągnij kursor po przekątnej przeciwległego rogu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)  
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)  
[Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md)