---
title: srand
ms.date: 01/02/2018
api_name:
- srand
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
ms.openlocfilehash: 03e2b87a37d1b520b6e2b32c2f756fea625eb9a2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957994"
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

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla funkcji [Rand](rand.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
