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
ms.openlocfilehash: 399230446977636cc8769efe32b8f86fad466b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616113"
---
# <a name="deriving-a-document-class-from-cdocument"></a>Wyprowadzanie klasy dokumentów z obiektu CDocument

Dokumenty zawierają dane aplikacji i zarządzają nimi. Aby użyć klasy dokumentu dostarczonej przez Kreatora aplikacji MFC, należy wykonać następujące czynności:

- Utwórz klasę `CDocument` dla każdego typu dokumentu.

- Dodaj Zmienne Członkowskie do przechowywania danych poszczególnych dokumentów.

- Przesłoń `CDocument` `Serialize` funkcję członkowską w klasie dokumentu. `Serialize`zapisuje i odczytuje dane dokumentu z i z dysku.

## <a name="other-document-functions-often-overridden"></a>Inne funkcje dokumentu są często zastępowane

Możesz również chcieć przesłonić inne `CDocument` funkcje składowe. W szczególności często trzeba przesłonić [OnNewDocument](reference/cdocument-class.md#onnewdocument) i [OnOpenDocument](reference/cdocument-class.md#onopendocument) , aby zainicjować składowe danych dokumentu i [DeleteContents](reference/cdocument-class.md#deletecontents) , aby zniszczyć dynamiczne przydzielane dane. Aby uzyskać informacje na temat składowych, zobacz Klasa [CDocument](reference/cdocument-class.md) w *dokumentacji MFC*.

## <a name="see-also"></a>Zobacz też

[Używanie dokumentów](using-documents.md)
