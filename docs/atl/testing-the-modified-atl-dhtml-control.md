---
title: Testowanie kontroli zmodyfikowane DHTML ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 84b9aa9ffb04b807cba07fdd3577622f62f6ab45
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Testowanie kontroli zmodyfikowane DHTML ATL
Wypróbuj nowe formantu można zobaczyć, jak działa teraz.  
  
#### <a name="to-build-and-test-the-modified-control"></a>Tworzenie i testowanie zmodyfikowanego formantu  
  
1.  Ponownie skompilować projekt i otworzyć go w kontenerze testowym. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat sposobu dostępu kontener testu.  
  
     Rozmiar formantu do wyświetlenia wszystkich przycisków dodane.  
  
2.  Sprawdź, czy dwa przyciski wstawione przez zmodyfikowanie pliku HTML. Każdy przycisk posiada etykiety został zidentyfikowany w [modyfikacji formantu ATL DHTML](../atl/modifying-the-atl-dhtml-control.md): **Odśwież** i **HelloHTML**.  
  
3.  Przetestuj dwa nowe przyciski, aby zobaczyć, jak działają.  
  
 Teraz można przetestować metody, które nie są częścią interfejsu użytkownika.  
  
1.  Zaznacz formantu, więc obramowania jest aktywny.  
  
2.  Na **kontroli** menu, kliknij przycisk **wywołania metody**.  
  
 Metody z listy **nazwę metody** metod, które można wywołać kontenera: `MethodInvoked` i `GoToURL`. Wszystkie inne metody są kontrolowane przez interfejs użytkownika.  
  
1.  Wybierz metodę do wywołania, a następnie kliknij przycisk `Invoke` wyświetlany komunikat metody lub przejdź do www.microsoft.com.  
  
2.  W **wywołania metody** okno dialogowe, kliknij przycisk **Zamknij**.  
  
 Aby dowiedzieć się więcej na temat różnych elementów i plików, które tworzą formantu ATL DHTML, zobacz [określający elementy projektu kontroli DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa dla DHTML](../atl/atl-support-for-dhtml-controls.md)

