---
title: _fpieee_flt
ms.date: 04/05/2018
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
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: 9a49ec403b1cb95407b0a366accf1d9374d9cb22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333251"
---
# <a name="fpieeeflt"></a>_fpieee_flt

Wywołuje program obsługi wyjątków zmiennoprzecinkowych IEEE pułapki zdefiniowanej przez użytkownika.

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
Wskaźnik do struktury informacji o wyjątku Windows NT.

*handler*<br/>
Wskaźnik do procedury uchwytu pułapki IEEE użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana przez **_fpieee_flt** jest wartość zwrócona przez obiekt *obsługi*. W efekcie procedury filtru IEEE mogą być używane w z wyjątkiem klauzuli ze strukturą mechanizm obsługi wyjątków (SEH).

## <a name="remarks"></a>Uwagi

**_Fpieee_flt** funkcja wywołuje program obsługi wyjątków zmiennoprzecinkowych IEEE pułapki zdefiniowanej przez użytkownika i zapewnia wszystkie istotne informacje. Ta procedura służy jako filtru wyjątków w mechanizm strukturalnej obsługi wyjątków, które wywołuje własne IEEE obsługi wyjątków, gdy jest to konieczne.

**_Fpieee_record —** struktury, zdefiniowanego w Fpieee.h, zawiera informacje dotyczące wyjątku zmiennopozycyjnego IEEE. Ta struktura jest przekazywany do uchwytu pułapki zdefiniowanej przez użytkownika, które przez **_fpieee_flt**.

|_Fpieee_record — pole|Opis|
|----------------------------|-----------------|
|**RoundingMode**<br/>**Precyzja**|Te **niepodpisane** **int** pola zawierają informacje na temat zmiennoprzecinkowych środowiska w momencie wystąpienia wyjątku.|
|**Operacja**|To **niepodpisane** **int** pole wskazuje typ operacji, która spowodowała pułapki. Jeśli typ jest porównanie (**_FpCodeCompare**), można dostarczyć jeden specjalny **_FPIEEE_COMPARE_RESULT** wartości (zgodnie z definicją w Fpieee.h) w **Result.Value** pola. Typ konwersji (**_FpCodeConvert**) wskazuje, że pułapki wystąpił podczas operacji konwersji zmiennoprzecinkowej. Można przyjrzeć się **Operand1** i **wynik** typów można ustalić typu próba konwersji.|
|**Operand1**<br/>**Operand2**<br/>**wynik**|Te **_FPIEEE_VALUE** struktury wskazują, typy i wartości proponowane wynik i argumentów operacji. Każda struktura zawiera następujące pola:<br /><br /> **OperandValid** — flagę wskazującą, czy odpowiada wartość jest prawidłowa.<br />**Format** — typ danych odpowiadająca wartość. Typ formatu może zostać zwrócona, nawet jeśli odpowiadająca wartość nie jest prawidłowy.<br />**Wartość** — wynik lub operand wartości danych.|
|**Przyczyna**<br/>**Enable**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS** zawiera pole o jeden bit na typ wyjątku punktu zmiennoprzecinkowego. Brak zgodności między te pola i argumenty używane do maskować wyjątki, przekazana do [_controlfp](control87-controlfp-control87-2.md). Dokładne znaczenie każdy bit zależy od kontekstu:<br /><br /> **Przyczyna** — każdy ustawionego bitu wskazuje określony wyjątek, który został zgłoszony.<br />**Włącz** — każdy ustawionego bitu. wskazuje, że określony wyjątek jest obecnie pozbawiony maskowania.<br />**Stan** — każdy ustawionego bitu. wskazuje, że określony wyjątek jest obecnie w stanie oczekiwania. W tym wyjątków, które nie mają zostało wywołane, ponieważ zostały zamaskować **_controlfp**.|

Oczekujących wyjątkach, które są wyłączone są wywoływane, gdy je włączyć. To może spowodować niezdefiniowane zachowanie, korzystając z **_fpieee_flt** jako filtru wyjątków. Zawsze wywołuj [_clearfp —](clear87-clearfp.md) przed włączeniem wyjątki zmiennoprzecinkowe.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
