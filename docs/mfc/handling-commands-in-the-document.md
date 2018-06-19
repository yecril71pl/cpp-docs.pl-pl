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
ms.openlocfilehash: c20ff02b2d72f1dfa6afab5a0d547b46aa55b18c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343557"
---
# <a name="handling-commands-in-the-document"></a>Obsługa poleceń w dokumencie
Klasy dokumentu może również obsługiwać niektórych poleceń generowane przez elementy menu, przycisków paska narzędzi lub klawiszy skrótów. Domyślnie **CDocument** obsługuje zapisywania i Zapisz jako polecenia w menu plik za pomocą serializacji. Inne polecenia, które mają wpływ na dane również mogą być obsługiwane przez funkcje Członkowskie dokumentu. Na przykład w programie bazgrołów klasy `CScribDoc` zapewnia obsługi polecenia Edytuj Wyczyść wszystko, co powoduje usunięcie wszystkich danych przechowywanych w dokumencie. Dokumenty mogą mieć mapy komunikatów, ale w przeciwieństwie do widoków, dokumentów nie może obsłużyć standardowe komunikaty systemu Windows — tylko **WM_COMMAND** wiadomości lub "polecenia".  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie dokumentów](../mfc/using-documents.md)

