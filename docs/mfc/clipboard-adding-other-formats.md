---
title: 'Schowek: Dodawanie innych formatów'
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 16e949973ff621b1e4e36475d95763ac47b4a00d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280221"
---
# <a name="clipboard-adding-other-formats"></a>Schowek: Dodawanie innych formatów

W tym temacie wyjaśniono, jak rozwinąć listę obsługiwanych formatów, szczególnie w przypadku obsługi. Temat [Schowka: Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md) opisuje minimalne wdrożenie niezbędne do obsługi kopiowanie i wklejanie ze Schowka. Jeśli to wszystko możesz wdrożyć są tylko formaty w Schowku znajduje **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**i ewentualnie **CF_LINKSOURCE**. Większość aplikacji będzie więcej formatów w Schowku niż tych trzech.

##  <a name="_core_registering_custom_formats"></a> Rejestrowanie niestandardowych formatów

Aby utworzyć własne niestandardowe formaty, postępuj zgodnie z tej samej procedury, należy użyć podczas rejestrowania dowolnego niestandardowego formatu Schowka: Przekaż nazwę formatu w celu **RegisterClipboardFormat** funkcja i używać jej wartość zwracana jako format identyfikatora.

##  <a name="_core_placing_formats_on_the_clipboard"></a> Wprowadzenie do formatów w Schowku

Aby dodać więcej formatów w Schowku znajduje, konieczne jest przesłonięcie `OnGetClipboardData` funkcja w klasie pochodnej z jednego `COleClientItem` lub `COleServerItem` (w zależności od tego, czy dane mają być kopiowane jest natywny). W tej funkcji należy użyć następującej procedury.

#### <a name="to-place-formats-on-the-clipboard"></a>Aby umieścić formatów w Schowku

1. Tworzy obiekt `COleDataSource`.

1. Przekazywanie tego źródła danych do funkcji, która dodaje swoje formatów danych natywnych listą obsługiwanych formatów, wywołując `COleDataSource::CacheGlobalData`.

1. Dodawanie standardowych formatów, wywołując `COleDataSource::CacheGlobalData` dla każdego standardowego formatu, które mają być obsługiwane.

Ta technika jest używany w programie MFC OLE próbki [HIERSVR](../visual-cpp-samples.md) (Sprawdź `OnGetClipboardData` funkcji składowej typu **CServerItem** klasy). Jedyną różnicą w tym przykładzie jest ten krok 3 nie jest zaimplementowana, ponieważ HIERSVR obsługuje nie standardowych formatów.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Źródła danych OLE obiekty i dane oraz jednolitego transferów danych](../mfc/data-objects-and-data-sources-ole.md)

- [Przeciąganie i upuszczanie OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Zobacz także

[Schowek: Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
