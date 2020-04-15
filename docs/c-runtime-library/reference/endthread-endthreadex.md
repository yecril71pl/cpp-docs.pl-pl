---
title: _endthread, _endthreadex
ms.date: 4/2/2020
api_name:
- _endthread
- _endthreadex
- _o__endthread
- _o__endthreadex
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
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: c76f479255080400e07678ef5dbde572b7a9dffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348035"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Kończy wątek; **_endthread** kończy wątek utworzony przez **_beginthread** i **_endthreadex** kończy wątek utworzony przez **_beginthreadex**.

## <a name="syntax"></a>Składnia

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>Parametry

*retval*<br/>
Kod zakończenia wątku.

## <a name="remarks"></a>Uwagi

Można wywołać **_endthread** lub **_endthreadex** jawnie, aby zakończyć wątek; jednak **_endthread** lub **_endthreadex** jest wywoływana automatycznie, gdy wątek zwraca z procedury przekazywane jako parametr do **_beginthread** lub **_beginthreadex**. Zakończenie wątku z wywołaniem **endthread** lub **_endthreadex** pomaga zapewnić prawidłowe odzyskiwanie zasobów przydzielonych dla wątku.

> [!NOTE]
> W przypadku pliku wykonywalnego połączonego z libcmt.lib nie należy wywoływać interfejsu API [Win32 ExitThread;](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) zapobiega to systemowi czasu wykonywania odzyskiwania przydzielonych zasobów. **_endthread** i **_endthreadex** odzyskać przydzielone zasoby wątku, a następnie **wywołać ExitThread**.

**_endthread** automatycznie zamyka uchwyt gwintu. (To zachowanie różni się od interfejsu API **Win32 ExitThread.)** W związku z tym podczas korzystania **z _beginthread** i **_endthread**, nie jawnie zamknąć dojście wątku, wywołując Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) INTERFEJSU API.

Podobnie jak win32 **ExitThread** interfejsu API, **_endthreadex** nie zamyka uchwyt wątku. W związku z tym podczas korzystania **z _beginthreadex** i **_endthreadex,** należy zamknąć dojście wątku, wywołując win32 **CloseHandle** INTERFEJSU API.

> [!NOTE]
> **_endthread** i **_endthreadex** spowodować, że destruktory języka C++ oczekujące w wątku nie zostanie wywołana.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_endthread**|\<> proces.h|
|**_endthreadex**|\<> proces.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wielowątkowe wersje [tylko bibliotek w czasie wykonywania języka C.](../../c-runtime-library/crt-library-features.md)

## <a name="example"></a>Przykład

Zobacz przykład [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
