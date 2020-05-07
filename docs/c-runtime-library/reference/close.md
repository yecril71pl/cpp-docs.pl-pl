---
title: _close
ms.date: 4/2/2020
api_name:
- _close
- _o__close
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
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: c642820bf1bc2e2afbd14e17832fb3fdb6f865b8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919857"
---
# <a name="_close"></a>_close

Zamyka plik.

## <a name="syntax"></a>Składnia

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku odwołujący się do otwartego pliku.

## <a name="return-value"></a>Wartość zwracana

**_close** zwraca wartość 0, jeśli plik został pomyślnie zamknięty. Zwracana wartość-1 wskazuje na błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_close** zamyka plik skojarzony z *FD*.

Deskryptor pliku i uchwyt pliku bazowego systemu operacyjnego są zamknięte. Dlatego nie jest konieczne Wywołaj metodę **CloseHandle** , jeśli plik został pierwotnie otwarty przy użyciu funkcji Win32 **File** i przekonwertowanej do deskryptora pliku przy użyciu **_open_osfhandle**.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *FD* jest nieprawidłowym deskryptorem pliku, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwracają wartość-1, a **errno** jest ustawiona na **EBADF**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_close**|\<IO. h>|\<errno. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [_open](open-wopen.md).

## <a name="see-also"></a>Zobacz też

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
