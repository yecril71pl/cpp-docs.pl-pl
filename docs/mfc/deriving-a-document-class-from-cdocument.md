---
title: Wyprowadzanie klasy dokumentów z obiektu CDocument
ms.date: 11/04/2016
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
ms.openlocfilehash: 5998d5707eb741be0e8ac270f6ac5ce77a9ff8d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272064"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Wyprowadzanie klasy dokumentów z obiektu CDocument

Dokumenty zawierają i Zarządzaj danymi swojej aplikacji. Aby użyć klasy dokumentów dostarczonych przez Kreatora aplikacji MFC, wykonaj następujące czynności:

- Wyprowadzić klasę z `CDocument` dla każdego typu dokumentu.

- Dodaj zmienne Członkowskie do przechowywania danych poszczególnych dokumentów.

- Zastąp `CDocument`firmy `Serialize` funkcja elementu członkowskiego w klasie dokumentów. `Serialize` zapisuje i odczytuje dane dokumentu i z dysku.

## <a name="other-document-functions-often-overridden"></a>Inne funkcje dokumentu często zastępowane

Możesz również chcieć zastąpić inne `CDocument` funkcji elementów członkowskich. W szczególności, często musisz przesłonić [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) i [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) zainicjować elementy członkowskie danych dokumentu i [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) do likwidacji dynamicznie przydzielane danych. Uzyskać informacji o możliwym do zastąpienia członków, zobacz klasę [CDocument](../mfc/reference/cdocument-class.md) w *odwołanie MFC*.

## <a name="see-also"></a>Zobacz także

[Używanie dokumentów](../mfc/using-documents.md)
