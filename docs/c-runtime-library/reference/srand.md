---
title: srand
ms.date: 4/2/2020
api_name:
- srand
- _o_srand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- srand
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.openlocfilehash: 3f6f97ad9a3bd0d7e4e88ad1797d369f012bbe5e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913596"
---
# <a name="srand"></a>srand

Ustawia początkową wartość inicjatora dla generatora numerów pseudolosowych używanych przez funkcję **Rand** .

## <a name="syntax"></a>Składnia

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parametry

*sadzenia*<br/>
Inicjator dla generowania numerów pseudolosowych

## <a name="remarks"></a>Uwagi

Funkcja **srand** ustawia punkt początkowy do generowania serii pseudolosowych liczb całkowitych w bieżącym wątku. Aby ponownie zainicjować generator, aby utworzyć taką samą sekwencję wyników, wywołaj funkcję **srand** i Użyj tego samego argumentu *inicjatora* . Każda inna wartość *inicjatora* ustawia generator do innego punktu początkowego w sekwencji pseudolosowych. **Rand** pobiera wygenerowane numery pseudolosowych. Wywołanie funkcji **Rand** przed wywołaniem funkcji **srand** generuje taką samą sekwencję jak wywołanie **srand** z *inicjatorem* , który przeszedł jako 1.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**srand**|\<STDLIB. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla funkcji [Rand](rand.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[Rand](rand.md)<br/>
