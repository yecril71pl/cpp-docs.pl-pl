---
title: Używanie dokumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f039b2e81b52c753a1fb065572d4eac53d55ec9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428710"
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

## <a name="see-also"></a>Zobacz też

[Architektura dokument/widok](../mfc/document-view-architecture.md)

