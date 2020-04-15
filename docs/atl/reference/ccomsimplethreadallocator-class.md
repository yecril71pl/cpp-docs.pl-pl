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
ms.openlocfilehash: 4a3cce492db4db9f46aeb4efe738ee6a594ddcfc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327342"
---
# <a name="ccomsimplethreadallocator-class"></a>Klasa CComSimpleThreadAllocator

Ta klasa zarządza wyborem `CComAutoThreadModule`wątku dla klasy .

## <a name="syntax"></a>Składnia

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSimpleLokator:GetThread](#getthread)|Wybiera wątek.|

## <a name="remarks"></a>Uwagi

`CComSimpleThreadAllocator`zarządza wyborem [wątku dla CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`po prostu przechodzi przez każdy wątek i zwraca następny w sekwencji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a>CComSimpleLokator:GetThread

Wybiera wątek, określając następny wątek w sekwencji.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Parametry

*pApt (pApt)*<br/>
Nie jest używany w domyślnej implementacji ATL.

*nWątki*<br/>
Maksymalna liczba wątków w module EXE.

### <a name="return-value"></a>Wartość zwracana

Liczą całkowitą między*nThreads* oder. Identyfikuje jeden z wątków w module EXE.

### <a name="remarks"></a>Uwagi

Można `GetThread` zastąpić, aby zapewnić inną metodę wyboru lub użyć *pApt* parametru.

`GetThread`jest wywoływana przez [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Zobacz też

[Klasa CComapartment](../../atl/reference/ccomapartment-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
