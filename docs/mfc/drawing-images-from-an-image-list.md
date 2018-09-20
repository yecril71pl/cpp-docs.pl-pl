---
title: Rysowanie obrazów z poziomu listy obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1a3d2004f0e939cef562ae7972fca88a2f31e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409910"
---
# <a name="drawing-images-from-an-image-list"></a>Rysowanie obrazów z poziomu listy obrazów

Aby narysować obrazu, należy użyć [CImageList::Draw](../mfc/reference/cimagelist-class.md#draw) funkcja elementu członkowskiego. Należy podać wskaźnik do obiektu kontekstu urządzenia: indeks obrazu, aby narysować lokalizacji w kontekście urządzenia, w którym do rysowania obrazu i zestaw flag, aby wskazać styl rysowania.

Po określeniu **ILD_TRANSPARENT** stylu `Draw` używa dwuetapowego procesu do rysowania obrazu maskowanego. Najpierw wykonuje logiczny — i operacji na bitów obrazu i bity maski. Następnie wykonuje operację XOR logiczne na wyniki pierwszej operacji i bity tła kontekstu urządzenia docelowego. Ten proces tworzy przezroczystych obszarów w obraz wynikowy; oznacza to, że każdy biały bit maski powoduje, że odnośny bit w Wynikowy obraz, który ma być przezroczysty.

Przed narysowaniem obrazu maskowanego na pełnego koloru tła, należy użyć [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) funkcję elementu członkowskiego, aby ustawić kolor tła, listy obrazów do tego samego koloru jako miejsce docelowe. Ustawianie koloru eliminuje potrzebę tworzenie obszarów przezroczystych obrazu i umożliwia `Draw` można po prostu skopiować obraz do kontekstu urządzenia docelowego, co spowoduje znaczne zwiększenie wydajności. Aby narysować obrazu, należy określić **ILD_NORMAL** stylu po wywołaniu `Draw`.

Można ustawić kolor tła dla listy obrazów maskowane ([CImageList](../mfc/reference/cimagelist-class.md)) w dowolnym momencie, dzięki czemu jej poprawnie rysuje na wszelkie stałe tła. Ustawianie koloru tła **CLR_NONE** powoduje, że obrazy, które będą używane w sposób niewidoczny dla użytkownika domyślnie. Aby pobrać kolor tła listy obrazów, użyj [GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) funkcja elementu członkowskiego.

**ILD_BLEND25** i **ILD_BLEND50** style Symulacja obraz z kolor wyróżnienia systemu. Te style są przydatne w przypadku maskowana obrazu do reprezentowania obiekt, który użytkownik może wybrać. Na przykład, można użyć **ILD_BLEND50** styl rysowania obrazu, gdy użytkownik wybierze je.

Nonmasked obrazu jest kopiowany do docelowego urządzenia kontekstu przy użyciu `SRCCOPY` operacji rastrowych. Kolory na obrazie są wyświetlane takie same, niezależnie od koloru tła kontekstu urządzenia. Style rysowania, określone w `Draw` również nie mają wpływu na wygląd nonmasked obrazu.

Oprócz funkcję składową Draw inną funkcję, [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), rozszerza możliwości renderowania obrazu. `DrawIndirect` przyjmuje jako parametr, [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) struktury. Ta struktura może służyć do dostosowywania renderowania bieżącego obrazu, łącznie z użyciem kody operacji (w prawym GÓRNYM) rastrowych. Aby uzyskać więcej informacji o kodach przycinanie — zobacz [kody operacji rastrowych](/windows/desktop/gdi/raster-operation-codes) i [map bitowych jako pędzle](/windows/desktop/gdi/bitmaps-as-brushes) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

