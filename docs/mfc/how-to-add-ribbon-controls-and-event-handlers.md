---
title: 'Porady: dodawanie formantów wstążki do programów obsługi zdarzeń | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 176323137b2ace0d27d9de162da7fa022441aa88
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Porady: dodawanie formantów wstążki do programów obsługi zdarzeń
Formanty wstążki są elementów, takich jak przycisków i pola kombi, które dodajesz do paneli. Panele są obszarów pasek wstążki wyświetlających grupy pokrewnych formantów.  
  
 W tym temacie będzie Otwórz projektanta wstążki, Dodawanie przycisku, a następnie połącz zdarzenie, które wyświetla "Hello World".  
  
### <a name="to-open-the-ribbon-designer"></a>Aby otworzyć projektanta wstążki  
  
1.  W programie Visual Studio na **widoku** menu, kliknij przycisk **widok zasobów**.  
  
2.  W **widok zasobów**, kliknij dwukrotnie plik zasobu wstążki, aby go wyświetlić na powierzchni projektu.  
  
### <a name="to-add-a-button-and-an-event-handler"></a>Aby dodać przycisk i program obsługi zdarzeń  
  
1.  Z **narzędzi**, kliknij przycisk **przycisk** i przeciągnij go do panelu na powierzchnię projektu.  
  
2.  Kliknij prawym przyciskiem myszy przycisk, a następnie kliknij przycisk **Dodaj program obsługi zdarzeń**.  
  
3.  W **Kreator obsługi zdarzeń**Sprawdź ustawienia domyślne i kliknij **dodawać i edytować**. Aby uzyskać więcej informacji, zobacz [Kreator obsługi zdarzeń](../ide/event-handler-wizard.md).  
  
4.  W edytorze kodu Dodaj następujący kod do funkcji programu obsługi:  
  
 ```  
    MessageBox((LPCTSTR)L"Hello World");

 ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykład RibbonGadgets: Wstążki gadżetów aplikacji](../visual-cpp-samples.md)   
 [Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)

