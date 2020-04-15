---
title: _get_doserrno
ms.date: 4/2/2020
api_name:
- _get_doserrno
- _o__get_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 2d5d4e224b39e9fa597e12975d27fa5720fbfbc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345254"
---
# <a name="_get_doserrno"></a>_get_doserrno

Pobiera wartość błędu zwróconą przez system operacyjny, zanim zostanie przetłumaczona na wartość **errno.**

## <a name="syntax"></a>Składnia

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parametry

*wartość pValue*<br/>
Wskaźnik do liczby całkowitej, który ma być wypełniony bieżącą wartością **_doserrno** makra globalnego.

## <a name="return-value"></a>Wartość zwracana

Jeśli **_get_doserrno** się powiedzie, zwraca zero; Jeśli się nie powiedzie, zwraca kod błędu. Jeśli *wartość pValue* ma **wartość NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

## <a name="remarks"></a>Uwagi

_doserrno **_doserrno** makro globalne jest ustawiona na zero podczas inicjowania CRT, przed rozpoczęciem wykonywania procesu. Jest ustawiona na wartość błędu systemu operacyjnego zwracana przez każde wywołanie funkcji na poziomie systemu, które zwraca błąd systemu operacyjnego i nigdy nie jest resetowany do zera podczas wykonywania. Podczas pisania kodu, aby sprawdzić wartość błędu zwróconą przez funkcję, zawsze wyczyść **_doserrno** za pomocą [_set_doserrno](set-doserrno.md) przed wywołaniem funkcji. Ponieważ inne wywołanie funkcji może zastąpić **_doserrno,** sprawdź wartość za pomocą **_get_doserrno** natychmiast po wywołaniu funkcji.

Zalecamy [_get_errno](get-errno.md) zamiast **_get_doserrno** dla przenośnych kodów błędów.

Możliwe wartości **_doserrno** są zdefiniowane \<w errno.h>.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<>, \<> cstdlib (C++)|\<\<>,> cerrno (C++)|

**_get_doserrno** jest rozszerzeniem firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
