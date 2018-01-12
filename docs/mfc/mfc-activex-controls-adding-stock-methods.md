---
title: 'Formanty MFC ActiveX: Dodawanie metod standardowych | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2531f84974626fcdb364df67b12f27d61e75a62a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>Kontrolki ActiveX MFC: dodawanie metod standardowych
Podstawowe metody różni się od niestandardowej metody w tym został już zaimplementowany przez klasę [colecontrol —](../mfc/reference/colecontrol-class.md). Na przykład `COleControl` zawiera funkcję wstępnie zdefiniowanego elementu członkowskiego, która obsługuje metoda odświeżania dla formantu. Wpis mapy wysyłania dla tej metody akcji jest **DISP_STOCKFUNC_REFRESH**.  
  
 `COleControl`obsługuje dwie metody akcji: DoClick i Odśwież. Odświeżanie jest wywoływany przez kontrolki użytkownika można natychmiast zaktualizować wygląd formantu; DoClick jest wywoływane w celu wyzwalać formantu kliknij zdarzenie.  
  
|Metoda|Wpisu mapy wysyłania|Komentarz|  
|------------|------------------------|-------------|  
|`DoClick`|**(DISP_STOCKPROP_DOCLICK)**|Wyzwala zdarzenie Click.|  
|**Odśwież**|**(DISP_STOCKPROP_REFRESH)**|Aktualizacje od razu wygląd formantu.|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a>Dodawanie metody akcji przy użyciu Kreator dodawania metody  
 Dodawanie metody akcji jest prosty przy użyciu [Kreator dodawania metody](../ide/add-method-wizard.md). W poniższej procedurze przedstawiono dodawanie do formantu utworzonych za pomocą Kreatora kontrolki ActiveX MFC metoda odświeżania.  
  
#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Aby dodać podstawowe metoda odświeżania za pomocą Kreatora dodawania — metoda  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj metodę**.  
  
     Spowoduje to otwarcie Kreatora dodawania metody.  
  
5.  W **nazwę metody** kliknij **Odśwież**.  
  
6.  Kliknij przycisk **Zakończ**.  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a>Dodawanie metody kreatora zmiany dla metod standardowych  
 Ponieważ standardowych metoda odświeżania jest obsługiwany przez klasę podstawową dla formantu, **Kreator dodawania metody** nie zmienia deklaracja klasy formantu w dowolny sposób. Dodaje wpis dla metody do formantu mapy wysyłania oraz na jej. Plik IDL. Następujący wiersz zostanie dodany do mapy wysyłania formantu, znajduje się w jej wdrożenia (. Pliku CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 Dzięki temu metoda odświeżania dostępne dla użytkowników formantu.  
  
 Następujący wiersz jest dodawany do formantu. Plik IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 Ten wiersz przypisuje metoda odświeżania określonych numer identyfikacyjny.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

