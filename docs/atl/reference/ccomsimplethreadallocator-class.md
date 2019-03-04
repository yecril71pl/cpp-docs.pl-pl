---
title: Klasa CComSimpleThreadAllocator
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: ef1f86ca832674ba5710083b08b67f0a775a7a33
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261898"
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

*pApt*<br/>
Nie używany w ATL domyślną implementację.

*nThreads*<br/>
Maksymalna liczba wątków w EXE module.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita między 0 a (*nThreads* - 1). Identyfikuje jeden z wątków w EXE module.

### <a name="remarks"></a>Uwagi

Można zastąpić `GetThread` zapewnienie inną metodę wyboru lub aby wprowadzić użytkowania *pApt* parametru.

`GetThread` jest wywoływana przez [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Zobacz także

[Klasa CComApartment](../../atl/reference/ccomapartment-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
