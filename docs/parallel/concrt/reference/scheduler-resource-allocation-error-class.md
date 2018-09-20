---
title: scheduler_resource_allocation_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
dev_langs:
- C++
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8639e70e74f122da8ffa2d58501ad04884aa306
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437147"
---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error — Klasa

Ta klasa opisuje wyjątek generowany z powodu błędu można uzyskać krytycznym zasobem w środowisku uruchomieniowym współbieżności.

## <a name="syntax"></a>Składnia

```
class scheduler_resource_allocation_error : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scheduler_resource_allocation_error](#ctor)|Przeciążone. Konstruuje `scheduler_resource_allocation_error` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_error_code](#get_error_code)|Zwraca kod błędu, który spowodował wyjątek.|

## <a name="remarks"></a>Uwagi

Ten wyjątek zazwyczaj jest zgłaszany, gdy system operacyjny z w środowisku uruchomieniowym współbieżności: wywołanie zakończy się niepowodzeniem. Kod błędu, który normalnie zostałyby zwrócone w wyniku wywołania metody Win32 `GetLastError` jest konwertowana na wartość typu `HRESULT` i mogą być pobierane przy użyciu `get_error_code` metody.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`scheduler_resource_allocation_error`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="get_error_code"></a> get_error_code —

Zwraca kod błędu, który spowodował wyjątek.

```
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>Wartość zwracana

`HRESULT` Wartości błędu, który spowodował wyjątek.

##  <a name="ctor"></a> scheduler_resource_allocation_error

Konstruuje `scheduler_resource_allocation_error` obiektu.

```
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

*_Hresult*<br/>
`HRESULT` Wartości błędu, który spowodował wyjątek.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
