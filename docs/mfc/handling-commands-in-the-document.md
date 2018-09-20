---
title: Obsługa poleceń w dokumencie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8845ea7c44fd5a34774db0508302f5959987cdc9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441268"
---
# <a name="handling-commands-in-the-document"></a>Obsługa poleceń w dokumencie

Klasa dokumentu może również obsługiwać niektórych poleceń generowane przez elementy menu, przyciski paska narzędzi lub klawiszy skrótów. Domyślnie `CDocument` obsługuje zapisywania i Zapisz jako polecenia w menu plik za pomocą serializacji. Innych poleceń, które wpływają na dane również mogą być obsługiwane przez funkcje Członkowskie dokumentu. Na przykład w programie bazgrołów klasy `CScribDoc` zawiera program obsługi polecenia Edytuj Wyczyść wszystko, co spowoduje usunięcie wszystkich danych przechowywanych w dokumencie. Dokumenty mogą mieć mapy komunikatów, ale w przeciwieństwie do widoków dokumentów nie może obsługiwać standardowe komunikaty Windows — tylko **WM_COMMAND** wiadomości lub "polecenia".

## <a name="see-also"></a>Zobacz też

[Używanie dokumentów](../mfc/using-documents.md)

