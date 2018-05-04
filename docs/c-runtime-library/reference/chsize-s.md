---
title: _chsize_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d131f5e21fa4980e77cfb9dc858d5329b94e2b93
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="chsizes"></a>_chsize_s

Zmienia rozmiar pliku. To jest wersja [_chsize —](chsize.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Plik deskryptora odwołujących się do otwartego pliku.

*Rozmiar*<br/>
Długość nowego pliku w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_chsize_s —** zwraca wartość 0, jeśli rozmiar pliku zostało pomyślnie zmienione. Podano niezerowe wartości zwracanej wskazuje błąd: wartość zwracana jest **eacces —** , jeśli określony plik jest zablokowany przed dostępem, **ebadf —** Jeśli określony plik jest tylko do odczytu lub jest nieprawidłowy, deskryptora **Enospc —** , jeśli nie ma jest wolnego miejsca na urządzeniu, lub **einval —** Jeśli rozmiar jest mniejszy od zera. **errno** jest ustawiona na tę samą wartość.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Chsize_s —** funkcja rozszerza lub obcina plik skojarzony z *fd* do długości określonej przez *rozmiar*. Plik musi być otwarty w trybie umożliwiającym zapis. Znaki null ('\0') są dołączane, jeśli plik zostanie rozszerzony. Jeśli plik został obcięty, wszystkie dane na końcu pliku skróconą długość oryginalnego pliku zostaną utracone.

**_chsize_s —** ma 64-bitową liczbę całkowitą jako rozmiar pliku, a więc może obsługiwać rozmiary plików większych niż 4 GB. **_chsize —** jest ograniczone do rozmiarów plików 32-bitowych.

Ta funkcja weryfikuje jego parametrów. Jeśli *fd* nie jest prawidłowy plik deskryptora lub rozmiar jest mniejszy od zera, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
