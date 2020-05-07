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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: faed95bfeb6fad88f502101e166ec6124b6e591d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910413"
---
# <a name="_chsize_s"></a>_chsize_s

Zmienia rozmiar pliku. Jest to wersja [_chsize](chsize.md) z ulepszonymi zabezpieczeniami, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku odwołujący się do otwartego pliku.

*size*<br/>
Nowa długość pliku w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_chsize_s** zwraca wartość 0, jeśli rozmiar pliku został pomyślnie zmieniony. Wartość zwracana niezerową wskazuje na błąd: wartość zwracana jest **EACCES** , jeśli określony plik jest zablokowany do dostępu, **EBADF** , jeśli określony plik jest tylko do odczytu lub deskryptor jest nieprawidłowy, **ENOSPC** , jeśli na urządzeniu nie pozostało miejsca, lub **EINVAL** , jeśli rozmiar jest mniejszy od zera. **errno** jest równa tej samej wartości.

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_chsize_s** rozszerza lub obcina plik skojarzony z *FD* do długości określonej przez *rozmiar*. Plik musi być otwarty w trybie, który umożliwia zapisywanie. Jeśli plik zostanie rozszerzony, dołączane są znaki null (' \ 0 '). Jeśli plik zostanie obcięty, wszystkie dane od końca skróconego pliku do oryginalnej długości pliku zostaną utracone.

**_chsize_s** przyjmuje 64-bitową liczbę całkowitą jako rozmiar pliku i w związku z tym mogą obsługiwać rozmiary plików większe niż 4 GB. **_chsize** jest ograniczony do 32-bitowych rozmiarów plików.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *FD* nie jest prawidłowym deskryptorem pliku lub jego rozmiar jest mniejszy od zera, wywoływana jest procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<IO. h>|\<errno. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
