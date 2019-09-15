---
title: _fpieee_flt
ms.date: 04/05/2018
api_name:
- _fpieee_flt
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
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: 8835a3184300f1c56f1123a09aa48cd34a387c87
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957024"
---
# <a name="_fpieee_flt"></a>_fpieee_flt

Wywołuje program obsługi pułapek zdefiniowany przez użytkownika dla wyjątków zmiennoprzecinkowych IEEE.

## <a name="syntax"></a>Składnia

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>Parametry

*excCode*<br/>
Kod wyjątku.

*excInfo*<br/>
Wskaźnik do struktury informacji o wyjątku systemu Windows NT.

*handler*<br/>
Wskaźnik do procedury obsługi wielopułapowego użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana przez **_fpieee_flt** jest wartością zwracaną przez *program obsługi*. W związku z tym procedura filtrowania IEEE może być używana w klauzuli except w mechanizmie obsługi wyjątków strukturalnych (SEH).

## <a name="remarks"></a>Uwagi

Funkcja **_fpieee_flt** wywołuje procedurę obsługi pułapek zdefiniowanych przez użytkownika dla wyjątków zmiennoprzecinkowych IEEE i udostępnia wszystkie istotne informacje. Ta procedura służy jako filtr wyjątku w mechanizmie SEH, który wywołuje własny program obsługi wyjątków IEEE, gdy jest to konieczne.

Struktura **_FPIEEE_RECORD** zdefiniowana w FPIEEE. h zawiera informacje dotyczące wyjątku zmiennoprzecinkowego IEEE. Ta struktura jest przenoszona do procedury obsługi pułapek zdefiniowanej przez użytkownika przez **_fpieee_flt**.

|Pole _FPIEEE_RECORD|Opis|
|----------------------------|-----------------|
|**Trybu zaokrąglania roundingmode**<br/>**Dokładne**|Te pola **bez znaku** **int** zawierają informacje o środowisku zmiennoprzecinkowym w momencie wystąpienia wyjątku.|
|**Operacja**|To **niepodpisane** pole **int** wskazuje typ operacji, która spowodowała pułapkę. Jeśli typ jest porównaniem ( **_FpCodeCompare**), można podać jedną z specjalnych wartości **_FPIEEE_COMPARE_RESULT** (zgodnie z definicją w FPIEEE. h) w polu **wynik. wartość** . Typ konwersji ( **_FpCodeConvert**) wskazuje, że pułapka wystąpiła podczas operacji konwersji zmiennoprzecinkowej. Można przyjrzeć się **Operand1** i typów **wyników** , aby określić typ próby konwersji.|
|**Operand1**<br/>**Operand2**<br/>**wynik**|Te struktury **_FPIEEE_VALUE** wskazują typy i wartości proponowanego wyniku i operandów. Każda struktura zawiera następujące pola:<br /><br /> **OperandValid** — flaga oznaczająca, czy wartość odpowiadająca jest prawidłowa.<br />**Format** — typ danych odpowiadającej wartości. Typ formatu może być zwracany nawet wtedy, gdy odpowiadająca wartość jest nieprawidłowa.<br />Wartość danych wyniku lub operandu **wartości** .|
|**Przyczyna**<br/>**Enable**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS** zawiera jedno pole bitowe dla typu wyjątku zmiennoprzecinkowego. Istnieje zgodność między tymi polami a argumentami używanymi do maskowania wyjątków dostarczonych do [_controlfp](control87-controlfp-control87-2.md). Dokładne znaczenie poszczególnych bitów zależy od kontekstu:<br /><br /> **Przyczyna** — każdy zestaw bitów wskazuje konkretny wyjątek, który został zgłoszony.<br />**Włącz** -każdy zestaw bitów wskazuje, że konkretny wyjątek jest aktualnie niemaskowany.<br />**Stan** — każdy bit zestawu wskazuje, że konkretny wyjątek jest aktualnie oczekujący. Obejmuje to wyjątki, które nie zostały zgłoszone, ponieważ zostały maskowane przez **_controlfp**.|

Oczekujące wyjątki, które są wyłączone, są wywoływane po ich włączeniu. Może to spowodować niezdefiniowane zachowanie w przypadku używania **_fpieee_flt** jako filtru wyjątków. Zawsze wywołuj [_clearfp](clear87-clearfp.md) przed włączeniem wyjątków zmiennoprzecinkowych.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fpieee.c
// This program demonstrates the implementation of
// a user-defined floating-point exception handler using the
// _fpieee_flt function.

#include <fpieee.h>
#include <excpt.h>
#include <float.h>
#include <stddef.h>

int fpieee_handler( _FPIEEE_RECORD * );

int fpieee_handler( _FPIEEE_RECORD *pieee )
{
   // user-defined ieee trap handler routine:
   // there is one handler for all
   // IEEE exceptions

   // Assume the user wants all invalid
   // operations to return 0.

   if ((pieee->Cause.InvalidOperation) &&
       (pieee->Result.Format == _FpFormatFp32))
   {
        pieee->Result.Value.Fp32Value = 0.0F;

        return EXCEPTION_CONTINUE_EXECUTION;
   }
   else
      return EXCEPTION_EXECUTE_HANDLER;
}

#define _EXC_MASK    \
    _EM_UNDERFLOW  + \
    _EM_OVERFLOW   + \
    _EM_ZERODIVIDE + \
    _EM_INEXACT

int main( void )
{
   // ...

   __try {
      // unmask invalid operation exception
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);

      // code that may generate
      // fp exceptions goes here
   }
   __except ( _fpieee_flt( GetExceptionCode(),
                GetExceptionInformation(),
                fpieee_handler ) ){

      // code that gets control

      // if fpieee_handler returns
      // EXCEPTION_EXECUTE_HANDLER goes here

   }

   // ...
}
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
