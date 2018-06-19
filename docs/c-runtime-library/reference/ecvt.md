---
title: _ecvt — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ecvt
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ecvt
dev_langs:
- C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63514db5abe0a7cd531590dd419aa4b5931e7729
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450966"
---
# <a name="ecvt"></a>_ecvt

Konwertuje **podwójne** numer na ciąg. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [_ecvt_s —](ecvt-s.md).

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
Numer do skonwertowania.

*Liczba*<br/>
Liczba cyfr przechowywane.

*DEC*<br/>
Przechowywane położenie punktu dziesiętnego.

*sign*<br/>
Znak przekonwertowany numer.

## <a name="return-value"></a>Wartość zwracana

**_ecvt —** zwraca wskaźnik do ciąg cyfr; **NULL** Jeśli wystąpił błąd.

## <a name="remarks"></a>Uwagi

**_Ecvt —** funkcja konwertuje liczba zmiennoprzecinkowa na ciąg znaków. *Wartość* parametr jest liczbie zmiennoprzecinkowej do skonwertowania. Ta funkcja przechowuje do *liczba* cyfr *wartość* jako ciąg i dołącza znak null ('\0'). Jeśli liczba cyfr w *wartość* przekracza *liczby*, cyfrę znaczącymi bitami jest zaokrąglana. Jeśli jest dostępnych mniej niż *liczba* cyfr, ten ciąg jest uzupełniana zerami z.

Całkowita liczba cyfr zwrócony przez **_ecvt —** nie przekroczy **_CVTBUFSIZE**.

Tylko cyfry są przechowywane w ciągu. Położenie punktu dziesiętnego i znak *wartość* można uzyskać od *gru* i *znak* po wywołaniu. *Gru* parametr wskazuje wartość całkowitą, podając położenie punktu dziesiętnego względem początku ciąg. Wartość liczby całkowitej 0 ani ujemna wskazuje dziesiętnego znajduje się na lewo od pierwszej cyfry. *Znak* parametr wskazuje na liczbę całkowitą wskazującą znak liczby przekonwertowany. Jeśli wartość całkowita ma wartość 0, liczba jest dodatnia. W przeciwnym razie liczba jest ujemna.

Różnica między **_ecvt —** i **_fcvt —** jest interpretacji *liczba* parametru. **_ecvt —** interpretuje *liczba* jako liczba cyfr w ciągu wyjściowego, natomiast **_fcvt —** interpretuje *liczby* jako liczbę cyfr po separatorem dziesiętnym.

**_ecvt —** i **_fcvt —** do konwersji użyj pojedynczego statycznie przydzielonego buforu. Każde wywołanie do jednej z tych procedur niszczy wynik poprzedniego wywołania.

Ta funkcja weryfikuje jego parametrów. Jeśli *gru* lub *znak* jest **NULL**, lub *liczba* wynosi 0, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i **NULL** jest zwracany.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
