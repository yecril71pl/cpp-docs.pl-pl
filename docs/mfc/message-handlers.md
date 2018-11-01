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
ms.openlocfilehash: 1d775fc98fc97236cd63caf1e4422d32a9245410
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588659"
---
# <a name="message-handlers"></a>Programy obsługi komunikatów

W MFC, dedykowany *obsługi* funkcja przetwarza każdy komunikat oddzielne. Funkcje obsługi komunikatów są funkcji składowych klasy. Ta dokumentacja używa warunki *funkcja elementu członkowskiego program obsługi komunikatów*, *funkcji obsługi wiadomości*, *obsługi wiadomości*, i *obsługi*zamiennie. Niektóre rodzaje obsługi komunikatów są również nazywane "programy obsługi poleceń."

Zapisywanie konta programy obsługi komunikatów dla znaczną część pracy w pisaniu aplikacji framework. Tej rodziny artykule opisano, jak działa mechanizm przetwarzania komunikatów.

Działanie procedury obsługi wiadomości zrobił jest dowolne gotowe w odpowiedzi na tę wiadomość. Można utworzyć procedury obsługi za pomocą okna właściwości klasy, a następnie wypełnij kodu programu obsługi, za pomocą edytora kodu źródłowego.

Można użyć wszystkich funkcji programu Microsoft Visual C++ i MFC, można zapisać inne programy obsługi. Aby uzyskać listę wszystkich klas, zobacz [Przegląd biblioteki klas](../mfc/class-library-overview.md) w *odwołanie MFC*.

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

