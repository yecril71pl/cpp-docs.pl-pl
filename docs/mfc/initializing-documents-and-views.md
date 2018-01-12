---
title: "Inicjowanie dokumentów i widoków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f80d870f9804454dc652fdda00f34fcdb7a52062
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-documents-and-views"></a>Inicjowanie dokumentów i widoków
Dokumenty są tworzone na dwa różne sposoby, więc klasy dokumentu musi obsługiwać obu kierunkach. Po pierwsze użytkownik może utworzyć nowy, pusty dokument przy użyciu polecenia nowy plik. W takim przypadku Inicjowanie dokumentu w zastąpienia z [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) funkcji członkowskiej klasy [CDocument](../mfc/reference/cdocument-class.md). Po drugie użytkownik służy polecenie Otwórz w menu Plik można utworzyć nowego dokumentu, których zawartość są odczytywane z pliku. W takim przypadku Inicjowanie dokumentu w zastąpienia z [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) funkcji członkowskiej klasy **CDocument**. Zarówno inicjalizacji są takie same, należy wywołać typowych funkcji członkowskiej z obu zastąpienia lub `OnOpenDocument` można wywołać `OnNewDocument` do zainicjowania czystą dokumentu, a następnie Zakończ operacja otwierania.  
  
 Widoki są tworzone po utworzeniu swoje dokumenty. Najlepszy moment na inicjowanie widoku jest po zakończeniu platformę tworzenie dokumentów, okien ramowych i widoku. Widok można zainicjować przez zastąpienie [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkcji członkowskiej klasy [CView](../mfc/reference/cview-class.md). Jeśli musisz ponownie zainicjować lub Dostosuj niczego każdej zmianie dokumentu, można zastąpić [OnUpdate](../mfc/reference/cview-class.md#onupdate).  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)

