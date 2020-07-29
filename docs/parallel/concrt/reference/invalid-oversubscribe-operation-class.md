---
title: invalid_oversubscribe_operation — Klasa
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 0c95d234fee412c1dacb014dd135ca56fc73bf5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193968"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy `Context::Oversubscribe` Metoda jest wywoływana z `_BeginOversubscription` parametrem ustawionym na **`false`** bez wcześniejszego wywołania `Context::Oversubscribe` metody z `_BeginOversubscription` parametrem ustawionym na **`true`** .

## <a name="syntax"></a>Składnia

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Przeciążone. Konstruuje `invalid_oversubscribe_operation` obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="invalid_oversubscribe_operation"></a><a name="ctor"></a>invalid_oversubscribe_operation

Konstruuje `invalid_oversubscribe_operation` obiekt.

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
