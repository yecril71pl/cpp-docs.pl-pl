---
title: _set_SSE2_enable
ms.date: 04/05/2018
api_name:
- _set_SSE2_enable
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: 8838282db851c6811a3f24c75a03b31c5870e6d3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948349"
---
# <a name="_set_sse2_enable"></a>_set_SSE2_enable

Włącza lub wyłącza użycie instrukcji Streaming SIMD Extensions 2 (SSE2) w procedurach matematycznych w CRT. (Ta funkcja jest niedostępna w architekturze x64, ponieważ SSE2 jest domyślnie włączona).

## <a name="syntax"></a>Składnia

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>Parametry

*flag*<br/>
1, aby włączyć implementację SSE2; 0, aby wyłączyć implementację SSE2. Domyślnie implementacja SSE2 jest włączona na procesorach, które je obsługują.

## <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli jest włączona implementacja SSE2; zero, jeśli implementacja SSE2 jest wyłączona.

## <a name="remarks"></a>Uwagi

Następujące funkcje mają implementacje SSE2, które można włączyć za pomocą **_set_SSE2_enable**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [CEIL —](ceil-ceilf-ceill.md)

- [EXP](exp-expf.md)

- [wykładzin](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [pow](pow-powf-powl.md)

Implementacje SSE2 tych funkcji mogą dać nieco różne odpowiedzi niż implementacje domyślne, ponieważ wartości pośrednie SSE2 są 64-bitowe ilości zmiennoprzecinkowe, ale domyślne wartości pośrednie implementacji to 80-bit liczby zmiennoprzecinkowe.

> [!NOTE]
> Jeśli używasz opcji kompilatora [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md) do kompilowania projektu, może się wydawać, że **_set_SSE2_enable** nie ma żadnego efektu. Opcja kompilatora **/Oi** daje kompilatorowi uprawnienia do używania elementów wewnętrznych do zastępowania wywołań CRT; to zachowanie zastępuje efekt **_set_SSE2_enable**. Jeśli chcesz zagwarantować, że **/Oi** nie przesłania **_set_SSE2_enable**, użyj **/Oi-** do skompilowania projektu. Może to być również dobre rozwiązanie w przypadku używania innych przełączników kompilatora, które wymagają **/Oi**.

Implementacja SSE2 jest używana tylko wtedy, gdy wszystkie wyjątki są maskowane. Użyj [_control87, _controlfp](control87-controlfp-control87-2.md) do maskowania wyjątków.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
