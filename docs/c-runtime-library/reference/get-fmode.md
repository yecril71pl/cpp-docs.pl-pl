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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3e59e608f83874088b64d316c04053b94d8fbfdd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909872"
---
# <a name="_get_fmode"></a>_get_fmode

Pobiera domyślny tryb tłumaczenia plików dla operacji we/wy na plikach.

## <a name="syntax"></a>Składnia

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Wskaźnik do liczby całkowitej, która ma zostać wypełniona bieżącym trybem domyślnym: **_O_TEXT** lub **_O_BINARY**.

## <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli pomyślne; kod błędu w przypadku niepowodzenia. Jeśli *PMODE* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja pobiera wartość [_fmode](../../c-runtime-library/fmode.md) zmiennej globalnej. Ta zmienna określa domyślny tryb tłumaczenia plików dla operacji we/wy na niskim poziomie i w strumieniu, takich jak **_open**, **_pipe**, **fopen**i [freopen](freopen-wfreopen.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<STDLIB. h>|\<fcntl. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Zobacz też

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[We/wy pliku w trybie tekstowym i binarnym](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
