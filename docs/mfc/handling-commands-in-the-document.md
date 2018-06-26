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
ms.openlocfilehash: 7a1e848827b46d40c1ec39f2af4788e6957932c5
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929115"
---
# <a name="handling-commands-in-the-document"></a>Obsługa poleceń w dokumencie
Klasy dokumentu może również obsługiwać niektórych poleceń generowane przez elementy menu, przycisków paska narzędzi lub klawiszy skrótów. Domyślnie `CDocument` obsługuje zapisywania i Zapisz jako polecenia w menu plik za pomocą serializacji. Inne polecenia, które mają wpływ na dane również mogą być obsługiwane przez funkcje Członkowskie dokumentu. Na przykład w programie bazgrołów klasy `CScribDoc` zapewnia obsługi polecenia Edytuj Wyczyść wszystko, co powoduje usunięcie wszystkich danych przechowywanych w dokumencie. Dokumenty mogą mieć mapy komunikatów, ale w przeciwieństwie do widoków, dokumentów nie może obsłużyć standardowe komunikaty systemu Windows — tylko **WM_COMMAND** wiadomości lub "polecenia".  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie dokumentów](../mfc/using-documents.md)

