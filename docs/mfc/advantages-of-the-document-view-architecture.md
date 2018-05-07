---
title: Zalety architektury dokument widok | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45065b38128a2e3239b1fd10ded490fdcbcb3eac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="advantages-of-the-documentview-architecture"></a>Zalety architektury dokument/widok
Zaletą korzystania z architektury dokument/widok MFC to architektura szczególnie dobrze obsługuje różne widoki tego samego dokumentu. (Jeśli nie potrzebujesz wielu widoków i małe obciążenie dokument/widok jest nadmierne w aplikacji, można uniknąć architektury. [Alternatywy dla architektury dokument/widok](../mfc/alternatives-to-the-document-view-architecture.md).)  
  
 Załóżmy, że aplikacja pozwala użytkownikom na wyświetlanie danych liczbowych, w postaci arkusz kalkulacyjny lub w postaci wykresu. Użytkownik może być Zobacz jednocześnie zarówno dane pierwotne, w formie arkusza kalkulacyjnego i wykres wyników z danych. Widoki te oddzielne była wyświetlana w oknach ramowych oddzielne lub w okienkach podziału w obrębie jednego okna. Teraz załóżmy, że użytkownik może edytować dane w arkuszu kalkulacyjnym i zobacz zmiany natychmiast widoczne na wykresie.  
  
 W MFC widok arkusza kalkulacyjnego i widok wykresu może opierać się na różnych klas pochodnych CView. Obu widokach zostałyby skojarzone z obiektem pojedynczego dokumentu. Dokument przechowuje dane (lub prawdopodobnie uzyskuje z bazy danych). Obu widokach dostępu do dokumentu i wyświetlić dane, które z niej pobierać.  
  
 Gdy użytkownik zaktualizuje jeden z widoków, które wyświetlać wywołania obiektu `CDocument::UpdateAllViews`. Ta funkcja powiadamia wszystkie widoki dokumentu, a każdy widok aktualizacji przy użyciu najnowszych danych z dokumentu. Wywołanie pojedynczego `UpdateAllViews` synchronizuje różne widoki.  
  
 Ten scenariusz jest trudna do kodu bez oddzielenie danych z widoku, zwłaszcza w wypadku widoki przechowywane dane samodzielnie. Dokument/widok jest bardzo proste. Platformę wykonuje większość pracy koordynacji.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Alternatywy dla dokument/widok](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [Cview —](../mfc/reference/cview-class.md)  
  
-   [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)  
  
-   [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura dokument/widok](../mfc/document-view-architecture.md)

