---
title: _get_fmode — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_fmode
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
- get_fmode
- _get_fmode
dev_langs:
- C++
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a28909e5e848712305fb28e8ac4d46180f8948cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398305"
---
# <a name="getfmode"></a>_get_fmode

Pobiera domyślny tryb tłumaczenia pliku dla operacji We/Wy na plikach.

## <a name="syntax"></a>Składnia

```C
errno_t _get_fmode( 
   int * pmode 
);
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Wskaźnik do wartości całkowitej, należy podać bieżący tryb domyślny: **_o_text —** lub **_o_binary —**.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero w przypadku powodzenia; błąd o kodzie błędu. Jeśli *pmode* jest **NULL**, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **einval —**.

## <a name="remarks"></a>Uwagi

Funkcja pobiera wartość [_fmode —](../../c-runtime-library/fmode.md) zmiennej globalnej. Ta zmienna Określa domyślny tryb tłumaczenia pliku dla obu niskiego poziomu i strumienia operacji We/Wy plików, takich jak **_otwórz**, **_pipe —**, **fopen —**, i [ freopen —](freopen-wfreopen.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [_set_fmode —](set-fmode.md).

## <a name="see-also"></a>Zobacz także

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[We/Wy pliku w trybie binarnym i tekstowym](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
