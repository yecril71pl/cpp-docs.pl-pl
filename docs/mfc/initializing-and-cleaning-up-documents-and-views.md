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
ms.openlocfilehash: 59e86f4000e2da588749ca48887d34c3effdfc3a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297193"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Inicjowanie i oczyszczanie dokumentów i widoków

Inicjowanie i oczyszczanie po dokumentów i widoków, skorzystaj z poniższych wskazówek:

- Struktura MFC inicjuje dokumentów i widoków; należy zainicjować wszelkimi danymi, które można dodawać do nich.

- Struktura czyści jako dokumentów i widoków Zamknij; należy cofnąć przydział wszystkie pamięci, która została przydzielona na stosie z w ramach funkcji elementów członkowskich tych dokumentów i widoków.

> [!NOTE]
>  Odwołaj ten inicjowania dla całej aplikacji odbywa się najlepiej w zastąpienie metody [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) funkcji składowej klasy typu `CWinApp`, i czyszczenia dla całej aplikacji odbywa się najlepiej w zastąpienie metody `CWinApp`funkcja elementu członkowskiego [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).

Cykl życia dokumentu (i jego ramki okna i widoku lub widoków) w MDI aplikacji jest następujący:

1. Podczas tworzenia dynamicznych Konstruktor dokumentu jest wywoływany.

1. Dla każdego nowego dokumentu, dokument firmy [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) lub [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) jest wywoływana.

1. Użytkownik wchodzi w interakcję z dokumentu w okresie swojego istnienia. Zwykle dzieje się jako użytkownik pracuje na dane dokumentu za pośrednictwem widoku, wybierając i edytowanie danych. Widok przekazuje zmian do dokumentu, przechowywania i aktualizowania z innymi widokami. W tym czasie dokument i widok może obsługiwać poleceń.

1. Struktura wywołuje [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) można usunąć danych specyficznych dla określonego dokumentu.

1. Dokumentu destruktor jest wywoływany.

W aplikacji interfejsu SDI kroku 1 jest wykonywane raz, po pierwszym utworzeniu dokumentu. Następnie kroki od 2 do 4 są wykonywane wielokrotnie każdorazowo, gdy zostanie otwarty nowy dokument. Nowy dokument ponownie używa istniejący obiekt dokumentu. Na koniec kroku 5 odbywa się podczas kończenia aplikacji.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Inicjowanie dokumentów i widoków](../mfc/initializing-documents-and-views.md)

- [Oczyszczanie dokumentów i widoków](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Zobacz także

[Architektura dokument/widok](../mfc/document-view-architecture.md)
