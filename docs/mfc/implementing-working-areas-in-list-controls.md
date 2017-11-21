---
title: "Implementowanie obszarów roboczych w formantach listy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8376a65a511f2a59342aa59f86a9cd6ecd9768e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementowanie obszarów roboczych w kontrolkach listy
Domyślnie przez kontrolki listy Rozmieszcza wszystkie elementy w sposób standardowy siatki. Jednak inna metoda jest obsługiwana, praca obszary Rozmieszcza elementy listy grup prostokątny. W przypadku obrazu formantu listy, który zawiera obszary robocze, zobacz za pomocą kontrolki widok listy w zestawie Windows SDK.  
  
> [!NOTE]
>  Obszary robocze są widoczne tylko wtedy, gdy kontrolka listy jest w trybie małych ikon lub ikonę. Jednak wszystkie bieżące obszary robocze są obsługiwane, jeśli widok się przełączone do trybu raportu lub listy.  
  
 Obszary robocze można wyświetlić puste obramowania (w lewo, top lub prawej elementy) lub spowodować poziomy pasek przewijania będzie wyświetlana po zwykle nie istnieć jedna. Inny użycie wspólnej jest można utworzyć wiele obszary robocze, do których elementów można przeniesiony lub usunięty. Przy użyciu tej metody można utworzyć obszary, w ramach jednego widoku, który ma inną funkcję. Użytkownik może następnie skategoryzować elementy przez umieszczenie ich w inny obszar. Przykładem tego może być widokiem systemu plików, który ma obszaru do odczytu i zapisu plików i w innym obszarze plików tylko do odczytu. Jeśli element pliku zostały przeniesione do obszaru tylko do odczytu, automatycznie czy stanie tylko do odczytu. Przenoszenie plików z widoku tylko do odczytu do obszaru odczytu/zapisu spowodowałoby pliku odczytu/zapisu.  
  
 `CListCtrl`zawiera kilka funkcji elementów członkowskich do tworzenia i zarządzania obszary robocze w formancie z listy. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) i [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) pobierać i ustawiać tablicę `CRect` obiektów (lub `RECT` struktury), który przechowywania obecnie implementowane obszary robocze dla formantu listy. Ponadto [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) pobiera bieżącą liczbę obszary robocze dla formantu listy (domyślnie 0).  
  
## <a name="items-and-working-areas"></a>Elementy i obszarów roboczych  
 Po utworzeniu obszaru roboczego elementy, które znajdują się w obszarze roboczym stać się członkami go. Podobnie jeśli element zostanie przeniesiony do obszaru roboczego, staje się on członkiem obszar roboczy, do której została przeniesiona. Jeśli element nie leży w dowolnym obszarze roboczym, staje się automatycznie członkiem pierwszego obszaru roboczego (indeks 0). Jeśli chcesz utworzyć element i umieścić w obszarze roboczym, należy utworzyć elementu i przenieś go do obszaru roboczego żądaną wywołaniem [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Drugi przykład poniżej przedstawiono tej metody.  
  
 Poniższy przykład implementuje czterech obszarów roboczych (`rcWorkAreas`), taki sam rozmiar z pikseli-10-całego obramowania każdego obszaru roboczego w formancie listy (`m_WorkAreaListCtrl`).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]  
  
 Wywołanie [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) została wprowadzona, aby oszacować całkowitego obszaru wymagane, aby wyświetlić wszystkie elementy w jeden region. Ta Szacowana następnie jest podzielony na cztery regiony i wypełniane obramowanie 5 pikseli na poziomie.  
  
 Kolejnym przykładzie przypisuje istniejących elementów listy do każdej grupy (`rcWorkAreas`) oraz odświeżenie widoku kontrolki (`m_WorkAreaListCtrl`) do ukończenia efekt.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

