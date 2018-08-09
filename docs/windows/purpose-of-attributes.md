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
ms.openlocfilehash: 4f44d6e4db7e09033e9c3f05d94cbf5294b306a3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018285"
---
# <a name="purpose-of-attributes"></a>Cel atrybutów
Atrybuty rozszerzenia C++ w kierunkach nie jest obecnie możliwe bez przerywania klasycznej struktury języka. Atrybuty zezwalać na dostawców (oddzielne biblioteki dll) do rozszerzenia funkcji języka dynamicznie. Podstawowym celem atrybutów jest uproszczenie tworzenia składników modelu COM, oprócz zwiększenie poziomu wydajności dla deweloperów składników. Atrybuty mogą być stosowane do niemal C++ konstrukcji, takich jak klasy, elementy członkowskie danych lub elementów członkowskich. Wyróżnienie korzyści zapewniane przez nowej technologii jest następująca:  
  
-   Opisuje dobrze znanych i proste konwencji wywoływania.  
  
-   Zastosowań wstawiony kod, który w przeciwieństwie do makra, rozpoznawanym przez debuger.  
  
-   Umożliwia łatwe tworzenie wartości pochodnych z klas bazowych bez szczegółów implementacji uciążliwe.  
  
-   Zastępuje dużą ilość kodu języka IDL wymagane przez składnik COM za pomocą kilku atrybutów zwięzły.  
  
 Na przykład, aby zaimplementować obiekt sink zdarzenia prostego ogólne klasy ATL, należy zastosować [event_receiver](../windows/event-receiver.md) atrybutu do określonej klasy, takie jak `CMyReceiver`. `event_receiver` Atrybutu są następnie kompilowane przez kompilator Visual C++, który wstawia prawidłowego kodu do pliku obiektu.  
  
```cpp  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 Następnie można skonfigurować `CMyReceiver` metody `handler1` i `handler2` do obsługi zdarzeń (przy użyciu wewnętrznej funkcji [__hook](../cpp/hook.md)) ze źródła zdarzeń, który można utworzyć przy użyciu [event_source](../windows/event-source.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../windows/attributed-programming-concepts.md)