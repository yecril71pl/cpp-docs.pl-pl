---
title: _chsize_s
ms.date: 4/2/2020
api_name:
- _chsize_s
- _o__chsize_s
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
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: 70845124eb889d73a0f87aadd923e2d86db96c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350080"
---
# <a name="_chsize_s"></a>_chsize_s

Zmienia rozmiar pliku. Jest to wersja [_chsize](chsize.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Deskryptora pliku odwołującego się do otwartego pliku.

*Rozmiar*<br/>
Nowa długość pliku w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_chsize_s** zwraca wartość 0, jeśli rozmiar pliku został pomyślnie zmieniony. Wartość zwracana niezerowa wskazuje błąd: zwracana wartość to **EACCES,** jeśli określony plik jest zablokowany przed dostępem, **EBADF,** jeśli określony plik jest tylko do odczytu lub deskryptor jest nieprawidłowy, **ENOSPC,** jeśli na urządzeniu nie ma miejsca, lub **EINVAL,** jeśli rozmiar jest mniejszy niż zero. **errno** jest ustawiona na tę samą wartość.

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_chsize_s** rozszerza lub obcina plik skojarzony z *fd* do długości określonej przez *rozmiar*. Plik musi być otwarty w trybie, który pozwala na zapisywanie. Znaki null ('\0') są dołączane, jeśli plik zostanie rozszerzony. Jeśli plik zostanie obcięty, wszystkie dane od końca skróconego pliku do oryginalnej długości pliku są tracone.

**_chsize_s** przyjmuje 64-bitową liczebność jako rozmiar pliku i dlatego może obsługiwać rozmiary plików większe niż 4 GB. **_chsize** jest ograniczona do 32-bitowych rozmiarów plików.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *fd* nie jest prawidłowym deskryptorem lub rozmiar pliku jest mniejszy niż zero, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [polu Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md)

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<> io.h|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
