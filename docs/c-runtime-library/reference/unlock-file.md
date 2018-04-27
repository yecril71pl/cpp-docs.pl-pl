---
title: _unlock_file — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 503087d84e65e556fa610efbf0054c66ee774d48
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="unlockfile"></a>_unlock_file

Umożliwia odblokowanie pliku, dzięki czemu inne procesy dostępu do tego pliku.

## <a name="syntax"></a>Składnia

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>Parametry

*plik* dojście do pliku.

## <a name="remarks"></a>Uwagi

**_Unlock_file —** funkcji powoduje odblokowanie pliku określonego przez *pliku*. Odblokowanie pliku zezwala na dostęp do pliku przez inne procesy. Ta funkcja nie powinna być wywoływana, chyba że **_lock_file —** wcześniej została wywołana w *pliku* wskaźnika. Wywoływanie **_unlock_file —** w pliku, który nie jest zablokowany może doprowadzić do zakleszczenia. Na przykład zobacz [_lock_file —](lock-file.md).

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
