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
ms.openlocfilehash: 52089364a6be423c69a7031cd0d99e1924de1444
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626066"
---
# <a name="clipboard-adding-other-formats"></a>Schowek: dodawanie innych formatów

W tym temacie wyjaśniono, jak rozszerzyć listę obsługiwanych formatów, szczególnie w przypadku obsługi OLE. Schowek tematu [: kopiowanie i wklejanie danych](clipboard-copying-and-pasting-data.md) zawiera opis minimalnej implementacji niezbędnej do obsługi kopiowania i wklejania ze schowka. Jeśli wszystko jest zaimplementowane, jedynym formatem umieszczonym w schowku są **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**i możliwie **CF_LINKSOURCE**. Większość aplikacji będzie potrzebować więcej formatów w schowku niż te trzy.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Rejestrowanie formatów niestandardowych

Aby utworzyć własne niestandardowe formaty, postępuj zgodnie z tą samą procedurą, która będzie używana podczas rejestrowania dowolnego niestandardowego formatu Schowka: przekaż nazwę formatu do funkcji **RegisterClipboardFormat** i użyj jej wartości zwracanej jako identyfikatora formatu.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Umieszczanie formatów w schowku

Aby dodać więcej formatów do tych umieszczonych w schowku, należy zastąpić `OnGetClipboardData` funkcję w klasie pochodnej `COleClientItem` lub `COleServerItem` (w zależności od tego, czy dane do skopiowania są natywne). W tej funkcji należy wykonać poniższą procedurę.

#### <a name="to-place-formats-on-the-clipboard"></a>Aby umieścić formaty w schowku

1. Utwórz `COleDataSource` obiekt.

1. Przekaż to źródło danych do funkcji, która dodaje natywne formaty danych do listy obsługiwanych formatów przez wywołanie `COleDataSource::CacheGlobalData` .

1. Dodaj standardowe formaty, wywołując `COleDataSource::CacheGlobalData` dla każdego formatu standardowego, który ma być obsługiwany.

Ta technika jest używana w przykładowym programie MFC OLE [HIERSVR](../overview/visual-cpp-samples.md) (badanie `OnGetClipboardData` funkcji składowej klasy **CServerItem** ). Jedyną różnicą w tym przykładzie jest to, że krok trzeci nie jest zaimplementowany, ponieważ HIERSVR nie obsługuje żadnych innych formatów standardowych.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Obiekty danych OLE i źródła danych oraz jednolity transfer danych](data-objects-and-data-sources-ole.md)

- [Przeciąganie i upuszczanie elementów OLE](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>Zobacz też

[Schowek: korzystanie z mechanizmu schowka OLE](clipboard-using-the-ole-clipboard-mechanism.md)
