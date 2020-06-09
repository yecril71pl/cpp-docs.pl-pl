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
ms.openlocfilehash: f9c5272b513a92dc6dcfa37559b00ae79b658918
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619975"
---
# <a name="message-handlers"></a>Programy obsługi komunikatów

W MFC, dedykowana funkcja *obsługi* przetwarza każdą oddzielny komunikat. Funkcje programu obsługi komunikatów są funkcjami składowymi klasy. Ta dokumentacja używa zamiennej *funkcji elementu członkowskiego obsługi*komunikatów, *funkcji obsługi komunikatów*, *obsługi komunikatów*i *programu obsługi* . Niektóre rodzaje obsługi komunikatów są również nazywane "programami obsługi poleceń".

Pisanie programów obsługi komunikatów dla dużej części pracy podczas pisania aplikacji struktury. W tym artykule opisano, jak działa mechanizm przetwarzania komunikatów.

Co robi program obsługi wiadomości, robi to niezależnie od tego, co chcesz zrobić w odpowiedzi na tę wiadomość. Programy obsługi można utworzyć za pomocą [kreatora klas](reference/mfc-class-wizard.md) klasy, a następnie wypełnić kod programu obsługi przy użyciu edytora kodu źródłowego.

Aby napisać programy obsługi, można użyć wszystkich udogodnień Microsoft Visual C++ i MFC. Aby zapoznać się z listą wszystkich klas, zobacz [Omówienie biblioteki klas](class-library-overview.md) w *dokumentacji MFC*.

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](messages-and-commands-in-the-framework.md)
