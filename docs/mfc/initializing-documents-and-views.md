---
title: Inicjowanie dokumentów i widoków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43610a08d5a3713cc40de0a2279286735a27d1da
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928185"
---
# <a name="initializing-documents-and-views"></a>Inicjowanie dokumentów i widoków
Dokumenty są tworzone na dwa różne sposoby, więc klasy dokumentu musi obsługiwać obu kierunkach. Po pierwsze użytkownik może utworzyć nowy, pusty dokument przy użyciu polecenia nowy plik. W takim przypadku Inicjowanie dokumentu w zastąpienia z [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) funkcji członkowskiej klasy [CDocument](../mfc/reference/cdocument-class.md). Po drugie użytkownik służy polecenie Otwórz w menu Plik można utworzyć nowego dokumentu, których zawartość są odczytywane z pliku. W takim przypadku Inicjowanie dokumentu w zastąpienia z [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) funkcji członkowskiej klasy `CDocument`. Zarówno inicjalizacji są takie same, należy wywołać typowych funkcji członkowskiej z obu zastąpienia lub `OnOpenDocument` można wywołać `OnNewDocument` do zainicjowania czystą dokumentu, a następnie Zakończ operacja otwierania.  
  
 Widoki są tworzone po utworzeniu swoje dokumenty. Najlepszy moment na inicjowanie widoku jest po zakończeniu platformę tworzenie dokumentów, okien ramowych i widoku. Widok można zainicjować przez zastąpienie [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkcji członkowskiej klasy [CView](../mfc/reference/cview-class.md). Jeśli musisz ponownie zainicjować lub Dostosuj niczego każdej zmianie dokumentu, można zastąpić [OnUpdate](../mfc/reference/cview-class.md#onupdate).  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)

