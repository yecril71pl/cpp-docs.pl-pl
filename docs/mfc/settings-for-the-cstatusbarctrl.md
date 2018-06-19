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
ms.openlocfilehash: 1eea701c33001ffa3585c2d5847f3056454b7850
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380165"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Ustawienia formantu CStatusBarCtrl
To domyślne położenie [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) okno stanu jest wzdłuż dolnej części okna nadrzędnego, ale można określić `CCS_TOP` styl, który był wyświetlany u góry obszaru klienckiego okna nadrzędnego.  
  
 Można określić **SBARS_SIZEGRIP** stylu, aby uwzględnić uchwyt zmiany rozmiaru w prawym końcu `CStatusBarCtrl` okno stanu. Uchwyt zmiany rozmiaru jest podobny do rozmiaru obramowanie; jest prostokątny obszar, który użytkownik może kliknij i przeciągnij, aby zmienić rozmiar okna nadrzędnego.  
  
> [!NOTE]
>  Jeśli znajdzie się `CCS_TOP` i **SBARS_SIZEGRIP** style, wynikowy uchwyt zmiany rozmiaru nie działa mimo że rysuje go w oknie Stan systemu.  
  
 Procedury okna dla okna stanu automatycznie ustawia początkowy rozmiar i położenie okna formantu. Szerokość jest taka sama jak obszaru klienckiego okna nadrzędnego. Wysokość jest oparta na metryki czcionki aktualnie wybranego w oknie Stan kontekstu urządzenia i szerokości obramowania okna.  
  
 Zawsze, gdy odbierze procedurę okna automatycznie dopasowuje rozmiar okna stanu `WM_SIZE` wiadomości. Zwykle, gdy okno nadrzędne zmienia się rozmiar, wysyła nadrzędnego `WM_SIZE` wiadomości do okna stanu.  
  
 Minimalna wysokość obszaru okno stanu można ustawić przez wywołanie metody [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), określając minimalną wysokość w pikselach. Obszar rysowania nie ma obramowanie okna.  
  
 Pobrać szerokości obramowania okno stanu przez wywołanie metody [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Ta funkcja członkowska obejmuje wskaźnik do tablicy trzech elementu, która odbiera szerokość obramowania poziome, pionowe obramowanie i granicę między prostokąty.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

