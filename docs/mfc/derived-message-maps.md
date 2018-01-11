---
title: "Pochodzące z mapy komunikatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e5901602368e60a3873a1dba2fc681c6ac146f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="derived-message-maps"></a>Pochodne mapy komunikatów
Podczas komunikat obsługi, sprawdzanie komunikatów dla klasy mapy nie jest końca artykułu mapy komunikatów. Co się stanie, jeśli klasa `CMyView` (pochodną `CView`) nie ma pasującego wpisu wiadomości  
  
 Należy pamiętać, że `CView`, klasa podstawowa `CMyView`, od którego pochodzi z kolei `CWnd`. W związku z tym `CMyView` *jest* `CView` i *jest* `CWnd`. Każda z tych klas ma własną mapy komunikatów. Wartość "A Widok hierarchii" poniżej przedstawia relacje hierarchiczne klasy, ale należy pamiętać, że `CMyView` obiekt jest pojedynczy obiekt, który ma właściwości wszystkich trzech klas.  
  
 ![Hierarchia widoku](../mfc/media/vc38621.gif "vc38621")  
Wyświetlanie hierarchii  
  
 Tak, jeśli nie można dopasować wiadomości w klasie `CMyView`na mapę komunikatów w ramach wyszukuje również mapę komunikatów w swojej klasie podstawowej bezpośrednim. `BEGIN_MESSAGE_MAP` Makro na początku mapy wiadomości określa dwie nazwy klasy jako argumenty:  
  
 [!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]  
  
 Pierwszy argument nazwy klasy, do której należy mapy komunikatów. Drugi argument zapewnia połączenie z bezpośrednim klasy podstawowej — `CView` tutaj — platformę można wyszukiwać za jego mapę komunikatów.  
  
 Programy obsługi wiadomości w klasie podstawowej, w związku z tym są dziedziczone przez klasy pochodnej. Jest to bardzo podobnie do normalnych wirtualnych funkcji Członkowskich bez konieczności Tworzenie wirtualnego wszystkie funkcje Członkowskie obsługi.  
  
 Jeśli nie odnaleźć programu obsługi jest w żadnym z mapy komunikatów klasy podstawowej, przeprowadzane jest domyślne przetwarzania komunikatu. Jeśli komunikat jest polecenie, platformę kieruje je do następnego docelowym polecenia. Jeśli jest standardowych komunikatów systemu Windows, wiadomości są przekazywane do odpowiednich domyślną procedurę okna.  
  
 Aby przyśpieszyć dopasowania mapy komunikatów, platformę buforuje ostatnie dopasowań na prawdopodobieństwo, że go otrzymają tę samą wiadomość ponownie. W wyniku tego jest procesów framework bardzo wydajnie nieobsługiwany wiadomości. Mapy komunikatów zajmują również więcej miejsca niż implementacje używające funkcji wirtualnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)

