---
title: Portret architektury dokumentu widoku
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
ms.openlocfilehash: 51f963acf5aacdfe4050a076d3bb0e651a92d021
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298870"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>Portret architektury dokument/widok

Dokumentów i widoków zostaną skojarzone w typowej aplikacji MFC. Dane są przechowywane w dokumencie, ale widoku ma uprzywilejowany dostęp do danych. Rozdzielenie dokumentu z widoku oddziela zasoby magazynowe od obsługi danych z jego wyświetlania.

## <a name="gaining-access-to-document-data-from-the-view"></a>Uzyskiwanie dostępu do danych z widoku dokumentów

Widok uzyskuje dostęp do swoich dokumentów danych za pomocą [GetDocument](../mfc/reference/cview-class.md#getdocument) funkcja, która zwraca wskaźnik do dokumentu lub przez dokonywanie widoku klasy C++ `friend` klasy dokumentu. Widoku jest używana jego dostęp do danych w celu uzyskania danych, gdy wszystko będzie gotowe narysować lub w przeciwnym razie manipulowania nimi.

Na przykład z tego widoku [OnDraw](../mfc/reference/cview-class.md#ondraw) funkcji składowej, jest używany w widoku `GetDocument` uzyskać wskaźnikiem dokumentu. Następnie używa tego wskaźnika do dostępu `CString` element członkowski danych w dokumencie. Widok przekazuje ciąg `TextOut` funkcji. Aby wyświetlić kod dla tego przykładu, zobacz [Rysowanie w widoku](../mfc/drawing-in-a-view.md).

## <a name="user-input-to-the-view"></a>Dane wejściowe użytkownika do widoku

Widok mogą również interpretować kliknięcia w sobie wybór lub edytowanie danych. Podobnie może go zinterpretować naciśnięć klawiszy jako wprowadzania danych lub edycji. Załóżmy, że użytkownik wpisze ciąg w widoku, który zarządza tekstu. Widok uzyskuje wskaźnik do dokumentu i używa wskaźnika do przekazania nowe dane do dokumentu, który zapisuje je w niektórych elementów struktury danych.

## <a name="updating-multiple-views-of-the-same-document"></a>Aktualizowanie wielu widoków tego samego dokumentu

W aplikacji z wielu widoków tego samego dokumentu — takich jak okna rozdzielacza w edytorze tekstów — widok najpierw przekazuje nowe dane do dokumentu. Następnie wywołuje dokumentu [funkcji UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) funkcja elementu członkowskiego, która informuje o tym wszystkich widoków dokumentu, aby zaktualizować, aby odzwierciedlić nowe dane. Synchronizacja widoków.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Zalety architektury dokument/widok](../mfc/advantages-of-the-document-view-architecture.md)

- [Alternatywy dla architektury dokument/widok](../mfc/alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>Zobacz także

[Architektura dokument/widok](../mfc/document-view-architecture.md)
