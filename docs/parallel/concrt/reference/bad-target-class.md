---
title: bad_target — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b13aecabbf7f9935671b6bd44b654e78c5cd58dd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395079"
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

