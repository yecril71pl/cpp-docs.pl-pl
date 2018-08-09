---
title: WeakReference, klasa1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 71de341be0cb482a49cbf35ddd34e414be8afde4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645545"
---
# <a name="weakreference-class1"></a>WeakReference, klasa1
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class WeakReference;  
```  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje *słabe odwołanie* które mogą być używane z Windows Runtime lub Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.  
  
 A **WeakReference** obiekt zachowuje *silne odwołanie*, który jest wskaźnikiem do obiektu, a *liczba silne odwołanie*, czyli liczbę kopii silnej odwołanie, które zostały przekazane przez `Resolve()` metody. Podczas gdy liczba silne odwołanie jest różna od zera, silne odwołanie jest prawidłowy, a obiekt jest dostępny. Gdy liczba silne odwołanie staje się zerem, silne odwołanie jest nieprawidłowe i obiektu jest niedostępny.  
  
 A **WeakReference** obiekt jest zwykle używana do reprezentowania obiekt, którego istnienie jest kontrolowane przez zewnętrzny wątek lub aplikację. Na przykład, utworzyć **WeakReference** obiektu z odwołaniem do obiektu pliku. Gdy plik jest otwarty, silne odwołanie jest prawidłowy. Ale jeśli ten plik będzie zamknięty, silne odwołanie staje się nieprawidłowy.  
  
 **WeakReference** metody są bezpieczne dla wątków.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[WeakReference::WeakReference, konstruktor](../windows/weakreference-weakreference-constructor.md)|Inicjuje nowe wystąpienie klasy **WeakReference** klasy.|  
|[WeakReference::~WeakReference, destruktor](../windows/weakreference-tilde-weakreference-destructor.md)|Wyłącza (niszczy) bieżące wystąpienie **WeakReference** klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference, metoda](../windows/weakreference-decrementstrongreference-method.md)|Dekrementuje silne odwołanie zliczane bieżącego **WeakReference** obiektu.|  
|[WeakReference::IncrementStrongReference, metoda](../windows/weakreference-incrementstrongreference-method.md)|Zwiększa liczbę silne odwołanie bieżącego **WeakReference** obiektu.|  
|[WeakReference::Resolve, metoda](../windows/weakreference-resolve-method.md)|Ustawia określony wskaźnik do bieżącej wartości silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.|  
|[WeakReference::SetUnknown, metoda](../windows/weakreference-setunknown-method.md)|Ustawia silne odwołanie bieżącego **WeakReference** obiekt określony wskaźnik interfejsu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `WeakReference`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)