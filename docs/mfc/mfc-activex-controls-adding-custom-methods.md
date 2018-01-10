---
title: 'Formanty MFC ActiveX: Dodawanie metod niestandardowych | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f79d4c5f7407e3de12ccf180a68b2b22e35bf10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>Kontrolki ActiveX MFC: dodawanie metod niestandardowych
Niestandardowe metody różnią się od metod standardowych, nie są już zaimplementowane przez `COleControl`. Należy podać implementacji dla każdej niestandardowej metody dodawany do formantu.  
  
 Użytkownik formantu ActiveX można wywołać metody niestandardowej w dowolnym momencie do wykonania akcji specyficzne dla formantu. Wpisu mapy wysyłania dla niestandardowej metody ma postać `DISP_FUNCTION`.  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a>Dodawanie niestandardowej metody z Kreator dodawania metody  
 W poniższej procedurze przedstawiono Dodawanie niestandardowej metody PtInCircle do formantu ActiveX szkielet kodu. PtInCircle Określa, czy współrzędne przekazany do formantu są wewnątrz lub na zewnątrz okręgu. Tę samą procedurę można również dodać innych metod niestandardowych. Zastąp nazwę niestandardowej metody i jego parametrów dla nazwy metody PtInCircle i parametry.  
  
> [!NOTE]
>  W tym przykładzie użyto `InCircle` funkcji w artykule zdarzenia. Aby uzyskać więcej informacji dotyczących tej funkcji, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie zdarzeń niestandardowych do formantu ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).  
  
#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Aby dodać PtInCircle niestandardowej metody za pomocą Kreatora dodawania — metoda  
  
1.  Załadowanie projektu formantu.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj metodę**.  
  
     Spowoduje to otwarcie Kreatora dodawania metody.  
  
5.  W **nazwę metody** wpisz `PtInCircle`.  
  
6.  W **wewnętrzna nazwa** wpisz nazwę metody wewnętrznej funkcji lub użyj wartości domyślnej (w tym przypadku `PtInCircle`).  
  
7.  W **typu zwracanego** kliknij **VARIANT_BOOL** dla zwracanego typu metody.  
  
8.  Przy użyciu **typ parametru** i **Nazwa parametru** formantów, Dodaj parametr o nazwie `xCoord` (typ **OLE_XPOS_PIXELS**).  
  
9. Przy użyciu **typ parametru** i **Nazwa parametru** formantów, Dodaj parametr o nazwie `yCoord` (typ **OLE_YPOS_PIXELS**).  
  
10. Kliknij przycisk **Zakończ**.  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a>Dodaj metody kreatora zmiany dla metod niestandardowych  
 Po dodaniu niestandardowej metody Kreator dodawania metody sprawia, że pewne zmiany do nagłówka klasy formantu (. H) i implementacji (. Pliki CPP). Następujący wiersz jest dodawany do deklaracji mapy wysyłania nagłówka klasy formantu (. H) plików:  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 Ten kod deklaruje obsługi metody wysyłania o nazwie `PtInCircle`. Ta funkcja może zostać wywołana kontroli użytkownik za pomocą zewnętrzną nazwę PtInCircle.  
  
 Następujący wiersz jest dodawany do formantu. Plik IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 Ten wiersz przypisuje metody PtInCircle określonych numer identyfikacyjny metody pozycję na liście właściwości i metod Kreator dodawania metody. Ponieważ Kreator dodawania metody został użyty do dodania niestandardowej metody, wpis dla niego był automatycznie dodawany do projektu. Plik IDL.  
  
 Ponadto następujący wiersz znajduje się w implementacji (. Pliku CPP) klasy formant został dodany do formantu mapy wysyłania:  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 `DISP_FUNCTION` Makra mapy metody PtInCircle funkcji obsługi formantu, `PtInCircle`, deklaruje typ zwrotny jako **VARIANT_BOOL**i deklaruje dwa parametry typu **vts_xpos_pixels —** i **VTS_YPOSPIXELS** do przekazania do `PtInCircle`.  
  
 Ponadto Kreator dodawania metody dodaje funkcję stub `CSampleCtrl::PtInCircle` z dolną krawędzią formantu implementacji (. Pliku CPP). Aby uzyskać `PtInCircle` działanie, jak wspomniano wcześniej, go muszą zostać zmodyfikowane w następujący sposób:  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Widok klasy i Przeglądarka obiektów, ikony](/visualstudio/ide/class-view-and-object-browser-icons)

