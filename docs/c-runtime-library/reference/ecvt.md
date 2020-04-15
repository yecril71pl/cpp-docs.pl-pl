---
title: _ecvt
ms.date: 4/2/2020
api_name:
- _ecvt
- _o__ecvt
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5e1760d5c68e650f6fbf44866d4e368b9d6233b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348022"
---
# <a name="_ecvt"></a>_ecvt

Konwertuje **podwójną** liczbę na ciąg. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [_ecvt_s](ecvt-s.md).

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
Liczba do konwersji.

*Liczba*<br/>
Liczba zapisanych cyfr.

*dec*<br/>
Przechowywana pozycja dziesiętna.

*Znak*<br/>
Znak przekonwertowanego numeru.

## <a name="return-value"></a>Wartość zwracana

**_ecvt** zwraca wskaźnik do ciągu cyfr; **NULL,** jeśli wystąpił błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_ecvt** konwertuje liczbę zmiennoprzecinkową na ciąg znaków. Parametr *value* jest numerem zmiennoprzecinkowym, który ma zostać przekonwertowany. Ta funkcja przechowuje się, aby *zliczać* cyfry *wartości* jako ciąg i dołącza znak null ('\0'). Jeśli liczba cyfr w *wartości* przekracza *liczbę,* cyfra niskiego rzędu jest zaokrąglana. Jeśli jest mniej niż *cyfry,* ciąg jest wyściełane zerami.

Całkowita liczba cyfr zwróconych przez **_ecvt** nie przekroczy **_CVTBUFSIZE**.

Tylko cyfry są przechowywane w ciągu. Położenie przecinka dziesiętnego i znak *wartości* można uzyskać od *dec* i *znak* po wywołaniu. Parametr *dec* wskazuje wartość całkowitą, podając pozycję przecinka dziesiętnego względem początku ciągu. Wartość całkowita 0 lub ujemna wskazuje, że przecinek dziesiętny znajduje się po lewej stronie pierwszej cyfry. Parametr *sign* wskazuje liczbę całkowitą, która wskazuje znak przekonwertowanego numeru. Jeśli wartość całkowita wynosi 0, liczba ta jest dodatnia. W przeciwnym razie liczba jest ujemna.

Różnica między **_ecvt** a **_fcvt** polega na interpretacji parametru *count.* **_ecvt** interpretuje *liczą* się jako całkowita liczba cyfr w ciągu wyjściowym, podczas gdy **_fcvt** interpretuje *liczyć* jako liczbę cyfr po przecinku.

**_ecvt** i **_fcvt** użyć pojedynczego buforu statycznie przydzielonego do konwersji. Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *dec* lub *znak* ma **wartość NULL**lub *liczba* wynosi 0, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i **NULL** jest zwracany.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_ecvt**|\<>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
