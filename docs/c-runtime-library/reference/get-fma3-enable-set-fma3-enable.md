---
title: _get_FMA3_enable, _set_FMA3_enable
ms.date: 04/05/2018
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
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: 19eabc3b5a11246d5b0056bdafbb169e2a7de9f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544368"
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable, _set_FMA3_enable

Pobiera lub ustawia flagę określającą, czy funkcje zmiennoprzecinkowe biblioteki matematyczne przestępna używać FMA3 instrukcji w kodzie skompilowanym X64 platform.

## <a name="syntax"></a>Składnia

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Parametry

*flag*<br/>
Ustawiona na 1, aby włączyć implementacje FMA3 funkcje zmiennoprzecinkowe biblioteki matematyczne przestępna na X64 platform, lub 0, aby użyć implementacji, które nie korzystają z FMA3 instrukcje.

## <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli implementacje FMA3 funkcji zmiennoprzecinkowej bibliotek matematycznych przestępna są włączone. W przeciwnym razie, wartość zero.

## <a name="remarks"></a>Uwagi

Użyj **_set_FMA3_enable** funkcję, aby włączyć lub wyłączyć użycie FMA3 zgodnie z instrukcjami w przestępna zmiennoprzecinkowych funkcje matematyczne w bibliotece CRT. Wartość zwracana odzwierciedla wdrażania używany po zmianie. Jeśli Procesor nie obsługuje instrukcji FMA3, ta funkcja nie może ich włączyć w bibliotece i wartość zwracana wynosi zero. Użyj **_get_FMA3_enable** można pobrać z bieżącym stanem biblioteki. Domyślnie na X64 platform, kod uruchamiający CRT wykrywa, czy procesor CPU obsługuje instrukcje FMA3 i włącza lub wyłącza implementacje FMA3 w bibliotece.

Ponieważ implementacje FMA3 używać różnych algorytmów, niewielkie różnice w wyniku obliczenia może istnieć możliwość obserwowania podczas implementacji FMA3 są włączone lub wyłączone lub między komputerami, które nie obsługują FMA3 lub nie. Aby uzyskać więcej informacji, zobacz [problemy przy migracji zmiennoprzecinkowych](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Wymagania

**_Set_FMA3_enable** i **_get_FMA3_enable** funkcje są dostępne tylko w X64 wersje CRT.

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C: \<math.h ><br />C++: \<cmath > lub \<math.h >|

**_Set_FMA3_enable** i **_get_FMA3_enable** funkcje są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[Problemy przy migracji liczb zmiennoprzecinkowych](../../porting/floating-point-migration-issues.md)<br/>
