---
title: Klasa CComSimpleThreadAllocator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2c8c7b2e6132bb39c8e548f6057ded0b0ca6c1e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752482"
---
# <a name="ccomsimplethreadallocator-class"></a>Klasa CComSimpleThreadAllocator

Ta klasa zarządza wybór wątku dla klasy `CComAutoThreadModule`.

## <a name="syntax"></a>Składnia

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|Wybiera wątku.|

## <a name="remarks"></a>Uwagi

`CComSimpleThreadAllocator` zarządza wybór wątku [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread` po prostu przewijać każdego wątku i zwraca kolejny w sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="getthread"></a>  CComSimpleThreadAllocator::GetThread

Wybiera wątku, określając następny wątek w sekwencji.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Parametry

*pApt*  
Nie używany w ATL domyślną implementację.

*nThreads*  
Maksymalna liczba wątków w EXE module.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita między 0 a (*nThreads* - 1). Identyfikuje jeden z wątków w EXE module.

### <a name="remarks"></a>Uwagi

Można zastąpić `GetThread` zapewnienie inną metodę wyboru lub aby wprowadzić użytkowania *pApt* parametru.

`GetThread` jest wywoływana przez [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Zobacz też

[Klasa CComApartment](../../atl/reference/ccomapartment-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
