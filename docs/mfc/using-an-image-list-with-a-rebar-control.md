---
title: Używanie listy obrazów z formantem paska pomocniczego
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: 3cf359a5d06396f9c2c31cbec511c04784053e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641444"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Używanie listy obrazów z formantem paska pomocniczego

Każdego pasma paska pomocniczego może zawierać, między innymi obraz z listy obrazów skojarzone. W poniższej procedurze szczegółowo czynności niezbędnych do wyświetlania obrazu w przedziale paska pomocniczego.

### <a name="to-display-images-in-a-rebar-band"></a>Aby wyświetlić obrazy w przedziale paska pomocniczego

1. Dołączanie listy obrazów do obiektu formantu paska pomocniczego poprzez wywołanie [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), przekazując wskaźnik do istniejącej listy obrazów.

1. Modyfikowanie **REBARBANDINFO** strukturę, aby przypisać obrazu do pasma paska pomocniczego:

   - Ustaw *fMask* członka do `RBBIM_IMAGE`, aby uwzględnić dodatkowe flagi zgodnie z potrzebami przy użyciu bitowego operatora OR.

   - Ustaw *iImage* członek indeks listy obrazu obrazu do wyświetlenia.

1. Inicjuj wszystkie pozostałe składowe danych, takich jak rozmiar tekstu i uchwyt okna podrzędnego zawartej niezbędne informacje.

1. Wstaw nową grupę (przy użyciu obrazu) z wywołaniem [CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband), przekazując **REBARBANDINFO** struktury.

W poniższym przykładzie założono, że istniejący obiekt listy obrazów z dwa obrazy został dołączony do obiektu formantu paska pomocniczego (`m_wndReBar`). Nową grupę paska pomocniczego (zdefiniowany przez `rbi`), zawierający pierwszy obraz, zostanie dodany z wywołaniem `InsertBand`:

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

