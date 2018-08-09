---
title: Klasa semaforu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5feb954a5bba1bfc7c3a98b1324e75bd2aa058f1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015706"
---
# <a name="semaphore-class"></a>Semaphore — Klasa
Reprezentuje obiekt synchronizacji, który kontroluje zasobu udostępnionego, który może obsługiwać ograniczoną liczbę użytkowników.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`SyncLock`|Synonim dla klasy, która obsługuje synchronicznej blokad.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Semaphore::Semaphore, konstruktor](../windows/semaphore-semaphore-constructor.md)|Inicjuje nowe wystąpienie klasy **semafora** klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InvokeHelper::Invoke, metoda](../windows/invokehelper-invoke-method.md)|Wywołuje program obsługi zdarzeń, którego podpis zawiera określoną liczbę argumentów.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Semaphore::Lock, metoda](../windows/semaphore-lock-method.md)|Czeka, aż do bieżącego obiektu lub obiektów skojarzonych z określone dojście jest w stanie sygnałowego lub przed upływem określonego limitu czasu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator Semaphore::operator=](../windows/semaphore-operator-assign-operator.md)|Przenosi określone dojście z **semafora** obiekt do bieżącego **semafora** obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Semaphore`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)