---
title: _fpieee_flt — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fpieee_flt
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
- fpieee_flt
- _fpieee_flt
dev_langs:
- C++
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 412eef6e3999c18901792643fa7a57ce18d19520
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403368"
---
# <a name="fpieeeflt"></a>_fpieee_flt

Wywołuje program obsługi pułapki zdefiniowane przez użytkownika wyjątki zmiennoprzecinkowe IEEE.

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
Wskaźnik do struktury informacji wyjątek systemu Windows NT.

*Program obsługi*<br/>
Wskaźnik do procedury obsługi pułapki IEEE użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana **_fpieee_flt —** jest wartość zwrócona przez *obsługi*. W efekcie procedury filtru IEEE mogą być używane w z wyjątkiem klauzuli strukturalne (SEH) mechanizm obsługi wyjątków.

## <a name="remarks"></a>Uwagi

**_Fpieee_flt —** funkcja wywołuje program obsługi pułapki zdefiniowane przez użytkownika wyjątki zmiennoprzecinkowe IEEE i zapewnia wszystkie informacje. Ta procedura służy jako filtru wyjątków SEH mechanizmu, który wywołuje własne IEEE obsługi wyjątków, gdy jest to konieczne.

**_Fpieee_record —** struktury zdefiniowane w Fpieee.h, zawiera informacje dotyczące IEEE zmiennoprzecinkowych wyjątków. Ta struktura jest przekazywane do programu obsługi zdefiniowane przez użytkownika pułapki przez **_fpieee_flt —**.

|_Fpieee_record — pola|Opis|
|----------------------------|-----------------|
|**RoundingMode**<br/>**dokładność**|Te **niepodpisane** **int** pola zawierają informacje o środowisku liczb zmiennoprzecinkowych w czasie Wystąpił wyjątek.|
|**Operacja**|To **niepodpisane** **int** pole wskazuje typ operacji, który spowodował pułapki. Jeśli typ znajduje się porównanie (**_FpCodeCompare**), możesz podać jeden specjalną **_FPIEEE_COMPARE_RESULT** wartości (zgodnie z definicją w Fpieee.h) w **Result.Value** pola. Typ konwersji (**_FpCodeConvert**) wskazuje, że pułapki wystąpił podczas operacji Konwersja typów zmiennoprzecinkowych. Można przyjrzeć się **Operand1** i **wynik** typy, można określić typu próby konwersji.|
|**operand1**<br/>**operand2**<br/>**wynik**|Te **_FPIEEE_VALUE** struktury wskazuje typy oraz wartości proponowanych wynik i argumentów operacji. Każda struktura zawiera następujące pola:<br /><br /> **OperandValid** — flagę wskazującą, czy wartość odpowiada jest prawidłowa.<br />**Format** — typ danych w odpowiadającej jej wartości. Może być zwrócony typ formatu, nawet jeśli odpowiadającej jej wartości nie jest prawidłowy.<br />**Wartość** -wynik lub argument wartości danych.|
|**Przyczyna**<br/>**Włączenie**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS** zawiera pole o jeden bit według typu zmiennoprzecinkowych wyjątków punktu. Brak zgodności między tych pól i argumenty używane do maskować wyjątki dostarczony do [_controlfp —](control87-controlfp-control87-2.md). Dokładne znaczenie każdy bit jest zależna od kontekstu:<br /><br /> **Przyczyna** — każdy zestaw bit wskazuje określonego wyjątku, który został zgłoszony.<br />**Włącz** — każdy zestaw bit wskazuje, że określonego wyjątku jest obecnie zaznaczona.<br />**Stan** — każdy zestaw bit wskazuje, że określonego wyjątku jest aktualnie oczekujący. Dotyczy to również wyjątki, które nie mają został zgłoszony, ponieważ zostały one zamaskować **_controlfp —**.|

Oczekujące wyjątki, które są wyłączone są wywoływane, gdy zostanie włączona. Może to spowodować niezdefiniowane zachowanie przy użyciu **_fpieee_flt —** jako filtru wyjątków. Wywoływanie zawsze [_clearfp —](clear87-clearfp.md) przed włączeniem wyjątki zmiennoprzecinkowe.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
