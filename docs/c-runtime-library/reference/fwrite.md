---
title: fwrite
ms.date: 4/2/2020
api_name:
- fwrite
- _o_fwrite
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: a5bd6da3c8d16189f7ff0db744901e03513acc21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345396"
---
# <a name="fwrite"></a>fwrite

Zapisuje dane do strumienia.

## <a name="syntax"></a>Składnia

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Buforu*<br/>
Wskaźnik do danych, które mają zostać zapisane.

*Rozmiar*<br/>
Rozmiar elementu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów do zapisania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

**fwrite** zwraca liczbę pełnych elementów faktycznie napisane, które mogą być mniejsze niż *liczyć,* jeśli wystąpi błąd. Ponadto w przypadku wystąpienia błędu nie można określić wskaźnika położenia pliku. Jeśli *strumień* lub *bufor* jest wskaźnikiem zerowym lub jeśli w trybie Unicode określono nieparzystą liczbę bajtów do zapisania, funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca 0.

## <a name="remarks"></a>Uwagi

Funkcja **fwrite** zapisuje do *zliczania* elementów o długości *rozmiaru* każdego, od *bufora* do *strumienia*wyjściowego . Wskaźnik pliku skojarzony ze *strumieniem* (jeśli istnieje) jest zwiększany o liczbę bajtów faktycznie zapisanych. Jeśli *strumień* jest otwierany w trybie tekstowym, każdy kanał informacyjny wiersza jest zastępowany parą podajnika wiersza powrotu karetki. Zastąpienie nie ma wpływu na wartość zwracaną.

Po *otwarciu strumienia* w trybie tłumaczenia Unicode — na przykład jeśli *strumień* jest otwierany przez wywołanie **fopen** i przy użyciu parametru trybu, który zawiera **ccs=UNICODE**, **ccs=UTF-16LE**lub **ccs=UTF-8**, lub jeśli tryb zostanie zmieniony na tryb tłumaczenia Unicode przy użyciu **_setmode** i parametru trybu, który zawiera **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT**—*bufor* jest interpretowany jako wskaźnik do tablicy **wchar_t** zawierającej dane UTF-16. Próba zapisania nieparzystej liczby bajtów w tym trybie powoduje błąd sprawdzania poprawności parametru.

Ponieważ ta funkcja blokuje wątku wywołującego, jest bezpieczne dla wątków. Aby uzyskać wersję niezablokującą, zobacz **_fwrite_nolock**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [fread](fread.md).

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
