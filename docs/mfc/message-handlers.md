---
title: Programy obsługi komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: 0d3ed6239b638a0e161cd7e3580f4fe6e1b4a7e7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304872"
---
# <a name="message-handlers"></a>Programy obsługi komunikatów

W MFC, dedykowany *obsługi* funkcja przetwarza każdy komunikat oddzielne. Funkcje obsługi komunikatów są funkcji składowych klasy. Ta dokumentacja używa warunki *funkcja elementu członkowskiego program obsługi komunikatów*, *funkcji obsługi wiadomości*, *obsługi wiadomości*, i *obsługi*zamiennie. Niektóre rodzaje obsługi komunikatów są również nazywane "programy obsługi poleceń."

Zapisywanie konta programy obsługi komunikatów dla znaczną część pracy w pisaniu aplikacji framework. Tej rodziny artykule opisano, jak działa mechanizm przetwarzania komunikatów.

Działanie procedury obsługi wiadomości zrobił jest dowolne gotowe w odpowiedzi na tę wiadomość. Można utworzyć procedury obsługi za pomocą okna właściwości klasy, a następnie wypełnij kodu programu obsługi, za pomocą edytora kodu źródłowego.

Można użyć wszystkich funkcji programu Microsoft Visual C++ i MFC, można zapisać inne programy obsługi. Aby uzyskać listę wszystkich klas, zobacz [Przegląd biblioteki klas](../mfc/class-library-overview.md) w *odwołanie MFC*.

## <a name="see-also"></a>Zobacz także

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)
