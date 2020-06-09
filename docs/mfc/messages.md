---
title: Komunikaty
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: f36dab679a2e41910b2445a7dab36f5786081563
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624278"
---
# <a name="messages"></a>Komunikaty

Pętla komunikatów w `Run` funkcji składowej klasy `CWinApp` Pobiera komunikaty w kolejce wygenerowane przez różne zdarzenia. Na przykład gdy użytkownik kliknie mysz, system Windows wyśle kilka komunikatów związanych z myszą, takich jak WM_LBUTTONDOWN po naciśnięciu lewego przycisku myszy i WM_LBUTTONUP po wydaniu lewego przycisku myszy. Implementacja platformy w pętli komunikatów aplikacji wysyła komunikat do odpowiedniego okna.

Ważne kategorie komunikatów są opisane w [kategorii komunikatów](message-categories.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](messages-and-commands-in-the-framework.md)
