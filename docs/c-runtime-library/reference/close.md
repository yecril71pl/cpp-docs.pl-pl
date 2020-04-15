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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 4d8b702a10624ae80629b4ce4644c428322500cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348644"
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

*Fd*<br/>
Deskryptora pliku odnoszącego się do otwartego pliku.

## <a name="return-value"></a>Wartość zwracana

**_close** zwraca wartość 0, jeśli plik został pomyślnie zamknięty. Zwracana wartość -1 oznacza błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_close** zamyka plik skojarzony z *fd*.

Deskryptor pliku i podstawowy uchwyt pliku systemu operacyjnego są zamknięte. W związku z tym nie jest konieczne wywołanie **CloseHandle,** jeśli plik został pierwotnie otwarty za pomocą funkcji Win32 **CreateFile** i przekonwertowany na deskryptor pliku za pomocą **_open_osfhandle**.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *fd* jest złym deskryptorem pliku, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcje zwraca -1 i **errno** jest ustawiona na **EBADF**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_close**|\<> io.h|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_open](open-wopen.md).

## <a name="see-also"></a>Zobacz też

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
