---
title: Ustawienia formantu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: 18c4c780ecf7865d8d648bfa4c54961bbffe7b18
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446387"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Ustawienia formantu CStatusBarCtrl

Domyślna pozycja okna stanu [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) znajduje się u dołu okna nadrzędnego, ale można określić styl CCS_TOP, aby był wyświetlany w górnej części obszaru klienckiego okna nadrzędnego.

Możesz określić styl SBARS_SIZEGRIP, aby dołączyć uchwyt zmiany wielkości po prawej stronie okna stanu `CStatusBarCtrl`. Uchwyt zmiany wielkości jest podobny do obramowania zmieniającego rozmiar; jest to prostokątny obszar, który użytkownik może kliknąć i przeciągnąć, aby zmienić rozmiar okna nadrzędnego.

> [!NOTE]
>  Jeśli połączysz style CCS_TOP i SBARS_SIZEGRIP, wynikowy uchwyt zmiany wielkości nie działa nawet wtedy, gdy system rysuje go w oknie stanu.

W oknie procedura okna stanu automatycznie ustawia się początkowy rozmiar i położenie okna sterowania. Szerokość jest taka sama jak w przypadku obszaru klienckiego okna nadrzędnego. Wysokość jest oparta na metrykach czcionki, które są aktualnie zaznaczone w kontekście urządzenia okna stanu i szerokości obramowania okna.

Procedura okna automatycznie dostosowuje rozmiar okna stanu za każdym razem, gdy odbierze komunikat WM_SIZE. Zazwyczaj gdy rozmiar okna nadrzędnego zostanie zmieniony, obiekt nadrzędny wysyła komunikat WM_SIZE do okna stanu.

Minimalną wysokość obszaru rysowania okna stanu można ustawić, wywołując [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), określając minimalną wysokość (w pikselach). Obszar rysowania nie zawiera obramowania okna.

Możesz pobrać szerokości obramowania okna stanu, wywołując metodę [Getborderers](../mfc/reference/cstatusbarctrl-class.md#getborders). Ta funkcja członkowska zawiera wskaźnik do tablicy składającej się z trzech elementów, która otrzymuje szerokość obramowania poziomego, obramowania pionowego i obramowania między prostokątami.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
