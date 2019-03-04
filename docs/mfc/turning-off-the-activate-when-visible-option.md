---
title: Wyłączanie opcji aktywacji w przypadku widoczności
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: a7afe9617aa356916fe184828d7684f228293e39
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304734"
---
# <a name="turning-off-the-activate-when-visible-option"></a>Wyłączanie opcji aktywacji w przypadku widoczności

Formant ma dwa podstawowe stany: aktywnych i nieaktywnych. Zazwyczaj te stany zostały rozróżnianych na podstawie tego, czy formant ma okna. Aktywny formant ma okna; nie kontrolkę, która jest nieaktywny. Wraz z wprowadzeniem aktywacji niepowiązanej z oknami wykonywania tego rozróżnienia nie jest już uniwersalne, ale nadal dotyczy wielu kontrolek.

Tworzenie okna, w porównaniu z pozostałą częścią inicjowania najczęściej wykonywane przez formant ActiveX, jest bardzo kosztowna operacja. Najlepiej, jeśli formant będzie Odrocz tworzenia jego okna, dopóki nie jest to absolutnie konieczne.

Wiele kontrolek jest konieczne jest aktywna przez cały czas, w których są one widoczne w kontenerze. Często formantu może pozostawać w stanie nieaktywne, dopóki użytkownik wykonuje operację, która wymaga staje się aktywny (na przykład kliknięcie myszą lub naciskając klawisz TAB). Aby spowodować, że formant do pozostaną nieaktywne do momentu kontenera, trzeba go uaktywnić, Usuń **OLEMISC_ACTIVATEWHENVISIBLE** flagi z formantu różnych flag:

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

**OLEMISC_ACTIVATEWHENVISIBLE** flagi automatycznie zostanie pominięty, jeśli klient wyłączy **aktywować, gdy widoczny** opcji [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony MFC ActiveX Kreator kontrolki podczas tworzenia kontrolki.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC: Optymalizacja](../mfc/mfc-activex-controls-optimization.md)
