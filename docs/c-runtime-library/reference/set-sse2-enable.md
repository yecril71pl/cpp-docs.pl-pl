---
title: _set_sse2_enable — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_SSE2_enable
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
dev_langs:
- C++
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45f4ed5333dd8ae6bab6291233391884e4efc7ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407854"
---
# <a name="setsse2enable"></a>_set_SSE2_enable

Włącza lub wyłącza korzystanie z instrukcjami procedury matematyczne CRT Streaming SIMD Extensions 2 (SSE2). (Ta funkcja nie jest dostępna w x64 architektury ponieważ SSE2 jest domyślnie włączona.)

## <a name="syntax"></a>Składnia

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>Parametry

*flag*<br/>
1 — włączenie implementacji SSE2; 0 — wyłączenie implementacji SSE2. Domyślnie implementacja SSE2 jest włączona na procesorów, które ją obsługują.

## <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli włączono implementacji SSE2; zero, jeśli implementacja SSE2 jest wyłączona.

## <a name="remarks"></a>Uwagi

Następujące funkcje mają implementacje SSE2, które można włączyć za pomocą **_set_sse2_enable —**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [EXP](exp-expf.md)

- [FLOOR](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [Pow](pow-powf-powl.md)

Implementacje SSE2 tych funkcji mogą nadać odpowiedzi nieco inne niż domyślnej implementacji, ponieważ wartości pośrednich SSE2 są 64-bitowych liczb zmiennoprzecinkowych, ale domyślne wartości pośrednich implementacji to 80-bitowa liczby zmiennoprzecinkowe.

> [!NOTE]
> Jeśli używasz [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md) opcję kompilatora, aby skompilować projekt, może okaże się, że **_set_sse2_enable —** nie ma wpływu. **/Oi** — opcja kompilatora zawierający kompilator urząd używany funkcje wewnętrzne, aby zastąpić wywołania funkcji CRT; to zachowanie zastępuje efekt **_set_sse2_enable —**. Jeśli chcesz zagwarantować, że **/Oi** nie przesłania **_set_sse2_enable —**, użyj **/Oi-** skompilować projekt. To może być również dobrym rozwiązaniem używania inne przełączniki kompilatora, sugerujących **/Oi**.

Implementacja SSE2 jest używane, jeśli wszystkie wyjątki są ukryte. Użyj [_control87 —, _controlfp —](control87-controlfp-control87-2.md) wyjątków maski.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_set_SSE2_enable.c
// processor: x86
#include <math.h>
#include <stdio.h>

int main()
{
   int i = _set_SSE2_enable(1);

   if (i)
      printf("SSE2 enabled.\n");
   else
      printf("SSE2 not enabled; processor does not support SSE2.\n");
}
```

```Output
SSE2 enabled.
```

## <a name="see-also"></a>Zobacz także

[Biblioteka CRT, funkcje](../../c-runtime-library/crt-library-features.md)<br/>
