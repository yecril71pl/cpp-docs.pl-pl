---
title: scheduler_resource_allocation_error — Klasa
ms.date: 11/04/2016
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
ms.openlocfilehash: 7f7254306253aabc33f46694f3da16734e6efccf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276497"
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

##  <a name="get_error_code"></a> get_error_code

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

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
