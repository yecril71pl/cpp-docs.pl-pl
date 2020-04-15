---
title: 'Schowek: dodawanie innych formatów'
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 6f4e159cc1b6918843d4a164dcca88500eb7b038
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374604"
---
# <a name="clipboard-adding-other-formats"></a>Schowek: dodawanie innych formatów

W tym temacie wyjaśniono, jak rozwinąć listę obsługiwanych formatów, szczególnie w przypadku obsługi OLE. Temat [Schowek: Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md) opisuje minimalną implementację niezbędną do obsługi kopiowania i wklejania ze Schowka. Jeśli to wszystko zaimplementujesz, jedynymi formatami umieszczonymi w Schowku są **CF_METAFILEPICT,** **CF_EMBEDSOURCE,** **CF_OBJECTDESCRIPTOR**i ewentualnie **CF_LINKSOURCE.** Większość aplikacji będzie potrzebować więcej formatów w Schowku niż te trzy.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Rejestrowanie formatów niestandardowych

Aby utworzyć własne formaty niestandardowe, wykonaj tę samą procedurę, która zostałaby użyta podczas rejestrowania dowolnego niestandardowego formatu Schowka: przekaż nazwę formatu funkcji **RegisterClipboardFormat** i użyj jej wartości zwracanej jako identyfikatora formatu.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Umieszczanie formatów w Schowku

Aby dodać więcej formatów do formatów umieszczonych w `OnGetClipboardData` Schowku, należy zastąpić `COleClientItem` funkcję `COleServerItem` w klasie, z której pochodzisz, czy (w zależności od tego, czy dane do skopiowania są natywne). W tej funkcji należy użyć poniższej procedury.

#### <a name="to-place-formats-on-the-clipboard"></a>Aby umieścić formaty w Schowku

1. Utwórz `COleDataSource` obiekt.

1. Przekaż to źródło danych do funkcji, która dodaje natywne formaty `COleDataSource::CacheGlobalData`danych do listy obsługiwanych formatów, wywołując program .

1. Dodaj standardowe formaty, wywołując `COleDataSource::CacheGlobalData` dla każdego standardowego formatu, który chcesz obsługiwać.

Ta technika jest używana w przykładowym programie MFC OLE [HIERSVR](../overview/visual-cpp-samples.md) (sprawdź funkcję `OnGetClipboardData` elementu członkowskiego klasy **CServerItem).** Jedyną różnicą w tym przykładzie jest to, że krok trzeci nie jest zaimplementowany, ponieważ HIERSVR nie obsługuje innych standardowych formatów.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Obiekty danych OLE i źródła danych oraz jednolity transfer danych](../mfc/data-objects-and-data-sources-ole.md)

- [Przeciąganie i upuszczanie elementów OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Zobacz też

[Schowek: korzystanie z mechanizmu schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
