---
title: "Cel atrybutów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed20c29d017527d5c2ce0b0c5ab8053fc75dc6ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="purpose-of-attributes"></a>Cel atrybutów
Atrybuty rozszerzenia C++ w kierunkach nie jest obecnie możliwe bez przerywania klasycznego struktury języka. Atrybuty zezwalać dostawców (oddzielne dll), aby rozszerzyć funkcjonalność języka dynamicznie. Podstawowym celem atrybutów jest uproszczenie tworzenia składników modelu COM, oprócz zwiększeniu poziomu wydajności projektanta składników. Można zastosować atrybutów do niemal wszystkie konstrukcji języka C++, takich jak klasy, elementy członkowskie danych lub funkcji elementów członkowskich. Poniżej przedstawiono wyróżnienie korzyści zapewniane przez to nowa technologia:  
  
-   Przedstawia znanych i proste konwencję wywołania.  
  
-   Używa dodaje kod, który w odróżnieniu od makra, jest rozpoznawana przez debuger.  
  
-   Umożliwia łatwe tworzenie wartości pochodnych z klas podstawowych bez szczegóły implementacji uciążliwe.  
  
-   Zastępuje dużą ilość kodu języka IDL wymagane przez składnik modelu COM o kilka atrybutów zwięzły.  
  
 Na przykład, aby zaimplementować klasy ogólnej ATL w zbiorniku zdarzenie proste, należy zastosować [event_receiver](../windows/event-receiver.md) atrybutu do określonej klasy, takich jak `CMyReceiver`. **Event_receiver** atrybutu jest następnie opracowane przez kompilator języka Visual C++, która wstawia prawidłowego kodu do pliku obiektu.  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 Następnie można ustawić **CMyReceiver** metody `handler1` i `handler2` do obsługi zdarzeń (przy użyciu funkcji wewnętrznej [__hook](../cpp/hook.md)) ze źródła zdarzeń, które można utworzyć przy użyciu [event_source —](../windows/event-source.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../windows/attributed-programming-concepts.md)