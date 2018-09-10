---
title: _Crtmemdumpstatistics — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 655d9be75fa031cc2cbebfd65c4634528f410e85
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110529"
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
