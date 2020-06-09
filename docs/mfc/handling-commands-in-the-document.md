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
ms.openlocfilehash: ed2ef635437408cacfd600d6cdba4b3731d575b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625744"
---
# <a name="handling-commands-in-the-document"></a>Obsługa poleceń w dokumencie

Klasa dokumentu może również obsługiwać niektóre polecenia generowane przez elementy menu, przyciski paska narzędzi lub klawisze skrótów. Domyślnie program `CDocument` obsługuje polecenia Zapisz i Zapisz jako w menu plik przy użyciu serializacji. Inne polecenia, które mają wpływ na dane mogą również być obsługiwane przez funkcje składowe dokumentu. Na przykład w programie bazgrołów Klasa `CScribDoc` zawiera procedurę obsługi dla polecenia Edytuj Wyczyść wszystko, które usuwa wszystkie dane przechowywane w dokumencie. Dokumenty mogą zawierać mapy komunikatów, ale w przeciwieństwie do widoków dokumenty nie mogą obsługiwać standardowych komunikatów systemu Windows — tylko **WM_COMMAND** komunikatów lub "polecenia".

## <a name="see-also"></a>Zobacz też

[Używanie dokumentów](using-documents.md)
