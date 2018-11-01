---
title: _fcvt
ms.date: 04/05/2018
apiname:
- _fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: ae9323e3bb629fd61b35a8c844b00bfcc73235bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662062"
---
# <a name="fcvt"></a>_fcvt

Konwertuje liczbę zmiennoprzecinkową na ciąg. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [_fcvt_s —](fcvt-s.md).

## <a name="syntax"></a>Składnia

```C
char *_fcvt(
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
Liczba cyfr po punkcie dziesiętnym.

*Gru*<br/>
Wskaźnik do przechowywanej położenie punktu dziesiętnego.

*sign*<br/>
Wskaźnik do wskaźnika przechowywanych logowania.

## <a name="return-value"></a>Wartość zwracana

**_fcvt —** zwraca wskaźnik do ciągu znaków, **NULL** w przypadku błędu.

## <a name="remarks"></a>Uwagi

**_Fcvt —** funkcja konwertuje liczbę zmiennoprzecinkową ciąg znaków zakończony znakiem null. *Wartość* parametr jest liczba zmiennoprzecinkowa, która ma zostać przekonwertowany. **_fcvt —** przechowuje cyfry *wartość* jako ciąg i dołącza znak null ('\0'). *Liczba* parametr określa liczbę cyfr, które mają być przechowywane po punkcie dziesiętnym. Nadmiarowe cyfry są zaokrąglane do *liczba* miejsc. W przypadku mniej niż *liczba* cyfr precyzji, ciąg jest dopełniana zerami.

Całkowita liczba cyfr, zwracany przez **_fcvt —** nie przekroczy **_CVTBUFSIZE**.

Tylko cyfry są przechowywane w ciągu. Pozycja punkt dziesiętny i znak *wartość* można otrzymać od *gru* i logowania po wywołaniu. *Gru* parametr wskazuje na wartość całkowitą; tej wartości liczby całkowitej zapewnia położenie punktu dziesiętnego w odniesieniu do początku ciągu. Zero lub wartość ujemną liczbę całkowitą wskazuje punkt dziesiętny znajduje się po lewej stronie pierwsza cyfra. Parametr *logowania* wskazuje na liczbę całkowitą określającą znak *wartość*. Liczba całkowita jest ustawiona na 0, jeśli *wartość* jest dodatnia i jest ustawiona na wartość różną od zera jeśli liczba *wartość* jest ujemna.

Różnica między **_ecvt —** i **_fcvt —** znajduje się w interpretacji *liczba* parametru. **_ecvt —** interpretuje *liczba* jako łączna liczba cyfr w ciągu wyjściowego, natomiast **_fcvt —** interpretuje *liczba* jako liczbę cyfr po punkt dziesiętny.

**_ecvt —** i **_fcvt —** pojedynczy bufor statycznie przydzielanego na użytek konwersji. Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *gru* lub *logowania* jest **NULL**, lub *liczba* wynosi 0, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i **NULL** jest zwracana.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fcvt.c
// compile with: /W3
// This program converts the constant
// 3.1415926535 to a string and sets the pointer
// buffer to point to that string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int  decimal, sign;
   char *buffer;
   double source = 3.1415926535;

   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996
   // Note: _fcvt is deprecated; consider using _fcvt_s instead
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",
            source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
