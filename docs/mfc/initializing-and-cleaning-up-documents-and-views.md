---
title: Inicjowanie i oczyszczanie dokumentów i widoków
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
ms.openlocfilehash: 3c92d60941cd6542bd0d6c27e8a879dc85e3a3d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377204"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicjowanie i oczyszczanie dokumentów i widoków

Użyj następujących wskazówek dotyczących inicjowania i czyszczenia dokumentów i widoków:

- Struktura MFC inicjuje dokumenty i widoki; zainicjować wszystkie dodane do nich dane.

- Struktura czyści się w miarę zamykania dokumentów i widoków; należy zlokalizować dowolną pamięć przydzieloną na stercie z funkcji członkowskich tych dokumentów i widoków.

> [!NOTE]
> Przypomnijmy, że inicjowanie dla całej aplikacji najlepiej jest wykonać w nadpisywanie funkcji elementu członkowskiego [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) klasy `CWinApp`, `CWinApp` a oczyszczanie dla całej aplikacji najlepiej jest wykonać w nadpisywaniu funkcji elementu członkowskiego [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).

Cykl życia dokumentu (i jego okna ramki oraz widoku lub widoków) w aplikacji MDI jest następujący:

1. Podczas tworzenia dynamicznego konstruktora dokumentu jest wywoływana.

1. Dla każdego nowego dokumentu jest wywoływana nazwa dokumentu [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) lub [OnOpenDocument.](../mfc/reference/cdocument-class.md#onopendocument)

1. Użytkownik wchodzi w interakcję z dokumentem przez cały okres jego istnienia. Zazwyczaj dzieje się tak, gdy użytkownik pracuje nad danymi dokumentu za pośrednictwem widoku, wybierając i edytując dane. Widok przekazuje zmiany do dokumentu do przechowywania i aktualizowania innych widoków. W tym czasie zarówno dokument, jak i widok mogą obsługiwać polecenia.

1. Struktura wywołuje [DeleteContents,](../mfc/reference/cdocument-class.md#deletecontents) aby usunąć dane specyficzne dla dokumentu.

1. Wywoływany jest destruktor dokumentu.

W aplikacji SDI krok 1 jest wykonywany raz, gdy dokument jest tworzony po raz pierwszy. Następnie kroki od 2 do 4 są wykonywane wielokrotnie za każdym razem, gdy otwierany jest nowy dokument. Nowy dokument ponownie używa istniejącego obiektu dokumentu. Na koniec krok 5 jest wykonywany po zakończeniu aplikacji.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Inicjowanie dokumentów i widoków](../mfc/initializing-documents-and-views.md)

- [Oczyszczanie dokumentów i widoków](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Zobacz też

[Architektura dokumentu/widoku](../mfc/document-view-architecture.md)
