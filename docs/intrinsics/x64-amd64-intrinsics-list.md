---
title: Lista funkcji wewnętrznych x64 (amd64)
ms.date: 04/18/2019
helpviewer_keywords:
- cl-exe compiler, intrinsics
- intrinsics, x64
- intrinsics, amd64
ms.openlocfilehash: 532ce6fd262c568198d8cc8aaeccc77201b805e9
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163529"
---
# <a name="x64-amd64-intrinsics-list"></a>Lista funkcji wewnętrznych x64 (amd64)

Ten dokument zawiera listę funkcji wewnętrznych obsługiwanych przez C++ kompilator firmy Microsoft, gdy jest przeznaczony dla architektury x64 (nazywanej również amd64).

Aby uzyskać informacje o poszczególnych funkcjach wewnętrznych, zapoznaj się z tymi zasobami, odpowiednio dla docelowej architektury procesora:

- Plik nagłówkowy. Wiele elementów wewnętrznych jest udokumentowanych w komentarzach w pliku nagłówkowym.

- [Przewodnik po architekturze Intel](https://software.intel.com/sites/landingpage/IntrinsicsGuide). Użyj pola wyszukiwania, aby znaleźć określone elementy wewnętrzne.

- [Architektury Intel 64 i IA-32 — instrukcje dla deweloperów oprogramowania](https://software.intel.com/articles/intel-sdm)

- [Dokumentacja dotycząca programowania rozszerzeń zestawu instrukcji Intel Architecture](https://software.intel.com/isa-extensions)

- [Wprowadzenie do zaawansowanych rozszerzeń wektorów firmy Intel](https://software.intel.com/articles/introduction-to-intel-advanced-vector-extensions)

- [Przewodniki programistyczne AMD, instrukcje & dokumenty ISA](https://developer.amd.com/resources/developer-guides-manuals/)

## <a name="x64-intrinsics"></a>wersje wewnętrzne x64

Poniższa tabela zawiera listę elementów wewnętrznych dostępnych w procesorach x64. W kolumnie technologii są wyświetlane wymagane instrukcje obsługi zestawu. Użyj wewnętrznego [__cpuid](cpuid-cpuidex.md) , aby określić obsługę zestawu instrukcji w czasie wykonywania. Jeśli dwa wpisy znajdują się w jednym wierszu, reprezentują różne punkty wejścia dla tego samego elementu wewnętrznego. [1] wskazuje, że element wewnętrzny jest dostępny tylko w przypadku procesorów AMD. [2] wskazuje, że element wewnętrzny jest dostępny tylko na procesorach firmy Intel. [3] wskazuje, że prototyp jest makrem. Nagłówek wymagany dla prototypu funkcji jest wymieniony w kolumnie nagłówek. Nagłówek intrin. h zawiera zarówno immintrin. h, jak i ammintrin. h dla uproszczenia.

|Nazwa funkcji wewnętrznej|Technologia|nagłówek|Prototyp funkcji|
|--------------------|----------------|------------|------------------------|
|_addcarry_u16||intrin. h|niepodpisany znak _addcarry_u16 (znak bez znaku, niepodpisane, krótkie, niepodpisane, krótkie \*)|
|[_addcarry_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_addcarry_u32)||intrin. h|niepodpisany znak _addcarry_u32 (znak niepodpisany, int, unsigned int, niepodpisane \*int)|
|[_addcarry_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_addcarry_u64)||intrin. h|niepodpisany znak _addcarry_u64 (znak bez znaku, niepodpisane \__int64, bez znaku \__int64, bez znaku \__int64)|
|_addcarry_u8||intrin. h|niepodpisany znak _addcarry_u8 (znak bez znaku, znak bez znaku, znak bez znaku, znak \*znaków)|
|[_addcarryx_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_addcarryx_u32)|ADX [2]|immintrin. h|niepodpisany znak _addcarryx_u32 (znak niepodpisany, int, unsigned int, niepodpisane \*int)|
|[_addcarryx_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_addcarryx_u64)|ADX [2]|immintrin. h|niepodpisany znak _addcarryx_u64 (znak bez znaku, niepodpisane \__int64, bez znaku \__int64, bez znaku \__int64)|
|[__addgsbyte](addgsbyte-addgsword-addgsdword-addgsqword.md)||intrin. h|void __addgsbyte (unsigned long, znak bez znaku)|
|[__addgsdword](addgsbyte-addgsword-addgsdword-addgsqword.md)||intrin. h|void __addgsdword (unsigned long, int unsigned)|
|[__addgsqword](addgsbyte-addgsword-addgsdword-addgsqword.md)||intrin. h|void __addgsqword (Long unsigned unsigned \__int64)|
|[__addgsword](addgsbyte-addgsword-addgsdword-addgsqword.md)||intrin. h|void __addgsword (Long unsigned unsigned Short)|
|[_AddressOfReturnAddress](addressofreturnaddress.md)||intrin. h|void \* _AddressOfReturnAddress (void)|
|_andn_u32|BMI [1]|ammintrin. h|niepodpisane _andn_u32 int (niepodpisane int, int bez znaku)|
|_andn_u64|BMI [1]|ammintrin. h|niepodpisane _andn_u64 __int64 (niepodpisane \__int64, bez znaku \_)|
|[_bextr_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_bextr_u32)|BMI|ammintrin. h, immintrin. h|niepodpisane _bextr_u32 int (niepodpisane int, int unsigned int)|
|[_bextr_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_bextr_u64)|BMI|ammintrin. h, immintrin. h|niepodpisane _bextr_u64 __int64 (niepodpisane \__int64, int bez znaku int)|
|_bextri_u32|ABM [1]|ammintrin. h|niepodpisane _bextri_u32 int (niepodpisane int, int bez znaku)|
|_bextri_u64|ABM [1]|ammintrin. h|niepodpisane _bextri_u64 __int64 (niepodpisane \__int64, bez znaku int)|
|[_BitScanForward](bitscanforward-bitscanforward64.md)||intrin. h|niepodpisany znak _BitScanForward (Long długi\*, bez znaku)|
|[_BitScanForward64](bitscanforward-bitscanforward64.md)||intrin. h|niepodpisany znak _BitScanForward64 (Long długi\*, bez znaku \__int64)|
|[_BitScanReverse](bitscanreverse-bitscanreverse64.md)||intrin. h|niepodpisany znak _BitScanReverse (Long długi\*, bez znaku)|
|[_BitScanReverse64](bitscanreverse-bitscanreverse64.md)||intrin. h|niepodpisany znak _BitScanReverse64 (Long długi\*, bez znaku \__int64)|
|[_bittest](bittest-bittest64.md)||intrin. h|niepodpisany znak _bittest (Long const \*, Long)|
|[_bittest64](bittest-bittest64.md)||intrin. h|niepodpisany znak _bittest64 (\__int64 const \*, \__int64)|
|[_bittestandcomplement](bittestandcomplement-bittestandcomplement64.md)||intrin. h|niepodpisany znak _bittestandcomplement (Long \*, Long)|
|[_bittestandcomplement64](bittestandcomplement-bittestandcomplement64.md)||intrin. h|niepodpisany znak _bittestandcomplement64 (\__int64 \*, \__int64)|
|[_bittestandreset](bittestandreset-bittestandreset64.md)||intrin. h|niepodpisany znak _bittestandreset (Long \*, Long)|
|[_bittestandreset64](bittestandreset-bittestandreset64.md)||intrin. h|niepodpisany znak _bittestandreset64 (\__int64 \*, \__int64)|
|[_bittestandset](bittestandset-bittestandset64.md)||intrin. h|niepodpisany znak _bittestandset (Long \*, Long)|
|[_bittestandset64](bittestandset-bittestandset64.md)||intrin. h|niepodpisany znak _bittestandset64 (\__int64 \*, \__int64)|
|_blcfill_u32|ABM [1]|ammintrin. h|niepodpisane _blcfill_u32 int (int bez znaku)|
|_blcfill_u64|ABM [1]|ammintrin. h|niepodpisane _blcfill_u64 __int64 (niepodpisane \__int64)|
|_blci_u32|ABM [1]|ammintrin. h|niepodpisane _blci_u32 int (int bez znaku)|
|_blci_u64|ABM [1]|ammintrin. h|niepodpisane _blci_u64 __int64 (niepodpisane \__int64)|
|_blcic_u32|ABM [1]|ammintrin. h|niepodpisane _blcic_u32 int (int bez znaku)|
|_blcic_u64|ABM [1]|ammintrin. h|niepodpisane _blcic_u64 __int64 (niepodpisane \__int64)|
|_blcmsk_u32|ABM [1]|ammintrin. h|niepodpisane _blcmsk_u32 int (int bez znaku)|
|_blcmsk_u64|ABM [1]|ammintrin. h|niepodpisane _blcmsk_u64 __int64 (niepodpisane \__int64)|
|_blcs_u32|ABM [1]|ammintrin. h|niepodpisane _blcs_u32 int (int bez znaku)|
|_blcs_u64|ABM [1]|ammintrin. h|niepodpisane _blcs_u64 __int64 (niepodpisane \__int64)|
|_blsfill_u32|ABM [1]|ammintrin. h|niepodpisane _blsfill_u32 int (int bez znaku)|
|_blsfill_u64|ABM [1]|ammintrin. h|niepodpisane _blsfill_u64 __int64 (niepodpisane \__int64)|
|[_blsi_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsi_u32)|BMI|ammintrin. h, immintrin. h|niepodpisane _blsi_u32 int (int bez znaku)|
|[_blsi_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsi_u64)|BMI|ammintrin. h, immintrin. h|niepodpisane _blsi_u64 __int64 (niepodpisane \__int64)|
|_blsic_u32|ABM [1]|ammintrin. h|niepodpisane _blsic_u32 int (int bez znaku)|
|_blsic_u64|ABM [1]|ammintrin. h|niepodpisane _blsic_u64 __int64 (niepodpisane \__int64)|
|[_blsmsk_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsmsk_u32)|BMI|ammintrin. h, immintrin. h|niepodpisane _blsmsk_u32 int (int bez znaku)|
|[_blsmsk_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsmsk_u64)|BMI|ammintrin. h, immintrin. h|niepodpisane _blsmsk_u64 __int64 (niepodpisane \__int64)|
|[_blsr_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsr_u32)|BMI|ammintrin. h, immintrin. h|niepodpisane _blsr_u32 int (int bez znaku)|
|[_blsr_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsr_u64)|BMI|ammintrin. h, immintrin. h|niepodpisane _blsr_u64 __int64 (niepodpisane \__int64)|
|[_bzhi_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_bzhi_u32)|BMI [2]|immintrin. h|niepodpisane _bzhi_u32 int (niepodpisane int, int bez znaku)|
|[_bzhi_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_bzhi_u64)|BMI [2]|immintrin. h|niepodpisane _bzhi_u64 __int64 (niepodpisane \__int64, bez znaku int)|
|_clac|SMAP|intrin. h|void _clac (void)|
|[__cpuid](cpuid-cpuidex.md)||intrin. h|void __cpuid (int \*, int)|
|[__cpuidex](cpuid-cpuidex.md)||intrin. h|void __cpuidex (int \*, int, int)|
|[__debugbreak](debugbreak.md)||intrin. h|void __debugbreak (void)|
|[_disable](disable.md)||intrin. h|void _disable (void)|
|[_div128](div128.md)||intrin. h| __int64 _div128 (\__int64, \__int64, \__int64, \__int64 \*)|
|[_div64](div64.md)||intrin. h| int \_div64 (\__int64, int, int *)|
|[__emul](emul-emulu.md)||intrin. h|__int64 [Pascal/CDECL] \__emul (int, int)|
|[__emulu](emul-emulu.md)||intrin. h|niepodpisane __int64 [Pascal/CDECL]\__emulu (int bez znaku int)|
|[_enable](enable.md)||intrin. h|void _enable (void)|
|[__fastfail](fastfail.md)||intrin. h|void __fastfail (bez znaku int)|
|[__faststorefence](faststorefence.md)||intrin. h|void __faststorefence (void)|
|[_fxrstor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_fxrstor)|FXSR [2]|immintrin. h|void _fxrstor (void const\*)|
|[_fxrstor64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_fxrstor64)|FXSR [2]|immintrin. h|void _fxrstor64 (void const\*)|
|[_fxsave](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_fxsave)|FXSR [2]|immintrin. h|void _fxsave (void\*)|
|[_fxsave64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_fxsave64)|FXSR [2]|immintrin. h|void _fxsave64 (void\*)|
|[__getcallerseflags](getcallerseflags.md)||intrin. h|(niepodpisany int __getcallerseflags ())|
|[__halt](halt.md)||intrin. h|void __halt (void)|
|[__inbyte](inbyte.md)||intrin. h|niepodpisany znak __inbyte (krótki niepodpisany)|
|[__inbytestring](inbytestring.md)||intrin. h|void __inbytestring (unsigned Short, unsigned char \*, unsigned long)|
|[__incgsbyte](incgsbyte-incgsword-incgsdword-incgsqword.md)||intrin. h|void __incgsbyte (liczba bez znaku)|
|[__incgsdword](incgsbyte-incgsword-incgsdword-incgsqword.md)||intrin. h|void __incgsdword (liczba bez znaku)|
|[__incgsqword](incgsbyte-incgsword-incgsdword-incgsqword.md)||intrin. h|void __incgsqword (liczba bez znaku)|
|[__incgsword](incgsbyte-incgsword-incgsdword-incgsqword.md)||intrin. h|void __incgsword (liczba bez znaku)|
|[__indword](indword.md)||intrin. h|niepodpisane długie __indword (krótkie bez znaku)|
|[__indwordstring](indwordstring.md)||intrin. h|void __indwordstring (niepodpisane, długie \*bez znaku)|
|[__int2c](int2c.md)||intrin. h|void __int2c (void)|
|[_InterlockedAnd](interlockedand-intrinsic-functions.md)||intrin. h|długi _InterlockedAnd (długa nietrwała \*, Long)|
|[_InterlockedAnd_HLEAcquire](interlockedand-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedAnd_HLEAcquire (długa nietrwała \*, Long)|
|[_InterlockedAnd_HLERelease](interlockedand-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedAnd_HLERelease (długa nietrwała \*, Long)|
|[_InterlockedAnd_np](interlockedand-intrinsic-functions.md)||intrin. h|długi _InterlockedAnd_np (Long \*, Long)|
|[_InterlockedAnd16](interlockedand-intrinsic-functions.md)||intrin. h|krótkie _InterlockedAnd16 (krótkie \*nietrwałe, krótkie)|
|[_InterlockedAnd16_np](interlockedand-intrinsic-functions.md)||intrin. h|krótkie _InterlockedAnd16_np (krótkie \*, krótkie)|
|[_InterlockedAnd64](interlockedand-intrinsic-functions.md)||intrin. h|_InterlockedAnd64 __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedAnd64_HLEAcquire](interlockedand-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedAnd64_HLEAcquire __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedAnd64_HLERelease](interlockedand-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedAnd64_HLERelease __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedAnd64_np](interlockedand-intrinsic-functions.md)||intrin. h|_InterlockedAnd64_np __int64 (\__int64 \*, \__int64)|
|[_InterlockedAnd8](interlockedand-intrinsic-functions.md)||intrin. h|znak _InterlockedAnd8 (znak nietrwały \*, Char)|
|[_InterlockedAnd8_np](interlockedand-intrinsic-functions.md)||intrin. h|znak _InterlockedAnd8_np (Char \*, Char)|
|[_interlockedbittestandreset](interlockedbittestandreset-intrinsic-functions.md)||intrin. h|niepodpisany znak _interlockedbittestandreset (Long \*, Long)|
|[_interlockedbittestandreset_HLEAcquire](interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin. h|niepodpisany znak _interlockedbittestandreset_HLEAcquire (Long \*, Long)|
|[_interlockedbittestandreset_HLERelease](interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin. h|niepodpisany znak _interlockedbittestandreset_HLERelease (Long \*, Long)|
|[_interlockedbittestandreset64](interlockedbittestandreset-intrinsic-functions.md)||intrin. h|niepodpisany znak _interlockedbittestandreset64 (\__int64 \*, \__int64)|
|[_interlockedbittestandreset64_HLEAcquire](interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin. h|niepodpisany znak _interlockedbittestandreset64_HLEAcquire (\__int64 \*, \__int64)|
|[_interlockedbittestandreset64_HLERelease](interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin. h|niepodpisany znak _interlockedbittestandreset64_HLERelease (\__int64 \*, \__int64)|
|[_interlockedbittestandset](interlockedbittestandset-intrinsic-functions.md)||intrin. h|niepodpisany znak _interlockedbittestandset (Long \*, Long)|
|[_interlockedbittestandset_HLEAcquire](interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin. h|niepodpisany znak _interlockedbittestandset_HLEAcquire (Long \*, Long)|
|[_interlockedbittestandset_HLERelease](interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin. h|niepodpisany znak _interlockedbittestandset_HLERelease (Long \*, Long)|
|[_interlockedbittestandset64](interlockedbittestandset-intrinsic-functions.md)||intrin. h|niepodpisany znak _interlockedbittestandset64 (\__int64 \*, \__int64)|
|[_interlockedbittestandset64_HLEAcquire](interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin. h|niepodpisany znak _interlockedbittestandset64_HLEAcquire (\__int64 \*, \__int64)|
|[_interlockedbittestandset64_HLERelease](interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin. h|niepodpisany znak _interlockedbittestandset64_HLERelease (\__int64 \*, \__int64)|
|[_InterlockedCompareExchange](interlockedcompareexchange-intrinsic-functions.md)||intrin. h|długi _InterlockedCompareExchange (długa nietrwała \*, Long, Long)|
|[_InterlockedCompareExchange_HLEAcquire](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedCompareExchange_HLEAcquire (długa nietrwała \*, Long, Long)|
|[_InterlockedCompareExchange_HLERelease](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedCompareExchange_HLERelease (długa nietrwała \*, Long, Long)|
|[_InterlockedCompareExchange_np](interlockedcompareexchange-intrinsic-functions.md)||intrin. h|długi _InterlockedCompareExchange_np (Long \*, Long, Long)|
|[_InterlockedCompareExchange128](interlockedcompareexchange128.md)||intrin. h|niepodpisany znak _InterlockedCompareExchange128 (\__int64 volatile \*, \__int64, \__int64, \__int64:\*)|
|[_InterlockedCompareExchange128_np](interlockedcompareexchange128.md)||intrin. h|niepodpisany znak _InterlockedCompareExchange128 (\__int64 volatile \*, \__int64, \__int64, \__int64:\*)|
|[_InterlockedCompareExchange16](interlockedcompareexchange-intrinsic-functions.md)||intrin. h|krótkie _InterlockedCompareExchange16 (krótkie nietrwałe \*, krótkie, krótkie)|
|[_InterlockedCompareExchange16_np](interlockedcompareexchange-intrinsic-functions.md)||intrin. h|krótkie _InterlockedCompareExchange16_np (krótkie nietrwałe \*, krótkie, krótkie)|
|[_InterlockedCompareExchange64](interlockedcompareexchange-intrinsic-functions.md)||intrin. h|__int64 _InterlockedCompareExchange64 (\__int64 volatile \*, \__int64, \__int64)|
|[_InterlockedCompareExchange64_HLEAcquire](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin. h|__int64 _InterlockedCompareExchange64_HLEAcquire (\__int64 volatile \*, \__int64, \__int64)|
|[_InterlockedCompareExchange64_HLERelease](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin. h|__int64 _InterlockedCompareExchange64_HLERelease (\__int64 volatile \*, \__int64, \__int64)|
|[_InterlockedCompareExchange64_np](interlockedcompareexchange-intrinsic-functions.md)||intrin. h|__int64 _InterlockedCompareExchange64_np (\__int64 \*, \__int64, \__int64)|
|[_InterlockedCompareExchange8](interlockedcompareexchange-intrinsic-functions.md)||intrin. h|znak _InterlockedCompareExchange8 (znak nietrwały \*, char, Char)|
|[_InterlockedCompareExchangePointer](interlockedcompareexchangepointer-intrinsic-functions.md)||intrin. h|_InterlockedCompareExchangePointer \*void (void \*volatile \*, void \*, void \*)|
|[_InterlockedCompareExchangePointer_HLEAcquire](interlockedcompareexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin. h|void * _InterlockedCompareExchangePointer_HLEAcquire (void \*volatile \*, void \*, void \*)|
|[_InterlockedCompareExchangePointer_HLERelease](interlockedcompareexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin. h|void * _InterlockedCompareExchangePointer_HLERelease (void \*volatile \*, void \*, void \*)|
|[_InterlockedCompareExchangePointer_np](interlockedcompareexchangepointer-intrinsic-functions.md)||intrin. h|void \*_InterlockedCompareExchangePointer_np (void \*\*, void \*, void \*)|
|[_InterlockedDecrement](interlockeddecrement-intrinsic-functions.md)||intrin. h|długi _InterlockedDecrement (Long volatile \*)|
|[_InterlockedDecrement16](interlockeddecrement-intrinsic-functions.md)||intrin. h|krótkie _InterlockedDecrement16 (krótkie \*nietrwałe)|
|[_InterlockedDecrement64](interlockeddecrement-intrinsic-functions.md)||intrin. h|_InterlockedDecrement64 __int64 (\__int64 volatile \*)|
|[_InterlockedExchange](interlockedexchange-intrinsic-functions.md)||intrin. h|długi _InterlockedExchange (długa nietrwała \*, Long)|
|[_InterlockedExchange_HLEAcquire](interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedExchange_HLEAcquire (długa nietrwała \*, Long)|
|[_InterlockedExchange_HLERelease](interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedExchange_HLERelease (długa nietrwała \*, Long)|
|[_InterlockedExchange16](interlockedexchange-intrinsic-functions.md)||intrin. h|krótkie _InterlockedExchange16 (krótkie \*nietrwałe, krótkie)|
|[_InterlockedExchange64](interlockedexchange-intrinsic-functions.md)||intrin. h|_InterlockedExchange64 __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedExchange64_HLEAcquire](interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedExchange64_HLEAcquire __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedExchange64_HLERelease](interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedExchange64_HLERelease __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedExchange8](interlockedexchange-intrinsic-functions.md)||intrin. h|znak _InterlockedExchange8 (znak nietrwały \*, Char)|
|[_InterlockedExchangeAdd](interlockedexchangeadd-intrinsic-functions.md)||intrin. h|długi _InterlockedExchangeAdd (długa nietrwała \*, Long)|
|[_InterlockedExchangeAdd_HLEAcquire](interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedExchangeAdd_HLEAcquire (długa nietrwała \*, Long)|
|[_InterlockedExchangeAdd_HLERelease](interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedExchangeAdd_HLERelease (długa nietrwała \*, Long)|
|[_InterlockedExchangeAdd16](interlockedexchangeadd-intrinsic-functions.md)||intrin. h|krótkie _InterlockedExchangeAdd16 (krótkie \*nietrwałe, krótkie)|
|[_InterlockedExchangeAdd64](interlockedexchangeadd-intrinsic-functions.md)||intrin. h|_InterlockedExchangeAdd64 __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedExchangeAdd64_HLEAcquire](interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedExchangeAdd64_HLEAcquire __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedExchangeAdd64_HLERelease](interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedExchangeAdd64_HLERelease __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedExchangeAdd8](interlockedexchangeadd-intrinsic-functions.md)||intrin. h|znak _InterlockedExchangeAdd8 (znak nietrwały \*, Char)|
|[_InterlockedExchangePointer](interlockedexchangepointer-intrinsic-functions.md)||intrin. h|_InterlockedExchangePointer \* void (void \*volatile \*, void \*)|
|[_InterlockedExchangePointer_HLEAcquire](interlockedexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedExchangePointer_HLEAcquire \* void (void \*volatile \*, void \*)|
|[_InterlockedExchangePointer_HLERelease](interlockedexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin. h|void * _InterlockedExchangePointer_HLERelease (void \*volatile \*, void \*)|
|[_InterlockedIncrement](interlockedincrement-intrinsic-functions.md)||intrin. h|długi _InterlockedIncrement (Long volatile \*)|
|[_InterlockedIncrement16](interlockedincrement-intrinsic-functions.md)||intrin. h|krótkie _InterlockedIncrement16 (krótkie \*nietrwałe)|
|[_InterlockedIncrement64](interlockedincrement-intrinsic-functions.md)||intrin. h|_InterlockedIncrement64 __int64 (\__int64 volatile \*)|
|[_InterlockedOr](interlockedor-intrinsic-functions.md)||intrin. h|długi _InterlockedOr (długa nietrwała \*, Long)|
|[_InterlockedOr_HLEAcquire](interlockedor-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedOr_HLEAcquire (długa nietrwała \*, Long)|
|[_InterlockedOr_HLERelease](interlockedor-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedOr_HLERelease (długa nietrwała \*, Long)|
|[_InterlockedOr_np](interlockedor-intrinsic-functions.md)||intrin. h|długi _InterlockedOr_np (Long \*, Long)|
|[_InterlockedOr16](interlockedor-intrinsic-functions.md)||intrin. h|krótkie _InterlockedOr16 (krótkie \*nietrwałe, krótkie)|
|[_InterlockedOr16_np](interlockedor-intrinsic-functions.md)||intrin. h|krótkie _InterlockedOr16_np (krótkie \*, krótkie)|
|[_InterlockedOr64](interlockedor-intrinsic-functions.md)||intrin. h|_InterlockedOr64 __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedOr64_HLEAcquire](interlockedor-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedOr64_HLEAcquire __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedOr64_HLERelease](interlockedor-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedOr64_HLERelease __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedOr64_np](interlockedor-intrinsic-functions.md)||intrin. h|_InterlockedOr64_np __int64 (\__int64 \*, \__int64)|
|[_InterlockedOr8](interlockedor-intrinsic-functions.md)||intrin. h|znak _InterlockedOr8 (znak nietrwały \*, Char)|
|[_InterlockedOr8_np](interlockedor-intrinsic-functions.md)||intrin. h|znak _InterlockedOr8_np (Char \*, Char)|
|[_InterlockedXor](interlockedxor-intrinsic-functions.md)||intrin. h|długi _InterlockedXor (długa nietrwała \*, Long)|
|[_InterlockedXor_HLEAcquire](interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedXor_HLEAcquire (długa nietrwała \*, Long)|
|[_InterlockedXor_HLERelease](interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin. h|długi _InterlockedXor_HLERelease (długa nietrwała \*, Long)|
|[_InterlockedXor_np](interlockedxor-intrinsic-functions.md)||intrin. h|długi _InterlockedXor_np (Long \*, Long)|
|[_InterlockedXor16](interlockedxor-intrinsic-functions.md)||intrin. h|krótkie _InterlockedXor16 (krótkie \*nietrwałe, krótkie)|
|[_InterlockedXor16_np](interlockedxor-intrinsic-functions.md)||intrin. h|krótkie _InterlockedXor16_np (krótkie \*, krótkie)|
|[_InterlockedXor64](interlockedxor-intrinsic-functions.md)||intrin. h|_InterlockedXor64 __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedXor64_HLEAcquire](interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedXor64_HLEAcquire __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedXor64_HLERelease](interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin. h|_InterlockedXor64_HLERelease __int64 (\__int64 volatile \*, \__int64)|
|[_InterlockedXor64_np](interlockedxor-intrinsic-functions.md)||intrin. h|_InterlockedXor64_np __int64 (\__int64 \*, \__int64)|
|[_InterlockedXor8](interlockedxor-intrinsic-functions.md)||intrin. h|znak _InterlockedXor8 (znak nietrwały \*, Char)|
|[_InterlockedXor8_np](interlockedxor-intrinsic-functions.md)||intrin. h|znak _InterlockedXor8_np (Char \*, Char)|
|[__invlpg](invlpg.md)||intrin. h|void __invlpg (void\*)|
|[_invpcid](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_invpcid)|INVPCID [2]|immintrin. h|void _invpcid (bez znaku int, void \*)|
|[__inword](inword.md)||intrin. h|krótkie __inword bez znaku (bez znaku)|
|[__inwordstring](inwordstring.md)||intrin. h|void __inwordstring (niepodpisane krótkie, niepodpisane, krótkie \*, Long unsigned)|
|_lgdt||intrin. h|void _lgdt (void\*)|
|[__lidt](lidt.md)||intrin. h|void __lidt (void\*)|
|[__ll_lshift](ll-lshift.md)||intrin. h|niepodpisane __int64 [Pascal/CDECL] \__ll_lshift (bez znaku \__int64, int)|
|[__ll_rshift](ll-rshift.md)||intrin. h|__int64 [Pascal/CDECL] \__ll_rshift (\__int64, int)|
|__llwpcb|LWP [1]|ammintrin. h|void __llwpcb (void \*)|
|_load_be_u16<br /><br /> [_loadbe_i16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i16&expand=3071)|MOVBE|immintrin. h|krótkie _load_be_u16 bez znaku (void const\*);<br /><br /> krótkie _loadbe_i16 (void const\*); r.3|
|_load_be_u32<br /><br /> [_loadbe_i32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i32&expand=3072)|MOVBE|immintrin. h|niepodpisane _load_be_u32 int (void const\*);<br /><br /> int _loadbe_i32 (void const\*); r.3|
|_load_be_u64<br /><br /> [_loadbe_i64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i64&expand=3073)|MOVBE|immintrin. h|niepodpisane _load_be_u64 __int64 (void const\*);<br /><br /> \__int64 _loadbe_i64 (void const\*); r.3|
|__lwpins32|LWP [1]|ammintrin. h|niepodpisany znak __lwpins32 (int unsigned, int unsigned int)|
|__lwpins64|LWP [1]|ammintrin. h|niepodpisany znak __lwpins64 (niepodpisane \__int64, int bez znaku int)|
|__lwpval32|LWP [1]|ammintrin. h|void __lwpval32 (niepodpisane int, int unsigned int)|
|__lwpval64|LWP [1]|ammintrin. h|void __lwpval64 (niepodpisane \__int64, int unsigned int)|
|[__lzcnt](lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin. h|niepodpisane __lzcnt int (int bez znaku)|
|[_lzcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_lzcnt_u32)|BMI|ammintrin. h, immintrin. h|niepodpisane _lzcnt_u32 int (int bez znaku)|
|[_lzcnt_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_lzcnt_u64)|BMI|ammintrin. h, immintrin. h|niepodpisane _lzcnt_u64 __int64 (niepodpisane \__int64)|
|[__lzcnt16](lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin. h|krótkie __lzcnt16 bez znaku (bez znaku)|
|[__lzcnt64](lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin. h|niepodpisane __int64 \__lzcnt64 (bez znaku \__int64)|
|_m_prefetch|3DNOW|intrin. h|void _m_prefetch (void\*)|
|_m_prefetchw|3DNOW|intrin. h|void _m_prefetchw (void\*)|
|[_mm_abs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi16)|SSSE3|intrin. h|_mm_abs_epi16 __m128i (\__m128i)|
|[_mm_abs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi32)|SSSE3|intrin. h|_mm_abs_epi32 __m128i (\__m128i)|
|[_mm_abs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi8)|SSSE3|intrin. h|_mm_abs_epi8 __m128i (\__m128i)|
|[_mm_add_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi16)|SSE2|intrin. h|_mm_add_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_add_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi32)|SSE2|intrin. h|_mm_add_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_add_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi64)|SSE2|intrin. h|_mm_add_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_add_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi8)|SSE2|intrin. h|_mm_add_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_add_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pd)|SSE2|intrin. h|_mm_add_pd __m128d (\__m128d, \__m128d)|
|[_mm_add_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_ps)|SSE|intrin. h|_mm_add_ps __m128 (\__m128, \__m128)|
|[_mm_add_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_sd)|SSE2|intrin. h|_mm_add_sd __m128d (\__m128d, \__m128d)|
|[_mm_add_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_ss)|SSE|intrin. h|_mm_add_ss __m128 (\__m128, \__m128)|
|[_mm_adds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epi16)|SSE2|intrin. h|_mm_adds_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_adds_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epi8)|SSE2|intrin. h|_mm_adds_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_adds_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epu16)|SSE2|intrin. h|_mm_adds_epu16 __m128i (\__m128i, \__m128i)|
|[_mm_adds_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epu8)|SSE2|intrin. h|_mm_adds_epu8 __m128i (\__m128i, \__m128i)|
|[_mm_addsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_addsub_pd)|SSE3|intrin. h|_mm_addsub_pd __m128d (\__m128d, \__m128d)|
|[_mm_addsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_addsub_ps)|SSE3|intrin. h|_mm_addsub_ps __m128 (\__m128, \__m128)|
|[_mm_aesdec_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesdec_si128)|AESNI [2]|immintrin. h|_mm_aesdec_si128 __m128i (\__m128i, \__m128i)|
|[_mm_aesdeclast_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesdeclast_si128)|AESNI [2]|immintrin. h|_mm_aesdeclast_si128 __m128i (\__m128i, \__m128i)|
|[_mm_aesenc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesenc_si128)|AESNI [2]|immintrin. h|_mm_aesenc_si128 __m128i (\__m128i, \__m128i)|
|[_mm_aesenclast_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesenclast_si128)|AESNI [2]|immintrin. h|_mm_aesenclast_si128 __m128i (\__m128i, \__m128i)|
|[_mm_aesimc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesimc_si128)|AESNI [2]|immintrin. h|_mm_aesimc_si128 __m128i (\__m128i)|
|[_mm_aeskeygenassist_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aeskeygenassist_si128)|AESNI [2]|immintrin. h|__m128i _mm_aeskeygenassist_si128 (\__m128i, const int)|
|[_mm_alignr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_alignr_epi8)|SSSE3|intrin. h|__m128i _mm_alignr_epi8 (\__m128i, \__m128i, int)|
|[_mm_and_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_pd)|SSE2|intrin. h|_mm_and_pd __m128d (\__m128d, \__m128d)|
|[_mm_and_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_ps)|SSE|intrin. h|_mm_and_ps __m128 (\__m128, \__m128)|
|[_mm_and_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_si128)|SSE2|intrin. h|_mm_and_si128 __m128i (\__m128i, \__m128i)|
|[_mm_andnot_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_pd)|SSE2|intrin. h|_mm_andnot_pd __m128d (\__m128d, \__m128d)|
|[_mm_andnot_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_ps)|SSE|intrin. h|_mm_andnot_ps __m128 (\__m128, \__m128)|
|[_mm_andnot_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_si128)|SSE2|intrin. h|_mm_andnot_si128 __m128i (\__m128i, \__m128i)|
|[_mm_avg_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_avg_epu16)|SSE2|intrin. h|_mm_avg_epu16 __m128i (\__m128i, \__m128i)|
|[_mm_avg_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_avg_epu8)|SSE2|intrin. h|_mm_avg_epu8 __m128i (\__m128i, \__m128i)|
|[_mm_blend_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_epi16)|SSE41|intrin. h|__m128i _mm_blend_epi16 (\__m128i, \__m128i, const int)|
|[_mm_blend_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_epi32)|AVX2 [2]|immintrin. h|__m128i _mm_blend_epi32 (\__m128i, \__m128i, const int)|
|[_mm_blend_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_pd)|SSE41|intrin. h|__m128d _mm_blend_pd (\__m128d, \__m128d, const int)|
|[_mm_blend_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_ps)|SSE41|intrin. h|__m128 _mm_blend_ps (\__m128, \__m128, const int)|
|[_mm_blendv_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_epi8)|SSE41|intrin. h|__m128i _mm_blendv_epi8 (\__m128i, \__m128i, \__m128i)|
|[_mm_blendv_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_pd)|SSE41|intrin. h|__m128d _mm_blendv_pd (\__m128d, \__m128d, \__m128d)|
|[_mm_blendv_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_ps)|SSE41|intrin. h|__m128 _mm_blendv_ps (\__m128, \__m128, \__m128)|
|[_mm_broadcast_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcast_ss)|AVX [2]|immintrin. h|__m128 _mm_broadcast_ss (float const \*)|
|[_mm_broadcastb_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastb_epi8)|AVX2 [2]|immintrin. h|_mm_broadcastb_epi8 __m128i (\__m128i)|
|[_mm_broadcastd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastd_epi32)|AVX2 [2]|immintrin. h|_mm_broadcastd_epi32 __m128i (\__m128i)|
|[_mm_broadcastq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastq_epi64)|AVX2 [2]|immintrin. h|_mm_broadcastq_epi64 __m128i (\__m128i)|
|[_mm_broadcastsd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastsd_pd)|AVX2 [2]|immintrin. h|_mm_broadcastsd_pd __m128d (\__m128d)|
|[_mm_broadcastss_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastss_ps)|AVX2 [2]|immintrin. h|_mm_broadcastss_ps __m128 (\__m128)|
|[_mm_broadcastw_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastw_epi16)|AVX2 [2]|immintrin. h|_mm_broadcastw_epi16 __m128i (\__m128i)|
|[_mm_castpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castpd_ps)|SSSE3|intrin. h|_mm_castpd_ps __m128 (\__m128d)|
|[_mm_castpd_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castpd_si128)|SSSE3|intrin. h|_mm_castpd_si128 __m128i (\__m128d)|
|[_mm_castps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castps_pd)|SSSE3|intrin. h|_mm_castps_pd __m128d (\__m128)|
|[_mm_castps_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castps_si128)|SSSE3|intrin. h|_mm_castps_si128 __m128i (\__m128)|
|[_mm_castsi128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castsi128_pd)|SSSE3|intrin. h|_mm_castsi128_pd __m128d (\__m128i)|
|[_mm_castsi128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castsi128_ps)|SSSE3|intrin. h|_mm_castsi128_ps __m128 (\__m128i)|
|[_mm_clflush](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_clflush)|SSE2|intrin. h|void _mm_clflush (void const \*)|
|[_mm_clmulepi64_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_clmulepi64_si128)|PCLMULQDQ [2]|immintrin. h|__m128i _mm_clmulepi64_si128 (\__m128i, \__m128i, const int)|
|_mm_cmov_si128|XOP [1]|ammintrin. h|__m128i _mm_cmov_si128 (\__m128i, \__m128i, \__m128i)|
|[_mm_cmp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_pd)|AVX [2]|immintrin. h|__m128d _mm_cmp_pd (\__m128d, \__m128d, const int)|
|[_mm_cmp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_ps)|AVX [2]|immintrin. h|__m128 _mm_cmp_ps (\__m128, \__m128, const int)|
|[_mm_cmp_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_sd)|AVX [2]|immintrin. h|__m128d _mm_cmp_sd (\__m128d, \__m128d, const int)|
|[_mm_cmp_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_ss)|AVX [2]|immintrin. h|__m128 _mm_cmp_ss (\__m128, \__m128, const int)|
|[_mm_cmpeq_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi16)|SSE2|intrin. h|_mm_cmpeq_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_cmpeq_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi32)|SSE2|intrin. h|_mm_cmpeq_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_cmpeq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi64)|SSE41|intrin. h|_mm_cmpeq_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_cmpeq_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi8)|SSE2|intrin. h|_mm_cmpeq_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_cmpeq_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pd)|SSE2|intrin. h|_mm_cmpeq_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpeq_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_ps)|SSE|intrin. h|_mm_cmpeq_ps __m128 (\__m128, \__m128)|
|[_mm_cmpeq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_sd)|SSE2|intrin. h|_mm_cmpeq_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpeq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_ss)|SSE|intrin. h|_mm_cmpeq_ss __m128 (\__m128, \__m128)|
|[_mm_cmpestra](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestra)|SSE42|intrin. h|int _mm_cmpestra (\__m128i, int, \__m128i, int, const int)|
|[_mm_cmpestrc](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrc)|SSE42|intrin. h|int _mm_cmpestrc (\__m128i, int, \__m128i, int, const int)|
|[_mm_cmpestri](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestri)|SSE42|intrin. h|int _mm_cmpestri (\__m128i, int, \__m128i, int, const int)|
|[_mm_cmpestrm](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrm)|SSE42|intrin. h|__m128i _mm_cmpestrm (\__m128i, int, \__m128i, int, const int)|
|[_mm_cmpestro](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestro)|SSE42|intrin. h|int _mm_cmpestro (\__m128i, int, \__m128i, int, const int)|
|[_mm_cmpestrs](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrs)|SSE42|intrin. h|int _mm_cmpestrs (\__m128i, int, \__m128i, int, const int)|
|[_mm_cmpestrz](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrz)|SSE42|intrin. h|int _mm_cmpestrz (\__m128i, int, \__m128i, int, const int)|
|[_mm_cmpge_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_pd)|SSE2|intrin. h|_mm_cmpge_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpge_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_ps)|SSE|intrin. h|_mm_cmpge_ps __m128 (\__m128, \__m128)|
|[_mm_cmpge_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_sd)|SSE2|intrin. h|_mm_cmpge_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpge_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_ss)|SSE|intrin. h|_mm_cmpge_ss __m128 (\__m128, \__m128)|
|[_mm_cmpgt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi16)|SSE2|intrin. h|_mm_cmpgt_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_cmpgt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi32)|SSE2|intrin. h|_mm_cmpgt_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_cmpgt_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi64)|SSE42|intrin. h|_mm_cmpgt_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_cmpgt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi8)|SSE2|intrin. h|_mm_cmpgt_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_cmpgt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pd)|SSE2|intrin. h|_mm_cmpgt_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpgt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_ps)|SSE|intrin. h|_mm_cmpgt_ps __m128 (\__m128, \__m128)|
|[_mm_cmpgt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_sd)|SSE2|intrin. h|_mm_cmpgt_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpgt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_ss)|SSE|intrin. h|_mm_cmpgt_ss __m128 (\__m128, \__m128)|
|[_mm_cmpistra](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistra)|SSE42|intrin. h|int _mm_cmpistra (\__m128i, \__m128i, const int)|
|[_mm_cmpistrc](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrc)|SSE42|intrin. h|int _mm_cmpistrc (\__m128i, \__m128i, const int)|
|[_mm_cmpistri](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistri)|SSE42|intrin. h|int _mm_cmpistri (\__m128i, \__m128i, const int)|
|[_mm_cmpistrm](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrm)|SSE42|intrin. h|__m128i _mm_cmpistrm (\__m128i, \__m128i, const int)|
|[_mm_cmpistro](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistro)|SSE42|intrin. h|int _mm_cmpistro (\__m128i, \__m128i, const int)|
|[_mm_cmpistrs](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrs)|SSE42|intrin. h|int _mm_cmpistrs (\__m128i, \__m128i, const int)|
|[_mm_cmpistrz](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrz)|SSE42|intrin. h|int _mm_cmpistrz (\__m128i, \__m128i, const int)|
|[_mm_cmple_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_pd)|SSE2|intrin. h|_mm_cmple_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmple_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_ps)|SSE|intrin. h|_mm_cmple_ps __m128 (\__m128, \__m128)|
|[_mm_cmple_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_sd)|SSE2|intrin. h|_mm_cmple_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmple_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_ss)|SSE|intrin. h|_mm_cmple_ss __m128 (\__m128, \__m128)|
|[_mm_cmplt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi16)|SSE2|intrin. h|_mm_cmplt_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_cmplt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi32)|SSE2|intrin. h|_mm_cmplt_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_cmplt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi8)|SSE2|intrin. h|_mm_cmplt_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_cmplt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_pd)|SSE2|intrin. h|_mm_cmplt_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmplt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_ps)|SSE|intrin. h|_mm_cmplt_ps __m128 (\__m128, \__m128)|
|[_mm_cmplt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_sd)|SSE2|intrin. h|_mm_cmplt_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmplt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_ss)|SSE|intrin. h|_mm_cmplt_ss __m128 (\__m128, \__m128)|
|[_mm_cmpneq_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_pd)|SSE2|intrin. h|_mm_cmpneq_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpneq_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_ps)|SSE|intrin. h|_mm_cmpneq_ps __m128 (\__m128, \__m128)|
|[_mm_cmpneq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_sd)|SSE2|intrin. h|_mm_cmpneq_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpneq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_ss)|SSE|intrin. h|_mm_cmpneq_ss __m128 (\__m128, \__m128)|
|[_mm_cmpnge_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_pd)|SSE2|intrin. h|_mm_cmpnge_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpnge_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_ps)|SSE|intrin. h|_mm_cmpnge_ps __m128 (\__m128, \__m128)|
|[_mm_cmpnge_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_sd)|SSE2|intrin. h|_mm_cmpnge_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpnge_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_ss)|SSE|intrin. h|_mm_cmpnge_ss __m128 (\__m128, \__m128)|
|[_mm_cmpngt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_pd)|SSE2|intrin. h|_mm_cmpngt_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpngt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_ps)|SSE|intrin. h|_mm_cmpngt_ps __m128 (\__m128, \__m128)|
|[_mm_cmpngt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_sd)|SSE2|intrin. h|_mm_cmpngt_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpngt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_ss)|SSE|intrin. h|_mm_cmpngt_ss __m128 (\__m128, \__m128)|
|[_mm_cmpnle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_pd)|SSE2|intrin. h|_mm_cmpnle_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpnle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_ps)|SSE|intrin. h|_mm_cmpnle_ps __m128 (\__m128, \__m128)|
|[_mm_cmpnle_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_sd)|SSE2|intrin. h|_mm_cmpnle_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpnle_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_ss)|SSE|intrin. h|_mm_cmpnle_ss __m128 (\__m128, \__m128)|
|[_mm_cmpnlt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_pd)|SSE2|intrin. h|_mm_cmpnlt_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpnlt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_ps)|SSE|intrin. h|_mm_cmpnlt_ps __m128 (\__m128, \__m128)|
|[_mm_cmpnlt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_sd)|SSE2|intrin. h|_mm_cmpnlt_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpnlt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_ss)|SSE|intrin. h|_mm_cmpnlt_ss __m128 (\__m128, \__m128)|
|[_mm_cmpord_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_pd)|SSE2|intrin. h|_mm_cmpord_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpord_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_ps)|SSE|intrin. h|_mm_cmpord_ps __m128 (\__m128, \__m128)|
|[_mm_cmpord_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_sd)|SSE2|intrin. h|_mm_cmpord_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpord_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_ss)|SSE|intrin. h|_mm_cmpord_ss __m128 (\__m128, \__m128)|
|[_mm_cmpunord_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_pd)|SSE2|intrin. h|_mm_cmpunord_pd __m128d (\__m128d, \__m128d)|
|[_mm_cmpunord_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_ps)|SSE|intrin. h|_mm_cmpunord_ps __m128 (\__m128, \__m128)|
|[_mm_cmpunord_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_sd)|SSE2|intrin. h|_mm_cmpunord_sd __m128d (\__m128d, \__m128d)|
|[_mm_cmpunord_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_ss)|SSE|intrin. h|_mm_cmpunord_ss __m128 (\__m128, \__m128)|
|_mm_com_epi16|XOP [1]|ammintrin. h|__m128i _mm_com_epi16 (\__m128i, \__m128i, int)|
|_mm_com_epi32|XOP [1]|ammintrin. h|__m128i _mm_com_epi32 (\__m128i, \__m128i, int)|
|_mm_com_epi64|XOP [1]|ammintrin. h|__m128i _mm_com_epi32 (\__m128i, \__m128i, int)|
|_mm_com_epi8|XOP [1]|ammintrin. h|__m128i _mm_com_epi8 (\__m128i, \__m128i, int)|
|_mm_com_epu16|XOP [1]|ammintrin. h|__m128i _mm_com_epu16 (\__m128i, \__m128i, int)|
|_mm_com_epu32|XOP [1]|ammintrin. h|__m128i _mm_com_epu32 (\__m128i, \__m128i, int)|
|_mm_com_epu64|XOP [1]|ammintrin. h|__m128i _mm_com_epu32 (\__m128i, \__m128i, int)|
|_mm_com_epu8|XOP [1]|ammintrin. h|__m128i _mm_com_epu8 (\__m128i, \__m128i, int)|
|[_mm_comieq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comieq_sd)|SSE2|intrin. h|int _mm_comieq_sd (\__m128d, \__m128d)|
|[_mm_comieq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comieq_ss)|SSE|intrin. h|int _mm_comieq_ss (\__m128, \__m128)|
|[_mm_comige_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comige_sd)|SSE2|intrin. h|int _mm_comige_sd (\__m128d, \__m128d)|
|[_mm_comige_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comige_ss)|SSE|intrin. h|int _mm_comige_ss (\__m128, \__m128)|
|[_mm_comigt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comigt_sd)|SSE2|intrin. h|int _mm_comigt_sd (\__m128d, \__m128d)|
|[_mm_comigt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comigt_ss)|SSE|intrin. h|int _mm_comigt_ss (\__m128, \__m128)|
|[_mm_comile_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comile_sd)|SSE2|intrin. h|int _mm_comile_sd (\__m128d, \__m128d)|
|[_mm_comile_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comile_ss)|SSE|intrin. h|int _mm_comile_ss (\__m128, \__m128)|
|[_mm_comilt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comilt_sd)|SSE2|intrin. h|int _mm_comilt_sd (\__m128d, \__m128d)|
|[_mm_comilt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comilt_ss)|SSE|intrin. h|int _mm_comilt_ss (\__m128, \__m128)|
|[_mm_comineq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comineq_sd)|SSE2|intrin. h|int _mm_comineq_sd (\__m128d, \__m128d)|
|[_mm_comineq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comineq_ss)|SSE|intrin. h|int _mm_comineq_ss (\__m128, \__m128)|
|[_mm_crc32_u16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u16)|SSE42|intrin. h|niepodpisane _mm_crc32_u16 int (niepodpisane int, bez znaku)|
|[_mm_crc32_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u32)|SSE42|intrin. h|niepodpisane _mm_crc32_u32 int (niepodpisane int, int bez znaku)|
|[_mm_crc32_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u64)|SSE42|intrin. h|niepodpisane _mm_crc32_u64 __int64 (niepodpisane \__int64, bez znaku \_)|
|[_mm_crc32_u8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u8)|SSE42|intrin. h|niepodpisane _mm_crc32_u8 int (bez znaku int, znak niepodpisany)|
|[_mm_cvt_si2ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_si2ss)|SSE|intrin. h|_mm_cvt_si2ss __m128 (\__m128, int)|
|[_mm_cvt_ss2si](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_ss2si)|SSE|intrin. h|int _mm_cvt_ss2si (\__m128)|
|[_mm_cvtepi16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi16_epi32)|SSE41|intrin. h|_mm_cvtepi16_epi32 __m128i (\__m128i)|
|[_mm_cvtepi16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi16_epi64)|SSE41|intrin. h|_mm_cvtepi16_epi64 __m128i (\__m128i)|
|[_mm_cvtepi32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_epi64)|SSE41|intrin. h|_mm_cvtepi32_epi64 __m128i (\__m128i)|
|[_mm_cvtepi32_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_pd)|SSE2|intrin. h|_mm_cvtepi32_pd __m128d (\__m128i)|
|[_mm_cvtepi32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_ps)|SSE2|intrin. h|_mm_cvtepi32_ps __m128 (\__m128i)|
|[_mm_cvtepi8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi16)|SSE41|intrin. h|_mm_cvtepi8_epi16 __m128i (\__m128i)|
|[_mm_cvtepi8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi32)|SSE41|intrin. h|_mm_cvtepi8_epi32 __m128i (\__m128i)|
|[_mm_cvtepi8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi64)|SSE41|intrin. h|_mm_cvtepi8_epi64 __m128i (\__m128i)|
|[_mm_cvtepu16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu16_epi32)|SSE41|intrin. h|_mm_cvtepu16_epi32 __m128i (\__m128i)|
|[_mm_cvtepu16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu16_epi64)|SSE41|intrin. h|_mm_cvtepu16_epi64 __m128i (\__m128i)|
|[_mm_cvtepu32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu32_epi64)|SSE41|intrin. h|_mm_cvtepu32_epi64 __m128i (\__m128i)|
|[_mm_cvtepu8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi16)|SSE41|intrin. h|_mm_cvtepu8_epi16 __m128i (\__m128i)|
|[_mm_cvtepu8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi32)|SSE41|intrin. h|_mm_cvtepu8_epi32 __m128i (\__m128i)|
|[_mm_cvtepu8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi64)|SSE41|intrin. h|_mm_cvtepu8_epi64 __m128i (\__m128i)|
|[_mm_cvtpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpd_epi32)|SSE2|intrin. h|_mm_cvtpd_epi32 __m128i (\__m128d)|
|[_mm_cvtpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpd_ps)|SSE2|intrin. h|_mm_cvtpd_ps __m128 (\__m128d)|
|[_mm_cvtph_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtph_ps)|F16C [2]|immintrin. h|_mm_cvtph_ps __m128 (\__m128i)|
|[_mm_cvtps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_epi32)|SSE2|intrin. h|_mm_cvtps_epi32 __m128i (\__m128)|
|[_mm_cvtps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_pd)|SSE2|intrin. h|_mm_cvtps_pd __m128d (\__m128)|
|[_mm_cvtps_ph](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_ph)|F16C [2]|immintrin. h|__m128i _mm_cvtps_ph (\__m128, const int)|
|[_mm_cvtsd_f64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_f64)|SSSE3|intrin. h|podwójne _mm_cvtsd_f64 (\__m128d)|
|[_mm_cvtsd_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_si32)|SSE2|intrin. h|int _mm_cvtsd_si32 (\__m128d)|
|[_mm_cvtsd_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_si64)|SSE2|intrin. h|_mm_cvtsd_si64 __int64 (\__m128d)|
|[_mm_cvtsd_si64x](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_si64x)|SSE2|intrin. h|_mm_cvtsd_si64x __int64 (\__m128d)|
|[_mm_cvtsd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_ss)|SSE2|intrin. h|_mm_cvtsd_ss __m128 (\__m128, \__m128d)|
|[_mm_cvtsi128_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi128_si32)|SSE2|intrin. h|int _mm_cvtsi128_si32 (\__m128i)|
|[_mm_cvtsi128_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi128_si64)|SSE2|intrin. h|_mm_cvtsi128_si64 __int64 (\__m128i)|
|[_mm_cvtsi128_si64x](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi128_si64x)|SSE2|intrin. h|_mm_cvtsi128_si64x __int64 (\__m128i)|
|[_mm_cvtsi32_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi32_sd)|SSE2|intrin. h|_mm_cvtsi32_sd __m128d (\__m128d, int)|
|[_mm_cvtsi32_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi32_si128)|SSE2|intrin. h|_mm_cvtsi32_si128 __m128i (int)|
|[_mm_cvtsi64_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi64_sd)|SSE2|intrin. h|_mm_cvtsi64_sd __m128d (\__m128d, \__int64)|
|[_mm_cvtsi64_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi64_si128)|SSE2|intrin. h|_mm_cvtsi64_si128 __m128i (\__int64)|
|[_mm_cvtsi64_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi64_ss)|SSE|intrin. h|_mm_cvtsi64_ss __m128 (\__m128, \__int64)|
|[_mm_cvtsi64x_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi64x_sd)|SSE2|intrin. h|_mm_cvtsi64x_sd __m128d (\__m128d, \__int64)|
|[_mm_cvtsi64x_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi64x_si128)|SSE2|intrin. h|_mm_cvtsi64x_si128 __m128i (\__int64)|
|[_mm_cvtsi64x_ss](mm-cvtsi64x-ss.md)|SSE2|intrin. h|_mm_cvtsi64x_ss __m128 (\__m128, \__int64)|
|[_mm_cvtss_f32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtss_f32)|SSSE3|intrin. h|_mm_cvtss_f32 zmiennoprzecinkowe (\__m128)|
|[_mm_cvtss_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtss_sd)|SSE2|intrin. h|_mm_cvtss_sd __m128d (\__m128d, \__m128)|
|[_mm_cvtss_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtss_si64)|SSE|intrin. h|_mm_cvtss_si64 __int64 (\__m128)|
|[_mm_cvtss_si64x](mm-cvtss-si64x.md)|SSE2|intrin. h|_mm_cvtss_si64x __int64 (\__m128)|
|[_mm_cvtt_ss2si](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtt_ss2si)|SSE|intrin. h|int _mm_cvtt_ss2si (\__m128)|
|[_mm_cvttpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttpd_epi32)|SSE2|intrin. h|_mm_cvttpd_epi32 __m128i (\__m128d)|
|[_mm_cvttps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttps_epi32)|SSE2|intrin. h|_mm_cvttps_epi32 __m128i (\__m128)|
|[_mm_cvttsd_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttsd_si32)|SSE2|intrin. h|int _mm_cvttsd_si32 (\__m128d)|
|[_mm_cvttsd_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttsd_si64)|SSE2|intrin. h|_mm_cvttsd_si64 __int64 (\__m128d)|
|[_mm_cvttsd_si64x](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttsd_si64x)|SSE2|intrin. h|_mm_cvttsd_si64x __int64 (\__m128d)|
|[_mm_cvttss_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttss_si64)|SSE2|intrin. h|_mm_cvttss_si64 __int64 (\__m128)|
|[_mm_cvttss_si64x](mm-cvttss-si64x.md)|SSE2|intrin. h|_mm_cvttss_si64x __int64 (\__m128)|
|[_mm_div_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_pd)|SSE2|intrin. h|_mm_div_pd __m128d (\__m128d, \__m128d)|
|[_mm_div_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_ps)|SSE|intrin. h|_mm_div_ps __m128 (\__m128, \__m128)|
|[_mm_div_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_sd)|SSE2|intrin. h|_mm_div_sd __m128d (\__m128d, \__m128d)|
|[_mm_div_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_ss)|SSE|intrin. h|_mm_div_ss __m128 (\__m128, \__m128)|
|[_mm_dp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_dp_pd)|SSE41|intrin. h|__m128d _mm_dp_pd (\__m128d, \__m128d, const int)|
|[_mm_dp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_dp_ps)|SSE41|intrin. h|__m128 _mm_dp_ps (\__m128, \__m128, const int)|
|[_mm_extract_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi16)|SSE2|intrin. h|int _mm_extract_epi16 (\__m128i, int)|
|[_mm_extract_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi32)|SSE41|intrin. h|int _mm_extract_epi32 (\__m128i, const int)|
|[_mm_extract_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi64)|SSE41|intrin. h|__int64 _mm_extract_epi64 (\__m128i, const int)|
|[_mm_extract_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi8)|SSE41|intrin. h|int _mm_extract_epi8 (\__m128i, const int)|
|[_mm_extract_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_ps)|SSE41|intrin. h|int _mm_extract_ps (\__m128, const int)|
|[_mm_extract_si64](mm-extract-si64-mm-extracti-si64.md)|SSE4a|intrin. h|_mm_extract_si64 __m128i (\__m128i, \__m128i)|
|[_mm_extracti_si64](mm-extract-si64-mm-extracti-si64.md)|SSE4a|intrin. h|_mm_extracti_si64 __m128i (\__m128i, int, int)|
|[_mm_fmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_pd)|FMA [2]|immintrin. h|__m128d _mm_fmadd_pd (\__m128d, \__m128d, \__m128d)|
|[_mm_fmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_ps)|FMA [2]|immintrin. h|__m128 _mm_fmadd_ps (\__m128, \__m128, \__m128)|
|[_mm_fmadd_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_sd)|FMA [2]|immintrin. h|__m128d _mm_fmadd_sd (\__m128d, \__m128d, \__m128d)|
|[_mm_fmadd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_ss)|FMA [2]|immintrin. h|__m128 _mm_fmadd_ss (\__m128, \__m128, \__m128)|
|[_mm_fmaddsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmaddsub_pd)|FMA [2]|immintrin. h|__m128d _mm_fmaddsub_pd (\__m128d, \__m128d, \__m128d)|
|[_mm_fmaddsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmaddsub_ps)|FMA [2]|immintrin. h|__m128 _mm_fmaddsub_ps (\__m128, \__m128, \__m128)|
|[_mm_fmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_pd)|FMA [2]|immintrin. h|__m128d _mm_fmsub_pd (\__m128d, \__m128d, \__m128d)|
|[_mm_fmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_ps)|FMA [2]|immintrin. h|__m128 _mm_fmsub_ps (\__m128, \__m128, \__m128)|
|[_mm_fmsub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_sd)|FMA [2]|immintrin. h|__m128d _mm_fmsub_sd (\__m128d, \__m128d, \__m128d)|
|[_mm_fmsub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_ss)|FMA [2]|immintrin. h|__m128 _mm_fmsub_ss (\__m128, \__m128, \__m128)|
|[_mm_fmsubadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsubadd_pd)|FMA [2]|immintrin. h|__m128d _mm_fmsubadd_pd (\__m128d, \__m128d, \__m128d)|
|[_mm_fmsubadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsubadd_ps)|FMA [2]|immintrin. h|__m128 _mm_fmsubadd_ps (\__m128, \__m128, \__m128)|
|[_mm_fnmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_pd)|FMA [2]|immintrin. h|__m128d _mm_fnmadd_pd (\__m128d, \__m128d, \__m128d)|
|[_mm_fnmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_ps)|FMA [2]|immintrin. h|__m128 _mm_fnmadd_ps (\__m128, \__m128, \__m128)|
|[_mm_fnmadd_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_sd)|FMA [2]|immintrin. h|__m128d _mm_fnmadd_sd (\__m128d, \__m128d, \__m128d)|
|[_mm_fnmadd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_ss)|FMA [2]|immintrin. h|__m128 _mm_fnmadd_ss (\__m128, \__m128, \__m128)|
|[_mm_fnmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_pd)|FMA [2]|immintrin. h|__m128d _mm_fnmsub_pd (\__m128d, \__m128d, \__m128d)|
|[_mm_fnmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_ps)|FMA [2]|immintrin. h|__m128 _mm_fnmsub_ps (\__m128, \__m128, \__m128)|
|[_mm_fnmsub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_sd)|FMA [2]|immintrin. h|__m128d _mm_fnmsub_sd (\__m128d, \__m128d, \__m128d)|
|[_mm_fnmsub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_ss)|FMA [2]|immintrin. h|__m128 _mm_fnmsub_ss (\__m128, \__m128, \__m128)|
|_mm_frcz_pd|XOP [1]|ammintrin. h|_mm_frcz_pd __m128d (\__m128d)|
|_mm_frcz_ps|XOP [1]|ammintrin. h|_mm_frcz_ps __m128 (\__m128)|
|_mm_frcz_sd|XOP [1]|ammintrin. h|_mm_frcz_sd __m128d (\__m128d, \__m128d)|
|_mm_frcz_ss|XOP [1]|ammintrin. h|_mm_frcz_ss __m128 (\__m128, \__m128)|
|[_mm_getcsr](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_getcsr)|SSE|intrin. h|niepodpisane _mm_getcsr int (void)|
|[_mm_hadd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_epi16)|SSSE3|intrin. h|_mm_hadd_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_hadd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_epi32)|SSSE3|intrin. h|_mm_hadd_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_hadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_pd)|SSE3|intrin. h|_mm_hadd_pd __m128d (\__m128d, \__m128d)|
|[_mm_hadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_ps)|SSE3|intrin. h|_mm_hadd_ps __m128 (\__m128, \__m128)|
|_mm_haddd_epi16|XOP [1]|ammintrin. h|_mm_haddd_epi16 __m128i (\__m128i)|
|_mm_haddd_epi8|XOP [1]|ammintrin. h|_mm_haddd_epi8 __m128i (\__m128i)|
|_mm_haddd_epu16|XOP [1]|ammintrin. h|_mm_haddd_epu16 __m128i (\__m128i)|
|_mm_haddd_epu8|XOP [1]|ammintrin. h|_mm_haddd_epu8 __m128i (\__m128i)|
|_mm_haddq_epi16|XOP [1]|ammintrin. h|_mm_haddq_epi16 __m128i (\__m128i)|
|_mm_haddq_epi32|XOP [1]|ammintrin. h|_mm_haddq_epi32 __m128i (\__m128i)|
|_mm_haddq_epi8|XOP [1]|ammintrin. h|_mm_haddq_epi8 __m128i (\__m128i)|
|_mm_haddq_epu16|XOP [1]|ammintrin. h|_mm_haddq_epu16 __m128i (\__m128i)|
|_mm_haddq_epu32|XOP [1]|ammintrin. h|_mm_haddq_epu32 __m128i (\__m128i)|
|_mm_haddq_epu8|XOP [1]|ammintrin. h|_mm_haddq_epu8 __m128i (\__m128i)|
|[_mm_hadds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadds_epi16)|SSSE3|intrin. h|_mm_hadds_epi16 __m128i (\__m128i, \__m128i)|
|_mm_haddw_epi8|XOP [1]|ammintrin. h|_mm_haddw_epi8 __m128i (\__m128i)|
|_mm_haddw_epu8|XOP [1]|ammintrin. h|_mm_haddw_epu8 __m128i (\__m128i)|
|[_mm_hsub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_epi16)|SSSE3|intrin. h|_mm_hsub_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_hsub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_epi32)|SSSE3|intrin. h|_mm_hsub_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_hsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_pd)|SSE3|intrin. h|_mm_hsub_pd __m128d (\__m128d, \__m128d)|
|[_mm_hsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_ps)|SSE3|intrin. h|_mm_hsub_ps __m128 (\__m128, \__m128)|
|_mm_hsubd_epi16|XOP [1]|ammintrin. h|_mm_hsubd_epi16 __m128i (\__m128i)|
|_mm_hsubq_epi32|XOP [1]|ammintrin. h|_mm_hsubq_epi32 __m128i (\__m128i)|
|[_mm_hsubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsubs_epi16)|SSSE3|intrin. h|_mm_hsubs_epi16 __m128i (\__m128i, \__m128i)|
|_mm_hsubw_epi8|XOP [1]|ammintrin. h|_mm_hsubw_epi8 __m128i (\__m128i)|
|[_mm_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_epi32)|AVX2 [2]|immintrin. h|__m128i _mm_i32gather_epi32 (int const \*, \__m128i, const int)|
|[_mm_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_epi64)|AVX2 [2]|immintrin. h|__m128i _mm_i32gather_epi64 (\__int64 const \*, \__m128i, const int)|
|[_mm_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_pd)|AVX2 [2]|immintrin. h|__m128d _mm_i32gather_pd (podwójna stała \*, \__m128i, const int)|
|[_mm_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_ps)|AVX2 [2]|immintrin. h|__m128 _mm_i32gather_ps (float const \*, \__m128i, const int)|
|[_mm_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_epi32)|AVX2 [2]|immintrin. h|__m128i _mm_i64gather_epi32 (int const \*, \__m128i, const int)|
|[_mm_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_epi64)|AVX2 [2]|immintrin. h|__m128i _mm_i64gather_epi64 (\__int64 const \*, \__m128i, const int)|
|[_mm_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_pd)|AVX2 [2]|immintrin. h|__m128d _mm_i64gather_pd (podwójna stała \*, \__m128i, const int)|
|[_mm_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_ps)|AVX2 [2]|immintrin. h|__m128 _mm_i64gather_ps (float const \*, \__m128i, const int)|
|[_mm_insert_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi16)|SSE2|intrin. h|_mm_insert_epi16 __m128i (\__m128i, int, int)|
|[_mm_insert_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi32)|SSE41|intrin. h|__m128i _mm_insert_epi32 (\__m128i, int, const int)|
|[_mm_insert_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi64)|SSE41|intrin. h|__m128i _mm_insert_epi64 (\__m128i, \__int64, const int)|
|[_mm_insert_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi8)|SSE41|intrin. h|__m128i _mm_insert_epi8 (\__m128i, int, const int)|
|[_mm_insert_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_ps)|SSE41|intrin. h|__m128 _mm_insert_ps (\__m128, \__m128, const int)|
|[_mm_insert_si64](mm-insert-si64-mm-inserti-si64.md)|SSE4a|intrin. h|_mm_insert_si64 __m128i (\__m128i, \__m128i)|
|[_mm_inserti_si64](mm-insert-si64-mm-inserti-si64.md)|SSE4a|intrin. h|__m128i _mm_inserti_si64 (\__m128i, \__m128i, int, int)|
|[_mm_lddqu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_lddqu_si128)|SSE3|intrin. h|_mm_lddqu_si128 __m128i (\__m128i const\*)|
|[_mm_lfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_lfence)|SSE2|intrin. h|void _mm_lfence (void)|
|[_mm_load_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_pd)|SSE2|intrin. h|_mm_load_pd __m128d (podwójne\*)|
|[_mm_load_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ps)|SSE|intrin. h|_mm_load_ps __m128 (float\*)|
|[_mm_load_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ps1)|SSE|intrin. h|_mm_load_ps1 __m128 (float\*)|
|[_mm_load_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_sd)|SSE2|intrin. h|_mm_load_sd __m128d (podwójne\*)|
|[_mm_load_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_si128)|SSE2|intrin. h|_mm_load_si128 __m128i (\__m128i\*)|
|[_mm_load_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ss)|SSE|intrin. h|_mm_load_ss __m128 (float\*)|
|[_mm_load1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load1_pd)|SSE2|intrin. h|_mm_load1_pd __m128d (podwójne\*)|
|[_mm_loaddup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loaddup_pd)|SSE3|intrin. h|_mm_loaddup_pd __m128d (podwójna stała\*)|
|[_mm_loadh_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadh_pd)|SSE2|intrin. h|_mm_loadh_pd __m128d (\__m128d, podwójne\*)|
|[_mm_loadh_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadh_pi)|SSE|intrin. h|_mm_loadh_pi __m128 (\__m128, \__m64\*)|
|[_mm_loadl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_epi64)|SSE2|intrin. h|_mm_loadl_epi64 __m128i (\__m128i\*)|
|[_mm_loadl_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_pd)|SSE2|intrin. h|_mm_loadl_pd __m128d (\__m128d, podwójne\*)|
|[_mm_loadl_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_pi)|SSE|intrin. h|_mm_loadl_pi __m128 (\__m128, \__m64\*)|
|[_mm_loadr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadr_pd)|SSE2|intrin. h|_mm_loadr_pd __m128d (podwójne\*)|
|[_mm_loadr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadr_ps)|SSE|intrin. h|_mm_loadr_ps __m128 (float\*)|
|[_mm_loadu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_pd)|SSE2|intrin. h|_mm_loadu_pd __m128d (podwójne\*)|
|[_mm_loadu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_ps)|SSE|intrin. h|_mm_loadu_ps __m128 (float\*)|
|[_mm_loadu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_si128)|SSE2|intrin. h|_mm_loadu_si128 __m128i (\__m128i\*)|
|_mm_macc_epi16|XOP [1]|ammintrin. h|__m128i _mm_macc_epi16 (\__m128i, \__m128i, \__m128i)|
|_mm_macc_epi32|XOP [1]|ammintrin. h|__m128i _mm_macc_epi32 (\__m128i, \__m128i, \__m128i)|
|_mm_macc_pd|FMA4 [1]|ammintrin. h|__m128d _mm_macc_pd (\__m128d, \__m128d, \__m128d)|
|_mm_macc_ps|FMA4 [1]|ammintrin. h|__m128 _mm_macc_ps (\__m128, \__m128, \__m128)|
|_mm_macc_sd|FMA4 [1]|ammintrin. h|__m128d _mm_macc_sd (\__m128d, \__m128d, \__m128d)|
|_mm_macc_ss|FMA4 [1]|ammintrin. h|__m128 _mm_macc_ss (\__m128, \__m128, \__m128)|
|_mm_maccd_epi16|XOP [1]|ammintrin. h|__m128i _mm_maccd_epi16 (\__m128i, \__m128i, \__m128i)|
|_mm_macchi_epi32|XOP [1]|ammintrin. h|__m128i _mm_macchi_epi32 (\__m128i, \__m128i, \__m128i)|
|_mm_macclo_epi32|XOP [1]|ammintrin. h|__m128i _mm_macclo_epi32 (\__m128i, \__m128i, \__m128i)|
|_mm_maccs_epi16|XOP [1]|ammintrin. h|__m128i _mm_maccs_epi16 (\__m128i, \__m128i, \__m128i)|
|_mm_maccs_epi32|XOP [1]|ammintrin. h|__m128i _mm_maccs_epi32 (\__m128i, \__m128i, \__m128i)|
|_mm_maccsd_epi16|XOP [1]|ammintrin. h|__m128i _mm_maccsd_epi16 (\__m128i, \__m128i, \__m128i)|
|_mm_maccshi_epi32|XOP [1]|ammintrin. h|__m128i _mm_maccshi_epi32 (\__m128i, \__m128i, \__m128i)|
|_mm_maccslo_epi32|XOP [1]|ammintrin. h|__m128i _mm_maccslo_epi32 (\__m128i, \__m128i, \__m128i)|
|[_mm_madd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_madd_epi16)|SSE2|intrin. h|_mm_madd_epi16 __m128i (\__m128i, \__m128i)|
|_mm_maddd_epi16|XOP [1]|ammintrin. h|__m128i _mm_maddd_epi16 (\__m128i, \__m128i, \__m128i)|
|_mm_maddsd_epi16|XOP [1]|ammintrin. h|__m128i _mm_maddsd_epi16 (\__m128i, \__m128i, \__m128i)|
|_mm_maddsub_pd|FMA4 [1]|ammintrin. h|__m128d _mm_maddsub_pd (\__m128d, \__m128d, \__m128d)|
|_mm_maddsub_ps|FMA4 [1]|ammintrin. h|__m128 _mm_maddsub_ps (\__m128, \__m128, \__m128)|
|[_mm_maddubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maddubs_epi16)|SSSE3|intrin. h|_mm_maddubs_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_mask_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_epi32)|AVX2 [2]|immintrin. h|__m128i _mm_mask_i32gather_epi32 (\__m128i, int const \*, \__m128i, \__m128i, const int)|
|[_mm_mask_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_epi64)|AVX2 [2]|immintrin. h|__m128i _mm_mask_i32gather_epi64 (\__m128i, \__int64 const \*, \__m128i, \__m128i, const int)|
|[_mm_mask_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_pd)|AVX2 [2]|immintrin. h|__m128d _mm_mask_i32gather_pd (\__m128d, podwójne stałe \*, \__m128i, \__m128d, const int)|
|[_mm_mask_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_ps)|AVX2 [2]|immintrin. h|__m128 _mm_mask_i32gather_ps (\__m128, float const \*, \__m128i, \__m128, const int)|
|[_mm_mask_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_epi32)|AVX2 [2]|immintrin. h|__m128i _mm_mask_i64gather_epi32 (\__m128i, int const \*, \__m128i, \__m128i, const int)|
|[_mm_mask_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_epi64)|AVX2 [2]|immintrin. h|__m128i _mm_mask_i64gather_epi64 (\__m128i, \__int64 const \*, \__m128i, \__m128i, const int)|
|[_mm_mask_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_pd)|AVX2 [2]|immintrin. h|__m128d _mm_mask_i64gather_pd (\__m128d, podwójne stałe \*, \__m128i, \__m128d, const int)|
|[_mm_mask_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_ps)|AVX2 [2]|immintrin. h|__m128 _mm_mask_i64gather_ps (\__m128, float const \*, \__m128i, \__m128, const int)|
|[_mm_maskload_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_epi32)|AVX2 [2]|immintrin. h|__m128i _mm_maskload_epi32 (int const \*, \__m128i)|
|[_mm_maskload_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_epi64)|AVX2 [2]|immintrin. h|_mm_maskload_epi64 __m128i (\__int64 const \*, \__m128i)|
|[_mm_maskload_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_pd)|AVX [2]|immintrin. h|__m128d _mm_maskload_pd (podwójna \*stała, \__m128i)|
|[_mm_maskload_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_ps)|AVX [2]|immintrin. h|__m128 _mm_maskload_ps (float const \*, \__m128i)|
|[_mm_maskmoveu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskmoveu_si128)|SSE2|intrin. h|void _mm_maskmoveu_si128 (\__m128i, \__m128i, char\*)|
|[_mm_maskstore_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_epi32)|AVX2 [2]|immintrin. h|void _mm_maskstore_epi32 (int \*, \__m128i, \__m128i)|
|[_mm_maskstore_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_epi64)|AVX2 [2]|immintrin. h|void _mm_maskstore_epi64 (\__int64 \*, \__m128i, \__m128i)|
|[_mm_maskstore_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_pd)|AVX [2]|immintrin. h|void _mm_maskstore_pd (podwójna \*, \__m128i, \__m128d)|
|[_mm_maskstore_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_ps)|AVX [2]|immintrin. h|void _mm_maskstore_ps (\*zmiennoprzecinkowych, \__m128i, \__m128)|
|[_mm_max_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi16)|SSE2|intrin. h|_mm_max_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_max_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi32)|SSE41|intrin. h|_mm_max_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_max_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi8)|SSE41|intrin. h|_mm_max_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_max_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu16)|SSE41|intrin. h|_mm_max_epu16 __m128i (\__m128i, \__m128i)|
|[_mm_max_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu32)|SSE41|intrin. h|_mm_max_epu32 __m128i (\__m128i, \__m128i)|
|[_mm_max_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu8)|SSE2|intrin. h|_mm_max_epu8 __m128i (\__m128i, \__m128i)|
|[_mm_max_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_pd)|SSE2|intrin. h|_mm_max_pd __m128d (\__m128d, \__m128d)|
|[_mm_max_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_ps)|SSE|intrin. h|_mm_max_ps __m128 (\__m128, \__m128)|
|[_mm_max_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_sd)|SSE2|intrin. h|_mm_max_sd __m128d (\__m128d, \__m128d)|
|[_mm_max_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_ss)|SSE|intrin. h|_mm_max_ss __m128 (\__m128, \__m128)|
|[_mm_mfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mfence)|SSE2|intrin. h|void _mm_mfence (void)|
|[_mm_min_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi16)|SSE2|intrin. h|_mm_min_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_min_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi32)|SSE41|intrin. h|_mm_min_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_min_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi8)|SSE41|intrin. h|_mm_min_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_min_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu16)|SSE41|intrin. h|_mm_min_epu16 __m128i (\__m128i, \__m128i)|
|[_mm_min_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu32)|SSE41|intrin. h|_mm_min_epu32 __m128i (\__m128i, \__m128i)|
|[_mm_min_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu8)|SSE2|intrin. h|_mm_min_epu8 __m128i (\__m128i, \__m128i)|
|[_mm_min_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_pd)|SSE2|intrin. h|_mm_min_pd __m128d (\__m128d, \__m128d)|
|[_mm_min_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_ps)|SSE|intrin. h|_mm_min_ps __m128 (\__m128, \__m128)|
|[_mm_min_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_sd)|SSE2|intrin. h|_mm_min_sd __m128d (\__m128d, \__m128d)|
|[_mm_min_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_ss)|SSE|intrin. h|_mm_min_ss __m128 (\__m128, \__m128)|
|[_mm_minpos_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_minpos_epu16)|SSE41|intrin. h|_mm_minpos_epu16 __m128i (\__m128i)|
|[_mm_monitor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_monitor)|SSE3|intrin. h|void _mm_monitor (void const\*, int unsigned int)|
|[_mm_move_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_epi64)|SSE2|intrin. h|_mm_move_epi64 __m128i (\__m128i)|
|[_mm_move_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_sd)|SSE2|intrin. h|_mm_move_sd __m128d (\__m128d, \__m128d)|
|[_mm_move_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_ss)|SSE|intrin. h|_mm_move_ss __m128 (\__m128, \__m128)|
|[_mm_movedup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movedup_pd)|SSE3|intrin. h|_mm_movedup_pd __m128d (\__m128d)|
|[_mm_movehdup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movehdup_ps)|SSE3|intrin. h|_mm_movehdup_ps __m128 (\__m128)|
|[_mm_movehl_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movehl_ps)|SSE|intrin. h|_mm_movehl_ps __m128 (\__m128, \__m128)|
|[_mm_moveldup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_moveldup_ps)|SSE3|intrin. h|_mm_moveldup_ps __m128 (\__m128)|
|[_mm_movelh_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movelh_ps)|SSE|intrin. h|_mm_movelh_ps __m128 (\__m128, \__m128)|
|[_mm_movemask_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_epi8)|SSE2|intrin. h|int _mm_movemask_epi8 (\__m128i)|
|[_mm_movemask_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_pd)|SSE2|intrin. h|int _mm_movemask_pd (\__m128d)|
|[_mm_movemask_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_ps)|SSE|intrin. h|int _mm_movemask_ps (\__m128)|
|[_mm_mpsadbw_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mpsadbw_epu8)|SSE41|intrin. h|__m128i _mm_mpsadbw_epu8 (\__m128i, \__m128i, const int)|
|_mm_msub_pd|FMA4 [1]|ammintrin. h|__m128d _mm_msub_pd (\__m128d, \__m128d, \__m128d)|
|_mm_msub_ps|FMA4 [1]|ammintrin. h|__m128 _mm_msub_ps (\__m128, \__m128, \__m128)|
|_mm_msub_sd|FMA4 [1]|ammintrin. h|__m128d _mm_msub_sd (\__m128d, \__m128d, \__m128d)|
|_mm_msub_ss|FMA4 [1]|ammintrin. h|__m128 _mm_msub_ss (\__m128, \__m128, \__m128)|
|_mm_msubadd_pd|FMA4 [1]|ammintrin. h|__m128d _mm_msubadd_pd (\__m128d, \__m128d, \__m128d)|
|_mm_msubadd_ps|FMA4 [1]|ammintrin. h|__m128 _mm_msubadd_ps (\__m128, \__m128, \__m128)|
|[_mm_mul_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_epi32)|SSE41|intrin. h|_mm_mul_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_mul_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_epu32)|SSE2|intrin. h|_mm_mul_epu32 __m128i (\__m128i, \__m128i)|
|[_mm_mul_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_pd)|SSE2|intrin. h|_mm_mul_pd __m128d (\__m128d, \__m128d)|
|[_mm_mul_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_ps)|SSE|intrin. h|_mm_mul_ps __m128 (\__m128, \__m128)|
|[_mm_mul_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_sd)|SSE2|intrin. h|_mm_mul_sd __m128d (\__m128d, \__m128d)|
|[_mm_mul_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_ss)|SSE|intrin. h|_mm_mul_ss __m128 (\__m128, \__m128)|
|[_mm_mulhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhi_epi16)|SSE2|intrin. h|_mm_mulhi_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_mulhi_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhi_epu16)|SSE2|intrin. h|_mm_mulhi_epu16 __m128i (\__m128i, \__m128i)|
|[_mm_mulhrs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhrs_epi16)|SSSE3|intrin. h|_mm_mulhrs_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_mullo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mullo_epi16)|SSE2|intrin. h|_mm_mullo_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_mullo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mullo_epi32)|SSE41|intrin. h|_mm_mullo_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_mwait](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mwait)|SSE3|intrin. h|void _mm_mwait (niepodpisane int, int bez znaku)|
|_mm_nmacc_pd|FMA4 [1]|ammintrin. h|__m128d _mm_nmacc_pd (\__m128d, \__m128d, \__m128d)|
|_mm_nmacc_ps|FMA4 [1]|ammintrin. h|__m128 _mm_nmacc_ps (\__m128, \__m128, \__m128)|
|_mm_nmacc_sd|FMA4 [1]|ammintrin. h|__m128d _mm_nmacc_sd (\__m128d, \__m128d, \__m128d)|
|_mm_nmacc_ss|FMA4 [1]|ammintrin. h|__m128 _mm_nmacc_ss (\__m128, \__m128, \__m128)|
|_mm_nmsub_pd|FMA4 [1]|ammintrin. h|__m128d _mm_nmsub_pd (\__m128d, \__m128d, \__m128d)|
|_mm_nmsub_ps|FMA4 [1]|ammintrin. h|__m128 _mm_nmsub_ps (\__m128, \__m128, \__m128)|
|_mm_nmsub_sd|FMA4 [1]|ammintrin. h|__m128d _mm_nmsub_sd (\__m128d, \__m128d, \__m128d)|
|_mm_nmsub_ss|FMA4 [1]|ammintrin. h|__m128 _mm_nmsub_ss (\__m128, \__m128, \__m128)|
|[_mm_or_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_pd)|SSE2|intrin. h|_mm_or_pd __m128d (\__m128d, \__m128d)|
|[_mm_or_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_ps)|SSE|intrin. h|_mm_or_ps __m128 (\__m128, \__m128)|
|[_mm_or_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_si128)|SSE2|intrin. h|_mm_or_si128 __m128i (\__m128i, \__m128i)|
|[_mm_packs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_epi16)|SSE2|intrin. h|_mm_packs_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_packs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_epi32)|SSE2|intrin. h|_mm_packs_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_packus_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packus_epi16)|SSE2|intrin. h|_mm_packus_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_packus_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packus_epi32)|SSE41|intrin. h|_mm_packus_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_pause](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_pause)|SSE2|intrin. h|void _mm_pause (void)|
|_mm_perm_epi8|XOP [1]|ammintrin. h|__m128i _mm_perm_epi8 (\__m128i, \__m128i, \__m128i)|
|[_mm_permute_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permute_pd)|AVX [2]|immintrin. h|_mm_permute_pd __m128d (\__m128d, int)|
|[_mm_permute_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permute_ps)|AVX [2]|immintrin. h|_mm_permute_ps __m128 (\__m128, int)|
|_mm_permute2_pd|XOP [1]|ammintrin. h|__m128d _mm_permute2_pd (\__m128d, \__m128d, \__m128i, int)|
|_mm_permute2_ps|XOP [1]|ammintrin. h|__m128 _mm_permute2_ps (\__m128, \__m128, \__m128i, int)|
|[_mm_permutevar_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permutevar_pd)|AVX [2]|immintrin. h|_mm_permutevar_pd __m128d (\__m128d, \__m128i)|
|[_mm_permutevar_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permutevar_ps)|AVX [2]|immintrin. h|_mm_permutevar_ps __m128 (\__m128, \__m128i)|
|[_mm_popcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_popcnt_u32)|POPCNT|intrin. h|int _mm_popcnt_u32 (liczba całkowita bez znaku)|
|[_mm_popcnt_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_popcnt_u64)|POPCNT|intrin. h|_mm_popcnt_u64 __int64 (niepodpisane \__int64)|
|[_mm_prefetch](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_prefetch)|SSE|intrin. h|void _mm_prefetch (znak\*, int)|
|[_mm_rcp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rcp_ps)|SSE|intrin. h|_mm_rcp_ps __m128 (\__m128)|
|[_mm_rcp_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rcp_ss)|SSE|intrin. h|_mm_rcp_ss __m128 (\__m128)|
|_mm_rot_epi16|XOP [1]|ammintrin. h|_mm_rot_epi16 __m128i (\__m128i, \__m128i)|
|_mm_rot_epi32|XOP [1]|ammintrin. h|_mm_rot_epi32 __m128i (\__m128i, \__m128i)|
|_mm_rot_epi64|XOP [1]|ammintrin. h|_mm_rot_epi64 __m128i (\__m128i, \__m128i)|
|_mm_rot_epi8|XOP [1]|ammintrin. h|_mm_rot_epi8 __m128i (\__m128i, \__m128i)|
|_mm_roti_epi16|XOP [1]|ammintrin. h|_mm_rot_epi16 __m128i (\__m128i, int)|
|_mm_roti_epi32|XOP [1]|ammintrin. h|_mm_rot_epi32 __m128i (\__m128i, int)|
|_mm_roti_epi64|XOP [1]|ammintrin. h|_mm_rot_epi64 __m128i (\__m128i, int)|
|_mm_roti_epi8|XOP [1]|ammintrin. h|_mm_rot_epi8 __m128i (\__m128i, int)|
|[_mm_round_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_pd)|SSE41|intrin. h|__m128d _mm_round_pd (\__m128d, const int)|
|[_mm_round_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_ps)|SSE41|intrin. h|__m128 _mm_round_ps (\__m128, const int)|
|[_mm_round_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_sd)|SSE41|intrin. h|__m128d _mm_round_sd (\__m128d, \__m128d, const int)|
|[_mm_round_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_ss)|SSE41|intrin. h|__m128 _mm_round_ss (\__m128, \__m128, const int)|
|[_mm_rsqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rsqrt_ps)|SSE|intrin. h|_mm_rsqrt_ps __m128 (\__m128)|
|[_mm_rsqrt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rsqrt_ss)|SSE|intrin. h|_mm_rsqrt_ss __m128 (\__m128)|
|[_mm_sad_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sad_epu8)|SSE2|intrin. h|_mm_sad_epu8 __m128i (\__m128i, \__m128i)|
|[_mm_set_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi16)|SSE2|intrin. h|__m128i _mm_set_epi16 (krótka, krótka, krótka, krótka, krótka i krótka)|
|[_mm_set_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi32)|SSE2|intrin. h|__m128i _mm_set_epi32 (int, int, int, int)|
|[_mm_set_epi64x](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi64x)|SSE2|intrin. h|_mm_set_epi64x __m128i (\__int64, \__int64)|
|[_mm_set_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi8)|SSE2|intrin. h|__m128i _mm_set_epi8 (Char, char, char, char, char, char, char, char, char, char, char, char, char, char, Char)|
|[_mm_set_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pd)|SSE2|intrin. h|__m128d _mm_set_pd (podwójna, podwójna)|
|[_mm_set_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ps)|SSE|intrin. h|__m128 _mm_set_ps (float, float, float, float)|
|[_mm_set_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ps1)|SSE|intrin. h|__m128 _mm_set_ps1 (float)|
|[_mm_set_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_sd)|SSE2|intrin. h|_mm_set_sd __m128d (Double)|
|[_mm_set_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ss)|SSE|intrin. h|__m128 _mm_set_ss (float)|
|[_mm_set1_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi16)|SSE2|intrin. h|__m128i _mm_set1_epi16 (krótki)|
|[_mm_set1_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi32)|SSE2|intrin. h|_mm_set1_epi32 __m128i (int)|
|[_mm_set1_epi64x](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi64x)|SSE2|intrin. h|_mm_set1_epi64x __m128i (\__int64)|
|[_mm_set1_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi8)|SSE2|intrin. h|__m128i _mm_set1_epi8 (Char)|
|[_mm_set1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pd)|SSE2|intrin. h|_mm_set1_pd __m128d (Double)|
|[_mm_setcsr](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setcsr)|SSE|intrin. h|void _mm_setcsr (bez znaku int)|
|_mm_setl_epi64|SSE2|intrin. h|_mm_setl_epi64 __m128i (\__m128i)|
|[_mm_setr_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi16)|SSE2|intrin. h|__m128i _mm_setr_epi16 (krótka, krótka, krótka, krótka, krótka i krótka)|
|[_mm_setr_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi32)|SSE2|intrin. h|__m128i _mm_setr_epi32 (int, int, int, int)|
|[_mm_setr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi8)|SSE2|intrin. h|__m128i _mm_setr_epi8 (Char, char, char, char, char, char, char, char, char, char, char, char, char, char, Char)|
|[_mm_setr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pd)|SSE2|intrin. h|__m128d _mm_setr_pd (podwójna, podwójna)|
|[_mm_setr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_ps)|SSE|intrin. h|__m128 _mm_setr_ps (float, float, float, float)|
|[_mm_setzero_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_pd)|SSE2|intrin. h|__m128d _mm_setzero_pd (void)|
|[_mm_setzero_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_ps)|SSE|intrin. h|__m128 _mm_setzero_ps (void)|
|[_mm_setzero_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_si128)|SSE2|intrin. h|__m128i _mm_setzero_si128 (void)|
|[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)|SSE|intrin. h|void _mm_sfence (void)|
|_mm_sha_epi16|XOP [1]|ammintrin. h|_mm_sha_epi16 __m128i (\__m128i, \__m128i)|
|_mm_sha_epi32|XOP [1]|ammintrin. h|_mm_sha_epi32 __m128i (\__m128i, \__m128i)|
|_mm_sha_epi64|XOP [1]|ammintrin. h|_mm_sha_epi64 __m128i (\__m128i, \__m128i)|
|_mm_sha_epi8|XOP [1]|ammintrin. h|_mm_sha_epi8 __m128i (\__m128i, \__m128i)|
|_mm_shl_epi16|XOP [1]|ammintrin. h|_mm_shl_epi16 __m128i (\__m128i, \__m128i)|
|_mm_shl_epi32|XOP [1]|ammintrin. h|_mm_shl_epi32 __m128i (\__m128i, \__m128i)|
|_mm_shl_epi64|XOP [1]|ammintrin. h|_mm_shl_epi64 __m128i (\__m128i, \__m128i)|
|_mm_shl_epi8|XOP [1]|ammintrin. h|_mm_shl_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_shuffle_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_epi32)|SSE2|intrin. h|_mm_shuffle_epi32 __m128i (\__m128i, int)|
|[_mm_shuffle_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_epi8)|SSSE3|intrin. h|_mm_shuffle_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_shuffle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_pd)|SSE2|intrin. h|__m128d _mm_shuffle_pd (\__m128d, \__m128d, int)|
|[_mm_shuffle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_ps)|SSE|intrin. h|__m128 _mm_shuffle_ps (\__m128, \__m128, niepodpisane int)|
|[_mm_shufflehi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shufflehi_epi16)|SSE2|intrin. h|_mm_shufflehi_epi16 __m128i (\__m128i, int)|
|[_mm_shufflelo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shufflelo_epi16)|SSE2|intrin. h|_mm_shufflelo_epi16 __m128i (\__m128i, int)|
|[_mm_sign_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi16)|SSSE3|intrin. h|_mm_sign_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_sign_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi32)|SSSE3|intrin. h|_mm_sign_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_sign_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi8)|SSSE3|intrin. h|_mm_sign_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_sll_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi16)|SSE2|intrin. h|_mm_sll_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_sll_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi32)|SSE2|intrin. h|_mm_sll_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_sll_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi64)|SSE2|intrin. h|_mm_sll_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_slli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi16)|SSE2|intrin. h|_mm_slli_epi16 __m128i (\__m128i, int)|
|[_mm_slli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi32)|SSE2|intrin. h|_mm_slli_epi32 __m128i (\__m128i, int)|
|[_mm_slli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi64)|SSE2|intrin. h|_mm_slli_epi64 __m128i (\__m128i, int)|
|[_mm_slli_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_si128)|SSE2|intrin. h|_mm_slli_si128 __m128i (\__m128i, int)|
|[_mm_sllv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sllv_epi32)|AVX2 [2]|immintrin. h|_mm_sllv_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_sllv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sllv_epi64)|AVX2 [2]|immintrin. h|_mm_sllv_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_sqrt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_pd)|SSE2|intrin. h|_mm_sqrt_pd __m128d (\__m128d)|
|[_mm_sqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_ps)|SSE|intrin. h|_mm_sqrt_ps __m128 (\__m128)|
|[_mm_sqrt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_sd)|SSE2|intrin. h|_mm_sqrt_sd __m128d (\__m128d, \__m128d)|
|[_mm_sqrt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_ss)|SSE|intrin. h|_mm_sqrt_ss __m128 (\__m128)|
|[_mm_sra_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_epi16)|SSE2|intrin. h|_mm_sra_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_sra_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_epi32)|SSE2|intrin. h|_mm_sra_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_srai_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_epi16)|SSE2|intrin. h|_mm_srai_epi16 __m128i (\__m128i, int)|
|[_mm_srai_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_epi32)|SSE2|intrin. h|_mm_srai_epi32 __m128i (\__m128i, int)|
|[_mm_srav_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srav_epi32)|AVX2 [2]|immintrin. h|_mm_srav_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_srl_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi16)|SSE2|intrin. h|_mm_srl_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_srl_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi32)|SSE2|intrin. h|_mm_srl_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_srl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi64)|SSE2|intrin. h|_mm_srl_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_srli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi16)|SSE2|intrin. h|_mm_srli_epi16 __m128i (\__m128i, int)|
|[_mm_srli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi32)|SSE2|intrin. h|_mm_srli_epi32 __m128i (\__m128i, int)|
|[_mm_srli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi64)|SSE2|intrin. h|_mm_srli_epi64 __m128i (\__m128i, int)|
|[_mm_srli_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_si128)|SSE2|intrin. h|_mm_srli_si128 __m128i (\__m128i, int)|
|[_mm_srlv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srlv_epi32)|AVX2 [2]|immintrin. h|_mm_srlv_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_srlv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srlv_epi64)|AVX2 [2]|immintrin. h|_mm_srlv_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_store_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_pd)|SSE2|intrin. h|void _mm_store_pd (Double\*, \__m128d)|
|[_mm_store_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ps)|SSE|intrin. h|void _mm_store_ps (zmiennoprzecinkowe\*, \__m128)|
|[_mm_store_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ps1)|SSE|intrin. h|void _mm_store_ps1 (zmiennoprzecinkowe\*, \__m128)|
|[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)|SSE2|intrin. h|void _mm_store_sd (Double\*, \__m128d)|
|[_mm_store_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_si128)|SSE2|intrin. h|void _mm_store_si128 (\__m128i\*, \__m128i)|
|[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)|SSE|intrin. h|void _mm_store_ss (zmiennoprzecinkowe\*, \__m128)|
|[_mm_store1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store1_pd)|SSE2|intrin. h|void _mm_store1_pd (Double\*, \__m128d)|
|[_mm_storeh_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeh_pd)|SSE2|intrin. h|void _mm_storeh_pd (Double\*, \__m128d)|
|[_mm_storeh_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeh_pi)|SSE|intrin. h|void _mm_storeh_pi (\__m64\*, \__m128)|
|[_mm_storel_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_epi64)|SSE2|intrin. h|void _mm_storel_epi64 (\__m128i\*, \__m128i)|
|[_mm_storel_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_pd)|SSE2|intrin. h|void _mm_storel_pd (Double\*, \__m128d)|
|[_mm_storel_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_pi)|SSE|intrin. h|void _mm_storel_pi (\__m64\*, \__m128)|
|[_mm_storer_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storer_pd)|SSE2|intrin. h|void _mm_storer_pd (Double\*, \__m128d)|
|[_mm_storer_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storer_ps)|SSE|intrin. h|void _mm_storer_ps (zmiennoprzecinkowe\*, \__m128)|
|[_mm_storeu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_pd)|SSE2|intrin. h|void _mm_storeu_pd (Double\*, \__m128d)|
|[_mm_storeu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_ps)|SSE|intrin. h|void _mm_storeu_ps (zmiennoprzecinkowe\*, \__m128)|
|[_mm_storeu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_si128)|SSE2|intrin. h|void _mm_storeu_si128 (\__m128i\*, \__m128i)|
|[_mm_stream_load_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_load_si128)|SSE41|intrin. h|_mm_stream_load_si128 __m128i (\__m128i\*)|
|[_mm_stream_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_pd)|SSE2|intrin. h|void _mm_stream_pd (Double\*, \__m128d)|
|[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)|SSE|intrin. h|void _mm_stream_ps (zmiennoprzecinkowe\*, \__m128)|
|[_mm_stream_sd](mm-stream-sd.md)|SSE4a|intrin. h|void _mm_stream_sd (Double\*, \__m128d)|
|[_mm_stream_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_si128)|SSE2|intrin. h|void _mm_stream_si128 (\__m128i\*, \__m128i)|
|[_mm_stream_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_si32)|SSE2|intrin. h|void _mm_stream_si32 (int\*, int)|
|[_mm_stream_si64x](mm-stream-si64x.md)|SSE2|intrin. h|void _mm_stream_si64x (\__int64 \*, \__int64)|
|[_mm_stream_ss](mm-stream-ss.md)|SSE4a|intrin. h|void _mm_stream_ss (zmiennoprzecinkowe\*, \__m128)|
|[_mm_sub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi16)|SSE2|intrin. h|_mm_sub_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_sub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi32)|SSE2|intrin. h|_mm_sub_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_sub_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi64)|SSE2|intrin. h|_mm_sub_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_sub_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi8)|SSE2|intrin. h|_mm_sub_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_sub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pd)|SSE2|intrin. h|_mm_sub_pd __m128d (\__m128d, \__m128d)|
|[_mm_sub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_ps)|SSE|intrin. h|_mm_sub_ps __m128 (\__m128, \__m128)|
|[_mm_sub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_sd)|SSE2|intrin. h|_mm_sub_sd __m128d (\__m128d, \__m128d)|
|[_mm_sub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_ss)|SSE|intrin. h|_mm_sub_ss __m128 (\__m128, \__m128)|
|[_mm_subs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epi16)|SSE2|intrin. h|_mm_subs_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_subs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epi8)|SSE2|intrin. h|_mm_subs_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_subs_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epu16)|SSE2|intrin. h|_mm_subs_epu16 __m128i (\__m128i, \__m128i)|
|[_mm_subs_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epu8)|SSE2|intrin. h|_mm_subs_epu8 __m128i (\__m128i, \__m128i)|
|[_mm_testc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_pd)|AVX [2]|immintrin. h|int _mm_testc_pd (\__m128d, \__m128d)|
|[_mm_testc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_ps)|AVX [2]|immintrin. h|int _mm_testc_ps (\__m128, \__m128)|
|[_mm_testc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_si128)|SSE41|intrin. h|int _mm_testc_si128 (\__m128i, \__m128i)|
|[_mm_testnzc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_pd)|AVX [2]|immintrin. h|int _mm_testnzc_pd (\__m128d, \__m128d)|
|[_mm_testnzc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_ps)|AVX [2]|immintrin. h|int _mm_testnzc_ps (\__m128, \__m128)|
|[_mm_testnzc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_si128)|SSE41|intrin. h|int _mm_testnzc_si128 (\__m128i, \__m128i)|
|[_mm_testz_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_pd)|AVX [2]|immintrin. h|int _mm_testz_pd (\__m128d, \__m128d)|
|[_mm_testz_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_ps)|AVX [2]|immintrin. h|int _mm_testz_ps (\__m128, \__m128)|
|[_mm_testz_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_si128)|SSE41|intrin. h|int _mm_testz_si128 (\__m128i, \__m128i)|
|[_mm_ucomieq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomieq_sd)|SSE2|intrin. h|int _mm_ucomieq_sd (\__m128d, \__m128d)|
|[_mm_ucomieq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomieq_ss)|SSE|intrin. h|int _mm_ucomieq_ss (\__m128, \__m128)|
|[_mm_ucomige_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomige_sd)|SSE2|intrin. h|int _mm_ucomige_sd (\__m128d, \__m128d)|
|[_mm_ucomige_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomige_ss)|SSE|intrin. h|int _mm_ucomige_ss (\__m128, \__m128)|
|[_mm_ucomigt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomigt_sd)|SSE2|intrin. h|int _mm_ucomigt_sd (\__m128d, \__m128d)|
|[_mm_ucomigt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomigt_ss)|SSE|intrin. h|int _mm_ucomigt_ss (\__m128, \__m128)|
|[_mm_ucomile_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomile_sd)|SSE2|intrin. h|int _mm_ucomile_sd (\__m128d, \__m128d)|
|[_mm_ucomile_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomile_ss)|SSE|intrin. h|int _mm_ucomile_ss (\__m128, \__m128)|
|[_mm_ucomilt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomilt_sd)|SSE2|intrin. h|int _mm_ucomilt_sd (\__m128d, \__m128d)|
|[_mm_ucomilt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomilt_ss)|SSE|intrin. h|int _mm_ucomilt_ss (\__m128, \__m128)|
|[_mm_ucomineq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomineq_sd)|SSE2|intrin. h|int _mm_ucomineq_sd (\__m128d, \__m128d)|
|[_mm_ucomineq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomineq_ss)|SSE|intrin. h|int _mm_ucomineq_ss (\__m128, \__m128)|
|[_mm_unpackhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi16)|SSE2|intrin. h|_mm_unpackhi_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_unpackhi_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi32)|SSE2|intrin. h|_mm_unpackhi_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_unpackhi_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi64)|SSE2|intrin. h|_mm_unpackhi_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_unpackhi_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi8)|SSE2|intrin. h|_mm_unpackhi_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_unpackhi_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pd)|SSE2|intrin. h|_mm_unpackhi_pd __m128d (\__m128d, \__m128d)|
|[_mm_unpackhi_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_ps)|SSE|intrin. h|_mm_unpackhi_ps __m128 (\__m128, \__m128)|
|[_mm_unpacklo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi16)|SSE2|intrin. h|_mm_unpacklo_epi16 __m128i (\__m128i, \__m128i)|
|[_mm_unpacklo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi32)|SSE2|intrin. h|_mm_unpacklo_epi32 __m128i (\__m128i, \__m128i)|
|[_mm_unpacklo_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi64)|SSE2|intrin. h|_mm_unpacklo_epi64 __m128i (\__m128i, \__m128i)|
|[_mm_unpacklo_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi8)|SSE2|intrin. h|_mm_unpacklo_epi8 __m128i (\__m128i, \__m128i)|
|[_mm_unpacklo_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pd)|SSE2|intrin. h|_mm_unpacklo_pd __m128d (\__m128d, \__m128d)|
|[_mm_unpacklo_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_ps)|SSE|intrin. h|_mm_unpacklo_ps __m128 (\__m128, \__m128)|
|[_mm_xor_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_pd)|SSE2|intrin. h|_mm_xor_pd __m128d (\__m128d, \__m128d)|
|[_mm_xor_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_ps)|SSE|intrin. h|_mm_xor_ps __m128 (\__m128, \__m128)|
|[_mm_xor_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_si128)|SSE2|intrin. h|_mm_xor_si128 __m128i (\__m128i, \__m128i)|
|[_mm256_abs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi16)|AVX2 [2]|immintrin. h|_mm256_abs_epi16 __m256i (\__m256i)|
|[_mm256_abs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi32)|AVX2 [2]|immintrin. h|_mm256_abs_epi32 __m256i (\__m256i)|
|[_mm256_abs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi8)|AVX2 [2]|immintrin. h|_mm256_abs_epi8 __m256i (\__m256i)|
|[_mm256_add_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi16)|AVX2 [2]|immintrin. h|_mm256_add_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_add_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi32)|AVX2 [2]|immintrin. h|_mm256_add_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_add_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi64)|AVX2 [2]|immintrin. h|_mm256_add_epi64 __m256i (\__m256i, \__m256i)|
|[_mm256_add_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi8)|AVX2 [2]|immintrin. h|_mm256_add_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_add_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_pd)|AVX [2]|immintrin. h|_mm256_add_pd __m256d (\__m256d, \__m256d)|
|[_mm256_add_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_ps)|AVX [2]|immintrin. h|_mm256_add_ps __m256 (\__m256, \__m256)|
|[_mm256_adds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epi16)|AVX2 [2]|immintrin. h|_mm256_adds_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_adds_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epi8)|AVX2 [2]|immintrin. h|_mm256_adds_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_adds_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epu16)|AVX2 [2]|immintrin. h|_mm256_adds_epu16 __m256i (\__m256i, \__m256i)|
|[_mm256_adds_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epu8)|AVX2 [2]|immintrin. h|_mm256_adds_epu8 __m256i (\__m256i, \__m256i)|
|[_mm256_addsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_addsub_pd)|AVX [2]|immintrin. h|_mm256_addsub_pd __m256d (\__m256d, \__m256d)|
|[_mm256_addsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_addsub_ps)|AVX [2]|immintrin. h|_mm256_addsub_ps __m256 (\__m256, \__m256)|
|[_mm256_alignr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_alignr_epi8)|AVX2 [2]|immintrin. h|__m256i _mm256_alignr_epi8 (\__m256i, \__m256i, const int)|
|[_mm256_and_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_pd)|AVX [2]|immintrin. h|_mm256_and_pd __m256d (\__m256d, \__m256d)|
|[_mm256_and_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_ps)|AVX [2]|immintrin. h|_mm256_and_ps __m256 (\__m256, \__m256)|
|[_mm256_and_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_si256)|AVX2 [2]|immintrin. h|_mm256_and_si256 __m256i (\__m256i, \__m256i)|
|[_mm256_andnot_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_pd)|AVX [2]|immintrin. h|_mm256_andnot_pd __m256d (\__m256d, \__m256d)|
|[_mm256_andnot_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_ps)|AVX [2]|immintrin. h|_mm256_andnot_ps __m256 (\__m256, \__m256)|
|[_mm256_andnot_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_si256)|AVX2 [2]|immintrin. h|_mm256_andnot_si256 __m256i (\__m256i, \__m256i)|
|[_mm256_avg_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_avg_epu16)|AVX2 [2]|immintrin. h|_mm256_avg_epu16 __m256i (\__m256i, \__m256i)|
|[_mm256_avg_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_avg_epu8)|AVX2 [2]|immintrin. h|_mm256_avg_epu8 __m256i (\__m256i, \__m256i)|
|[_mm256_blend_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_epi16)|AVX2 [2]|immintrin. h|__m256i _mm256_blend_epi16 (\__m256i, \__m256i, const int)|
|[_mm256_blend_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_epi32)|AVX2 [2]|immintrin. h|__m256i _mm256_blend_epi32 (\__m256i, \__m256i, const int)|
|[_mm256_blend_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_pd)|AVX [2]|immintrin. h|__m256d _mm256_blend_pd (\__m256d, \__m256d, const int)|
|[_mm256_blend_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_ps)|AVX [2]|immintrin. h|__m256 _mm256_blend_ps (\__m256, \__m256, const int)|
|[_mm256_blendv_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_epi8)|AVX2 [2]|immintrin. h|__m256i _mm256_blendv_epi8 (\__m256i, \__m256i, \__m256i)|
|[_mm256_blendv_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_pd)|AVX [2]|immintrin. h|__m256d _mm256_blendv_pd (\__m256d, \__m256d, \__m256d)|
|[_mm256_blendv_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_ps)|AVX [2]|immintrin. h|__m256 _mm256_blendv_ps (\__m256, \__m256, \__m256)|
|[_mm256_broadcast_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_pd)|AVX [2]|immintrin. h|_mm256_broadcast_pd __m256d (\__m128d const \*)|
|[_mm256_broadcast_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_ps)|AVX [2]|immintrin. h|_mm256_broadcast_ps __m256 (\__m128 const \*)|
|[_mm256_broadcast_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_sd)|AVX [2]|immintrin. h|_mm256_broadcast_sd __m256d (podwójna stała \*)|
|[_mm256_broadcast_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_ss)|AVX [2]|immintrin. h|__m256 _mm256_broadcast_ss (float const \*)|
|[_mm256_broadcastb_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastb_epi8)|AVX2 [2]|immintrin. h|_mm256_broadcastb_epi8 __m256i (\__m128i)|
|[_mm256_broadcastd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastd_epi32)|AVX2 [2]|immintrin. h|_mm256_broadcastd_epi32 __m256i (\__m128i)|
|[_mm256_broadcastq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastq_epi64)|AVX2 [2]|immintrin. h|_mm256_broadcastq_epi64 __m256i (\__m128i)|
|[_mm256_broadcastsd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastsd_pd)|AVX2 [2]|immintrin. h|_mm256_broadcastsd_pd __m256d (\__m128d)|
|[_mm256_broadcastsi128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastsi128_si256)|AVX2 [2]|immintrin. h|_mm256_broadcastsi128_si256 __m256i (\__m128i)|
|[_mm256_broadcastss_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastss_ps)|AVX2 [2]|immintrin. h|_mm256_broadcastss_ps __m256 (\__m128)|
|[_mm256_broadcastw_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastw_epi16)|AVX2 [2]|immintrin. h|_mm256_broadcastw_epi16 __m256i (\__m128i)|
|[_mm256_castpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd_ps)|AVX [2]|immintrin. h|_mm256_castpd_ps __m256 (\__m256d)|
|[_mm256_castpd_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd_si256)|AVX [2]|immintrin. h|_mm256_castpd_si256 __m256i (\__m256d)|
|[_mm256_castpd128_pd256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd128_pd256)|AVX [2]|immintrin. h|_mm256_castpd128_pd256 __m256d (\__m128d)|
|[_mm256_castpd256_pd128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd256_pd128)|AVX [2]|immintrin. h|_mm256_castpd256_pd128 __m128d (\__m256d)|
|[_mm256_castps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps_pd)|AVX [2]|immintrin. h|_mm256_castps_pd __m256d (\__m256)|
|[_mm256_castps_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps_si256)|AVX [2]|immintrin. h|_mm256_castps_si256 __m256i (\__m256)|
|[_mm256_castps128_ps256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps128_ps256)|AVX [2]|immintrin. h|_mm256_castps128_ps256 __m256 (\__m128)|
|[_mm256_castps256_ps128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps256_ps128)|AVX [2]|immintrin. h|_mm256_castps256_ps128 __m128 (\__m256)|
|[_mm256_castsi128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi128_si256)|AVX [2]|immintrin. h|_mm256_castsi128_si256 __m256i (\__m128i)|
|[_mm256_castsi256_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_pd)|AVX [2]|immintrin. h|_mm256_castsi256_pd __m256d (\__m256i)|
|[_mm256_castsi256_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_ps)|AVX [2]|immintrin. h|_mm256_castsi256_ps __m256 (\__m256i)|
|[_mm256_castsi256_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_si128)|AVX [2]|immintrin. h|_mm256_castsi256_si128 __m128i (\__m256i)|
|_mm256_cmov_si256|XOP [1]|ammintrin. h|__m256i _mm256_cmov_si256 (\__m256i, \__m256i, \__m256i)|
|[_mm256_cmp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmp_pd)|AVX [2]|immintrin. h|__m256d _mm256_cmp_pd (\__m256d, \__m256d, const int)|
|[_mm256_cmp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmp_ps)|AVX [2]|immintrin. h|__m256 _mm256_cmp_ps (\__m256, \__m256, const int)|
|[_mm256_cmpeq_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi16)|AVX2 [2]|immintrin. h|_mm256_cmpeq_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_cmpeq_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi32)|AVX2 [2]|immintrin. h|_mm256_cmpeq_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_cmpeq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi64)|AVX2 [2]|immintrin. h|_mm256_cmpeq_epi64 __m256i (\__m256i, \__m256i)|
|[_mm256_cmpeq_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi8)|AVX2 [2]|immintrin. h|_mm256_cmpeq_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_cmpgt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi16)|AVX2 [2]|immintrin. h|_mm256_cmpgt_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_cmpgt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi32)|AVX2 [2]|immintrin. h|_mm256_cmpgt_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_cmpgt_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi64)|AVX2 [2]|immintrin. h|_mm256_cmpgt_epi64 __m256i (\__m256i, \__m256i)|
|[_mm256_cmpgt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi8)|AVX2 [2]|immintrin. h|_mm256_cmpgt_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_cvtepi16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi16_epi32)|AVX2 [2]|immintrin. h|_mm256_cvtepi16_epi32 __m256i (\__m128i)|
|[_mm256_cvtepi16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi16_epi64)|AVX2 [2]|immintrin. h|_mm256_cvtepi16_epi64 __m256i (\__m128i)|
|[_mm256_cvtepi32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_epi64)|AVX2 [2]|immintrin. h|_mm256_cvtepi32_epi64 __m256i (\__m128i)|
|[_mm256_cvtepi32_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_pd)|AVX [2]|immintrin. h|_mm256_cvtepi32_pd __m256d (\__m128i)|
|[_mm256_cvtepi32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_ps)|AVX [2]|immintrin. h|_mm256_cvtepi32_ps __m256 (\__m256i)|
|[_mm256_cvtepi8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi16)|AVX2 [2]|immintrin. h|_mm256_cvtepi8_epi16 __m256i (\__m128i)|
|[_mm256_cvtepi8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi32)|AVX2 [2]|immintrin. h|_mm256_cvtepi8_epi32 __m256i (\__m128i)|
|[_mm256_cvtepi8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi64)|AVX2 [2]|immintrin. h|_mm256_cvtepi8_epi64 __m256i (\__m128i)|
|[_mm256_cvtepu16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu16_epi32)|AVX2 [2]|immintrin. h|_mm256_cvtepu16_epi32 __m256i (\__m128i)|
|[_mm256_cvtepu16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu16_epi64)|AVX2 [2]|immintrin. h|_mm256_cvtepu16_epi64 __m256i (\__m128i)|
|[_mm256_cvtepu32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu32_epi64)|AVX2 [2]|immintrin. h|_mm256_cvtepu32_epi64 __m256i (\__m128i)|
|[_mm256_cvtepu8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi16)|AVX2 [2]|immintrin. h|_mm256_cvtepu8_epi16 __m256i (\__m128i)|
|[_mm256_cvtepu8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi32)|AVX2 [2]|immintrin. h|_mm256_cvtepu8_epi32 __m256i (\__m128i)|
|[_mm256_cvtepu8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi64)|AVX2 [2]|immintrin. h|_mm256_cvtepu8_epi64 __m256i (\__m128i)|
|[_mm256_cvtpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtpd_epi32)|AVX [2]|immintrin. h|_mm256_cvtpd_epi32 __m128i (\__m256d)|
|[_mm256_cvtpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtpd_ps)|AVX [2]|immintrin. h|_mm256_cvtpd_ps __m128 (\__m256d)|
|[_mm256_cvtph_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtph_ps)|F16C [2]|immintrin. h|_mm256_cvtph_ps __m256 (\__m128i)|
|[_mm256_cvtps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_epi32)|AVX [2]|immintrin. h|_mm256_cvtps_epi32 __m256i (\__m256)|
|[_mm256_cvtps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_pd)|AVX [2]|immintrin. h|_mm256_cvtps_pd __m256d (\__m128)|
|[_mm256_cvtps_ph](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_ph)|F16C [2]|immintrin. h|__m128i _mm256_cvtps_ph (\__m256, const int)|
|[_mm256_cvttpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvttpd_epi32)|AVX [2]|immintrin. h|_mm256_cvttpd_epi32 __m128i (\__m256d)|
|[_mm256_cvttps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvttps_epi32)|AVX [2]|immintrin. h|_mm256_cvttps_epi32 __m256i (\__m256)|
|[_mm256_div_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_div_pd)|AVX [2]|immintrin. h|_mm256_div_pd __m256d (\__m256d, \__m256d)|
|[_mm256_div_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_div_ps)|AVX [2]|immintrin. h|_mm256_div_ps __m256 (\__m256, \__m256)|
|[_mm256_dp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_dp_ps)|AVX [2]|immintrin. h|__m256 _mm256_dp_ps (\__m256, \__m256, const int)|
|[_mm256_extractf128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_pd)|AVX [2]|immintrin. h|__m128d _mm256_extractf128_pd (\__m256d, const int)|
|[_mm256_extractf128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_ps)|AVX [2]|immintrin. h|__m128 _mm256_extractf128_ps (\__m256, const int)|
|[_mm256_extractf128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_si256)|AVX [2]|immintrin. h|__m128i _mm256_extractf128_si256 (\__m256i, const int)|
|[_mm256_extracti128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extracti128_si256)|AVX2 [2]|immintrin. h|_mm256_extracti128_si256 __m128i (\__m256i, int)|
|[_mm256_fmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmadd_pd)|FMA [2]|immintrin. h|__m256d _mm256_fmadd_pd (\__m256d, \__m256d, \__m256d)|
|[_mm256_fmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmadd_ps)|FMA [2]|immintrin. h|__m256 _mm256_fmadd_ps (\__m256, \__m256, \__m256)|
|[_mm256_fmaddsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmaddsub_pd)|FMA [2]|immintrin. h|__m256d _mm256_fmaddsub_pd (\__m256d, \__m256d, \__m256d)|
|[_mm256_fmaddsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmaddsub_ps)|FMA [2]|immintrin. h|__m256 _mm256_fmaddsub_ps (\__m256, \__m256, \__m256)|
|[_mm256_fmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsub_pd)|FMA [2]|immintrin. h|__m256d _mm256_fmsub_pd (\__m256d, \__m256d, \__m256d)|
|[_mm256_fmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsub_ps)|FMA [2]|immintrin. h|__m256 _mm256_fmsub_ps (\__m256, \__m256, \__m256)|
|[_mm256_fmsubadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsubadd_pd)|FMA [2]|immintrin. h|__m256d _mm256_fmsubadd_pd (\__m256d, \__m256d, \__m256d)|
|[_mm256_fmsubadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsubadd_ps)|FMA [2]|immintrin. h|__m256 _mm256_fmsubadd_ps (\__m256, \__m256, \__m256)|
|[_mm256_fnmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmadd_pd)|FMA [2]|immintrin. h|__m256d _mm256_fnmadd_pd (\__m256d, \__m256d, \__m256d)|
|[_mm256_fnmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmadd_ps)|FMA [2]|immintrin. h|__m256 _mm256_fnmadd_ps (\__m256, \__m256, \__m256)|
|[_mm256_fnmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmsub_pd)|FMA [2]|immintrin. h|__m256d _mm256_fnmsub_pd (\__m256d, \__m256d, \__m256d)|
|[_mm256_fnmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmsub_ps)|FMA [2]|immintrin. h|__m256 _mm256_fnmsub_ps (\__m256, \__m256, \__m256)|
|_mm256_frcz_pd|XOP [1]|ammintrin. h|_mm256_frcz_pd __m256d (\__m256d)|
|_mm256_frcz_ps|XOP [1]|ammintrin. h|_mm256_frcz_ps __m256 (\__m256)|
|[_mm256_hadd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_epi16)|AVX2 [2]|immintrin. h|_mm256_hadd_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_hadd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_epi32)|AVX2 [2]|immintrin. h|_mm256_hadd_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_hadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_pd)|AVX [2]|immintrin. h|_mm256_hadd_pd __m256d (\__m256d, \__m256d)|
|[_mm256_hadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_ps)|AVX [2]|immintrin. h|_mm256_hadd_ps __m256 (\__m256, \__m256)|
|[_mm256_hadds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadds_epi16)|AVX2 [2]|immintrin. h|_mm256_hadds_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_hsub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_epi16)|AVX2 [2]|immintrin. h|_mm256_hsub_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_hsub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_epi32)|AVX2 [2]|immintrin. h|_mm256_hsub_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_hsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_pd)|AVX [2]|immintrin. h|_mm256_hsub_pd __m256d (\__m256d, \__m256d)|
|[_mm256_hsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_ps)|AVX [2]|immintrin. h|_mm256_hsub_ps __m256 (\__m256, \__m256)|
|[_mm256_hsubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsubs_epi16)|AVX2 [2]|immintrin. h|_mm256_hsubs_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_epi32)|AVX2 [2]|immintrin. h|__m256i _mm256_i32gather_epi32 (int const \*, \__m256i, const int)|
|[_mm256_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_epi64)|AVX2 [2]|immintrin. h|__m256i _mm256_i32gather_epi64 (\__int64 const \*, \__m128i, const int)|
|[_mm256_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_pd)|AVX2 [2]|immintrin. h|__m256d _mm256_i32gather_pd (podwójna stała \*, \__m128i, const int)|
|[_mm256_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_ps)|AVX2 [2]|immintrin. h|__m256 _mm256_i32gather_ps (float const \*, \__m256i, const int)|
|[_mm256_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_epi32)|AVX2 [2]|immintrin. h|__m256i _mm256_i64gather_epi32 (int const \*, \__m256i, const int)|
|[_mm256_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_epi64)|AVX2 [2]|immintrin. h|__m256i _mm256_i64gather_epi64 (\__int64 const \*, \__m256i, const int)|
|[_mm256_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_pd)|AVX2 [2]|immintrin. h|__m256d _mm256_i64gather_pd (podwójna stała \*, \__m256i, const int)|
|[_mm256_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_ps)|AVX2 [2]|immintrin. h|__m128 _mm256_i64gather_ps (float const \*, \__m256i, const int)|
|[_mm256_insertf128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_pd)|AVX [2]|immintrin. h|__m256d _mm256_insertf128_pd (\__m256d, \__m128d, int)|
|[_mm256_insertf128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_ps)|AVX [2]|immintrin. h|__m256 _mm256_insertf128_ps (\__m256, \__m128, int)|
|[_mm256_insertf128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_si256)|AVX [2]|immintrin. h|__m256i _mm256_insertf128_si256 (\__m256i, \__m128i, int)|
|[_mm256_inserti128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_inserti128_si256)|AVX2 [2]|immintrin. h|__m256i _mm256_inserti128_si256 (\__m256i, \__m128i, int)|
|[_mm256_lddqu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_lddqu_si256)|AVX [2]|immintrin. h|_mm256_lddqu_si256 __m256i (\__m256i \*)|
|[_mm256_load_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_pd)|AVX [2]|immintrin. h|_mm256_load_pd __m256d (podwójna stała \*)|
|[_mm256_load_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_ps)|AVX [2]|immintrin. h|__m256 _mm256_load_ps (float const \*)|
|[_mm256_load_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_si256)|AVX [2]|immintrin. h|_mm256_load_si256 __m256i (\__m256i \*)|
|[_mm256_loadu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_pd)|AVX [2]|immintrin. h|_mm256_loadu_pd __m256d (podwójna stała \*)|
|[_mm256_loadu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_ps)|AVX [2]|immintrin. h|__m256 _mm256_loadu_ps (float const \*)|
|[_mm256_loadu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_si256)|AVX [2]|immintrin. h|_mm256_loadu_si256 __m256i (\__m256i \*)|
|_mm256_macc_pd|FMA4 [1]|ammintrin. h|__m256d _mm_macc_pd (\__m256d, \__m256d, \__m256d)|
|_mm256_macc_ps|FMA4 [1]|ammintrin. h|__m256 _mm_macc_ps (\__m256, \__m256, \__m256)|
|[_mm256_madd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_madd_epi16)|AVX2 [2]|immintrin. h|_mm256_madd_epi16 __m256i (\__m256i, \__m256i)|
|_mm256_maddsub_pd|FMA4 [1]|ammintrin. h|__m256d _mm_maddsub_pd (\__m256d, \__m256d, \__m256d)|
|_mm256_maddsub_ps|FMA4 [1]|ammintrin. h|__m256 _mm_maddsub_ps (\__m256, \__m256, \__m256)|
|[_mm256_maddubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maddubs_epi16)|AVX2 [2]|immintrin. h|_mm256_maddubs_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_mask_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_epi32)|AVX2 [2]|immintrin. h|__m256i _mm256_mask_i32gather_epi32 (\__m256i, int const \*, \__m256i, \__m256i, const int)|
|[_mm256_mask_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_epi64)|AVX2 [2]|immintrin. h|__m256i _mm256_mask_i32gather_epi64 (\__m256i, \__int64 const \\*, \__m128i, \__m256i, const int)|
|[_mm256_mask_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_pd)|AVX2 [2]|immintrin. h|__m256d _mm256_mask_i32gather_pd (\__m256d, podwójne stałe \*, \__m128i, \__m256d, const int)|
|[_mm256_mask_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_ps)|AVX2 [2]|immintrin. h|__m256 _mm256_mask_i32gather_ps (\__m256, float const \*, \__m256i, \__m256, const int)|
|[_mm256_mask_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_epi32)|AVX2 [2]|immintrin. h|__m128i _mm256_mask_i64gather_epi32 (\__m128i, int const \*, \__m256i, \__m128i, const int)|
|[_mm256_mask_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_epi64)|AVX2 [2]|immintrin. h|__m256i _mm256_mask_i64gather_epi64 (\__m256i, \__int64 const \*, \__m256i, \__m256i, const int)|
|[_mm256_mask_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_pd)|AVX2 [2]|immintrin. h|__m256d _mm256_mask_i64gather_pd (\__m256d, podwójne stałe \*, \__m256i, \__m256d, const int)|
|[_mm256_mask_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_ps)|AVX2 [2]|immintrin. h|__m128 _mm256_mask_i64gather_ps (\__m128, float const \*, \__m256i, \__m128, const int)|
|[_mm256_maskload_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_epi32)|AVX2 [2]|immintrin. h|__m256i _mm256_maskload_epi32 (int const \*, \__m256i)|
|[_mm256_maskload_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_epi64)|AVX2 [2]|immintrin. h|_mm256_maskload_epi64 __m256i (\__int64 const \*, \__m256i)|
|[_mm256_maskload_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_pd)|AVX [2]|immintrin. h|__m256d _mm256_maskload_pd (podwójna \*stała, \__m256i)|
|[_mm256_maskload_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_ps)|AVX [2]|immintrin. h|__m256 _mm256_maskload_ps (float const \*, \__m256i)|
|[_mm256_maskstore_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_epi32)|AVX2 [2]|immintrin. h|void _mm256_maskstore_epi32 (int \*, \__m256i, \__m256i)|
|[_mm256_maskstore_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_epi64)|AVX2 [2]|immintrin. h|void _mm256_maskstore_epi64 (\__int64 \*, \__m256i, \__m256i)|
|[_mm256_maskstore_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_pd)|AVX [2]|immintrin. h|void _mm256_maskstore_pd (podwójna \*, \__m256i, \__m256d)|
|[_mm256_maskstore_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_ps)|AVX [2]|immintrin. h|void _mm256_maskstore_ps (\*zmiennoprzecinkowych, \__m256i, \__m256)|
|[_mm256_max_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi16)|AVX2 [2]|immintrin. h|_mm256_max_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_max_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi32)|AVX2 [2]|immintrin. h|_mm256_max_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_max_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi8)|AVX2 [2]|immintrin. h|_mm256_max_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_max_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu16)|AVX2 [2]|immintrin. h|_mm256_max_epu16 __m256i (\__m256i, \__m256i)|
|[_mm256_max_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu32)|AVX2 [2]|immintrin. h|_mm256_max_epu32 __m256i (\__m256i, \__m256i)|
|[_mm256_max_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu8)|AVX2 [2]|immintrin. h|_mm256_max_epu8 __m256i (\__m256i, \__m256i)|
|[_mm256_max_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_pd)|AVX [2]|immintrin. h|_mm256_max_pd __m256d (\__m256d, \__m256d)|
|[_mm256_max_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_ps)|AVX [2]|immintrin. h|_mm256_max_ps __m256 (\__m256, \__m256)|
|[_mm256_min_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi16)|AVX2 [2]|immintrin. h|_mm256_min_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_min_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi32)|AVX2 [2]|immintrin. h|_mm256_min_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_min_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi8)|AVX2 [2]|immintrin. h|_mm256_min_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_min_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu16)|AVX2 [2]|immintrin. h|_mm256_min_epu16 __m256i (\__m256i, \__m256i)|
|[_mm256_min_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu32)|AVX2 [2]|immintrin. h|_mm256_min_epu32 __m256i (\__m256i, \__m256i)|
|[_mm256_min_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu8)|AVX2 [2]|immintrin. h|_mm256_min_epu8 __m256i (\__m256i, \__m256i)|
|[_mm256_min_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_pd)|AVX [2]|immintrin. h|_mm256_min_pd __m256d (\__m256d, \__m256d)|
|[_mm256_min_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_ps)|AVX [2]|immintrin. h|_mm256_min_ps __m256 (\__m256, \__m256)|
|[_mm256_movedup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movedup_pd)|AVX [2]|immintrin. h|_mm256_movedup_pd __m256d (\__m256d)|
|[_mm256_movehdup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movehdup_ps)|AVX [2]|immintrin. h|_mm256_movehdup_ps __m256 (\__m256)|
|[_mm256_moveldup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_moveldup_ps)|AVX [2]|immintrin. h|_mm256_moveldup_ps __m256 (\__m256)|
|[_mm256_movemask_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_epi8)|AVX2 [2]|immintrin. h|int _mm256_movemask_epi8 (\__m256i)|
|[_mm256_movemask_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_pd)|AVX [2]|immintrin. h|int _mm256_movemask_pd (\__m256d)|
|[_mm256_movemask_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_ps)|AVX [2]|immintrin. h|int _mm256_movemask_ps (\__m256)|
|[_mm256_mpsadbw_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mpsadbw_epu8)|AVX2 [2]|immintrin. h|__m256i _mm256_mpsadbw_epu8 (\__m256i, \__m256i, const int)|
|_mm256_msub_pd|FMA4 [1]|ammintrin. h|__m256d _mm_msub_pd (\__m256d, \__m256d, \__m256d)|
|_mm256_msub_ps|FMA4 [1]|ammintrin. h|__m256 _mm_msub_ps (\__m256, \__m256, \__m256)|
|_mm256_msubadd_pd|FMA4 [1]|ammintrin. h|__m256d _mm_msubadd_pd (\__m256d, \__m256d, \__m256d)|
|_mm256_msubadd_ps|FMA4 [1]|ammintrin. h|__m256 _mm_msubadd_ps (\__m256, \__m256, \__m256)|
|[_mm256_mul_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_epi32)|AVX2 [2]|immintrin. h|_mm256_mul_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_mul_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_epu32)|AVX2 [2]|immintrin. h|_mm256_mul_epu32 __m256i (\__m256i, \__m256i)|
|[_mm256_mul_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_pd)|AVX [2]|immintrin. h|_mm256_mul_pd __m256d (\__m256d, \__m256d)|
|[_mm256_mul_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_ps)|AVX [2]|immintrin. h|_mm256_mul_ps __m256 (\__m256, \__m256)|
|[_mm256_mulhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhi_epi16)|AVX2 [2]|immintrin. h|_mm256_mulhi_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_mulhi_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhi_epu16)|AVX2 [2]|immintrin. h|_mm256_mulhi_epu16 __m256i (\__m256i, \__m256i)|
|[_mm256_mulhrs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhrs_epi16)|AVX2 [2]|immintrin. h|_mm256_mulhrs_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_mullo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mullo_epi16)|AVX2 [2]|immintrin. h|_mm256_mullo_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_mullo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mullo_epi32)|AVX2 [2]|immintrin. h|_mm256_mullo_epi32 __m256i (\__m256i, \__m256i)|
|_mm256_nmacc_pd|FMA4 [1]|ammintrin. h|__m256d _mm_nmacc_pd (\__m256d, \__m256d, \__m256d)|
|_mm256_nmacc_ps|FMA4 [1]|ammintrin. h|__m256 _mm_nmacc_ps (\__m256, \__m256, \__m256)|
|_mm256_nmsub_pd|FMA4 [1]|ammintrin. h|__m256d _mm_nmsub_pd (\__m256d, \__m256d, \__m256d)|
|_mm256_nmsub_ps|FMA4 [1]|ammintrin. h|__m256 _mm_nmsub_ps (\__m256, \__m256, \__m256)|
|[_mm256_or_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_pd)|AVX [2]|immintrin. h|_mm256_or_pd __m256d (\__m256d, \__m256d)|
|[_mm256_or_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_ps)|AVX [2]|immintrin. h|_mm256_or_ps __m256 (\__m256, \__m256)|
|[_mm256_or_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_si256)|AVX2 [2]|immintrin. h|_mm256_or_si256 __m256i (\__m256i, \__m256i)|
|[_mm256_packs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packs_epi16)|AVX2 [2]|immintrin. h|_mm256_packs_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_packs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packs_epi32)|AVX2 [2]|immintrin. h|_mm256_packs_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_packus_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packus_epi16)|AVX2 [2]|immintrin. h|_mm256_packus_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_packus_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packus_epi32)|AVX2 [2]|immintrin. h|_mm256_packus_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_permute_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute_pd)|AVX [2]|immintrin. h|_mm256_permute_pd __m256d (\__m256d, int)|
|[_mm256_permute_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute_ps)|AVX [2]|immintrin. h|_mm256_permute_ps __m256 (\__m256, int)|
|_mm256_permute2_pd|XOP [1]|ammintrin. h|__m256d _mm256_permute2_pd (\__m256d, \__m256d, \__m256i, int)|
|_mm256_permute2_ps|XOP [1]|ammintrin. h|__m256 _mm256_permute2_ps (\__m256, \__m256, \__m256i, int)|
|[_mm256_permute2f128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_pd)|AVX [2]|immintrin. h|__m256d _mm256_permute2f128_pd (\__m256d, \__m256d, int)|
|[_mm256_permute2f128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_ps)|AVX [2]|immintrin. h|__m256 _mm256_permute2f128_ps (\__m256, \__m256, int)|
|[_mm256_permute2f128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_si256)|AVX [2]|immintrin. h|__m256i _mm256_permute2f128_si256 (\__m256i, \__m256i, int)|
|[_mm256_permute2x128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2x128_si256)|AVX2 [2]|immintrin. h|__m256i _mm256_permute2x128_si256 (\__m256i, \__m256i, const int)|
|[_mm256_permute4x64_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute4x64_epi64)|AVX2 [2]|immintrin. h|__m256i _mm256_permute4x64_epi64 (\__m256i, const int)|
|[_mm256_permute4x64_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute4x64_pd)|AVX2 [2]|immintrin. h|__m256d _mm256_permute4x64_pd (\__m256d, const int)|
|[_mm256_permutevar_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar_pd)|AVX [2]|immintrin. h|_mm256_permutevar_pd __m256d (\__m256d, \__m256i)|
|[_mm256_permutevar_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar_ps)|AVX [2]|immintrin. h|_mm256_permutevar_ps __m256 (\__m256, \__m256i)|
|[_mm256_permutevar8x32_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar8x32_epi32)|AVX2 [2]|immintrin. h|_mm256_permutevar8x32_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_permutevar8x32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar8x32_ps)|AVX2 [2]|immintrin. h|_mm256_permutevar8x32_ps __m256 (\__m256, \__m256i)|
|[_mm256_rcp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_rcp_ps)|AVX [2]|immintrin. h|_mm256_rcp_ps __m256 (\__m256)|
|[_mm256_round_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_round_pd)|AVX [2]|immintrin. h|_mm256_round_pd __m256d (\__m256d, int)|
|[_mm256_round_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_round_ps)|AVX [2]|immintrin. h|_mm256_round_ps __m256 (\__m256, int)|
|[_mm256_rsqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_rsqrt_ps)|AVX [2]|immintrin. h|_mm256_rsqrt_ps __m256 (\__m256)|
|[_mm256_sad_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sad_epu8)|AVX2 [2]|immintrin. h|_mm256_sad_epu8 __m256i (\__m256i, \__m256i)|
|[_mm256_set_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi16)|AVX [2]|immintrin. h|(__m256i _mm256_set_epi16 (krótkie|
|[_mm256_set_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi32)|AVX [2]|immintrin. h|__m256i _mm256_set_epi32 (int, int, int, int, int, int, int, int)|
|[_mm256_set_epi64x](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi64x)|AVX [2]|immintrin. h|__m256i _mm256_set_epi64x (długim długim, długim długim, długim długim, długim długim)|
|[_mm256_set_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi8)|AVX [2]|immintrin. h|__m256i _mm256_set_epi8e (Char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, znak)|
|[_mm256_set_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_pd)|AVX [2]|immintrin. h|__m256d _mm256_set_pd (podwójna, podwójna, podwójna, podwójna)|
|[_mm256_set_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_ps)|AVX [2]|immintrin. h|__m256 _mm256_set_ps (float, float, float, float, float, float, float, float)|
|[_mm256_set1_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi16)|AVX [2]|immintrin. h|__m256i _mm256_set1_epi16 (krótki)|
|[_mm256_set1_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi32)|AVX [2]|immintrin. h|_mm256_set1_epi32 __m256i (int)|
|[_mm256_set1_epi64x](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi64x)|AVX [2]|immintrin. h|__m256i _mm256_set1_epi64x (long long)|
|[_mm256_set1_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi8)|AVX [2]|immintrin. h|__m256i _mm256_set1_epi8 (Char)|
|[_mm256_set1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_pd)|AVX [2]|immintrin. h|_mm256_set1_pd __m256d (Double)|
|[_mm256_set1_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_ps)|AVX [2]|immintrin. h|__m256 _mm256_set1_ps (float)|
|[_mm256_setr_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi16)|AVX [2]|immintrin. h|(__m256i _mm256_setr_epi16 (krótkie|
|[_mm256_setr_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi32)|AVX [2]|immintrin. h|__m256i _mm256_setr_epi32 (int, int, int, int, int, int, int, int)|
|[_mm256_setr_epi64x](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi64x)|AVX [2]|immintrin. h|__m256i _mm256_setr_epi64x (długim długim, długim długim, długim długim, długim długim)|
|[_mm256_setr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi8)|AVX [2]|immintrin. h|(__m256i _mm256_setr_epi8 (Char|
|[_mm256_setr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_pd)|AVX [2]|immintrin. h|__m256d _mm256_setr_pd (podwójna, podwójna, podwójna, podwójna)|
|[_mm256_setr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_ps)|AVX [2]|immintrin. h|__m256 _mm256_setr_ps (float, float, float, float, float, float, float, float)|
|[_mm256_setzero_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_pd)|AVX [2]|immintrin. h|__m256d _mm256_setzero_pd (void)|
|[_mm256_setzero_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_ps)|AVX [2]|immintrin. h|__m256 _mm256_setzero_ps (void)|
|[_mm256_setzero_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_si256)|AVX [2]|immintrin. h|__m256i _mm256_setzero_si256 (void)|
|[_mm256_shuffle_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_epi32)|AVX2 [2]|immintrin. h|__m256i _mm256_shuffle_epi32 (\__m256i, const int)|
|[_mm256_shuffle_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_epi8)|AVX2 [2]|immintrin. h|_mm256_shuffle_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_shuffle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_pd)|AVX [2]|immintrin. h|__m256d _mm256_shuffle_pd (\__m256d, \__m256d, const int)|
|[_mm256_shuffle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_ps)|AVX [2]|immintrin. h|__m256 _mm256_shuffle_ps (\__m256, \__m256, const int)|
|[_mm256_shufflehi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shufflehi_epi16)|AVX2 [2]|immintrin. h|__m256i _mm256_shufflehi_epi16 (\__m256i, const int)|
|[_mm256_shufflelo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shufflelo_epi16)|AVX2 [2]|immintrin. h|__m256i _mm256_shufflelo_epi16 (\__m256i, const int)|
|[_mm256_sign_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi16)|AVX2 [2]|immintrin. h|_mm256_sign_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_sign_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi32)|AVX2 [2]|immintrin. h|_mm256_sign_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_sign_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi8)|AVX2 [2]|immintrin. h|_mm256_sign_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_sll_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi16)|AVX2 [2]|immintrin. h|_mm256_sll_epi16 __m256i (\__m256i, \__m128i)|
|[_mm256_sll_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi32)|AVX2 [2]|immintrin. h|_mm256_sll_epi32 __m256i (\__m256i, \__m128i)|
|[_mm256_sll_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi64)|AVX2 [2]|immintrin. h|_mm256_sll_epi64 __m256i (\__m256i, \__m128i)|
|[_mm256_slli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi16)|AVX2 [2]|immintrin. h|_mm256_slli_epi16 __m256i (\__m256i, int)|
|[_mm256_slli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi32)|AVX2 [2]|immintrin. h|_mm256_slli_epi32 __m256i (\__m256i, int)|
|[_mm256_slli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi64)|AVX2 [2]|immintrin. h|_mm256_slli_epi64 __m256i (\__m256i, int)|
|[_mm256_slli_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_si256)|AVX2 [2]|immintrin. h|_mm256_slli_si256 __m256i (\__m256i, int)|
|[_mm256_sllv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sllv_epi32)|AVX2 [2]|immintrin. h|_mm256_sllv_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_sllv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sllv_epi64)|AVX2 [2]|immintrin. h|_mm256_sllv_epi64 __m256i (\__m256i, \__m256i)|
|[_mm256_sqrt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sqrt_pd)|AVX [2]|immintrin. h|_mm256_sqrt_pd __m256d (\__m256d)|
|[_mm256_sqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sqrt_ps)|AVX [2]|immintrin. h|_mm256_sqrt_ps __m256 (\__m256)|
|[_mm256_sra_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sra_epi16)|AVX2 [2]|immintrin. h|_mm256_sra_epi16 __m256i (\__m256i, \__m128i)|
|[_mm256_sra_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sra_epi32)|AVX2 [2]|immintrin. h|_mm256_sra_epi32 __m256i (\__m256i, \__m128i)|
|[_mm256_srai_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srai_epi16)|AVX2 [2]|immintrin. h|_mm256_srai_epi16 __m256i (\__m256i, int)|
|[_mm256_srai_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srai_epi32)|AVX2 [2]|immintrin. h|_mm256_srai_epi32 __m256i (\__m256i, int)|
|[_mm256_srav_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srav_epi32)|AVX2 [2]|immintrin. h|_mm256_srav_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_srl_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi16)|AVX2 [2]|immintrin. h|_mm256_srl_epi16 __m256i (\__m256i, \__m128i)|
|[_mm256_srl_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi32)|AVX2 [2]|immintrin. h|_mm256_srl_epi32 __m256i (\__m256i, \__m128i)|
|[_mm256_srl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi64)|AVX2 [2]|immintrin. h|_mm256_srl_epi64 __m256i (\__m256i, \__m128i)|
|[_mm256_srli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi16)|AVX2 [2]|immintrin. h|_mm256_srli_epi16 __m256i (\__m256i, int)|
|[_mm256_srli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi32)|AVX2 [2]|immintrin. h|_mm256_srli_epi32 __m256i (\__m256i, int)|
|[_mm256_srli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi64)|AVX2 [2]|immintrin. h|_mm256_srli_epi64 __m256i (\__m256i, int)|
|[_mm256_srli_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_si256)|AVX2 [2]|immintrin. h|_mm256_srli_si256 __m256i (\__m256i, int)|
|[_mm256_srlv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srlv_epi32)|AVX2 [2]|immintrin. h|_mm256_srlv_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_srlv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srlv_epi64)|AVX2 [2]|immintrin. h|_mm256_srlv_epi64 __m256i (\__m256i, \__m256i)|
|[_mm256_store_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_pd)|AVX [2]|immintrin. h|void _mm256_store_pd (Double \*, \__m256d)|
|[_mm256_store_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_ps)|AVX [2]|immintrin. h|void _mm256_store_ps (zmiennoprzecinkowe \*, \__m256)|
|[_mm256_store_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_si256)|AVX [2]|immintrin. h|void _mm256_store_si256 (\__m256i \*, \__m256i)|
|[_mm256_storeu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_pd)|AVX [2]|immintrin. h|void _mm256_storeu_pd (Double \*, \__m256d)|
|[_mm256_storeu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_ps)|AVX [2]|immintrin. h|void _mm256_storeu_ps (zmiennoprzecinkowe \*, \__m256)|
|[_mm256_storeu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_si256)|AVX [2]|immintrin. h|void _mm256_storeu_si256 (\__m256i \*, \__m256i)|
|[_mm256_stream_load_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_load_si256)|AVX2 [2]|immintrin. h|_mm256_stream_load_si256 __m256i (\__m256i const \*)|
|[_mm256_stream_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_pd)|AVX [2]|immintrin. h|void __mm256_stream_pd (Double \*, \__m256d)|
|[_mm256_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_ps)|AVX [2]|immintrin. h|void _mm256_stream_ps (zmiennoprzecinkowe \*, \__m256)|
|[_mm256_stream_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_si256)|AVX [2]|immintrin. h|void __mm256_stream_si256 (\__m256i \*, \__m256i)|
|[_mm256_sub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi16)|AVX2 [2]|immintrin. h|_mm256_sub_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_sub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi32)|AVX2 [2]|immintrin. h|_mm256_sub_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_sub_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi64)|AVX2 [2]|immintrin. h|_mm256_sub_epi64 __m256i (\__m256i, \__m256i)|
|[_mm256_sub_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi8)|AVX2 [2]|immintrin. h|_mm256_sub_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_sub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_pd)|AVX [2]|immintrin. h|_mm256_sub_pd __m256d (\__m256d, \__m256d)|
|[_mm256_sub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_ps)|AVX [2]|immintrin. h|_mm256_sub_ps __m256 (\__m256, \__m256)|
|[_mm256_subs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epi16)|AVX2 [2]|immintrin. h|_mm256_subs_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_subs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epi8)|AVX2 [2]|immintrin. h|_mm256_subs_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_subs_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epu16)|AVX2 [2]|immintrin. h|_mm256_subs_epu16 __m256i (\__m256i, \__m256i)|
|[_mm256_subs_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epu8)|AVX2 [2]|immintrin. h|_mm256_subs_epu8 __m256i (\__m256i, \__m256i)|
|[_mm256_testc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_pd)|AVX [2]|immintrin. h|int _mm256_testc_pd (\__m256d, \__m256d)|
|[_mm256_testc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_ps)|AVX [2]|immintrin. h|int _mm256_testc_ps (\__m256, \__m256)|
|[_mm256_testc_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_si256)|AVX [2]|immintrin. h|int _mm256_testc_si256 (\__m256i, \__m256i)|
|[_mm256_testnzc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_pd)|AVX [2]|immintrin. h|int _mm256_testnzc_pd (\__m256d, \__m256d)|
|[_mm256_testnzc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_ps)|AVX [2]|immintrin. h|int _mm256_testnzc_ps (\__m256, \__m256)|
|[_mm256_testnzc_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_si256)|AVX [2]|immintrin. h|int _mm256_testnzc_si256 (\__m256i, \__m256i)|
|[_mm256_testz_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_pd)|AVX [2]|immintrin. h|int _mm256_testz_pd (\__m256d, \__m256d)|
|[_mm256_testz_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_ps)|AVX [2]|immintrin. h|int _mm256_testz_ps (\__m256, \__m256)|
|[_mm256_testz_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_si256)|AVX [2]|immintrin. h|int _mm256_testz_si256 (\__m256i, \__m256i)|
|[_mm256_unpackhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi16)|AVX2 [2]|immintrin. h|_mm256_unpackhi_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_unpackhi_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi32)|AVX2 [2]|immintrin. h|_mm256_unpackhi_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_unpackhi_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi64)|AVX2 [2]|immintrin. h|_mm256_unpackhi_epi64 __m256i (\__m256i, \__m256i)|
|[_mm256_unpackhi_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi8)|AVX2 [2]|immintrin. h|_mm256_unpackhi_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_unpackhi_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_pd)|AVX [2]|immintrin. h|_mm256_unpackhi_pd __m256d (\__m256d, \__m256d)|
|[_mm256_unpackhi_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_ps)|AVX [2]|immintrin. h|_mm256_unpackhi_ps __m256 (\__m256, \__m256)|
|[_mm256_unpacklo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi16)|AVX2 [2]|immintrin. h|_mm256_unpacklo_epi16 __m256i (\__m256i, \__m256i)|
|[_mm256_unpacklo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi32)|AVX2 [2]|immintrin. h|_mm256_unpacklo_epi32 __m256i (\__m256i, \__m256i)|
|[_mm256_unpacklo_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi64)|AVX2 [2]|immintrin. h|_mm256_unpacklo_epi64 __m256i (\__m256i, \__m256i)|
|[_mm256_unpacklo_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi8)|AVX2 [2]|immintrin. h|_mm256_unpacklo_epi8 __m256i (\__m256i, \__m256i)|
|[_mm256_unpacklo_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_pd)|AVX [2]|immintrin. h|_mm256_unpacklo_pd __m256d (\__m256d, \__m256d)|
|[_mm256_unpacklo_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_ps)|AVX [2]|immintrin. h|_mm256_unpacklo_ps __m256 (\__m256, \__m256)|
|[_mm256_xor_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_pd)|AVX [2]|immintrin. h|_mm256_xor_pd __m256d (\__m256d, \__m256d)|
|[_mm256_xor_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_ps)|AVX [2]|immintrin. h|_mm256_xor_ps __m256 (\__m256, \__m256)|
|[_mm256_xor_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_si256)|AVX2 [2]|immintrin. h|_mm256_xor_si256 __m256i (\__m256i, \__m256i)|
|[_mm256_zeroall](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_zeroall)|AVX [2]|immintrin. h|void _mm256_zeroall (void)|
|[_mm256_zeroupper](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_zeroupper)|AVX [2]|immintrin. h|void _mm256_zeroupper (void)|
|[__movsb](movsb.md)||intrin. h|VOID __movsb (niepodpisane znaki \*, niepodpisane znaki const \*, size_t)|
|[__movsd](movsd.md)||intrin. h|VOID __movsd (niepodpisane długie \*, niepodpisane Long const \*, size_t)|
|[__movsq](movsq.md)||intrin. h|VOID __movsq (bez znaku \__int64 \*, bez znaku \__int64 const \*, size_t)|
|[__movsw](movsw.md)||intrin. h|VOID __movsw (krótkie niepodpisane \*, Short const \*, size_t)|
|[_mul128](mul128.md)||intrin. h|__int64 _mul128 (\__int64, \__int64, \__int64 \*)|
|[__mulh](mulh.md)||intrin. h|__int64 \__mulh (\__int64, \__int64)|
|_mulx_u32|BMI [2]|immintrin. h|niepodpisane _mulx_u32 int (niepodpisane int, int unsigned int\*)|
|_mulx_u64|BMI [2]|immintrin. h|niepodpisane __int64 _mulx_u64 (niepodpisane \__int64, bez znaku \__int64, bez znaku \__int64)|
|[__nop](nop.md)||intrin. h|void __nop (void)|
|__nvreg_restore_fence||intrin. h|void __nvreg_restore_fence (void)|
|__nvreg_save_fence||intrin. h|void __nvreg_save_fence (void)|
|[__outbyte](outbyte.md)||intrin. h|void __outbyte (unsigned Short, unsigned char)|
|[__outbytestring](outbytestring.md)||intrin. h|void __outbytestring (unsigned Short, unsigned char \*, unsigned long)|
|[__outdword](outdword.md)||intrin. h|void __outdword (unsigned Short, unsigned long)|
|[__outdwordstring](outdwordstring.md)||intrin. h|void __outdwordstring (niepodpisane, długie \*bez znaku)|
|[__outword](outword.md)||intrin. h|void __outword (unsigned Short, unsigned Short)|
|[__outwordstring](outwordstring.md)||intrin. h|void __outwordstring (niepodpisane krótkie, niepodpisane, krótkie \*, Long unsigned)|
|[_pdep_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_pdep_u32)|BMI [2]|immintrin. h|niepodpisane _pdep_u32 int (niepodpisane int, int bez znaku)|
|[_pdep_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_pdep_u64)|BMI [2]|immintrin. h|niepodpisane _pdep_u64 __int64 (niepodpisane \__int64, bez znaku \_)|
|[_pext_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_pext_u32)|BMI [2]|immintrin. h|niepodpisane _pext_u32 int (niepodpisane int, int bez znaku)|
|[_pext_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_pext_u64)|BMI [2]|immintrin. h|niepodpisane _pext_u64 __int64 (niepodpisane \__int64, bez znaku \_)|
|[__popcnt](popcnt16-popcnt-popcnt64.md)|POPCNT|intrin. h|niepodpisane __popcnt int (int bez znaku)|
|[__popcnt16](popcnt16-popcnt-popcnt64.md)|POPCNT|intrin. h|krótkie __popcnt16 bez znaku (bez znaku)|
|[__popcnt64](popcnt16-popcnt-popcnt64.md)|POPCNT|intrin. h|niepodpisane __int64 \__popcnt64 (bez znaku \__int64)|
|[_rdrand16_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdrand16_step)|RDRAND [2]|immintrin. h|int _rdrand16_step (krótkie \*niepodpisane)|
|[_rdrand32_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdrand32_step)|RDRAND [2]|immintrin. h|int _rdrand32_step (niepodpisane \*int)|
|[_rdrand64_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdrand64_step)|RDRAND [2]|immintrin. h|int _rdrand64_step (niepodpisane \__int64 \*)|
|[_rdseed16_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdseed16_step)|RDSEED [2]|immintrin. h|int _rdseed16_step (krótkie \*niepodpisane)|
|[_rdseed32_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdseed32_step)|RDSEED [2]|immintrin. h|int _rdseed32_step (niepodpisane \*int)|
|[_rdseed64_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdseed64_step)|RDSEED [2]|immintrin. h|int _rdseed64_step (niepodpisane \__int64 \*)|
|[__rdtsc](rdtsc.md)||intrin. h|niepodpisane __int64 \__rdtsc (void)|
|[__rdtscp](rdtscp.md)|RDTSCP|intrin. h|niepodpisane __int64 \__rdtscp (niepodpisane\*int)|
|[_ReadBarrier](readbarrier.md)||intrin. h|void _ReadBarrier (void)|
|[__readcr0](readcr0.md)||intrin. h|niepodpisane __int64 \__readcr0 (void)|
|[__readcr2](readcr2.md)||intrin. h|niepodpisane __int64 \__readcr2 (void)|
|[__readcr3](readcr3.md)||intrin. h|niepodpisane __int64 \__readcr3 (void)|
|[__readcr4](readcr4.md)||intrin. h|niepodpisane __int64 \__readcr4 (void)|
|[__readcr8](readcr8.md)||intrin. h|niepodpisane __int64 \__readcr8 (void)|
|[__readdr](readdr.md)||intrin. h|niepodpisane __int64 \__readdr (bez znaku)|
|[__readeflags](readeflags.md)||intrin. h|niepodpisane __int64 \__readeflags (void)|
|[_readfsbase_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_readfsbase_u32)|FSGSBASE [2]|immintrin. h|niepodpisane _readfsbase_u32 int (void)|
|[_readfsbase_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_readfsbase_u64)|FSGSBASE [2]|immintrin. h|niepodpisane _readfsbase_u64 __int64 (void)|
|[_readgsbase_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_readgsbase_u32)|FSGSBASE [2]|immintrin. h|niepodpisane _readgsbase_u32 int (void)|
|[_readgsbase_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_readgsbase_u64)|FSGSBASE [2]|immintrin. h|niepodpisane _readgsbase_u64 __int64 (void)|
|[__readgsbyte](readgsbyte-readgsdword-readgsqword-readgsword.md)||intrin. h|niepodpisany znak __readgsbyte (liczba bez znaku)|
|[__readgsdword](readgsbyte-readgsdword-readgsqword-readgsword.md)||intrin. h|niepodpisane długie __readgsdword (liczba bez znaku)|
|[__readgsqword](readgsbyte-readgsdword-readgsqword-readgsword.md)||intrin. h|niepodpisane __int64 \__readgsqword (bez znaku)|
|[__readgsword](readgsbyte-readgsdword-readgsqword-readgsword.md)||intrin. h|krótkie __readgsword bez znaku (bez znaku)|
|[__readmsr](readmsr.md)||intrin. h|niepodpisane __int64 \__readmsr (bez znaku)|
|[__readpmc](readpmc.md)||intrin. h|niepodpisane __int64 \__readpmc (bez znaku)|
|[_ReadWriteBarrier](readwritebarrier.md)||intrin. h|void _ReadWriteBarrier (void)|
|[_ReturnAddress](returnaddress.md)||intrin. h|void \* _ReturnAddress (void)|
|_rorx_u32|BMI [2]|immintrin. h|unsigned int _rorx_u32 (unsigned int, const unsigned int)|
|_rorx_u64|BMI [2]|immintrin. h|niepodpisane _rorx_u64 __int64 (niepodpisane \__int64, const unsigned int)|
|[_rotl16](rotl8-rotl16.md)||intrin. h|krótkie _rotl16 bez znaku (bez znaku)|
|[_rotl8](rotl8-rotl16.md)||intrin. h|niepodpisany znak _rotl8 (znak bez znaku, znak bez znaku)|
|[_rotr16](rotr8-rotr16.md)||intrin. h|krótkie _rotr16 bez znaku (bez znaku)|
|[_rotr8](rotr8-rotr16.md)||intrin. h|niepodpisany znak _rotr8 (znak bez znaku, znak bez znaku)|
|_rsm||intrin. h|void _rsm (void)|
|_sarx_i32|BMI [2]|immintrin. h|int _sarx_i32 (int, unsigned int)|
|_sarx_i64|BMI [2]|immintrin. h|_sarx_i64 __int64 (\__int64, bez znaku int)|
|[__segmentlimit](segmentlimit.md)||intrin. h|niepodpisane długie __segmentlimit (liczba bez znaku)|
|_sgdt||intrin. h|void _sgdt (void\*)|
|[__shiftleft128](shiftleft128.md)||intrin. h|niepodpisane __int64 \__shiftleft128 (bez znaku \__int64, bez znaku \__int64, znak bez znaku)|
|[__shiftright128](shiftright128.md)||intrin. h|niepodpisane __int64 \__shiftright128 (bez znaku \__int64, bez znaku \__int64, znak bez znaku)|
|_shlx_u32|BMI [2]|immintrin. h|niepodpisane _shlx_u32 int (niepodpisane int, int bez znaku)|
|_shlx_u64|BMI [2]|immintrin. h|niepodpisane _shlx_u64 __int64 (niepodpisane \__int64, bez znaku int)|
|_shrx_u32|BMI [2]|immintrin. h|niepodpisane _shrx_u32 int (niepodpisane int, int bez znaku)|
|_shrx_u64|BMI [2]|immintrin. h|niepodpisane _shrx_u64 __int64 (niepodpisane \__int64, bez znaku int)|
|[__sidt](sidt.md)||intrin. h|void __sidt (void\*)|
|__slwpcb|LWP [1]|ammintrin. h|void \*__slwpcb (void)|
|_stac|SMAP|intrin. h|void _stac (void)|
|_store_be_u16<br /><br /> [_storebe_i16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i16&expand=5141)|MOVBE|immintrin. h|void _store_be_u16 (void \*, unsigned Short);<br /><br /> void _storebe_i16 (void \*, Short); r.3|
|_store_be_u32<br /><br /> [_storebe_i32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i32&expand=5142)|MOVBE|immintrin. h|void _store_be_u32 (void \*, bez znaku int);<br /><br /> void _storebe_i32 (void \*, int); r.3|
|_store_be_u64<br /><br /> [_storebe_i64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i64&expand=5143)|MOVBE|immintrin. h|void _store_be_u64 (void \*, bez znaku \__int64);<br /><br /> void _storebe_i64 (void \*, \__int64); r.3|
|_Store_HLERelease|HLE [2]|immintrin. h|void _Store_HLERelease (długa nietrwała \*, Long)|
|_Store64_HLERelease|HLE [2]|immintrin. h|void _Store64_HLERelease (\__int64 volatile \*, \__int64)|
|_StorePointer_HLERelease|HLE [2]|immintrin. h|void _StorePointer_HLERelease (void \* volatile \*, void \*)|
|[__stosb](stosb.md)||intrin. h|void __stosb (niepodpisany znak \*, znak bez znaku, size_t)|
|[__stosd](stosd.md)||intrin. h|void __stosd (unsigned long \*, Long unsigned, size_t)|
|[__stosq](stosq.md)||intrin. h|void __stosq (niepodpisane \__int64 \*, niepodpisane \__int64, size_t)|
|[__stosw](stosw.md)||intrin. h|void __stosw (krótkie niepodpisane \*, krótkie niepodpisane, size_t)|
|_subborrow_u16||intrin. h|niepodpisany znak _subborrow_u16 (znak bez znaku, niepodpisane, krótkie, niepodpisane, krótkie \*)|
|[_subborrow_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_subborrow_u32)||intrin. h|niepodpisany znak _subborrow_u32 (znak niepodpisany, int, unsigned int, niepodpisane \*int)|
|[_subborrow_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_subborrow_u64)||intrin. h|niepodpisany znak _subborrow_u64 (znak bez znaku, niepodpisane \__int64, bez znaku \__int64, bez znaku \__int64)|
|_subborrow_u8||intrin. h|niepodpisany znak _subborrow_u8 (znak bez znaku, znak bez znaku, znak bez znaku, znak \*znaków)|
|[__svm_clgi](svm-clgi.md)||intrin. h|void __svm_clgi (void)|
|[__svm_invlpga](svm-invlpga.md)||intrin. h|void __svm_invlpga (void\*, int)|
|[__svm_skinit](svm-skinit.md)||intrin. h|void __svm_skinit (int)|
|[__svm_stgi](svm-stgi.md)||intrin. h|void __svm_stgi (void)|
|[__svm_vmload](svm-vmload.md)||intrin. h|void __svm_vmload (size_t)|
|[__svm_vmrun](svm-vmrun.md)||intrin. h|void __svm_vmrun (size_t)|
|[__svm_vmsave](svm-vmsave.md)||intrin. h|void __svm_vmsave (size_t)|
|_t1mskc_u32|ABM [1]|ammintrin. h|niepodpisane _t1mskc_u32 int (int bez znaku)|
|_t1mskc_u64|ABM [1]|ammintrin. h|niepodpisane _t1mskc_u64 __int64 (niepodpisane \__int64)|
|[_tzcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_tzcnt_u32)|BMI|ammintrin. h, immintrin. h|niepodpisane _tzcnt_u32 int (int bez znaku)|
|[_tzcnt_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_tzcnt_u64)|BMI|ammintrin. h, immintrin. h|niepodpisane _tzcnt_u64 __int64 (niepodpisane \__int64)|
|_tzmsk_u32|ABM [1]|ammintrin. h|niepodpisane _tzmsk_u32 int (int bez znaku)|
|_tzmsk_u64|ABM [1]|ammintrin. h|niepodpisane _tzmsk_u64 __int64 (niepodpisane \__int64)|
|[__ud2](ud2.md)||intrin. h|void __ud2 (void)|
|[_udiv128](udiv128.md)||intrin. h|niepodpisane __int64 _udiv128 (niepodpisane \__int64, bez znaku \__int64, bez znaku \__int64, bez znaku \__int64)|
|[_udiv64](udiv64.md)||intrin. h|niepodpisane int \_udiv64 (niepodpisane \__int64, int unsigned int *)|
|[__ull_rshift](ull-rshift.md)||intrin. h|niepodpisane __int64 [Pascal/CDECL] \__ull_rshift (bez znaku \__int64, int)|
|[_umul128](umul128.md)||intrin. h|niepodpisane __int64 _umul128 (niepodpisane \__int64, bez znaku \__int64, bez znaku \__int64)|
|[__umulh](umulh.md)||intrin. h|niepodpisane __int64 \__umulh (bez znaku \__int64, bez znaku \_)|
|[__vmx_off](vmx-off.md)||intrin. h|void __vmx_off (void)|
|[__vmx_on](vmx-on.md)||intrin. h|niepodpisany znak __vmx_on (niepodpisane \__int64\*)|
|[__vmx_vmclear](vmx-vmclear.md)||intrin. h|niepodpisany znak __vmx_vmclear (niepodpisane \__int64\*)|
|[__vmx_vmlaunch](vmx-vmlaunch.md)||intrin. h|niepodpisany znak __vmx_vmlaunch (void)|
|[__vmx_vmptrld](vmx-vmptrld.md)||intrin. h|niepodpisany znak __vmx_vmptrld (niepodpisane \__int64\*)|
|[__vmx_vmptrst](vmx-vmptrst.md)||intrin. h|void __vmx_vmptrst (niepodpisane \__int64 \*)|
|[__vmx_vmread](vmx-vmread.md)||intrin. h|niepodpisany znak __vmx_vmread (size_t, size_t\*)|
|[__vmx_vmresume](vmx-vmresume.md)||intrin. h|niepodpisany znak __vmx_vmresume (void)|
|[__vmx_vmwrite](vmx-vmwrite.md)||intrin. h|niepodpisany znak __vmx_vmwrite (size_t, size_t)|
|[__wbinvd](wbinvd.md)||intrin. h|void __wbinvd (void)|
|[_WriteBarrier](writebarrier.md)||intrin. h|void _WriteBarrier (void)|
|[__writecr0](writecr0.md)||intrin. h|void __writecr0 (niepodpisane \__int64)|
|[__writecr3](writecr3.md)||intrin. h|void __writecr3 (niepodpisane \__int64)|
|[__writecr4](writecr4.md)||intrin. h|void __writecr4 (niepodpisane \__int64)|
|[__writecr8](writecr8.md)||intrin. h|void __writecr8 (niepodpisane \__int64)|
|[__writedr](writedr.md)||intrin. h|void __writedr (niepodpisane, niepodpisane \__int64)|
|[__writeeflags](writeeflags.md)||intrin. h|void __writeeflags (niepodpisane \__int64)|
|[_writefsbase_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_writefsbase_u32)|FSGSBASE [2]|immintrin. h|void _writefsbase_u32 (bez znaku int)|
|[_writefsbase_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_writefsbase_u64)|FSGSBASE [2]|immintrin. h|void _writefsbase_u64 (niepodpisane \__int64)|
|[_writegsbase_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_writegsbase_u32)|FSGSBASE [2]|immintrin. h|void _writegsbase_u32 (bez znaku int)|
|[_writegsbase_u64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_writegsbase_u64)|FSGSBASE [2]|immintrin. h|void _writegsbase_u64 (niepodpisane \__int64)|
|[__writegsbyte](writegsbyte-writegsdword-writegsqword-writegsword.md)||intrin. h|void __writegsbyte (unsigned long, znak bez znaku)|
|[__writegsdword](writegsbyte-writegsdword-writegsqword-writegsword.md)||intrin. h|void __writegsdword (Long bez znaku, Long unsigned)|
|[__writegsqword](writegsbyte-writegsdword-writegsqword-writegsword.md)||intrin. h|void __writegsqword (Long unsigned unsigned \__int64)|
|[__writegsword](writegsbyte-writegsdword-writegsqword-writegsword.md)||intrin. h|void __writegsword (Long unsigned unsigned Short)|
|[__writemsr](writemsr.md)||intrin. h|void __writemsr (Long unsigned unsigned \__int64)|
|[_xabort](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xabort)|RTM [2]|immintrin. h|void _xabort (bez znaku int)|
|[_xbegin](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xbegin)|RTM [2]|immintrin. h|niepodpisany _xbegin (void)|
|[_xend](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xend)|RTM [2]|immintrin. h|void _xend (void)|
|[_xgetbv](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xgetbv)|XSAVE [2]|immintrin. h|niepodpisane __int64 _xgetbv (int bez znaku)|
|[_xrstor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xrstor)|XSAVE [2]|immintrin. h|void _xrstor (void const\*, niepodpisane \__int64)|
|[_xrstor64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xrstor64)|XSAVE [2]|immintrin. h|void _xrstor64 (void const\*, niepodpisane \__int64)|
|[_xsave](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsave)|XSAVE [2]|immintrin. h|void _xsave (void\*, bez znaku \__int64)|
|[_xsave64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsave64)|XSAVE [2]|immintrin. h|void _xsave64 (void\*, bez znaku \__int64)|
|[_xsaveopt](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsaveopt)|XSAVEOPT [2]|immintrin. h|void _xsaveopt (void\*, bez znaku \__int64)|
|[_xsaveopt64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsaveopt64)|XSAVEOPT [2]|immintrin. h|void _xsaveopt64 (void\*, bez znaku \__int64)|
|[_xsetbv](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsetbv)|XSAVE [2]|immintrin. h|void _xsetbv (bez znaku int, unsigned \__int64)|
|[_xtest](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xtest)|XTEST [2]|immintrin. h|niepodpisany znak _xtest (void)|

## <a name="see-also"></a>Zobacz także

\ [Wewnętrzne kompilatora](compiler-intrinsics.md)
\ [wewnętrzne ARM](arm-intrinsics.md)
[Arm64 wewnętrzne](arm64-intrinsics.md)\
[x86 — wewnętrzne](x86-intrinsics-list.md)
