---
title: _unlock_file
ms.date: 4/2/2020
api_name:
- _unlock_file
- _o__unlock_file
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: ed79f66baebf71c89e537c8343779bef44ebfbb8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909204"
---
# <a name="_unlock_file"></a>_unlock_file

Odblokowuje plik, umożliwiając innym procesom dostęp do pliku.

## <a name="syntax"></a>Składnia

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>Parametry

*rozszerzeniem*<br/>
Dojście do pliku.

## <a name="remarks"></a>Uwagi

Funkcja **_unlock_file** odblokowuje plik określony przez *plik*. Odblokowanie pliku umożliwia dostęp do pliku przez inne procesy. Ta funkcja nie powinna być wywoływana, chyba że **_lock_file** została wcześniej wywołana na wskaźniku *pliku* . Wywołanie **_unlock_file** w pliku, który nie jest zablokowany, może spowodować zakleszczenie. Aby zapoznać się z przykładem, zobacz [_lock_file](lock-file.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_unlock_file**|\<stdio. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
