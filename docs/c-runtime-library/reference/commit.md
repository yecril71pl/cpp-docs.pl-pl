---
title: _commit
ms.date: 11/04/2016
apiname:
- _commit
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
- _commit
- commit
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
ms.openlocfilehash: 8408158cb3d4ef0d29d9af24d8a2acbd28e00192
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523074"
---
# <a name="commit"></a>_commit

Opróżnia plik bezpośrednio na dysku.

## <a name="syntax"></a>Składnia

```C
int _commit(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptor pliku odnoszące się do otwartego pliku.

## <a name="return-value"></a>Wartość zwracana

**_commit** zwraca wartość 0, jeśli plik został pomyślnie wyczyszczone na dysku. Zwracana wartość-1 wskazuje błąd.

## <a name="remarks"></a>Uwagi

**_Commit** funkcja wymusza systemu operacyjnego, aby zapisać plik skojarzony z *fd* na dysku. To wywołanie gwarantuje, że określony plik jest opróżniany natychmiast, nie uznania systemu operacyjnego.

Jeśli *fd* nieprawidłowego deskryptora pliku, jest wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość -1 i **errno** ustawiono **EBADF**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>
