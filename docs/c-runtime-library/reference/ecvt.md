---
title: _ecvt
ms.date: 04/05/2018
api_name:
- _ecvt
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 9f91733c566c1782d5ccfc9a7c01e490a5915a85
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942036"
---
# <a name="_ecvt"></a>_ecvt

Konwertuje liczbę **podwójną** na ciąg. Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [_ecvt_s](ecvt-s.md).

## <a name="syntax"></a>Składnia

```C
char *_ecvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Liczba do przekonwertowania.

*liczbą*<br/>
Liczba przechowywanych cyfr.

*grudzień*<br/>
Przechowywana pozycja punktu dziesiętnego.

*sign*<br/>
Znak przekonwertowanego numeru.

## <a name="return-value"></a>Wartość zwracana

**_ecvt** zwraca wskaźnik do ciągu cyfr; **Wartość null** , jeśli wystąpił błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_ecvt** konwertuje liczbę zmiennoprzecinkową na ciąg znaków. Parametr *Value* jest liczbą zmiennoprzecinkową do przekonwertowania. Ta funkcja przechowuje maksymalnie *liczbę* cyfr *wartości* jako ciąg i dołącza znak null (' \ 0 '). Jeśli liczba cyfr w *wartości* przekracza *liczbę*, zaokrąglana jest mała kolejność. Jeśli jest mniej niż *Liczba* cyfr, ciąg jest dopełniany zerami.

Łączna liczba cyfr zwracanych przez **_ecvt** nie będzie większa niż **_CVTBUFSIZE**.

W ciągu są przechowywane tylko cyfry. Pozycja punktu dziesiętnego i znak *wartości* można uzyskać od *gru* i *podpisywać* po wywołaniu. Parametr *gru* wskazuje liczbę całkowitą określającą położenie przecinka dziesiętnego w odniesieniu do początku ciągu. Wartość 0 lub ujemna liczba całkowita wskazuje, że punkt dziesiętny znajduje się po lewej stronie pierwszej cyfry. Parametr *Sign* wskazuje liczbę całkowitą wskazującą znak przekonwertowanego numeru. Jeśli wartość całkowita to 0, liczba jest dodatnia. W przeciwnym razie liczba jest ujemna.

Różnica między **_ecvt** i **_fcvt** jest interpretacją parametru *Count* . **_ecvt** interpretuje *liczbę* jako łączną liczbę cyfr w ciągu danych wyjściowych, podczas gdy **_fcvt** interpretuje *liczbę cyfr* po przecinku dziesiętnym.

**_ecvt** i **_fcvt** używają jednego buforu przydzielenia statycznie dla konwersji. Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *gru* lub *Sign* ma **wartość null**lub *licznik* ma wartość 0, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** i zwracana jest **wartość null** .

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
