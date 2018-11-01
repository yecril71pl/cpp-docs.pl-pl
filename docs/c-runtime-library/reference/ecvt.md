---
title: _ecvt
ms.date: 04/05/2018
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
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 36c9cb2e8cd9eb4dd67bb91e9e4dbd36d8d1fc8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605732"
---
# <a name="ecvt"></a>_ecvt

Konwertuje **double** liczb na ciąg. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [_ecvt_s —](ecvt-s.md).

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
Numer ma zostać przekonwertowany.

*Liczba*<br/>
Liczba cyfr przechowywane.

*Gru*<br/>
Przechowywane położenie punktu dziesiętnego.

*sign*<br/>
Znak przekonwertowany numer.

## <a name="return-value"></a>Wartość zwracana

**_ecvt —** zwraca wskaźnik do ciągu znaków; **NULL** Jeśli wystąpił błąd.

## <a name="remarks"></a>Uwagi

**_Ecvt —** funkcja konwertuje liczbę zmiennoprzecinkową ciąg znaków. *Wartość* parametr jest liczba zmiennoprzecinkowa, która ma zostać przekonwertowany. Ta funkcja przechowuje maksymalnie *liczba* cyfr *wartość* jako ciąg i dołącza znak null ('\0'). Jeśli liczba cyfr w *wartość* przekracza *liczba*, cyfra niskiego rzędu jest zaokrąglana. W przypadku mniej niż *liczba* cyfry, ciąg jest dopełniana zerami.

Całkowita liczba cyfr, zwracany przez **_ecvt —** nie przekroczy **_CVTBUFSIZE**.

Tylko cyfry są przechowywane w ciągu. Pozycja punkt dziesiętny i znak *wartość* można otrzymać od *gru* i *logowania* po wywołaniu. *Gru* parametr wskazuje wartość całkowitą, dzięki czemu położenie punktu dziesiętnego w odniesieniu do początku ciągu. Wartość 0 ani ujemna liczba całkowita wskazuje, punkt dziesiętny znajduje się po lewej stronie pierwsza cyfra. *Logowania* parametr wskazuje na liczbę całkowitą, która określa znak przekonwertowany numer. Jeśli wartość całkowitą ma wartość 0, liczba jest dodatnia. W przeciwnym razie liczba jest ujemna.

Różnica między **_ecvt —** i **_fcvt —** znajduje się w interpretacji *liczba* parametru. **_ecvt —** interpretuje *liczba* jako łączna liczba cyfr w ciągu wyjściowego, natomiast **_fcvt —** interpretuje *liczba* jako liczbę cyfr po punkt dziesiętny.

**_ecvt —** i **_fcvt —** pojedynczy bufor statycznie przydzielanego na użytek konwersji. Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *gru* lub *logowania* jest **NULL**, lub *liczba* wynosi 0, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i **NULL** jest zwracana.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
