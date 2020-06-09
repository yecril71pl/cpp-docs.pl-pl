---
title: Zalety architektury dokumentu-widoku
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: 80f7141ec62d509defdea361586399bd375df0d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623279"
---
# <a name="advantages-of-the-documentview-architecture"></a>Zalety architektury dokument/widok

Główną zaletą korzystania z architektury dokumentu MFC/widoku jest to, że architektura obsługuje wiele widoków tego samego dokumentu. (Jeśli nie potrzebujesz wielu widoków i niewielkie obciążenie dokumentu/widoku jest nadmierne w aplikacji, możesz uniknąć użycia architektury. [Alternatywy dla architektury dokumentu/widoku](alternatives-to-the-document-view-architecture.md)).

Załóżmy, że aplikacja umożliwia użytkownikom wyświetlanie danych liczbowych w formularzu arkusza kalkulacyjnego lub w formularzu wykresu. Użytkownik może chcieć zobaczyć jednocześnie zarówno dane pierwotne, w formularzu arkusza kalkulacyjnego, jak i wykres, który wynika z danych. Te osobne widoki są wyświetlane w oddzielnych oknach ramowych lub w okienkach rozdzielacza w jednym oknie. Teraz Załóżmy, że użytkownik może edytować dane w arkuszu kalkulacyjnym, a zmiany są natychmiast widoczne na wykresie.

W MFC, widok arkusza kalkulacyjnego i widok wykresu byłyby oparte na różnych klasach pochodnych CView. Oba widoki są skojarzone z pojedynczym obiektem dokumentu. W dokumencie są przechowywane dane (lub prawdopodobnie są one uzyskiwane z bazy danych). Oba widoki uzyskują dostęp do dokumentu i wyświetlają dane z nich pobierane.

Gdy użytkownik zaktualizuje jeden z widoków, ten obiekt widoku wywołuje `CDocument::UpdateAllViews` . Ta funkcja powiadamia wszystkie widoki dokumentu, a każdy widok jest aktualizowany przy użyciu najnowszych danych z dokumentu. Pojedyncze wywołanie `UpdateAllViews` synchronizacji różnych widoków.

W tym scenariuszu trudno jest kod bez rozdzielania danych z widoku, szczególnie w przypadku, gdy w widokach Zapisano same dane. Za pomocą dokumentu/widoku jest to łatwe. Platforma wykonuje większość zadań koordynacyjnych.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Alternatywy dla dokumentu/widoku](alternatives-to-the-document-view-architecture.md)

- [CDocument](reference/cdocument-class.md)

- [CView](reference/cview-class.md)

- [CDocument:: funkcji UpdateAllViews](reference/cdocument-class.md#updateallviews)

- [CView:: GetDocument](reference/cview-class.md#getdocument)

## <a name="see-also"></a>Zobacz też

[Architektura dokumentu/widoku](document-view-architecture.md)
