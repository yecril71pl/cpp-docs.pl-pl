---
title: _zamknij | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eabf084d2e4dd7e280c0ff730d1ec34d86f1ed98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394200"
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
Plik deskryptora odwołujących się do otwartego pliku.

## <a name="return-value"></a>Wartość zwracana

**_zamknij** zwraca wartość 0, jeśli plik został zamknięty pomyślnie. Zwracana wartość -1 wskazuje błąd.

## <a name="remarks"></a>Uwagi

**_Zamknij** funkcja zamyka plik skojarzony z *fd*.

Deskryptorów plików i dojście do pliku podstawowego systemu operacyjnego są zamknięte. W związku z tym nie jest konieczne do wywołania **CloseHandle** Jeśli plik został pierwotnie otwarty przy użyciu funkcji Win32 **CreateFile** i przekonwertować deskryptora pliku przy użyciu **_open_osfhandle —**.

Ta funkcja weryfikuje jego parametrów. Jeśli *fd* deskryptor nieprawidłowego pliku, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, funkcje, zwraca -1 i **errno** ustawiono **ebadf —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_otwórz](open-wopen.md).

## <a name="see-also"></a>Zobacz także

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
