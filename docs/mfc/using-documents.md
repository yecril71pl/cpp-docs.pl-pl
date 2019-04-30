---
title: Używanie dokumentów
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
ms.openlocfilehash: fb35d1731912b2e322bc61621f7900e0d98e1e72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411594"
---
# <a name="using-documents"></a>Używanie dokumentów

Praca ze sobą, dokumentów i widoków:

- Zawiera, zarządzanie i wyświetlanie określonych aplikacji [danych](../mfc/managing-data-with-document-data-variables.md).

- Zapewniają interfejs składający się z [zmiennych danych dokumentu](../mfc/managing-data-with-document-data-variables.md) do manipulowania danymi.

- Uczestniczyć w [zapisywania i odczytywania plików](../mfc/serializing-data-to-and-from-files.md).

- Uczestniczyć w [drukowania](../mfc/role-of-the-view-in-printing.md).

- [Obsługa](../mfc/handling-commands-in-the-document.md) większości poleceń i komunikatów aplikacji.

Dokument jest szczególnie związane z zarządzaniem danymi. Store dane, zwykle w zmiennych elementu członkowskiego klasy dokumentu. Widok używa tych zmiennych, dostęp do danych w celu wyświetlenia i aktualizacji. Mechanizm serializacji domyślnego dokumentu zarządza odczytywanie i zapisywanie danych do i z plików. Dokumenty może również obsługiwać poleceń (ale nie Windows wiadomości, innej niż WM_COMMAND).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Wyprowadzanie klasy dokumentów z obiektu CDocument](../mfc/deriving-a-document-class-from-cdocument.md)

- [Zarządzanie danymi za pomocą zmiennych danych dokumentu](../mfc/managing-data-with-document-data-variables.md)

- [Serializacja danych do i z plików](../mfc/serializing-data-to-and-from-files.md)

- [Pomijanie mechanizmu serializacji](../mfc/bypassing-the-serialization-mechanism.md)

- [Obsługa poleceń w dokumencie](../mfc/handling-commands-in-the-document.md)

- [Funkcja elementu członkowskiego OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)

- [Funkcja elementu członkowskiego DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>Zobacz także

[Architektura dokument/widok](../mfc/document-view-architecture.md)
