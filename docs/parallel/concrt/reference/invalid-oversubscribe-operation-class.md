---
title: invalid_oversubscribe_operation — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1728053c7b42afedb4cda9b2dc96a089750a866
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161700"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation — Klasa

Ta klasa opisuje wyjątek generowany, gdy `Context::Oversubscribe` metoda jest wywoływana z `_BeginOversubscription` parametr **false** bez uprzedniego wywołania do `Context::Oversubscribe` metody z `_BeginOversubscription` parametr wartość **true**.

## <a name="syntax"></a>Składnia

```
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Przeciążone. Konstruuje `invalid_oversubscribe_operation` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> invalid_oversubscribe_operation —

Konstruuje `invalid_oversubscribe_operation` obiektu.

```
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
