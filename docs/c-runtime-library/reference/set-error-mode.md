---
title: _set_error_mode — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 130e9fee13401c8b598a5d6eef7d1fab3ed80ae9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="seterrormode"></a>_set_error_mode

Modyfikuje **__error_mode** do określenia lokalizacji innych niż domyślne, gdzie C runtime zapisuje komunikat o błędzie dla błędu, który może zakończyć program.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Określa ujście danych wyjściowych błędu, ustawiając wartość **__error_mode**. Na przykład Przekieruj dane wyjściowe do standardowego błędu lub użyj **MessageBox** interfejsu API.

*Mode_val* parametru może należeć do jednej z następujących wartości.

|Parametr|Opis|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|Błąd zbiornika jest określany przez **__app_type**.|
|**_OUT_TO_STDERR**|Błąd zbiornika jest błąd standardowy.|
|**_OUT_TO_MSGBOX**|Błąd zbiornika jest okno komunikatu.|
|**_REPORT_ERRMODE**|Bieżący raport **__error_mode** wartości.|

Jeśli przekazano wartość inną niż wymienione program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **_set_error_mode —** ustawia **errno** do **einval —** i zwraca wartość -1.

Gdy jest używana z [assert](assert-macro-assert-wassert.md), **_set_error_mode —** wyświetla instrukcji nie powiodło się w oknie dialogowym i umożliwia wybór **Ignoruj** przycisk Tak, aby można było Kontynuuj uruchomić program.

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
