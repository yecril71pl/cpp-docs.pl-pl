---
title: fwrite
ms.date: 11/04/2016
api_name:
- fwrite
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
ms.openlocfilehash: 8149e0f2cbc84c2c28093d86fecd5ff2a9db7aba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956196"
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
Wskaźnik do danych do zapisania.

*zmienia*<br/>
Rozmiar elementu, w bajtach.

*liczbą*<br/>
Maksymalna liczba elementów do zapisania.

*stream*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

**fwrite** zwraca liczbę pełnych elementów, które faktycznie zapisano, co może być mniejsze niż *Liczba* w przypadku wystąpienia błędu. Ponadto, jeśli wystąpi błąd, nie można określić wskaźnika położenia pliku. Jeśli *strumień* lub *bufor* jest wskaźnikiem typu null lub jeśli w trybie Unicode określono nieparzystą liczbę bajtów do zapisania, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca wartość 0.

## <a name="remarks"></a>Uwagi

Funkcja **fwrite** zapisuje maksymalnie *liczbę* elementów *o długości każdego* z bufora do *strumienia*wyjściowego . Wskaźnik pliku skojarzony ze *strumieniem* (jeśli istnieje) jest zwiększany o liczbę bajtów rzeczywiście zapisywana. Jeśli *strumień* jest otwarty w trybie tekstowym, każde źródło wierszy jest zastępowane parą wysuwu wiersza. Zastąpienie nie ma wpływu na wartość zwracaną.

Gdy *strumień* jest otwarty w trybie tłumaczenia Unicode — na przykład, jeśli *strumień* jest otwarty przez wywołanie **fopen** i przy użyciu parametru trybu, który zawiera **CCS = Unicode**, **CCS = UTF-16LE**lub **CCS = UTF-8**, lub jeśli tryb jest Zmieniono do trybu translacji Unicode przy użyciu **_setmode** i parametru trybu, który zawiera **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT**—*bufor* jest interpretowany jako wskaźnik do tablicy **wchar_t** , która zawiera Dane UTF-16. Próba zapisania nieparzystej liczby bajtów w tym trybie powoduje błąd walidacji parametru.

Ponieważ ta funkcja blokuje wątek wywołujący, jest bezpieczny wątkowo. W przypadku wersji, która nie jest blokowana, zobacz **_fwrite_nolock**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [fread](fread.md).

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
