---
title: fwrite — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1320bcc61830833f2b1a4a225dff30652df2d3a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400583"
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

*buffer*<br/>
Wskaźnik do zapisania danych.

*Rozmiar*<br/>
Rozmiar elementu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów do zapisania.

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fwrite —** zwraca liczbę pełnych zapisana elementów, które mogą być mniejsza niż *liczba* w przypadku wystąpienia błędu. Ponadto jeśli wystąpi błąd, nie można ustalić wskaźnika położenia pliku. Jeśli dowolny *strumienia* lub *buforu* jest wskaźnika o wartości null, lub jeśli nieparzystą liczbę bajtów do zapisania określono w trybie Unicode, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [ Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**Fwrite —** funkcja zapisuje do *liczba* elementów, z *rozmiar* długość, z *buforu* z danymi wyjściowymi *strumienia*. Wskaźnika pliku skojarzone z *strumienia* (jeśli istnieje) jest zwiększany o liczba bajtów zapisanych w rzeczywistości. Jeśli *strumienia* jest otwarty w trybie tekstowym każdego wysuwu wiersza jest zastępowany znak powrotu karetki - pary wysuwu wiersza. Zastąpienie nie ma wpływu na wartość zwracaną.

Gdy *strumienia* jest otwarty w trybie translacji Unicode — na przykład, jeśli *strumienia* jest otwarty przez wywołanie metody **fopen —** i przy użyciu trybu parametru, który zawiera **ccs = UNICODE**, **ccs = UTF-16LE**, lub **ccs = UTF-8**, lub jeśli tryb jest zmienione na tryb tłumaczenia Unicode za pomocą **_setmode —** i tryb parametr, który zawiera **_O_WTEXT**, **_O_U16TEXT**, lub **_O_U8TEXT**—*buforu* jest interpretowana jako wskaźnik do Tablica **wchar_t** zawierający dane UTF-16. Próba zapisu nieparzystą liczbę bajtów w tym trybie powoduje błąd sprawdzania poprawności parametru.

Ponieważ ta funkcja umożliwia zablokowanie wątek wywołujący, jest bezpieczne wątkowo. Wersja — blokowanie dla **_fwrite_nolock —**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [fread —](fread.md).

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
