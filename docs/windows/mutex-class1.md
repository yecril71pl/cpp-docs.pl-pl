---
title: Mutex Class1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9a9e9674dd8ac5aa7d444a77df66c1aff4a70299
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878414"
---
# <a name="mutex-class1"></a>Mutex Class1
Reprezentuje obiekt synchronizacji wyłącznie kontrolujące zasobu udostępnionego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|**SyncLock**|Synonim dla klasy, która obsługuje synchronicznej blokad.|  
  
### <a name="public-constructor"></a>Konstruktor publiczny  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Mutex::Mutex, konstruktor](../windows/mutex-mutex-constructor.md)|Inicjuje nowe wystąpienie klasy obiektu Mutex.|  
  
### <a name="public-members"></a>Publiczne elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Mutex::Lock, metoda](../windows/mutex-lock-method.md)|Czeka, aż do bieżącego obiektu lub obiektu Mutex skojarzonego z określonego dojścia zwalnia obiektu mutex lub przed upływem określonego limitu czasu.|  
  
### <a name="public-operator"></a>Operator publiczny  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator Mutex::operator=](../windows/mutex-operator-assign-operator.md)|Przypisuje (przenosi) określonego obiektu Mutex obiekt do bieżącego obiektu Mutex.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Mutex`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)