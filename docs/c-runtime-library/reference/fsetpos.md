---
title: fsetpos
ms.date: 4/2/2020
api_name:
- fsetpos
- _o_fsetpos
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
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: 22b8cebd0154c0dbfc3d21843380ebc9a139059a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345721"
---
# <a name="fsetpos"></a>fsetpos

Ustawia wskaźnik położenia strumienia.

## <a name="syntax"></a>Składnia

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

*Poz*<br/>
Przechowywanie wskaźnika położenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **fsetpos** zwraca wartość 0. W przypadku awarii funkcja zwraca wartość niezerową i ustawia **errno** na jedną z następujących stałych manifestu (zdefiniowaną w ERRNO. H): **EBADF**, co oznacza, że plik nie jest dostępny lub obiekt, który *wskazuje strumień* nie jest prawidłową strukturą plików; lub **EINVAL**, co oznacza nieprawidłową wartość *dla strumienia* lub *pos* została przekazana. Jeśli nieprawidłowy parametr jest przekazywany, te funkcje wywołają nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Funkcja **fsetpos** ustawia wskaźnik położenia pliku dla *strumienia* na wartość *pos*, która jest uzyskiwana we wcześniejszym wywołaniu **fgetpos** względem *strumienia.* Funkcja czyści wskaźnik końca pliku i cofa wszelkie skutki [ungetc](ungetc-ungetwc.md) na *strumień*. Po wywołaniu **fsetpos**następna operacja na *strumień* może być albo wejście lub wyjście.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [dla fgetpos](fgetpos.md).

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
