---
title: _findclose
ms.date: 11/04/2016
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
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: 29010f8a502d463eeb6ca98837a1b7dae9f5ae6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538115"
---
# <a name="findclose"></a>_findclose

Zamyka uchwyt wyszukiwania i zwalnia skojarzonych zasobów.

## <a name="syntax"></a>Składnia

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>Parametry

*uchwyt*<br/>
Dojście wyszukiwania zwrócony przez poprzednie wywołanie **_findfirst**.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_findclose —** zwraca wartość 0. W przeciwnym razie zwraca wartość -1 i ustawia **errno** do **ENOENT**, wskazujący, że dopasowanie nie ma więcej plików został odnaleziony.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_findclose**|\<io.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wywołania systemowe](../../c-runtime-library/system-calls.md)<br/>
[Funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md)<br/>
