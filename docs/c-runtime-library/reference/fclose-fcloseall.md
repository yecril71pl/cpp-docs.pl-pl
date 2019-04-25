---
title: fclose, _fcloseall
ms.date: 11/04/2016
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 4713ffb7ecdf8da73e5f949bbef7be124dfaf28a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334882"
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall

Zamyka strumienia (**fclose —**) lub zamyka wszystkie otwarte strumienie (**_fcloseall**).

## <a name="syntax"></a>Składnia

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fclose —** zwraca wartość 0, jeśli strumień jest zamknięty pomyślnie. **_fcloseall** zwraca łączna liczbę strumieni zamknięte. Obie funkcje zwracają **EOF** wystąpił błąd.

## <a name="remarks"></a>Uwagi

**Fclose —** funkcji zamyka *strumienia*. Jeśli *strumienia* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **fclose —** ustawia **errno** do **EINVAL** i zwraca **EOF**. Zalecane jest, *strumienia* wskaźnika można zawsze sprawdzić przed wywołaniem tej funkcji.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

**_Fcloseall** funkcji spowoduje zamknięcie wszystkich otwartych strumieni z wyjątkiem **stdin**, **stdout**, **stderr** (i w systemie MS-DOS, **_stdaux**  i **_stdprn**). Ponadto zamyka i spowoduje usunięcie plików tymczasowych utworzonych przez **tmpfile —**. W obu tych funkcji wszystkie bufory skojarzone ze strumienia jest opróżniany przed zamknięciem. Bufory przypisane do systemu są zwalniane, gdy strumień jest zamknięty. Bufory przypisane przez użytkownika za pomocą **setbuf —** i **setvbuf —** nie są automatycznie zwalniane.

**Uwaga:** W przypadku używania tych funkcji, aby zamknąć strumień bazowego deskryptorów plików i systemu operacyjnego dojście do pliku (lub gniazda) zostały zamknięte, a także strumień. W związku z tym, jeśli pierwotnie został otworzony plik jako plik obsługi deskryptor pliku lub jest zamknięty z **fclose —**, czy nie również wywołanie **_zamknij** do zamknij deskryptora pliku; nie należy wywoływać funkcję Win32  **Funkcja CloseHandle** zamknąć dojście do pliku.

**fclose —** i **_fcloseall** obejmują kodu w celu ochrony przed zakłóceniami z innych wątków. Dla wersji bez blokady z **fclose —**, zobacz **_fclose_nolock —**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fclose —**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [fopen —](fopen-wfopen.md).

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
