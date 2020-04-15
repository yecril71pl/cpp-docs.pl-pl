---
title: _findclose
ms.date: 4/2/2020
api_name:
- _findclose
- _o__findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: ed17963dc7331962c3ac0d522db2843822ec5f79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346783"
---
# <a name="_findclose"></a>_findclose

Zamyka określony dojście wyszukiwania i zwalnia skojarzone zasoby.

## <a name="syntax"></a>Składnia

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>Parametry

*Obsługi*<br/>
Uchwyt wyszukiwania zwrócony przez poprzednie wywołanie **_findfirst**.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **_findclose** zwraca wartość 0. W przeciwnym razie zwraca -1 i ustawia **errno** na **ENOENT**, wskazując, że nie można znaleźć więcej pasujących plików.

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_findclose**|\<> io.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazwy plików](../../c-runtime-library/filename-search-functions.md)<br/>
