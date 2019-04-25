---
title: offsetof Macro
ms.date: 11/04/2016
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
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: a0f367dbe6fa2681a7d413304f32b5699b8f7cee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156074"
---
# <a name="offsetof-macro"></a>offsetof Macro

Pobiera przesunięcie elementu członkowskiego od początku jego nadrzędnej struktury.

## <a name="syntax"></a>Składnia

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>Parametry

*structName*<br/>
Nazwa nadrzędnej struktury danych.

*memberName*<br/>
Nazwa elementu członkowskiego w nadrzędnej struktury danych, do których chcesz określić przesunięcie.

## <a name="return-value"></a>Wartość zwracana

**Makro offsetof** zwraca przesunięcie w bajtach określonego elementu członkowskiego od początku jego nadrzędnej struktury danych. Jest niezdefiniowany dla pól bitowych.

## <a name="remarks"></a>Uwagi

**Offsetof** — makro zwraca przesunięcie w bajtach *memberName* od początku struktury, określony przez *structName* jako wartość typu **size_ t**. Można określić typy z **struktury** — słowo kluczowe.

> [!NOTE]
> **Makro offsetof** nie jest funkcją i nie może być opisany przy użyciu prototypu C.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
