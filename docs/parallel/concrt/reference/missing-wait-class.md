---
title: missing_wait — Klasa
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: 68d24d710eec4fd602e64cc3cbde810db2b1a495
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297648"
---
# <a name="missingwait-class"></a>missing_wait — Klasa

Ta klasa opisuje wyjątek generowany, gdy istnieją zadania zaplanowane nadal `task_group` lub `structured_task_group` obiektu w czasie tego obiektu wykonuje destruktora. Ten wyjątek nigdy nie zostanie zgłoszony, jeśli zostanie osiągnięty destruktor, ze względu na stosie rozwinięcia jako wynik wyjątku.

## <a name="syntax"></a>Składnia

```
class missing_wait : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[missing_wait](#ctor)|Przeciążone. Konstruuje `missing_wait` obiektu.|

## <a name="remarks"></a>Uwagi

Nieobecny przepływu wyjątek odpowiedzialność za wywołanie dowolnej `wait` lub `run_and_wait` metody `task_group` lub `structured_task_group` obiektu przed zezwoleniem na ten obiekt do niszczenia. Środowisko wykonawcze zgłasza ten wyjątek w celu wskazania, że pamiętasz wywołać `wait` lub `run_and_wait` metody.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`missing_wait`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> missing_wait —

Konstruuje `missing_wait` obiektu.

```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[task_group, klasa](task-group-class.md)<br/>
[Czekaj](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group, klasa](structured-task-group-class.md)
