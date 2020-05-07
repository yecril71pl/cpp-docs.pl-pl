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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7b889bccc0b1f1fd99a9a0526bbfb42a2e520970
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919383"
---
# <a name="_get_doserrno"></a>_get_doserrno

Pobiera wartość błędu zwróconą przez system operacyjny przed przetłumaczeniem jej na wartość **errno** .

## <a name="syntax"></a>Składnia

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Wskaźnik do liczby całkowitej, która ma zostać wypełniona bieżącą wartością **_doserrnogo** makra globalnego.

## <a name="return-value"></a>Wartość zwracana

Jeśli **_get_doserrno** się powiedzie, zwraca zero; Jeśli to się nie powiedzie, zwraca kod błędu. Jeśli *pValue* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Po rozpoczęciu uruchamiania procesu, **_doserrno** makro globalne ma wartość zero. Jest ona ustawiona na wartość błędu systemu operacyjnego zwróconą przez wywołanie funkcji na poziomie systemu, które zwraca błąd systemu operacyjnego i nigdy nie jest resetowany do zera podczas wykonywania. Podczas pisania kodu w celu sprawdzenia wartości błędu zwróconej przez funkcję, zawsze Wyczyść **_doserrno** przy użyciu [_set_doserrno](set-doserrno.md) przed wywołaniem funkcji. Ponieważ inne wywołanie funkcji może zastąpić **_doserrno**, sprawdź wartość przy użyciu **_get_doserrno** natychmiast po wywołaniu funkcji.

Zalecamy [_get_errno](get-errno.md) zamiast **_get_doserrno** dla przenośnych kodów błędów.

Możliwe wartości **_doserrno** są zdefiniowane w \<> errno. h.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<STDLIB. h>, \<cstdlib> (C++)|\<errno. h>, \<cerrno> (C++)|

**_get_doserrno** to rozszerzenie firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
