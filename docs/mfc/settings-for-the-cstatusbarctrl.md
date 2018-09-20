---
title: Ustawienia formantu CStatusBarCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2411659e6ae33fe9ce81d508d3e7c206b1e5b113
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440033"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Ustawienia formantu CStatusBarCtrl

Domyślne położenie [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) okno stanu jest wzdłuż dolnej części okna nadrzędnego, ale można określić styl CCS_TOP, aby był wyświetlany w górnej części obszaru klienckiego okna nadrzędnego.

Można określić styl SBARS_SIZEGRIP obejmujący uchwyt zmiany rozmiaru na prawym końcu `CStatusBarCtrl` okno stanu. Uchwyt zmiany rozmiaru jest podobny do granicę z ustalanym; jest prostokątny obszar, który użytkownik może kliknij i przeciągnij, aby zmienić rozmiar okna nadrzędnego.

> [!NOTE]
>  Jeśli łączone style CCS_TOP i SBARS_SIZEGRIP wynikowy uchwyt zmiany rozmiaru nie działa mimo, że system rysuje go w oknie stanu.

Procedurę okna dla okna stanu automatycznie ustawia początkowy rozmiar i położenie okna kontrolki. Szerokość jest taka sama jak obszar klienta okna nadrzędnego. Wysokość opiera się na metryki czcionki, który jest aktualnie wybrany do kontekstu urządzenia okno stanu i szerokości obramowania okna.

Po każdym odebraniu komunikatu WM_SIZE procedurę okna automatycznie dostosowuje rozmiar okna stanu. Zwykle po zmianie rozmiaru okna nadrzędnego obiektu nadrzędnego wysyła komunikat WM_SIZE do okna stanu.

Minimalna wysokość obszaru okno stanu można ustawić, wywołując [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), określając minimalną wysokość w pikselach. Obszar rysowania nie ma obramowania okna.

Pobieranie szerokości obramowania okna stanu przez wywołanie metody [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Ta funkcja elementu członkowskiego zawiera wskaźnik do trzech elementowej tablicy, która odbiera szerokość obramowania poziome, pionowe obramowanie i granicy między prostokąty.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

