---
title: offsetof Macro
ms.date: 11/04/2016
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: 278fca89046fcfc98e8c3ff726918cb4319e4ab0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951252"
---
# <a name="offsetof-macro"></a>offsetof Macro

Pobiera przesunięcie elementu członkowskiego od początku jego struktury nadrzędnej.

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
Nazwa elementu członkowskiego w nadrzędnej strukturze danych, dla którego ma zostać określone przesunięcie.

## <a name="return-value"></a>Wartość zwracana

**makro OffsetOf** zwraca przesunięcie w bajtach określonego elementu członkowskiego od początku jego nadrzędnej struktury danych. Nie jest on zdefiniowany dla pól bitowych.

## <a name="remarks"></a>Uwagi

Makro **makro OffsetOf** zwraca przesunięcie w bajtach *elementu MemberName* od początku struktury określonej przez *structname* jako wartość typu **size_t**. Można określić typy za pomocą słowa kluczowego **struct** .

> [!NOTE]
> **makro OffsetOf** nie jest funkcją i nie można jej opisać przy użyciu prototypu języka C.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
