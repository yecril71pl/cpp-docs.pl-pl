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
ms.openlocfilehash: 25805187f88c5423ea41cd7cbe346e44e7d7d36a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907458"
---
# <a name="message-handlers"></a>Programy obsługi komunikatów

W MFC, dedykowana funkcja *obsługi* przetwarza każdą oddzielny komunikat. Funkcje programu obsługi komunikatów są funkcjami składowymi klasy. Ta dokumentacja używa zamiennej *funkcji elementu członkowskiego obsługi*komunikatów, *funkcji obsługi komunikatów*, *obsługi komunikatów*i *programu obsługi* . Niektóre rodzaje obsługi komunikatów są również nazywane "programami obsługi poleceń".

Pisanie programów obsługi komunikatów dla dużej części pracy podczas pisania aplikacji struktury. W tym artykule opisano, jak działa mechanizm przetwarzania komunikatów.

Co robi program obsługi wiadomości, robi to niezależnie od tego, co chcesz zrobić w odpowiedzi na tę wiadomość. Programy obsługi można utworzyć za pomocą [kreatora klas](reference/mfc-class-wizard.md) klasy, a następnie wypełnić kod programu obsługi przy użyciu edytora kodu źródłowego.

Możesz użyć wszystkich funkcji programu Microsoft Visual C++ i MFC, aby napisać programy obsługi. Aby zapoznać się z listą wszystkich klas, zobacz [Omówienie biblioteki klas](../mfc/class-library-overview.md) w *dokumentacji MFC*.

## <a name="see-also"></a>Zobacz także

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)
