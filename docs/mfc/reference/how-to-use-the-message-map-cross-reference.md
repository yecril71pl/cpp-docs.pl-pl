---
title: "Porady: używanie odsyłacza mapy komunikatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.messages
dev_langs: C++
helpviewer_keywords: windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ffa7b39962d78476e971750e92569eb14229606b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Porady: używanie odsyłacza mapy komunikatów
W pozycji z etykietą \<memberFxn >, napisz własną funkcję elementu członkowskiego dla pochodnego [CWnd](../../mfc/reference/cwnd-class.md) klasy. Nadaj funkcji dowolną nazwę, którą chcesz. Inne funkcje, takie jak `OnActivate`, są funkcje elementów członkowskich klasy `CWnd`. Jeśli wywołany, przekazaniem ich do `DefWindowProc` funkcji systemu Windows. Aby przetwarzać komunikatów powiadomień systemu Windows, Zastąp odpowiadającą jej `CWnd` funkcji w klasie pochodnej. Funkcja powinna wywołać funkcję zastąpiony w klasie podstawowej, aby umożliwić klasy podstawowej i udzielenia odpowiedzi systemu Windows.  
  
 We wszystkich przypadkach, umieść prototypu funkcji w `CWnd`-nagłówka klasy pochodnej i kod wpisu mapy wiadomości, jak pokazano.  
  
 Poniższe terminy są używane:  
  
|Termin|Definicja|  
|----------|----------------|  
|identyfikator|Wszelkie zdefiniowane przez użytkownika identyfikator elementu menu (**WM_COMMAND** wiadomości) lub identyfikator (komunikaty powiadomień okna podrzędnego) formantu.|  
|"komunikat" i "wNotifyCode"|Windows komunikatów identyfikatory, zgodnie z definicją w systemie WINDOWS. H.|  
|nMessageVariable|Nazwa zmiennej, która zawiera wartość zwrotną z elementu **RegisterWindowMessage** funkcji systemu Windows.|  
  
## <a name="see-also"></a>Zobacz też  
 [Mapy komunikatów](../../mfc/reference/message-maps-mfc.md)

