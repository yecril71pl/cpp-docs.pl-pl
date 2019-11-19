---
title: Funkcje wewnętrzne dostępne we wszystkich architekturach
ms.date: 09/02/2019
helpviewer_keywords:
- cl.exe compiler, intrinsics
ms.assetid: 1fe3958e-d2fe-4188-8e34-5896738246eb
ms.openlocfilehash: 0293daacd717b3ae85b993729090fe363f7e0b9b
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163471"
---
# <a name="intrinsics-available-on-all-architectures"></a>Funkcje wewnętrzne dostępne we wszystkich architekturach

Kompilator Microsoft C/C++ Compiler i uniwersalna biblioteka środowiska uruchomieniowego C (UCRT) sprawiają, że niektóre funkcje wewnętrzne są dostępne we wszystkich architekturach.

## <a name="compiler-intrinsics"></a>Funkcje wewnętrzne kompilatora

Następujące elementy wewnętrzne są dostępne w architekturze x86, AMD64, ARM i ARM64:

|Wewnętrznej|nagłówek|
|---------------|------------|
|[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)|intrin. h|
|[_BitScanForward](../intrinsics/bitscanforward-bitscanforward64.md)|intrin. h|
|[_BitScanReverse](../intrinsics/bitscanreverse-bitscanreverse64.md)|intrin. h|
|[_bittest](../intrinsics/bittest-bittest64.md)|intrin. h|
|[_bittestandcomplement](../intrinsics/bittestandcomplement-bittestandcomplement64.md)|intrin. h|
|[_bittestandreset](../intrinsics/bittestandreset-bittestandreset64.md)|intrin. h|
|[_bittestandset](../intrinsics/bittestandset-bittestandset64.md)|intrin. h|
|__code_seg|intrin. h|
|[__debugbreak](../intrinsics/debugbreak.md)|intrin. h|
|[_disable](../intrinsics/disable.md)|intrin. h|
|[_enable](../intrinsics/enable.md)|intrin. h|
|[__fastfail](../intrinsics/fastfail.md)|intrin. h|
|[_InterlockedAnd](../intrinsics/interlockedand-intrinsic-functions.md)|intrin. h|
|[_InterlockedAnd16](../intrinsics/interlockedand-intrinsic-functions.md)|intrin. h|
|[_InterlockedAnd8](../intrinsics/interlockedand-intrinsic-functions.md)|intrin. h|
|[_interlockedbittestandreset](../intrinsics/interlockedbittestandreset-intrinsic-functions.md)|intrin. h|
|[_interlockedbittestandset](../intrinsics/interlockedbittestandset-intrinsic-functions.md)|intrin. h|
|[_InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)|intrin. h|
|[_InterlockedCompareExchange16](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)|intrin. h|
|[_InterlockedCompareExchange8](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)|intrin. h|
|[_InterlockedCompareExchangePointer](../intrinsics/interlockedcompareexchangepointer-intrinsic-functions.md)|intrin. h|
|[_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)|intrin. h|
|[_InterlockedDecrement16](../intrinsics/interlockeddecrement-intrinsic-functions.md)|intrin. h|
|[_InterlockedExchange](../intrinsics/interlockedexchange-intrinsic-functions.md)|intrin. h|
|[_InterlockedExchange16](../intrinsics/interlockedexchange-intrinsic-functions.md)|intrin. h|
|[_InterlockedExchange8](../intrinsics/interlockedexchange-intrinsic-functions.md)|intrin. h|
|[_InterlockedExchangeAdd](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)|intrin. h|
|[_InterlockedExchangeAdd16](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)|intrin. h|
|[_InterlockedExchangeAdd8](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)|intrin. h|
|[_InterlockedExchangePointer](../intrinsics/interlockedexchangepointer-intrinsic-functions.md)|intrin. h|
|[_InterlockedIncrement](../intrinsics/interlockedincrement-intrinsic-functions.md)|intrin. h|
|[_InterlockedIncrement16](../intrinsics/interlockedincrement-intrinsic-functions.md)|intrin. h|
|[_InterlockedOr](../intrinsics/interlockedor-intrinsic-functions.md)|intrin. h|
|[_InterlockedOr16](../intrinsics/interlockedor-intrinsic-functions.md)|intrin. h|
|[_InterlockedOr8](../intrinsics/interlockedor-intrinsic-functions.md)|intrin. h|
|[_InterlockedXor](../intrinsics/interlockedxor-intrinsic-functions.md)|intrin. h|
|[_InterlockedXor16](../intrinsics/interlockedxor-intrinsic-functions.md)|intrin. h|
|[_InterlockedXor8](../intrinsics/interlockedxor-intrinsic-functions.md)|intrin. h|
|[__nop](../intrinsics/nop.md)|intrin. h|
|[_ReadBarrier](../intrinsics/readbarrier.md)|intrin. h|
|[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)|intrin. h|
|[_ReturnAddress](../intrinsics/returnaddress.md)|intrin. h|
|[_rotl16](../intrinsics/rotl8-rotl16.md)|intrin. h|
|[_rotl8](../intrinsics/rotl8-rotl16.md)|intrin. h|
|[_rotr16](../intrinsics/rotr8-rotr16.md)|intrin. h|
|[_rotr8](../intrinsics/rotr8-rotr16.md)|intrin. h|
|[_WriteBarrier](../intrinsics/writebarrier.md)|intrin. h|

## <a name="ucrt-intrinsics"></a>UCRT wewnętrzne

Następujące funkcje UCRT mają wewnętrzne formularze dla wszystkich architektur:

