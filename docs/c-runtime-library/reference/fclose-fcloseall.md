---
title: fclose, _fcloseall
ms.date: 4/2/2020
api_name:
- fclose
- _fcloseall
- _o__fcloseall
- _o_fclose
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: b2ee14c5fc8bb47cc2652443c0263bd14147c90d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347489"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Zamyka strumień (**fclose**) lub zamyka wszystkie otwarte strumienie **(_fcloseall**).

## <a name="syntax"></a>Składnia

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

**fclose** zwraca wartość 0, jeśli strumień został pomyślnie zamknięty. **_fcloseall** zwraca całkowitą liczbę zamkniętych strumieni. Obie funkcje zwracają **EOF,** aby wskazać błąd.

## <a name="remarks"></a>Uwagi

Funkcja **fclose** zamyka *strumień*. Jeśli *strumień* ma **wartość NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **fclose** ustawia **errno** na **EINVAL** i zwraca **EOF**. Zaleca się, aby wskaźnik *strumienia* zawsze sprawdzał przed wywołaniem tej funkcji.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr aby](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) uzyskać więcej informacji na temat tych i innych kodów błędów.

Funkcja **_fcloseall** zamyka wszystkie otwarte strumienie z wyjątkiem **stdin**, **stdout**, **stderr** (oraz, w MS-DOS, **_stdaux** i **_stdprn).** Zamyka również i usuwa wszystkie pliki tymczasowe utworzone przez **tmpfile**. W obu funkcjach wszystkie bufory skojarzone ze strumieniem są opróżniane przed zamknięciem. Bufory przydzielone systemowe są zwalniane po zamknięciu strumienia. Bufory przypisane przez użytkownika z **setbuf** i **setvbuf** nie są zwalniane automatycznie.

**Uwaga:** Gdy te funkcje są używane do zamykania strumienia, podstawowy deskryptor pliku i dojście do pliku systemu operacyjnego (lub gniazdo) są zamknięte, a także strumień. Tak więc, jeśli plik został pierwotnie otwarty jako uchwyt pliku lub deskryptor pliku i jest zamknięty **z fclose**, nie należy również wywoływać **_close,** aby zamknąć deskryptor pliku; nie należy wywoływać funkcji Win32 **CloseHandle,** aby zamknąć dojście do pliku.

**fclose** i **_fcloseall** zawierają kod w celu ochrony przed zakłóceniami od innych wątków. Aby uzyskać nieblokującą wersję **fclose**, zobacz **_fclose_nolock**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fclose ( fclose )**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
