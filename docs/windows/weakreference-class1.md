---
title: "Weakreference — Class1 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference
dev_langs: C++
helpviewer_keywords: WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8985434365cb8144fc2ee3680ef19c5b8ed99301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="weakreference-class1"></a>Weakreference — Class1
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class WeakReference;  
```  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje *słabe odwołanie* które mogą być używane z środowiska wykonawczego systemu Windows lub klasycznego modelu COM. Słabe odwołanie reprezentuje obiekt, który może lub nie mogą być niedostępne.  
  
 A `WeakReference` obiekt zachowuje *silne odwołanie*, która jest wskaźnik do obiektu, a *liczba silne odwołanie*, czyli liczby kopii silne odwołanie, które zostały przekazane przez Metoda Resolve(). Podczas gdy liczba silne odwołanie jest różna od zera, silne odwołanie jest prawidłowe, a obiekt jest dostępny. Liczba silne odwołanie wynosi zero, silne odwołanie jest nieprawidłowe, a obiekt jest niedostępny.  
  
 Obiekt weakreference — zazwyczaj jest używana do reprezentowania obiekt, którego istnienie jest kontrolowany przez wątek zewnętrznych lub aplikacji. Na przykład utworzyć obiekt weakreference — z odwołaniem do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowe. Jednak jeśli plik zostanie zamknięty, silne odwołanie staje się nieprawidłowy.  
  
 Metody weakreference — są bezpieczne dla wątków.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[WeakReference::WeakReference, konstruktor](../windows/weakreference-weakreference-constructor.md)|Inicjuje nowe wystąpienie klasy weakreference —.|  
|[WeakReference::~WeakReference, destruktor](../windows/weakreference-tilde-weakreference-destructor.md)|Deinitializes (niszczy) bieżące wystąpienie klasy weakreference — klasa.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference, metoda](../windows/weakreference-decrementstrongreference-method.md)|Zmniejsza silne odwołanie liczba bieżące weakreference — obiektu.|  
|[WeakReference::IncrementStrongReference, metoda](../windows/weakreference-incrementstrongreference-method.md)|Zwiększa liczbę silne odwołanie do bieżącego obiektu weakreference —.|  
|[WeakReference::Resolve, metoda](../windows/weakreference-resolve-method.md)|Ustawia określony wskaźnik do bieżącej wartości silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.|  
|[WeakReference::SetUnknown, metoda](../windows/weakreference-setunknown-method.md)|Ustawia silne odwołanie obiektu bieżące weakreference — wskaźnik określonego interfejsu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `WeakReference`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)