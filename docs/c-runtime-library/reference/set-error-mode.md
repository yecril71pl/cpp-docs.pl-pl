---
title: _set_error_mode
ms.date: 11/04/2016
apiname:
- _set_error_mode
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
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: 8c95ed45423b791a688f05ea30f48e188826a797
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356657"
---
# <a name="seterrormode"></a>_set_error_mode

Modyfikuje **__error_mode** do określenia lokalizacji innej niż domyślna, w którym środowisko wykonawcze C zapisuje komunikat o błędzie Wystąpił błąd może się to zakończyć program.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>Parametry

*mode_val*<br/>
Miejsce docelowe komunikaty o błędach.

## <a name="return-value"></a>Wartość zwracana

Zwraca stare ustawienia lub wartość -1, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Kontroluje ujścia danych wyjściowych błędu, ustawiając wartość **__error_mode**. Na przykład, Przekieruj dane wyjściowe do błędu standardowego lub użyj **MessageBox** interfejsu API.

*Mode_val* parametr może być ustawiony na jedną z następujących wartości.

|Parametr|Opis|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|Błąd ujścia jest określana przez **__app_type**.|
|**_OUT_TO_STDERR**|Błąd ujścia jest błąd standardowy.|
|**_OUT_TO_MSGBOX**|Błąd obiektu sink to okno komunikatu.|
|**_REPORT_ERRMODE**|Zgłoś bieżącą **__error_mode** wartości.|

Jeśli przekazanym wartość inna niż te wymienione procedurę obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_set_error_mode —** ustawia **errno** do **EINVAL** i zwraca wartość -1.

Gdy jest używany z [asercja](assert-macro-assert-wassert.md), **_set_error_mode —** wyświetla instrukcji nie powiodło się w oknie dialogowym i zapewnia wybór **Ignoruj** przycisk, aby można było Kontynuuj uruchomić program.

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

## <a name="see-also"></a>Zobacz także

[assert Macro, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
