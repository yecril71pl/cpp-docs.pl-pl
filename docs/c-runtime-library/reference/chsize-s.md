---
title: _chsize_s
ms.date: 11/04/2016
apiname:
- _chsize_s
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
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: a56efe826d43c80dc2cdee295e58872e7dd3c9ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348513"
---
# <a name="chsizes"></a>_chsize_s

Zmienia rozmiar pliku. To jest wersja [_chsize —](chsize.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptor pliku odnoszące się do otwartego pliku.

*Rozmiar*<br/>
Długość nowego pliku w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_chsize_s —** zwraca wartość 0, jeśli rozmiar pliku zostało pomyślnie zmienione. Wartość różną od zera, zwracana wartość wskazuje błąd: wartość zwracana jest **EACCES** Jeśli określony plik jest zablokowany przed dostępem, **EBADF** Jeśli określony plik jest tylko do odczytu lub deskryptora jest nieprawidłowy, **ENOSPC** Jeśli nie miejsca na urządzeniu lub **EINVAL** Jeśli rozmiar jest mniejszy od zera. **errno** jest ustawiona na tę samą wartość.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Chsize_s —** funkcja rozszerza lub obcina plik skojarzony z *fd* do długości określonej przez *rozmiar*. Plik musi być otwarty w trybie który pozwala na zapis. Znaki null ('\0') są dołączane, jeśli plik zostanie rozszerzony. Jeśli plik został obcięty, wszystkie dane na końcu pliku skróconą długość oryginalnego pliku zostaną utracone.

**_chsize_s —** ma 64-bitową liczbę całkowitą jako rozmiar pliku, a więc może obsługiwać plików o rozmiarze większym niż 4 GB. **_chsize —** jest ograniczona do rozmiarów plików 32-bitowych.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *fd* nie jest prawidłowy plik deskryptora lub rozmiar jest mniejszy od zera, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
