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
ms.openlocfilehash: d2f0a7271452ace9b9e06ff995af61881db4403c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548957"
---
# <a name="handling-commands-in-the-document"></a>Obsługa poleceń w dokumencie

Klasa dokumentu może również obsługiwać niektórych poleceń generowane przez elementy menu, przyciski paska narzędzi lub klawiszy skrótów. Domyślnie `CDocument` obsługuje zapisywania i Zapisz jako polecenia w menu plik za pomocą serializacji. Innych poleceń, które wpływają na dane również mogą być obsługiwane przez funkcje Członkowskie dokumentu. Na przykład w programie bazgrołów klasy `CScribDoc` zawiera program obsługi polecenia Edytuj Wyczyść wszystko, co spowoduje usunięcie wszystkich danych przechowywanych w dokumencie. Dokumenty mogą mieć mapy komunikatów, ale w przeciwieństwie do widoków dokumentów nie może obsługiwać standardowe komunikaty Windows — tylko **WM_COMMAND** wiadomości lub "polecenia".

## <a name="see-also"></a>Zobacz też

[Używanie dokumentów](../mfc/using-documents.md)

