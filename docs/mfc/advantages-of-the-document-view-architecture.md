---
title: Zalety architektury dokumentu widoku
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: e250630bf3c9714fc01ff66b66fba3ac0d5b1cc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394731"
---
# <a name="advantages-of-the-documentview-architecture"></a>Zalety architektury dokument/widok

Kluczową zaletą przy użyciu architektury dokument/widok MFC jest architektura szczególnie dobrze obsługuje różne widoki tego samego dokumentu. (Jeśli nie potrzebujesz wielu widoków i małe obciążenie dokument/widok jest nadmierne w aplikacji, możesz uniknąć architektury. [Alternatywy dla architektury dokument/widok](../mfc/alternatives-to-the-document-view-architecture.md).)

Załóżmy, że aplikacja pozwala użytkownikom na wyświetlanie danych liczbowych, w postaci arkusz kalkulacyjny lub w postaci wykresu. Użytkownik może chcieć zobaczyć jednocześnie nieprzetworzone dane, w formie arkusza kalkulacyjnego i wykres, która wynika z danych. Możesz wyświetlić te osobne widoki w oddzielnych okna ramowe lub rozdzielacz okienka, w ramach jednego okna. Teraz załóżmy, że użytkownik może edytować dane w arkuszu kalkulacyjnym i zobaczyć zmiany natychmiast widoczne na wykresie.

W MFC widok arkusza kalkulacyjnego i widoku wykresu będzie opierać się na różnych klas pochodnych CView. Obu widokach będzie skojarzony z obiektem pojedynczego dokumentu. Dokument przechowuje dane (lub może być uzyskuje z bazy danych). Obu widokach uzyskać dostęp do dokumentów i wyświetlić dane, które mogą pobrać z niego.

Gdy użytkownik aktualizuje, jeden z widoków, które wyświetlić wywołania obiektu `CDocument::UpdateAllViews`. Ta funkcja powiadomi wszystkich widoków dokumentu, a każdy widok aktualizuje się sama za pomocą najnowszych danych z dokumentu. Jedno wywołanie `UpdateAllViews` synchronizuje różne widoki.

W tym scenariuszu trudno będzie kodu bez przeprowadzania oddzielenie danych z widoku, szczególnie w przypadku, gdy widoków znajdowały się dane, samodzielnie. Za pomocą dokument/widok jest proste. Struktura wykonuje większość pracy koordynacji.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Alternatywy dla dokumentu/widoku](../mfc/alternatives-to-the-document-view-architecture.md)

- [CDocument](../mfc/reference/cdocument-class.md)

- [CView](../mfc/reference/cview-class.md)

- [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)

- [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)

## <a name="see-also"></a>Zobacz także

[Architektura dokument/widok](../mfc/document-view-architecture.md)
