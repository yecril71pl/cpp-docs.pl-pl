---
title: Wymiana danych
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: 84e2ff9478cb3606bafb7f0408b7e2cc8fee2c00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569638"
---
# <a name="exchanging-data"></a>Wymiana danych

Podobnie jak w przypadku większości okien dialogowych, wymianę danych między arkusza właściwości, a aplikacja jest jedną z najważniejszych funkcji arkusza właściwości. W tym artykule opisano sposób wykonania tego zadania.

Wymiana danych z arkusza właściwości jest faktycznie kwestią wymiana danych z na stronach właściwości indywidualnych arkusza właściwości. Procedury wymiany danych za pomocą strony właściwości jest taka sama, jak w przypadku wymiany danych okna dialogowego, ponieważ [CPropertyPage](../mfc/reference/cpropertypage-class.md) obiekt jest szczególnymi rodzajami [CDialog](../mfc/reference/cdialog-class.md) obiektu. Procedura wykorzystuje instrumentu struktury okna dialogowego dane programu exchange (DDX), który wymienia dane między kontrolkami w zmiennych okna dialogowego pole i elementów członkowskich obiektu okno dialogowe.

Istotną różnicą między wymiana danych z arkusza właściwości i okno dialogowe normalnego to, że arkusz właściwości zawiera wiele stron, dlatego konieczna jest wymiana danych ze wszystkich stron w arkuszu właściwości. Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md).

Poniższy przykład ilustruje wymianie danych między widokiem i dwie strony arkusza właściwości:

[!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](../mfc/property-sheets-mfc.md)

