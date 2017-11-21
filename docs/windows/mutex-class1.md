---
title: Mutex Class1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs: C++
helpviewer_keywords: Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b3f0295ce9456822337c9beac3e6d1c35f7d80bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Mutex::mutex — Konstruktor](../windows/mutex-mutex-constructor.md)|Inicjuje nowe wystąpienie klasy obiektu Mutex.|  
  
### <a name="public-members"></a>Publiczne elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Mutex::Lock — Metoda](../windows/mutex-lock-method.md)|Czeka, aż do bieżącego obiektu lub obiektu Mutex skojarzonego z określonego dojścia zwalnia obiektu mutex lub przed upływem określonego limitu czasu.|  
  
### <a name="public-operator"></a>Operator publiczny  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Mutex::operator = — Operator](../windows/mutex-operator-assign-operator.md)|Przypisuje (przenosi) określonego obiektu Mutex obiekt do bieżącego obiektu Mutex.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Mutex`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: wrappers — Namespace](../windows/microsoft-wrl-wrappers-namespace.md)