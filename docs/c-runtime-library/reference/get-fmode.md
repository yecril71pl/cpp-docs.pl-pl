---
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: fbaa30d0842400037f37508df94726f3e7fd7090
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345168"
---
# <a name="_get_fmode"></a>_get_fmode

Pobiera domyślny tryb tłumaczenia plików dla operacji we/wy pliku.

## <a name="syntax"></a>Składnia

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Wskaźnik do liczby całkowitej, który ma być wypełniony bieżącym trybem domyślnym: **_O_TEXT** lub **_O_BINARY**.

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli zakończy się pomyślnie; kod błędu w przypadku awarii. Jeśli *pmode* ma **wartość NULL,** nieprawidłowy program obsługi parametrów jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i funkcja zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja pobiera wartość [zmiennej globalnej _fmode.](../../c-runtime-library/fmode.md) Ta zmienna określa domyślny tryb tłumaczenia plików zarówno dla operacji we/wy pliku niskiego poziomu, jak i dla pliku strumieniowego, takich jak **_open**, **_pipe**, **fopen**i [freopen](freopen-wfreopen.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<>|\<fcntl.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Zobacz też

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[We/Wy pliku w trybie tekstowym i binarnym](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
