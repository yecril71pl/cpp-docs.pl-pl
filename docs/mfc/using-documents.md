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
ms.openlocfilehash: 48f3bd6c6463bbbe26214a29960260d2be583e20
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385641"
---
# <a name="using-documents"></a>Używanie dokumentów
Praca ze sobą, dokumentów i widoków:  
  
-   Zawiera, zarządzanie i wyświetlanie określonych aplikacji [danych](../mfc/managing-data-with-document-data-variables.md).  
  
-   Udostępniają interfejs składające się z [zmiennych danych dokumentu](../mfc/managing-data-with-document-data-variables.md) do manipulowania danymi.  
  
-   Uczestniczenie w [zapisywania i odczytywania plików](../mfc/serializing-data-to-and-from-files.md).  
  
-   Uczestniczenie w [drukowania](../mfc/role-of-the-view-in-printing.md).  
  
-   [Obsługa](../mfc/handling-commands-in-the-document.md) większość poleceń i komunikatów aplikacji.  
  
 Dokument jest szczególnie zaangażowane w zarządzaniu danymi. Przechowywanie danych, zwykle w zmiennych Członkowskich klasy dokumentu. Widok używa tych zmiennych dostępu do danych w celu wyświetlenia i aktualizacji. Dokument domyślny mechanizm serializacji zarządza odczytywania i zapisywania danych do i z plików. Dokumenty mogą również obejmować poleceń (, ale nie systemu Windows inne niż wiadomości **WM_COMMAND**).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Wyprowadzanie klasy dokumentów z obiektu CDocument](../mfc/deriving-a-document-class-from-cdocument.md)  
  
-   [Zarządzanie danymi za pomocą zmiennych danych dokumentu](../mfc/managing-data-with-document-data-variables.md)  
  
-   [Serializacja danych do i z plików](../mfc/serializing-data-to-and-from-files.md)  
  
-   [Pomijanie mechanizmu serializacji](../mfc/bypassing-the-serialization-mechanism.md)  
  
-   [Obsługa poleceń w dokumencie](../mfc/handling-commands-in-the-document.md)  
  
-   [Funkcja członkowska OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)  
  
-   [Funkcja członkowska DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura dokument/widok](../mfc/document-view-architecture.md)

