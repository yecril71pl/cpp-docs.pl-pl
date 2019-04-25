---
title: context_self_unblock — Klasa
ms.date: 11/04/2016
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
ms.openlocfilehash: 900dc68eac4441bd1db3818d3c1f30698b80a6e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296179"
---
# <a name="contextselfunblock-class"></a>context_self_unblock — Klasa

Ta klasa opisuje wyjątek generowany, gdy `Unblock` metody `Context` obiektu jest wywoływana z tym samym kontekście. To wskazuje w danym kontekście zostanie podjęta próba odblokowania sam.

## <a name="syntax"></a>Składnia

```
class context_self_unblock : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[context_self_unblock](#ctor)|Przeciążone. Konstruuje `context_self_unblock` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`context_self_unblock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> context_self_unblock

Konstruuje `context_self_unblock` obiektu.

```
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
