---
title: srand
ms.date: 01/02/2018
apiname:
- srand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: d74ae4cbec5a76df48bb2b56acab7329e6cf8aa5
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927404"
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
