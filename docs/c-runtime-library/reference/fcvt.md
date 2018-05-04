---
title: _fcvt — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fefe9bbfc1904847af5594a4d663b1eb8299fc9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fcvt"></a>_fcvt

Konwertuje liczba zmiennoprzecinkowa na ciąg. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [_fcvt_s —](fcvt-s.md).

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
Numer do skonwertowania.

*Liczba*<br/>
Liczba cyfr po punkcie dziesiętnym.

*DEC*<br/>
Wskaźnik do składowanej położenie punktu dziesiętnego.

*sign*<br/>
Wskaźnik do wskaźnika logowania przechowywanej.

## <a name="return-value"></a>Wartość zwracana

**_fcvt —** zwraca wskaźnik do ciągu znaków, wartość NULL w przypadku błędu.

## <a name="remarks"></a>Uwagi

**_Fcvt —** funkcja konwertuje liczba zmiennoprzecinkowa na ciąg znaków zakończony znakiem null. *Wartość* parametr jest liczbie zmiennoprzecinkowej do skonwertowania. **_fcvt —** przechowuje cyfry *wartość* jako ciąg i dołącza znak null ('\0'). *Liczba* parametr określa liczbę cyfr po punkcie dziesiętnym przechowywania. Nadmiarowe cyfry są zaokrąglane do *liczba* miejsca. Jeśli jest dostępnych mniej niż *liczba* cyfr precyzji, ten ciąg jest uzupełniana zerami z.

Całkowita liczba cyfr zwrócony przez **_fcvt —** nie przekroczy **_CVTBUFSIZE**.

Tylko cyfry są przechowywane w ciągu. Położenie punktu dziesiętnego i znak *wartość* można uzyskać od *gru* i zalogować się po wywołaniu. *Gru* parametr wskazuje na wartość całkowitą; daje to wartość całkowita położenie punktu dziesiętnego względem początku ciąg. Wartość zero lub wartość ujemną całkowitą wskazuje dziesiętnego znajduje się na lewo od pierwszą. Parametr *znak* wskazuje na liczbę całkowitą określającą znak *wartość*. Liczba całkowita jest ustawiony na 0, jeśli *wartość* jest dodatnia i ma ustawioną wartość różna od zera, jeśli liczba *wartość* jest ujemna.

Różnica między **_ecvt —** i **_fcvt —** jest interpretacji *liczba* parametru. **_ecvt —** interpretuje *liczba* jako liczba cyfr w ciągu wyjściowego, natomiast **_fcvt —** interpretuje *liczby* jako liczbę cyfr po separatorem dziesiętnym.

**_ecvt —** i **_fcvt —** do konwersji użyj pojedynczego statycznie przydzielonego buforu. Każde wywołanie do jednej z tych procedur niszczy wyniki poprzedniego wywołania.

Ta funkcja weryfikuje jego parametrów. Jeśli *gru* lub *znak* ma wartość NULL, lub *liczba* wynosi 0, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i zostanie zwrócona wartość NULL.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
