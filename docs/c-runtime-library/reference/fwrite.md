---
title: fwrite
ms.date: 11/04/2016
apiname:
- fwrite
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: b4d6b9ce4fb66ee545f52946e28e4984d9e4f924
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287550"
---
# <a name="fwrite"></a>fwrite

Zapisuje dane w strumieniu.

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

*buffer*<br/>
Wskaźnik do danych, które ma zostać zapisany.

*Rozmiar*<br/>
Rozmiar elementu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów, które mają być zapisywane.

*stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fwrite —** zwraca liczbę pełnych elementów rzeczywiście zapisanych, która może być mniejsza niż *liczba* w przypadku wystąpienia błędu. Ponadto jeśli wystąpi błąd, nie można określić wskaźnik położenia pliku. Jeśli *strumienia* lub *buforu* jest wskaźnikiem typu null lub jeżeli nieparzystą liczbę bajtów do zapisania została określona w trybie Unicode, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**Fwrite —** funkcja zapisuje do *liczba* elementów, z *rozmiar* długość każdej z nich i z *buforu* w danych wyjściowych *strumienia*. Skojarzony wskaźnik pliku *strumienia* (jeśli istnieje) jest zwiększany o liczbę bajtów, które rzeczywiście zapisanych. Jeśli *strumienia* jest otwarty w trybie tekstowym każdego wysuwu wiersza jest zastępowany znaku powrotu karetki - pary wysuwu wiersza. Zastąpienie nie ma wpływu na wartość zwracaną.

Gdy *strumienia* jest otwarty w trybie tłumaczenia Unicode — na przykład, jeśli *strumienia* jest otwarty przez wywołanie metody **fopen —** i za pomocą parametru tryb, który zawiera **ccs = UNICODE**, **ccs = UTF-16LE**, lub **ccs = UTF-8**, lub zmiana tryb na tryb translacji Unicode przy użyciu **_setmode —** i tryb parametr, który zawiera **_O_WTEXT**, **_O_U16TEXT**, lub **_O_U8TEXT**—*buforu* jest interpretowany jako wskaźnik do Tablica **wchar_t** zawierający dane UTF-16. Błąd sprawdzania poprawności parametru powoduje, że próba zapisu nieparzystą liczbę bajtów w tym trybie.

Ponieważ ta funkcja blokuje wątek wywołujący, jest metodą o bezpiecznych wątkach. Dla wersji bez blokady, zobacz **_fwrite_nolock —**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [fread —](fread.md).

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
