---
title: Cel atrybutów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ea3b731cc22d144e2e20dc70f14e6b0b76b1479
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877839"
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