---
title: _get_doserrno
ms.date: 11/04/2016
apiname:
- _get_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 700f710e6d94f48b03697325bb720dbc539fe04e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287749"
---
# <a name="getdoserrno"></a>_get_doserrno

Pobiera wartość błąd, zwrócone przez system operacyjny, zanim je przetłumaczyć **errno** wartości.

## <a name="syntax"></a>Składnia

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Wskaźnik do liczby całkowitej trzeba napełniać bieżącą wartość **_doserrno** makro globalne.

## <a name="return-value"></a>Wartość zwracana

Jeśli **_get_doserrno —** zakończy się powodzeniem, funkcja zwraca zero; jeśli nie powiedzie się, zwraca kod błędu. Jeśli *pValue* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Doserrno** globalnego makro jest równa zero podczas inicjowania CRT, zanim proces rozpoczyna wykonywanie. Jest ustawiona na wartość Błąd systemu operacyjnego, zwracany przez każde wywołanie funkcji na poziomie systemu, który zwraca błąd systemu operacyjnego, a to, że nigdy nie jest resetowany do zera, podczas wykonywania. Podczas wpisywania kodu, aby sprawdzić wartość błędu zwrócony przez funkcję, zawsze wyczyść **_doserrno** przy użyciu [_set_doserrno —](set-doserrno.md) przed wywołaniem funkcji. Ponieważ inne wywołanie funkcji może spowodować zastąpienie **_doserrno**, sprawdź wartość przy użyciu **_get_doserrno —** natychmiast po wywołaniu funkcji.

Firma Microsoft zaleca [_get_errno —](get-errno.md) zamiast **_get_doserrno —** kody błędów przenośny.

Możliwe wartości **_doserrno** są zdefiniowane w \<errno.h >.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno —** jest rozszerzeniem firmy Microsoft. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
