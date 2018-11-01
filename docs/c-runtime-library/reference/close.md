---
title: _close
ms.date: 11/04/2016
apiname:
- _close
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
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: faea008903136e8abdc39297672b31800ada796d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528027"
---
# <a name="close"></a>_close

Zamyka plik.

## <a name="syntax"></a>Składnia

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptor pliku odnoszące się do otwartego pliku.

## <a name="return-value"></a>Wartość zwracana

**_zamknij** zwraca wartość 0, jeśli plik został pomyślnie zamknięty. Zwracana wartość-1 wskazuje błąd.

## <a name="remarks"></a>Uwagi

**_Zamknij** funkcja zamyka plik skojarzony z *fd*.

Deskryptor pliku i dojście do pliku podstawowego systemu operacyjnego są zamknięte. W związku z tym, nie jest konieczne do wywołania **funkcja CloseHandle** Jeśli plik został pierwotnie otwarty przy użyciu funkcji Win32 **CreateFile** i przekonwertowane na deskryptor pliku przy użyciu **_open_osfhandle —**.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *fd* deskryptor pliku uszkodzonych jest wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwraca wartość -1 i **errno** ustawiono **EBADF**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_otwórz](open-wopen.md).

## <a name="see-also"></a>Zobacz także

[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
