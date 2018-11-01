---
title: _set_SSE2_enable
ms.date: 04/05/2018
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
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: c340423e93b6487a4a951e4b96055cba6e474269
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539337"
---
# <a name="setsse2enable"></a>_set_SSE2_enable

Włącza lub wyłącza przyciski regulacji Streaming SIMD Extensions 2 (SSE2) instrukcjami procedury matematyczne CRT. (Ta funkcja nie jest dostępna w x64 architektury ponieważ SSE2 jest domyślnie włączona.)

## <a name="syntax"></a>Składnia

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>Parametry

*flag*<br/>
1, aby umożliwić wykonanie SSE2; 0 — wyłączenie implementacji SSE2. Domyślnie implementacja SSE2 jest włączona na procesorach, które go obsługują.

## <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli implementacja SSE2 jest włączone; zero, jeśli implementacja SSE2 jest wyłączona.

## <a name="remarks"></a>Uwagi

Następujące funkcje zostały implementacji SSE2, które można włączyć za pomocą **_set_sse2_enable —**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [Ceil —](ceil-ceilf-ceill.md)

- [EXP](exp-expf.md)

- [FLOOR](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [Pow](pow-powf-powl.md)

Implementacje SSE2 tych funkcji może udzielić odpowiedzi nieco inna niż domyślna implementacja, ponieważ SSE2 wartości pośrednie są ilości zmiennoprzecinkowych 64-bitowych, ale domyślne wartości pośrednich implementacja to 80-bitowych liczby zmiennoprzecinkowe.

> [!NOTE]
> Jeśli używasz [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md) — opcja kompilatora do skompilowania projektu, może być okaże się, że **_set_sse2_enable —** nie ma wpływu. **/Oi** — opcja kompilatora zapewnia kompilator urząd, aby użyć funkcji wewnętrznych, aby zamienić wywołania funkcji CRT; to zachowanie zastępuje efekt **_set_sse2_enable —**. Jeśli chcesz zagwarantować, że **/Oi** nie zastępuje **_set_sse2_enable —**, użyj **/Oi-** do skompilowania projektu. Przyczyną może też być dobrym rozwiązaniem korzystając z innych przełączniki kompilatora, które oznaczają **/Oi**.

Implementacja SSE2 jest używana tylko w przypadku, jeśli wszystkie wyjątki są maskowane. Użyj [_control87 —, _controlfp](control87-controlfp-control87-2.md) maski wyjątków.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
