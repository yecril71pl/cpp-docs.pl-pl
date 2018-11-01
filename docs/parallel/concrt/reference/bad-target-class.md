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
ms.openlocfilehash: 0440955718bee3b426f5e4625b5eb3fc559a5d28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434486"
---
# <a name="badtarget-class"></a>bad_target — Klasa

Ta klasa opisuje wyjątek generowany, gdy blok obsługi wiadomości podano wskaźnik do obiektu docelowego, która jest nieprawidłowa dla wykonywanej operacji.

## <a name="syntax"></a>Składnia

```
class bad_target : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[bad_target](#ctor)|Przeciążone. Konstruuje `bad_target` obiektu.|

## <a name="remarks"></a>Uwagi

To jest zwykle wyjątek powodów, takich jak docelowy próby używanie komunikat, który jest zarezerwowana w innej docelowej lub zwalnianiu zliczania rezerwacji, który przechowuje.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`bad_target`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> bad_target —

Konstruuje `bad_target` obiektu.

```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md)