|Wewnętrznej|nagłówek|
|---------------|------------|
|[ABS](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|STDLIB. h|
|[_abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|STDLIB. h|
|[Acos](../c-runtime-library/reference/acos-acosf-acosl.md)|Math. h|
|[acosf —](../c-runtime-library/reference/acos-acosf-acosl.md)|Math. h|
|[acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Math. h|
|[_alloca](../c-runtime-library/reference/alloca.md)|malloc. h|
|[Asin](../c-runtime-library/reference/asin-asinf-asinl.md)|Math. h|
|[asinf —](../c-runtime-library/reference/asin-asinf-asinl.md)|Math. h|
|[asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Math. h|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Math. h|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Math. h|
|[atan2f —](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Math. h|
|[atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Math. h|
|[atanf —](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Math. h|
|[atanl](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Math. h|
|[_byteswap_uint64](../c-runtime-library/reference/byteswap-uint64-byteswap-ulong-byteswap-ushort.md)|STDLIB. h|
|[_byteswap_ulong](../c-runtime-library/reference/byteswap-uint64-byteswap-ulong-byteswap-ushort.md)|STDLIB. h|
|[_byteswap_ushort](../c-runtime-library/reference/byteswap-uint64-byteswap-ulong-byteswap-ushort.md)|STDLIB. h|
|[CEIL —](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Math. h|
|[ceilf —](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Math. h|
|[ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Math. h|
|[cosinus](../c-runtime-library/reference/cos-cosf-cosl.md)|Math. h|
|[cosf —](../c-runtime-library/reference/cos-cosf-cosl.md)|Math. h|
|[cosh —](../c-runtime-library/reference/cosh-coshf-coshl.md)|Math. h|
|[coshf —](../c-runtime-library/reference/cosh-coshf-coshl.md)|Math. h|
|[coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Math. h|
|[cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|Math. h|
|[EXP](../c-runtime-library/reference/exp-expf.md)|Math. h|
|[expf —](../c-runtime-library/reference/exp-expf.md)|Math. h|
|[expl](../c-runtime-library/reference/exp-expf.md)|Math. h|
|[fabs —](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Math. h|
|[fabsf —](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Math. h|
|[wykładzin](../c-runtime-library/reference/floor-floorf-floorl.md)|Math. h|
|[floorf —](../c-runtime-library/reference/floor-floorf-floorl.md)|Math. h|
|[piętro](../c-runtime-library/reference/floor-floorf-floorl.md)|Math. h|
|[FMOD —](../c-runtime-library/reference/fmod-fmodf.md)|Math. h|
|[fmodf —](../c-runtime-library/reference/fmod-fmodf.md)|Math. h|
|[fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Math. h|
|[Labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|STDLIB. h|
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|STDLIB. h|
|[rejestrowane](../c-runtime-library/reference/log-logf-log10-log10f.md)|Math. h|
|[log10 —](../c-runtime-library/reference/log-logf-log10-log10f.md)|Math. h|
|[log10f —](../c-runtime-library/reference/log-logf-log10-log10f.md)|Math. h|
|[log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Math. h|
|[logf —](../c-runtime-library/reference/log-logf-log10-log10f.md)|Math. h|
|[logl](../c-runtime-library/reference/log-logf-log10-log10f.md)|Math. h|
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|STDLIB. h|
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|STDLIB. h|
|[funkcji memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|ciąg. h|
|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)|ciąg. h|
|[funkcji memset](../c-runtime-library/reference/memset-wmemset.md)|ciąg. h|
|[pow](../c-runtime-library/reference/pow-powf-powl.md)|Math. h|
|[powf —](../c-runtime-library/reference/pow-powf-powl.md)|Math. h|
|[powl](../c-runtime-library/reference/pow-powf-powl.md)|Math. h|
|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|STDLIB. h|
|[_rotl64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|STDLIB. h|
|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|STDLIB. h|
|[_rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|STDLIB. h|
|[sinus](../c-runtime-library/reference/sin-sinf-sinl.md)|Math. h|
|[SINF —](../c-runtime-library/reference/sin-sinf-sinl.md)|Math. h|
|[SINH](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Math. h|
|[sinhf —](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Math. h|
|[SINH](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Math. h|
|[sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Math. h|
|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Math. h|
|[sqrtf —](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Math. h|
|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Math. h|
|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)|ciąg. h|
|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|ciąg. h|
|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|ciąg. h|
|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|ciąg. h|
|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|ciąg. h|
|[strset](../c-runtime-library/reference/strset-wcsset.md)|ciąg. h|
|[Tan](../c-runtime-library/reference/tan-tanf-tanl.md)|Math. h|
|[TANF —](../c-runtime-library/reference/tan-tanf-tanl.md)|Math. h|
|[TANH —](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Math. h|
|[tanhf —](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Math. h|
|[tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Math. h|
|[tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Math. h|
|[wcscat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)|ciąg. h|
|[wcscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|ciąg. h|
|[wcscpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|ciąg. h|
|[wcslen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|ciąg. h|
|[_wcsset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|ciąg. h|

## <a name="see-also"></a>Zobacz także

\ [wewnętrzne ARM](../intrinsics/arm-intrinsics.md)
[Arm64 wewnętrzne](../intrinsics/arm64-intrinsics.md)\
[Lista elementów wewnętrznych x86](../intrinsics/x86-intrinsics-list.md)\
[Lista funkcji wewnętrznych x64 (amd64)](../intrinsics/x64-amd64-intrinsics-list.md)
