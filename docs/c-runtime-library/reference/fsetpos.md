---
title: fsetpos — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fsetpos
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
- fsetpos
dev_langs:
- C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ceacacbe029488995c47e305682b56751347591
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="fsetpos"></a>fsetpos

Ustawia wskaźnik pozycji w strumieniu.

## <a name="syntax"></a>Składnia

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

*POS*<br/>
Wskaźnik położenia magazynu.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **fsetpos —** zwraca wartość 0. W przypadku awarii, funkcja zwraca wartość różną od zera i ustawia **errno** do jednej z następujących manifestu — stałe (zdefiniowany w numer błędu. H): **ebadf —**, co oznacza, że plik nie jest dostępny lub obiekt który *strumienia* punktów nie jest prawidłowym plikiem strukturą; lub **einval —**, co oznacza nieprawidłową wartością dla *strumienia* lub *pos* został przekazany. Jeśli przekazano nieprawidłowy parametr tych funkcji Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.

## <a name="remarks"></a>Uwagi

**Fsetpos —** funkcja ustawia wskaźnik położenia pliku *strumienia* wartość *pos*, jest uzyskiwany wcześniejszym wywołaniu **fgetpos —**przed *strumienia*. Funkcja usuwa plik końcowy wskaźnika i cofa efekty [ungetc —](ungetc-ungetwc.md) na *strumienia*. Po wywołaniu **fsetpos —**, następnej operacji na *strumienia* mogą być danych wejściowych lub wyjściowych.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [fgetpos —](fgetpos.md).

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
