---
title: _CrtMemDumpStatistics
ms.date: 11/04/2016
apiname:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
ms.openlocfilehash: 66eb58b65f3fa20e01ad16d68f3fe1baafd8cd04
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739807"
---
# <a name="_crtmemdumpstatistics"></a>_CrtMemDumpStatistics

Zrzuca informacje nagłówka debugowania dla określonego stanu sterty w formularzu możliwym do odczytu (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*state*<br/>
Wskaźnik do stanu sterty do zrzutu.

## <a name="remarks"></a>Uwagi

Funkcja **_CrtMemDumpStatistics** zrzuca informacje nagłówka debugowania dla określonego stanu sterty w formie możliwej do odczytu przez użytkownika. Dane statystyczne zrzutu mogą być używane przez aplikację do śledzenia alokacji i wykrywania problemów z pamięcią. Stan pamięci może zawierać określony stan sterty lub różnicę między dwoma stanami. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtMemDumpStatistics** są usuwane podczas przetwarzania wstępnego.

Parametr *State* musi być wskaźnikiem do struktury **_CrtMemState** , która została wprowadzona przez [_CrtMemCheckpoint](crtmemcheckpoint.md) lub zwrócona przez [_CrtMemDifference](crtmemdifference.md) przed wywołaniem **_CrtMemDumpStatistics** . Jeśli *stan* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** i nie jest podejmowana żadna akcja. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby uzyskać więcej informacji na temat funkcji stanu sterty i struktury **_CrtMemState** , zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

**Bibliotece** Debuguj tylko wersje [funkcji biblioteki CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
