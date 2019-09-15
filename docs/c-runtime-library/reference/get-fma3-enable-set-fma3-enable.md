---
title: _get_FMA3_enable, _set_FMA3_enable
ms.date: 04/05/2018
api_name:
- _get_FMA3_enable
- _set_FMA3_enable
api_location:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: e18db90779ed59a6ca6976f69a5993d94d61c6bc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955932"
---
# <a name="_get_fma3_enable-_set_fma3_enable"></a>_get_FMA3_enable, _set_FMA3_enable

Pobiera lub ustawia flagę określającą, czy funkcje biblioteki zmiennoprzecinkowej przestępną Math używają instrukcji FMA3 w kodzie skompilowanym dla platform x64.

## <a name="syntax"></a>Składnia

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Parametry

*flag*<br/>
Ustaw wartość 1, aby włączyć implementacje FMA3 funkcji biblioteki zmiennoprzecinkowej przestępną Math na platformach x64 lub 0, aby użyć implementacji, które nie używają instrukcji FMA3.

## <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli są włączone implementacje FMA3 funkcji biblioteki zmiennoprzecinkowej przestępną Math. W przeciwnym razie zero.

## <a name="remarks"></a>Uwagi

Użyj funkcji **_set_FMA3_enable** , aby włączyć lub wyłączyć korzystanie z instrukcji FMA3 w funkcjach zmiennoprzecinkowych przestępną Math w bibliotece CRT. Wartość zwracana odzwierciedla implementację używaną po zmianie. Jeśli procesor nie obsługuje instrukcji FMA3, ta funkcja nie może włączyć ich w bibliotece, a zwracana wartość to zero. Użyj **_get_FMA3_enable** , aby uzyskać bieżący stan biblioteki. Domyślnie na platformach x64 kod uruchomienia CRT wykrywa, czy procesor obsługuje instrukcje FMA3, oraz włącza lub wyłącza implementacje FMA3 w bibliotece.

Ponieważ implementacje FMA3 używają różnych algorytmów, nieznaczne różnice w wyniku obliczeń mogą być zauważalne, gdy implementacje FMA3 są włączone lub wyłączone, lub między komputerami, które wykonują lub nie obsługują FMA3. Aby uzyskać więcej informacji, zobacz [problemy dotyczące migracji zmiennoprzecinkowej](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Wymagania

Funkcje **_set_FMA3_enable** i **_get_FMA3_enable** są dostępne tylko w wersjach x64 architektury CRT.

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C: \<Math. h ><br />C++: \<cmath > lub \<Math. h >|

Funkcje **_set_FMA3_enable** i **_get_FMA3_enable** są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[Problemy przy migracji liczb zmiennoprzecinkowych](../../porting/floating-point-migration-issues.md)<br/>
