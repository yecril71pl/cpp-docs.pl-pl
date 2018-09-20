---
title: message_not_found — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
dev_langs:
- C++
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e73a33817ef39d8998173dacc282e6ee9477944
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445613"
---
# <a name="messagenotfound-class"></a>message_not_found — Klasa

Ta klasa opisuje wyjątek generowany, gdy blok komunikatów jest nie można odnaleźć żądanej wiadomości.

## <a name="syntax"></a>Składnia

```
class message_not_found : public std::exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[message_not_found](#ctor)|Przeciążone. Konstruuje `message_not_found` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`message_not_found`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> message_not_found —

Konstruuje `message_not_found` obiektu.

```
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opisowy komunikat dotyczący błędu.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md)

