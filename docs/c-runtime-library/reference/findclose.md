---
title: _findclose — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _findclose
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
- _findclose
- findclose
dev_langs:
- C++
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a25ed42f1a53eb81c834997f42db0154658f376
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395689"
---
# <a name="findclose"></a>_findclose

Zamyka dojście wyszukiwania i zwalnia zasoby skojarzone.

## <a name="syntax"></a>Składnia

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>Parametry

*Dojście*<br/>
Dojście wyszukiwania zwrócony przez poprzednie wywołanie **_findfirst —**.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_findclose —** zwraca wartość 0. W przeciwnym razie zwraca wartość -1 i ustawia **errno** do **enoent —**, wskazujący, że już pasujących plików można znaleźć.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_findclose**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md)<br/>
