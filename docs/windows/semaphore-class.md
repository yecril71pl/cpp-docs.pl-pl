---
title: Klasa semaforu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60373c12220fce57672389b98455a123990f3c93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="semaphore-class"></a>Semaphore — Klasa
Reprezentuje obiekt synchronizacji, która kontroluje, czy obsługują ograniczoną liczbę użytkowników zasobu udostępnionego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`SyncLock`|Synonim dla klasy, która obsługuje synchronicznej blokad.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Semaphore::Semaphore, konstruktor](../windows/semaphore-semaphore-constructor.md)|Inicjuje nowe wystąpienie klasy semafora.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[InvokeHelper::Invoke, metoda](../windows/invokehelper-invoke-method.md)|Wywołuje program obsługi zdarzeń, którego sygnatura zawiera określoną liczbę argumentów.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Semaphore::Lock, metoda](../windows/semaphore-lock-method.md)|Czeka, aż do bieżącego obiektu lub obiektów skojarzonych z określonego dojścia jest w stanie sygnałowego lub przed upływem określonego limitu czasu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator Semaphore::operator=](../windows/semaphore-operator-assign-operator.md)|Przenosi bieżący obiekt semafora określone dojście z obiektu semafora.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Semaphore`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)