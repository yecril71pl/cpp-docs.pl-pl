---
title: _get_FMA3_enable, _set_FMA3_enable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_FMA3_enable
- _set_FMA3_enable
apilocation:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
dev_langs:
- C++
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
caps.latest.revision: 1
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84087e0883aef3de65081dd2337b8ec588bd1528
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable, _set_FMA3_enable

Pobiera lub ustawia flagę określającą, czy funkcje liczb zmiennoprzecinkowych biblioteki matematyczne przestępne skorzystaj z FMA3 instrukcji w kodzie skompilowanym X64 platform.

## <a name="syntax"></a>Składnia

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Parametry

*flag*<br/>
Ustawiona na 1, aby włączyć implementacje FMA3 funkcje liczb zmiennoprzecinkowych biblioteki matematyczne przestępne na X64 platformy, lub na 0, aby użyć implementacji, które nie korzystają z FMA3 instrukcje.

## <a name="return-value"></a>Wartość zwracana

Wartość inną niż zero, jeśli implementacje FMA3 funkcje liczb zmiennoprzecinkowych biblioteki matematyczne przestępne są włączone. W przeciwnym razie wartość zero.

## <a name="remarks"></a>Uwagi

Użyj **_set_FMA3_enable** funkcji, aby włączyć lub wyłączyć korzystanie z instrukcjami FMA3 funkcje liczb zmiennoprzecinkowych przestępne matematyczne biblioteki CRT. Wartość zwracana odzwierciedla wdrażania używany po zmianie. Jeśli Procesor nie obsługuje instrukcji FMA3, tej funkcji nie można włączyć je w bibliotece, a wartość zwracana jest wartość zero. Użyj **_get_FMA3_enable** można pobrać z bieżącym stanem biblioteki. Domyślnie na X64 platform, kod uruchomienia CRT wykrywa, czy procesor CPU obsługuje instrukcje FMA3 i włącza lub wyłącza implementacje FMA3 w bibliotece.

Ponieważ implementacje FMA3 używają różnych algorytmów, niewielkie różnice w wyniku obliczenia może być według, gdy implementacje FMA3 są włączone lub wyłączone lub między komputerami, które nie obsługują FMA3 lub nie. Aby uzyskać więcej informacji, zobacz [problemy przy migracji zmiennoprzecinkowe](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Wymagania

**_Set_FMA3_enable** i **_get_FMA3_enable** funkcje są dostępne tylko w X64 wersji CRT.

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C: \<math.h ><br />C++: \<cmath > lub \<math.h >|

**_Set_FMA3_enable** i **_get_FMA3_enable** funkcje są określone firmy Microsoft. Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[Problemy przy migracji liczb zmiennoprzecinkowych](../../porting/floating-point-migration-issues.md)<br/>
