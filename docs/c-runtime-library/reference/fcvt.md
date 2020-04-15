---
title: _fcvt
ms.date: 4/2/2020
api_name:
- _fcvt
- _o__fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: a017ed58b962520793d5b10b088793dbc9b8a83d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347426"
---
# <a name="_fcvt"></a>_fcvt

Konwertuje liczbę zmiennoprzecinkową na ciąg. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [_fcvt_s](fcvt-s.md).

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
Liczba do konwersji.

*Liczba*<br/>
Liczba cyfr po przecinku.

*dec*<br/>
Wskaźnik do zapisanej pozycji dziesiętnej.

*Znak*<br/>
Wskaźnik do zapisanego wskaźnika znaku.

## <a name="return-value"></a>Wartość zwracana

**_fcvt** zwraca wskaźnik do ciągu cyfr, **NULL** na błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_fcvt** konwertuje liczbę zmiennoprzecinkową na ciąg znaków zakończonych z wartością null. Parametr *value* jest numerem zmiennoprzecinkowym, który ma zostać przekonwertowany. **_fcvt** przechowuje cyfry *wartości* jako ciąg i dołącza znak zerowy ('\0'). Parametr *count* określa liczbę cyfr, które mają być przechowywane po przecinku dziesiętnym. Nadmiar cyfr jest zaokrąglany w celu *zliczania* miejsc. Jeśli istnieje mniej niż *liczba* cyfr precyzji, ciąg jest wyściełane zerami.

Całkowita liczba cyfr zwróconych przez **_fcvt** nie przekroczy **_CVTBUFSIZE**.

Tylko cyfry są przechowywane w ciągu. Położenie przecinka dziesiętnego i znak *wartości* można uzyskać od *dec* i znak po wywołaniu. Parametr *dec* wskazuje wartość całkowitą; ta wartość całkowita podaje położenie przecinka dziesiętnego względem początku ciągu. Wartość całkowita zero lub ujemna wskazuje, że przecinek dziesiętnych znajduje się po lewej stronie pierwszej cyfry. *Znak* parametru wskazuje na liczbę całkowitą wskazującą znak *wartości*. Liczba całkowita jest ustawiona na 0, jeśli *wartość* jest dodatnia i jest ustawiona na liczbę niezerową, jeśli *wartość* jest ujemna.

Różnica między **_ecvt** a **_fcvt** polega na interpretacji parametru *count.* **_ecvt** interpretuje *liczą* się jako całkowita liczba cyfr w ciągu wyjściowym, podczas gdy **_fcvt** interpretuje *liczyć* jako liczbę cyfr po przecinku.

**_ecvt** i **_fcvt** użyć pojedynczego buforu statycznie przydzielonego do konwersji. Każde wywołanie jednej z tych procedur niszczy wyniki poprzedniego wywołania.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *dec* lub *znak* ma **wartość NULL**lub *liczba* wynosi 0, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i **NULL** jest zwracany.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fcvt**|\<>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
