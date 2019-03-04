---
title: Obsługa poleceń w dokumencie
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: f3cce539d52bd04e97a6b5f84cbd833b05afb5bb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280436"
---
# <a name="handling-commands-in-the-document"></a>Obsługa poleceń w dokumencie

Klasa dokumentu może również obsługiwać niektórych poleceń generowane przez elementy menu, przyciski paska narzędzi lub klawiszy skrótów. Domyślnie `CDocument` obsługuje zapisywania i Zapisz jako polecenia w menu plik za pomocą serializacji. Innych poleceń, które wpływają na dane również mogą być obsługiwane przez funkcje Członkowskie dokumentu. Na przykład w programie bazgrołów klasy `CScribDoc` zawiera program obsługi polecenia Edytuj Wyczyść wszystko, co spowoduje usunięcie wszystkich danych przechowywanych w dokumencie. Dokumenty mogą mieć mapy komunikatów, ale w przeciwieństwie do widoków dokumentów nie może obsługiwać standardowe komunikaty Windows — tylko **WM_COMMAND** wiadomości lub "polecenia".

## <a name="see-also"></a>Zobacz także

[Używanie dokumentów](../mfc/using-documents.md)
