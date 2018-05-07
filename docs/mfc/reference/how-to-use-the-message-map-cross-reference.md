---
title: 'Porady: używanie odsyłacza mapy komunikatów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d59d0bfc75f654cd9f8f15ff851ad42a619e271f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

