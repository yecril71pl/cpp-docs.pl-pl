---
title: _commit — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9396fd502f5137b469c9f92110bfc23c9d2fb246
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="commit"></a>_commit

Liczba opróżnień pliku bezpośrednio na dysku.

## <a name="syntax"></a>Składnia

```C
int _commit(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Plik deskryptora odwołujących się do otwartego pliku.

## <a name="return-value"></a>Wartość zwracana

**_commit —** zwraca wartość 0, jeśli plik został pomyślnie wyczyszczone na dysku. Zwracana wartość -1 wskazuje błąd.

## <a name="remarks"></a>Uwagi

**_Commit —** funkcja wymusza systemu operacyjnego można zapisać pliku skojarzone z *fd* na dysku. To wywołanie gwarantuje, że określony plik jest opróżniany natychmiast, nie uznania systemu operacyjnego.

Jeśli *fd* jest deskryptora nieprawidłowy plik wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, funkcja zwraca wartość -1 i **errno** ustawiono **ebadf —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>
