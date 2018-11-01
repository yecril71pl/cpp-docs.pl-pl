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
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605130"
---
# <a name="crtmemdumpstatistics"></a>_CrtMemDumpStatistics

Zrzuca informacji nagłówka debugowania stanu sterty określony w formie czytelny dla użytkownika (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*state*<br/>
Wskaźnik stanu sterty do zrzutu.

## <a name="remarks"></a>Uwagi

**_Crtmemdumpstatistics —** funkcja zrzuty informacji nagłówka debugowania dla określonego stanu sterty w postaci czytelny dla użytkownika. Statystyki zrzutu może służyć przez aplikację do śledzenia alokacji i wykrycia problemów z pamięcią. Stan pamięci może zawierać stanu sterty określonych lub różnicę między dwoma stanami. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_crtmemdumpstatistics —** są usuwane podczas przetwarzania wstępnego.

*Stanu* parametru musi być wskaźnikiem do **_CrtMemState** strukturę, która ma zostać wypełnione podczas [_crtmemcheckpoint —](crtmemcheckpoint.md) lub zwróconych przez [_ Crtmemdifference —](crtmemdifference.md) przed **_crtmemdumpstatistics —** jest wywoływana. Jeśli *stanu* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i nie podjęto żadnej akcji. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby uzyskać więcej informacji o funkcjach stanu sterty i **_CrtMemState** struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji na temat sposobu bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** Debuguj wersje [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
