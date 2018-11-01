---
title: Wyłączanie opcji aktywacji w przypadku widoczności
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: 42dbec7a55085235e43fa14ab6406bfb3526afdb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464834"
---
# <a name="turning-off-the-activate-when-visible-option"></a>Wyłączanie opcji aktywacji w przypadku widoczności

Formant ma dwa podstawowe stany: aktywnych i nieaktywnych. Zazwyczaj te stany zostały rozróżnianych na podstawie tego, czy formant ma okna. Aktywny formant ma okna; nie kontrolkę, która jest nieaktywny. Wraz z wprowadzeniem aktywacji niepowiązanej z oknami wykonywania tego rozróżnienia nie jest już uniwersalne, ale nadal dotyczy wielu kontrolek.

Tworzenie okna, w porównaniu z pozostałą częścią inicjowania najczęściej wykonywane przez formant ActiveX, jest bardzo kosztowna operacja. Najlepiej, jeśli formant będzie Odrocz tworzenia jego okna, dopóki nie jest to absolutnie konieczne.

Wiele kontrolek jest konieczne jest aktywna przez cały czas, w których są one widoczne w kontenerze. Często formantu może pozostawać w stanie nieaktywne, dopóki użytkownik wykonuje operację, która wymaga staje się aktywny (na przykład kliknięcie myszą lub naciskając klawisz TAB). Aby spowodować, że formant do pozostaną nieaktywne do momentu kontenera, trzeba go uaktywnić, Usuń **OLEMISC_ACTIVATEWHENVISIBLE** flagi z formantu różnych flag:

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

**OLEMISC_ACTIVATEWHENVISIBLE** flagi automatycznie zostanie pominięty, jeśli klient wyłączy **aktywować, gdy widoczny** opcji [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony MFC ActiveX Kreator kontrolki podczas tworzenia kontrolki.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

