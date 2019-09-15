---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
api_name:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: edf91cd8c76fd080326e2e5eeac98f7f81ab90cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942367"
---
# <a name="_crtmemcheckpoint"></a>_CrtMemCheckpoint

Uzyskuje bieżący stan sterty debugowania i przechowuje je w strukturze **_CrtMemState** dostarczonej przez aplikację (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*state*<br/>
Wskaźnik do struktury **_CrtMemState** , aby wypełnić punkt kontrolny pamięci.

## <a name="remarks"></a>Uwagi

Funkcja **_CrtMemCheckpoint** tworzy migawkę bieżącego stanu sterty debugowania w danym momencie. Ta migawka może być używana przez inne funkcje stanu sterty, takie jak [_CrtMemDifference](crtmemdifference.md) , aby ułatwić wykrywanie przecieków pamięci i innych problemów. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtMemState** są usuwane podczas przetwarzania wstępnego.

Aplikacja musi przekazać wskaźnik do wcześniej przydzielonych wystąpień struktury **_CrtMemState** zdefiniowanej w CRTDBG. h w parametrze *State* . Jeśli **_CrtMemCheckpoint** napotka błąd podczas tworzenia punktu kontrolnego, funkcja generuje raport debugowania **_CRT_WARN** opisujący problem.

Aby uzyskać więcej informacji na temat funkcji stanu sterty i struktury **_CrtMemState** , zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Jeśli *stan* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ma wartość **EINVAL** , a funkcja zwraca.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

**Bibliotece** Tylko debugowanie wersji UCRT.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
