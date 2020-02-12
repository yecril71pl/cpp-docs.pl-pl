---
title: context_unblock_unbalanced — Klasa
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: 261ec96c1a83fbec423e6dbbfe403c4db53a2962
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143097"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy wywołania metod `Block` i `Unblock` obiektu `Context` nie są prawidłowo sparowane.

## <a name="syntax"></a>Składnia

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|Przeciążone. Konstruuje obiekt `context_unblock_unbalanced`.|

## <a name="remarks"></a>Uwagi

Wywołania metod `Block` i `Unblock` obiektu `Context` muszą zawsze być prawidłowo sparowane. Środowisko uruchomieniowe współbieżności umożliwia wykonywanie operacji w dowolnej kolejności. Na przykład wywołanie `Block` może następować po wywołaniu `Unblock`lub na odwrót. Ten wyjątek zostałby wygenerowany, jeśli na przykład dwa wywołania metody `Unblock` zostały wykonane w wierszu, obiekt `Context`, który nie został zablokowany.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>context_unblock_unbalanced

Konstruuje obiekt `context_unblock_unbalanced`.

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
