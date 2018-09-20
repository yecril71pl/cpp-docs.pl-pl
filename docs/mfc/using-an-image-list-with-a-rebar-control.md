---
title: Używanie List obrazów z formantem paska pomocniczego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff524f1f29e4db2ac5bb4628064583f0fe7583e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372369"
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

