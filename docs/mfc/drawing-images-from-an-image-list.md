---
title: Rysowanie obrazów z poziomu listy obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: e4e60f0e6e4ee22712e4bbce344fd6437cf3db7e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916408"
---
# <a name="drawing-images-from-an-image-list"></a>Rysowanie obrazów z poziomu listy obrazów

Aby narysować obraz, użyj funkcji [Korzystanie CImageList::D RAW](../mfc/reference/cimagelist-class.md#draw) . Określisz wskaźnik do obiektu kontekstu urządzenia, indeks obrazu do rysowania, lokalizację w kontekście urządzenia, w której ma nastąpić Rysowanie obrazu, oraz zestaw flag wskazujących styl rysowania.

Po określeniu stylu **ILD_TRANSPARENT** program `Draw` używa procesu dwuetapowego do rysowania zamaskowanego obrazu. Po pierwsze wykonuje operacje logiczne i w bitach obrazu oraz bity maski. Następnie wykonuje operacje logiczne-XOR na wyniki pierwszej operacji i bitów w tle kontekstu urządzenia docelowego. Ten proces tworzy przezroczyste obszary na obrazie wyników; oznacza to, że każdy biały bit w masce powoduje, że odpowiedni bit w obrazie, który ma być przezroczysty.

Przed rysowaniem zamaskowanego obrazu na tle pełnego koloru należy użyć funkcji składowej [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) , aby ustawić kolor tła listy obrazów na taki sam kolor jak miejsce docelowe. Ustawienie koloru eliminuje konieczność tworzenia przezroczystych obszarów na obrazie i umożliwia `Draw` po prostu skopiowanie obrazu do kontekstu urządzenia docelowego, co spowodowało znaczny wzrost wydajności. Aby narysować obraz, określ styl **ILD_NORMAL** podczas wywoływania `Draw`.

Możesz ustawić kolor tła dla listy zamaskowanego obrazu ([Korzystanie CImageList](../mfc/reference/cimagelist-class.md)) w dowolnym momencie, tak aby był prawidłowo pobierany na dowolnym ciągłym tle. Ustawienie koloru tła na **CLR_NONE** powoduje, że obrazy są rysowane domyślnie w sposób przezroczysty. Aby pobrać kolor tła listy obrazów, użyj funkcji składowej [GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) .

Style **ILD_BLEND25** i **ILD_BLEND50** są symulowane dla obrazu za pomocą koloru wyróżnienia systemu. Te style są przydatne w przypadku użycia zamaskowanego obrazu do reprezentowania obiektu, który użytkownik może wybrać. Na przykład można użyć stylu **ILD_BLEND50** do narysowania obrazu, gdy użytkownik go wybierze.

Obraz niemaskowany jest kopiowany do kontekstu urządzenia docelowego przy użyciu `SRCCOPY` operacji rastrowej. Kolory obrazu są wyświetlane w taki sam sposób, niezależnie od koloru tła kontekstu urządzenia. Style rysowania określone w programie `Draw` również nie mają wpływu na wygląd obrazu niemaskowanego.

Oprócz funkcji rysowania elementu członkowskiego, inna funkcja, [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), rozszerza możliwość renderowania obrazu. `DrawIndirect`przyjmuje jako parametr [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-imagelistdrawparams) strukturę. Ta struktura może służyć do dostosowywania renderowania bieżącego obrazu, łącznie z użyciem kodów operacji rastrowych (ROP). Aby uzyskać więcej informacji na temat kodów ROP, zobacz sekcję [operacje rastrowe](/windows/desktop/gdi/raster-operation-codes) i [mapy bitowe jako pędzle](/windows/desktop/gdi/bitmaps-as-brushes) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
