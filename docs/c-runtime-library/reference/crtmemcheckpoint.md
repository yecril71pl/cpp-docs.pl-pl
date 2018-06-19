---
title: _Crtmemcheckpoint — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
dev_langs:
- C++
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ca83a9b9b48302e9ff4974d083d0a95796a1ef3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395516"
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint

Pobiera bieżący stan sterty debugowania i zapisuje w dostarczonych aplikacji **_crtmemstate —** struktury (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*Stan* wskaźnik do **_crtmemstate —** struktury umożliwia wypełnienie pamięci punktu kontrolnego.

## <a name="remarks"></a>Uwagi

**_Crtmemcheckpoint —** funkcja tworzy migawkę bieżącego stanu sterty debugowania w danym momencie. Ta migawka mogą być używane przez inne funkcje stanu sterty takich jak [_crtmemdifference —](crtmemdifference.md) ułatwia wykrywanie przecieków pamięci i innych problemów. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtmemstate —** są usuwane podczas przetwarzania wstępnego.

Aplikacja musi przekazać wskaźnik do wcześniej alokowanego wystąpienia elementu **_crtmemstate —** struktury zdefiniowane w Crtdbg.h, w *stanu* parametru. Jeśli **_crtmemcheckpoint —** napotka błąd podczas tworzenia punktu kontrolnego, funkcja generuje **_CRT_WARN** debugowania raport opisujący problem.

Aby uzyskać więcej informacji na temat funkcji stanu sterty i **_crtmemstate —** struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji dotyczących sposobu bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Jeśli *stanu* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono **einval —** i zwraca funkcję.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wersja biblioteka UCRT tylko debugowania.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
