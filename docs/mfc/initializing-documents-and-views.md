---
title: Inicjowanie dokumentów i widoków
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 0cf9faecbb7e0d74c2199a1a829aa68241e1c019
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264095"
---
# <a name="initializing-documents-and-views"></a>Inicjowanie dokumentów i widoków

Dokumenty są tworzone na dwa różne sposoby, więc klasy dokumentu musi obsługiwać w obu kierunkach. Po pierwsze użytkownik może utworzyć nowy pusty dokument za pomocą polecenia nowy plik. W takim przypadku Inicjowanie dokumentu w zastąpienie metody [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) funkcji składowej klasy typu [CDocument](../mfc/reference/cdocument-class.md). Po drugie użytkownik służy polecenie Otwórz menu Plik można utworzyć nowego dokumentu, w których zawartość są odczytywane z pliku. W takim przypadku Inicjowanie dokumentu w zastąpienie metody [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) funkcji składowej klasy typu `CDocument`. Jeśli oba inicjalizacje są takie same, można wywołać typowych funkcji składowej z obu zastąpienia lub `OnOpenDocument` może wywołać `OnNewDocument` na inicjowanie dokumentu czyste, a następnie Zakończ operacja otwierania.

Widoki są tworzone po utworzeniu swoich dokumentów. Najlepszy moment na inicjowanie widok jest po zakończeniu przez platformę, tworzenie dokumentów, ramki okna i widoku. Widok można zainicjować przez zastąpienie [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkcji składowej typu [CView](../mfc/reference/cview-class.md). Jeśli musisz ponownie zainicjować lub nic dopasować każdym zmiany w dokumencie, można zastąpić [OnUpdate](../mfc/reference/cview-class.md#onupdate).

## <a name="see-also"></a>Zobacz także

[Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)
