---
title: _commit
ms.date: 11/04/2016
api_name:
- _commit
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _commit
- commit
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
ms.openlocfilehash: b5a417deef48c89751f56feec480e90444728687
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939049"
---
# <a name="_commit"></a>_commit

Opróżnia plik bezpośrednio na dysk.

## <a name="syntax"></a>Składnia

```C
int _commit(
   int fd
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku odwołujący się do otwartego pliku.

## <a name="return-value"></a>Wartość zwracana

**_commit** zwraca wartość 0, jeśli plik został pomyślnie opróżniony na dysk. Zwracana wartość-1 wskazuje na błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_commit** wymusza, aby system operacyjny pisał plik skojarzony z *FD* na dysk. To wywołanie gwarantuje, że określony plik jest natychmiast opróżniany, a nie na poziomie uznania systemu operacyjnego.

Jeśli *FD* jest nieprawidłowym deskryptorem pliku, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1, a **errno** jest ustawiona na **EBADF**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>
