---
title: Wymiana danych
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
ms.openlocfilehash: de82a337f19b7b2ac6039fd3f3c16ab67aa1dc99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405849"
---
# <a name="exchanging-data"></a>Wymiana danych

Podobnie jak w przypadku większości okien dialogowych, wymianę danych między arkusza właściwości, a aplikacja jest jedną z najważniejszych funkcji arkusza właściwości. W tym artykule opisano sposób wykonania tego zadania.

Wymiana danych z arkusza właściwości jest faktycznie kwestią wymiana danych z na stronach właściwości indywidualnych arkusza właściwości. Procedury wymiany danych za pomocą strony właściwości jest taka sama, jak w przypadku wymiany danych okna dialogowego, ponieważ [CPropertyPage](../mfc/reference/cpropertypage-class.md) obiekt jest szczególnymi rodzajami [CDialog](../mfc/reference/cdialog-class.md) obiektu. Procedura wykorzystuje instrumentu struktury okna dialogowego dane programu exchange (DDX), który wymienia dane między kontrolkami w zmiennych okna dialogowego pole i elementów członkowskich obiektu okno dialogowe.

Istotną różnicą między wymiana danych z arkusza właściwości i okno dialogowe normalnego to, że arkusz właściwości zawiera wiele stron, dlatego konieczna jest wymiana danych ze wszystkich stron w arkuszu właściwości. Aby uzyskać więcej informacji na temat DDX, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md).

Poniższy przykład ilustruje wymianie danych między widokiem i dwie strony arkusza właściwości:

[!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Arkusze właściwości](../mfc/property-sheets-mfc.md)
