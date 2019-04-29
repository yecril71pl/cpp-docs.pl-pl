---
title: _unlock_file
ms.date: 11/04/2016
apiname:
- _unlock_file
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: e3d11cbd59ef5846b33908ae6b6c40d7ea6125e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353550"
---
# <a name="unlockfile"></a>_unlock_file

Umożliwia odblokowanie pliku, dzięki czemu inne procesy uzyskać dostęp do pliku.

## <a name="syntax"></a>Składnia

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>Parametry

*Plik*<br/>
Dojście do pliku.

## <a name="remarks"></a>Uwagi

**_Unlock_file —** funkcji powoduje odblokowanie pliku określonego przez *pliku*. Odblokowanie pliku zezwala na dostęp do pliku przez inne procesy. Ta funkcja nie powinien być wywoływany, chyba że **_lock_file —** był wcześniej nazywany programem na *pliku* wskaźnika. Wywoływanie **_unlock_file —** w pliku, który nie jest zablokowany może doprowadzić do zakleszczenia. Aby uzyskać przykład, zobacz [_lock_file —](lock-file.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
