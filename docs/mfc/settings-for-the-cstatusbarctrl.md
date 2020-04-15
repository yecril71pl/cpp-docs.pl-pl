---
title: Ustawienia formantu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: dd7c68d6721c48f751c04437e43c8770f6ec5736
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365376"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Ustawienia formantu CStatusBarCtrl

Domyślna pozycja okna stanu [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) znajduje się u dołu okna nadrzędnego, ale można określić styl CCS_TOP, aby był wyświetlany w górnej części obszaru klienta okna nadrzędnego.

Styl SBARS_SIZEGRIP można określić, aby uwzględnić uchwyt zmiany rozmiaru `CStatusBarCtrl` na prawym końcu okna stanu. Uchwyt zmiany rozmiaru jest podobny do obramowania rozmiaru; jest to prostokątny obszar, który użytkownik może kliknąć i przeciągnąć, aby zmienić rozmiar okna nadrzędnego.

> [!NOTE]
> Jeśli połączysz style CCS_TOP i SBARS_SIZEGRIP, wynikowy uchwyt zmiany rozmiaru nie będzie funkcjonalny, nawet jeśli system rysuje go w oknie stanu.

Procedura okna okna stanu automatycznie ustawia początkowy rozmiar i położenie okna kontrolnego. Szerokość jest taka sama jak w obszarze klienta okna nadrzędnego. Wysokość jest oparta na metrykach czcionki, która jest aktualnie wybrana w kontekście urządzenia okna stanu i na szerokości obramowań okna.

Procedura okna automatycznie dostosowuje rozmiar okna stanu za każdym razem, gdy odbiera komunikat WM_SIZE. Zazwyczaj po zmianie rozmiaru okna nadrzędnego element nadrzędny wysyła komunikat WM_SIZE do okna stanu.

Minimalną wysokość obszaru rysunku okna stanu można ustawić, wywołując [setminheight](../mfc/reference/cstatusbarctrl-class.md#setminheight), określając minimalną wysokość w pikselach. Obszar rysunku nie zawiera obramowań okna.

Można pobrać szerokości obramowań okna stanu, wywołując [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Ta funkcja elementu członkowskiego zawiera wskaźnik do tablicy trzyelementowej, która odbiera szerokość obramowania poziomego, obramowanie pionowe i obramowanie między prostokątami.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
