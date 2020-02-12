---
title: bad_target — Klasa
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 023607ff142b7fa39165cc9b5280a8e9345a3645
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142857"
---
# <a name="bad_target-class"></a>bad_target — Klasa

Ta klasa opisuje wyjątek zgłoszony, gdy blok komunikatów otrzymuje wskaźnik do obiektu docelowego, który jest nieprawidłowy dla wykonywanej operacji.

## <a name="syntax"></a>Składnia

```cpp
class bad_target : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[bad_target](#ctor)|Przeciążone. Konstruuje obiekt `bad_target`.|

## <a name="remarks"></a>Uwagi

Ten wyjątek jest zazwyczaj generowany z powodów, takich jak obiekt docelowy próbujący wykorzystać komunikat, który jest zarezerwowany dla innego obiektu docelowego lub zwalnia rezerwację, która nie została wstrzymana.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`bad_target`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>bad_target

Konstruuje obiekt `bad_target`.

```cpp
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md)
