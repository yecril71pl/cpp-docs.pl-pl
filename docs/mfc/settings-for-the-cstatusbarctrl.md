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
ms.openlocfilehash: 1dde1f005e53aff7ebe505d1ce619bf5c94410f8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955459"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Ustawienia formantu CStatusBarCtrl
To domyślne położenie [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) okno stanu jest wzdłuż dolnej części okna nadrzędnego, ale można określić styl CCS_TOP, który był wyświetlany u góry obszaru klienckiego okna nadrzędnego.  
  
 Można określić styl SBARS_SIZEGRIP, aby uwzględnić uchwyt zmiany rozmiaru w prawym końcu `CStatusBarCtrl` okno stanu. Uchwyt zmiany rozmiaru jest podobny do rozmiaru obramowanie; jest prostokątny obszar, który użytkownik może kliknij i przeciągnij, aby zmienić rozmiar okna nadrzędnego.  
  
> [!NOTE]
>  Jeśli znajdzie style CCS_TOP i SBARS_SIZEGRIP wynikowy uchwyt zmiany rozmiaru nie działa mimo że rysuje go w oknie Stan systemu.  
  
 Procedury okna dla okna stanu automatycznie ustawia początkowy rozmiar i położenie okna formantu. Szerokość jest taka sama jak obszaru klienckiego okna nadrzędnego. Wysokość jest oparta na metryki czcionki aktualnie wybranego w oknie Stan kontekstu urządzenia i szerokości obramowania okna.  
  
 Zawsze, gdy odbierze komunikat WM_SIZE procedurę okna automatycznie dostosowuje rozmiar okna stanu. Zwykle gdy zmienia się rozmiar okna nadrzędnego, nadrzędnego wysyła komunikat WM_SIZE w oknie stanu.  
  
 Minimalna wysokość obszaru okno stanu można ustawić przez wywołanie metody [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), określając minimalną wysokość w pikselach. Obszar rysowania nie ma obramowanie okna.  
  
 Pobrać szerokości obramowania okno stanu przez wywołanie metody [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Ta funkcja członkowska obejmuje wskaźnik do tablicy trzech elementu, która odbiera szerokość obramowania poziome, pionowe obramowanie i granicę między prostokąty.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

