---
title: _set_error_mode
ms.date: 11/04/2016
api_name:
- _set_error_mode
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
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: c1bb617e0f3792f2ac41d59df13d184423d56a9e
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562041"
---
# <a name="_set_error_mode"></a>_set_error_mode

Modyfikuje **__error_mode** w celu określenia lokalizacji innej niż domyślna, w której środowisko uruchomieniowe języka C zapisuje komunikat o błędzie, który może spowodować zakończenie tego programu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>Parametry

*mode_val*<br/>
Lokalizacja docelowa komunikatów o błędach.

## <a name="return-value"></a>Wartość zwracana

Zwraca stare ustawienie lub-1, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Steruje ujściam wyjściowym błędu przez ustawienie wartości **__error_mode**. Na przykład można skierować dane wyjściowe do błędu standardowego lub użyć interfejsu API **MessageBox** .

Parametr *mode_val* można ustawić na jedną z następujących wartości.

|Wartość|Opis|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|Ujścia błędów jest określana przez **__app_type**.|
|**_OUT_TO_STDERR**|Błąd ujścia jest standardowym błędem.|
|**_OUT_TO_MSGBOX**|Ujścia błędu to okno komunikatu.|
|**_REPORT_ERRMODE**|Zgłoś bieżącą wartość **__error_mode** .|

Jeśli wartość inna niż wymienione na liście jest przenoszona w programie, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_set_error_mode** ustawia **errno** na **EINVAL** i zwraca wartość-1.

Gdy jest używany z [potwierdzeniem](assert-macro-assert-wassert.md), **_set_error_mode** wyświetla instrukcję zakończonych niepowodzeniem w oknie dialogowym i daje możliwość wyboru przycisku **Ignoruj** , aby można było kontynuować uruchamianie programu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_error_mode**|\<stdlib.h>|

## <a name="example"></a>Przykład

```C
// crt_set_error_mode.c
// compile with: /c
#include <stdlib.h>
#include <assert.h>

int main()
{
   _set_error_mode(_OUT_TO_STDERR);
   assert(2+2==5);
}
```

```Output
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Zobacz też

[potwierdzj makro, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
