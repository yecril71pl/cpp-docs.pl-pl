---
title: offsetof Macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- offsetof
dev_langs:
- C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 308aac2493751cfe2147187ed9848347124a90d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401467"
---
# <a name="offsetof-macro"></a>offsetof Macro

Pobiera przesunięcie elementu członkowskiego z początku jego struktury nadrzędnej.

## <a name="syntax"></a>Składnia

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>Parametry

*structName*<br/>
Nazwa nadrzędnego struktury danych.

*memberName*<br/>
Nazwa elementu członkowskiego w nadrzędnej struktury danych do ustalania przesunięcie.

## <a name="return-value"></a>Wartość zwracana

**makra offsetof** zwraca przesunięcie w bajtach określonego elementu członkowskiego, od początku jej nadrzędnej struktury danych. Jest niezdefiniowany dla pól bitowych.

## <a name="remarks"></a>Uwagi

**Makra offsetof** makro zwraca przesunięcie w bajtach *memberName* od początku struktury określony przez *structName* jako wartość typu **size_ t**. Można określić typy z **struktury** — słowo kluczowe.

> [!NOTE]
> **makra offsetof** nie jest funkcją i nie może być opisana przy użyciu prototypu C.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
