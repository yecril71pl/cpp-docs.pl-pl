---
title: _get_doserrno
ms.date: 11/04/2016
api_name:
- _get_doserrno
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
ms.openlocfilehash: 2810ead8bdd7d6c77cb2b55f4f97371bfc9751e6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956040"
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
Wskaźnik do liczby całkowitej, która ma zostać wypełniona bieżącą wartością makra globalnego **_doserrno** .

## <a name="return-value"></a>Wartość zwracana

Jeśli **_get_doserrno** powiedzie się, zwraca zero; Jeśli to się nie powiedzie, zwraca kod błędu. Jeśli *pValue* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Po rozpoczęciu uruchamiania procesu **_doserrno** globalne makro ma wartość zero. Jest ona ustawiona na wartość błędu systemu operacyjnego zwróconą przez wywołanie funkcji na poziomie systemu, które zwraca błąd systemu operacyjnego i nigdy nie jest resetowany do zera podczas wykonywania. Podczas pisania kodu w celu sprawdzenia wartości błędu zwróconej przez funkcję zawsze Wyczyść **_doserrno** przy użyciu [_set_doserrno](set-doserrno.md) przed wywołaniem funkcji. Ponieważ inne wywołanie funkcji może zastąpić **_doserrno**, sprawdź wartość przy użyciu **_get_doserrno** bezpośrednio po wywołaniu funkcji.

Zalecamy [_get_errno](get-errno.md) zamiast **_get_doserrno** dla przenośnych kodów błędów.

Możliwe wartości **_doserrno** są zdefiniowane w \<errno. h >.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno. h >, \<cerrno > (C++)|

**_get_doserrno** jest rozszerzeniem firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
