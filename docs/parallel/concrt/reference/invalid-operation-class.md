---
title: invalid_operation — Klasa
ms.date: 11/04/2016
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
ms.openlocfilehash: 8b971a12ff83753546cfea7b90288d1bc43400c0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341039"
---
# <a name="invalidoperation-class"></a>invalid_operation — Klasa

Ta klasa opisuje wyjątek generowany, gdy jest wykonywana Nieprawidłowa operacja, która jest dokładniej opisana przez inny typ wyjątku generowanego przez środowisko uruchomieniowe współbieżności.

## <a name="syntax"></a>Składnia

```
class invalid_operation : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[invalid_operation](#ctor)|Przeciążone. Konstruuje `invalid_operation` obiektu.|

## <a name="remarks"></a>Uwagi

Różne metody, które generują ten wyjątek będzie na ogół udokumentowane w jakich okolicznościach go generują.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_operation`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> invalid_operation —

Konstruuje `invalid_operation` obiektu.

```
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
