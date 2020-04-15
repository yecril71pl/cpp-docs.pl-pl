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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a8d018d429b2a484f88b7c1e0679f1f799983910
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355484"
---
# <a name="srand"></a>srand

Ustawia początkową wartość inicjatora dla generatora liczb pseudolosowych używanych przez funkcję **rand.**

## <a name="syntax"></a>Składnia

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parametry

*Nasion*<br/>
Materiał siewny do generowania numerów pseudolosowych

## <a name="remarks"></a>Uwagi

Funkcja **srand** ustawia punkt początkowy generowania serii pseudolosowych liczby całkowite w bieżącym wątku. Aby ponownie zainicjować generator, aby utworzyć tę samą sekwencję wyników, wywołaj funkcję **srand** i ponownie użyj tego samego argumentu *źródłowego.* Każda inna wartość dla *materiału siewnego* ustawia generator do innego punktu początkowego w sekwencji pseudorandom. **rand** pobiera numery pseudolosowe, które są generowane. Wywołanie **rand** przed każdym wywołaniem **srand** generuje taką samą sekwencję jak **wywołanie srand** z *seed* przeszedł jako 1.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**srand**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [rand](rand.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[Rand](rand.md)<br/>
