---
title: "x64 (amd64) lista funkcji wewnętrznych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cl-exe compiler, intrinsics
- intrinsics, x64
- intrinsics, amd64
ms.assetid: a2b65471-f1db-426c-8464-eff4a3761dee
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9687a7e4d40757a202d8ffa01fa6a31311deed64
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="x64-amd64-intrinsics-list"></a>Lista funkcji wewnętrznych x64 (amd64)
Ten dokument zawiera listę funkcji wewnętrznych obsługiwanych przez kompilator Visual C++, gdy architekturą docelową jest x64 (zwane też amd64).  
  
 Aby uzyskać informacje o poszczególnych funkcjach wewnętrznych, zapoznaj się z tymi zasobami, odpowiednio dla docelowej architektury procesora:  
  
-   Plik nagłówka. Wiele funkcji wewnętrznych są udokumentowane w komentarzach w pliku nagłówka.  
  
-   [Przewodnik funkcje wewnętrzne Intel](http://go.microsoft.com/fwlink/p/?LinkId=512130). Użyj pola wyszukiwania, aby znaleźć określone funkcje wewnętrzne.  
  
-   [Podręczniki deweloperów oprogramowania architektur 64 i IA-32 Intel](http://go.microsoft.com/fwlink/p/?LinkId=251198)  
  
-   [Intel AVX](http://go.microsoft.com/fwlink/p/?LinkId=251202)  
  
-   [Przewodniki Developer AMD & podręczniki](http://go.microsoft.com/fwlink/p/?LinkId=251203)  
  
 W poniższej tabeli wymieniono funkcje wewnętrzne dostępne na x64 procesorów. Kolumna technologii zawiera zestaw instrukcji obsługi technicznej. Użyj [__cpuid](../intrinsics/cpuid-cpuidex.md) wewnętrznego, aby określić zestaw instrukcji obsługi w czasie wykonywania. W przypadku dwóch wpisów w jednym wierszu, reprezentują one różne punkty wejścia dla tego samego wewnętrznej. [1] wskazuje, że wewnętrznej jest dostępna tylko na procesory AMD. [2] wskazuje, że wewnętrznej jest dostępna tylko na procesory Intel. [3] wskazuje, że makro jest prototypu. Nagłówek wymaganych przez prototypu funkcji znajduje się w nagłówku kolumny. Nagłówek intrin.h zawiera immintrin.h i ammintrin.h dla uproszczenia.  
  
|Nazwa funkcji wewnętrznej|Technologia|nagłówek|Prototyp funkcji|  
|--------------------|----------------|------------|------------------------|  
|_addcarry_u16||intrin.h|unsigned char _addcarry_u16 (unsigned char c_in, niepodpisane src1 krótkich, niepodpisane src2 krótkie, bez znaku krótko * Suma)|  
|[_addcarry_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)||intrin.h|unsigned char _addcarry_u32 (unsigned char c_in, src1 unsigned int, src2 unsigned int, int bez znaku * Suma)|  
|[_addcarry_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)||intrin.h|unsigned char _addcarry_u64 (unsigned char c_in, bez znaku \_src1 _int64, bez znaku \_src2 _int64, bez znaku \__int64 * Suma)|  
|_addcarry_u8||intrin.h|unsigned char _addcarry_u8 (unsigned char c_in, src1 char bez znaku, src2 unsigned char unsigned char * Suma)|  
|[_addcarryx_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|ADX [2]|immintrin.h|unsigned char _addcarryx_u32 (unsigned char c_in, src1 unsigned int, src2 unsigned int, int bez znaku * Suma)|  
|[_addcarryx_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|ADX [2]|immintrin.h|unsigned char _addcarryx_u64 (unsigned char c_in, bez znaku \_src1 _int64, bez znaku \_src2 _int64, bez znaku \__int64 * Suma)|  
|[__addgsbyte](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)||intrin.h|void __addgsbyte (unsigned char długie, bez znaku)|  
|[__addgsdword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)||intrin.h|void __addgsdword (unsigned int długie, bez znaku)|  
|[__addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)||intrin.h|void __addgsqword (unsigned long, bez znaku \__int64)|  
|[__addgsword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)||intrin.h|void __addgsword (bez znaku krótkiej długie, bez znaku)|  
|[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)||intrin.h|void * _AddressOfReturnAddress(void)|  
|_andn_u32|BMI [1]|ammintrin.h|unsigned int _andn_u32 (unsigned int, int bez znaku)|  
|_andn_u64|BMI [1]|ammintrin.h|niepodpisane __int64 _andn_u64 (bez znaku \__int64 niepodpisane \__int64)|  
|[_bextr_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|unsigned int _bextr_u32 (unsigned int, int bez znaku, unsigned int)|  
|[_bextr_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|niepodpisane __int64 _bextr_u64 (bez znaku \__int64, unsigned int, unsigned int)|  
|_bextri_u32|ABM [1]|ammintrin.h|unsigned int _bextri_u32 (unsigned int, int bez znaku)|  
|_bextri_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _bextri_u64 (bez znaku \__int64, unsigned int)|  
|[_BitScanForward](../intrinsics/bitscanforward-bitscanforward64.md)||intrin.h|Wartość logiczna _BitScanForward (OUT ULONG * maska ULONG indeksu, IN)|  
|[_BitScanForward64](../intrinsics/bitscanforward-bitscanforward64.md)||intrin.h|Wartość logiczna _BitScanForward64 (OUT ULONG * maska ULONG64 indeksu, IN)|  
|[_BitScanReverse](../intrinsics/bitscanreverse-bitscanreverse64.md)||intrin.h|Wartość logiczna _BitScanReverse (OUT ULONG * maska ULONG indeksu, IN)|  
|[_BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md)||intrin.h|Wartość logiczna _BitScanReverse64 (OUT ULONG * maska ULONG64 indeksu, IN)|  
|[_bittest](../intrinsics/bittest-bittest64.md)||intrin.h|unsigned char _bittest (długo const *, długi b).|  
|[_bittest64](../intrinsics/bittest-bittest64.md)||intrin.h|_bittest64 char bez znaku (\__int64 const *,\__int64 b).|  
|[_bittestandcomplement](../intrinsics/bittestandcomplement-bittestandcomplement64.md)||intrin.h|unsigned char _bittestandcomplement (Liczba długa *, długi b).|  
|[_bittestandcomplement64](../intrinsics/bittestandcomplement-bittestandcomplement64.md)||intrin.h|_bittestandcomplement64 char bez znaku (\__int64 *,\__int64 b).|  
|[_bittestandreset](../intrinsics/bittestandreset-bittestandreset64.md)||intrin.h|unsigned char _bittestandreset (Liczba długa *, długi b).|  
|[_bittestandreset64](../intrinsics/bittestandreset-bittestandreset64.md)||intrin.h|_bittestandreset64 char bez znaku (\__int64 *,\__int64 b).|  
|[_bittestandset](../intrinsics/bittestandset-bittestandset64.md)||intrin.h|unsigned char _bittestandset (Liczba długa *, długi b).|  
|[_bittestandset64](../intrinsics/bittestandset-bittestandset64.md)||intrin.h|_bittestandset64 char bez znaku (\__int64 *,\__int64 b).|  
|_blcfill_u32|ABM [1]|ammintrin.h|_blcfill_u32(unsigned int) unsigned int|  
|_blcfill_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _blcfill_u64 (bez znaku \__int64)|  
|_blci_u32|ABM [1]|ammintrin.h|_blci_u32(unsigned int) unsigned int|  
|_blci_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _blci_u64 (bez znaku \__int64)|  
|_blcic_u32|ABM [1]|ammintrin.h|_blcic_u32(unsigned int) unsigned int|  
|_blcic_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _blcic_u64 (bez znaku \__int64)|  
|_blcmsk_u32|ABM [1]|ammintrin.h|_blcmsk_u32(unsigned int) unsigned int|  
|_blcmsk_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _blcmsk_u64 (bez znaku \__int64)|  
|_blcs_u32|ABM [1]|ammintrin.h|_blcs_u32(unsigned int) unsigned int|  
|_blcs_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _blcs_u64 (bez znaku \__int64)|  
|_blsfill_u32|ABM [1]|ammintrin.h|_blsfill_u32(unsigned int) unsigned int|  
|_blsfill_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _blsfill_u64 (bez znaku \__int64)|  
|[_blsi_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|_blsi_u32(unsigned int) unsigned int|  
|[_blsi_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|niepodpisane __int64 _blsi_u64 (bez znaku \__int64)|  
|_blsic_u32|ABM [1]|ammintrin.h|_blsic_u32(unsigned int) unsigned int|  
|_blsic_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _blsic_u64 (bez znaku \__int64)|  
|[_blsmsk_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|_blsmsk_u32(unsigned int) unsigned int|  
|[_blsmsk_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|niepodpisane __int64 _blsmsk_u64 (bez znaku \__int64)|  
|[_blsr_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|_blsr_u32(unsigned int) unsigned int|  
|[_blsr_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|niepodpisane __int64 _blsr_u64 (bez znaku \__int64)|  
|[_bzhi_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI [2]|immintrin.h|unsigned int _bzhi_u32 (unsigned int, int bez znaku)|  
|[_bzhi_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI [2]|immintrin.h|niepodpisane __int64 _bzhi_u64 (bez znaku \__int64, unsigned int)|  
|_clac|SMAP|intrin.h|void _clac(void)|  
|[__cpuid](../intrinsics/cpuid-cpuidex.md)||intrin.h|void __cpuid (int * int, (b).|  
|[__cpuidex](../intrinsics/cpuid-cpuidex.md)||intrin.h|void __cpuidex (int * b, int, int c).|  
|[__debugbreak](../intrinsics/debugbreak.md)||intrin.h|void __debugbreak(void)|  
|[_disable](../intrinsics/disable.md)||intrin.h|void _disable(void)|  
|[__emul](../intrinsics/emul-emulu.md)||intrin.h|__int64 [pascal/cdecl] \__emul(int,int)|  
|[__emulu](../intrinsics/emul-emulu.md)||intrin.h|__int64 bez znaku [pascal/cdecl]\__emulu (unsigned int, int bez znaku)|  
|[_włącz](../intrinsics/enable.md)||intrin.h|void _enable(void)|  
|[__fastfail](../intrinsics/fastfail.md)||intrin.h|void __fastfail(unsigned int)|  
|[__faststorefence](../intrinsics/faststorefence.md)||intrin.h|void __faststorefence(void)|  
|[_fxrstor](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FXSR [2]|immintrin.h|void _fxrstor (void const *)|  
|[_fxrstor64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FXSR [2]|immintrin.h|void _fxrstor64 (void) const *|  
|[_fxsave](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FXSR [2]|immintrin.h|void _fxsave(void*)|  
|[_fxsave64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FXSR [2]|immintrin.h|void _fxsave64(void*)|  
|[__getcallerseflags](../intrinsics/getcallerseflags.md)||intrin.h|(unsigned int __getcallerseflags())|  
|[__halt](../intrinsics/halt.md)||intrin.h|void __halt(void)|  
|[__inbyte](../intrinsics/inbyte.md)||intrin.h|__inbyte char bez znaku (bez znaku krótkich Port)|  
|[__inbytestring](../intrinsics/inbytestring.md)||intrin.h|void __inbytestring (bez znaku portu krótkich, unsigned char * buforu, bez znaku liczba długa)|  
|[__incgsbyte](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)||intrin.h|void __incgsbyte(unsigned long)|  
|[__incgsdword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)||intrin.h|void __incgsdword(unsigned long)|  
|[__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)||intrin.h|void __incgsqword(unsigned long)|  
|[__incgsword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)||intrin.h|void __incgsword(unsigned long)|  
|[__indword](../intrinsics/indword.md)||intrin.h|niepodpisane __indword długi (bez znaku krótkich Port)|  
|[__indwordstring](../intrinsics/indwordstring.md)||intrin.h|void __indwordstring (unsigned portu krótkie, unsigned long * buforu, bez znaku liczba długa)|  
|[__int2c](../intrinsics/int2c.md)||intrin.h|void __int2c(void)|  
|[_InterlockedAnd](../intrinsics/interlockedand-intrinsic-functions.md)||intrin.h|długie _InterlockedAnd (długo volatile * długim)|  
|[_InterlockedAnd_HLEAcquire](../intrinsics/interlockedand-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedAnd_HLEAcquire (długo volatile * długim)|  
|[_InterlockedAnd_HLERelease](../intrinsics/interlockedand-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedAnd_HLERelease (długo volatile * długim)|  
|[_InterlockedAnd_np](../intrinsics/interlockedand-intrinsic-functions.md)||intrin.h|_InterlockedAnd_np długa (Liczba długa * długim)|  
|[_InterlockedAnd16](../intrinsics/interlockedand-intrinsic-functions.md)||intrin.h|krótki _InterlockedAnd16 (krótka volatile *, krótki)|  
|[_InterlockedAnd16_np](../intrinsics/interlockedand-intrinsic-functions.md)||intrin.h|krótki _InterlockedAnd16_np (short *, krótki)|  
|[_InterlockedAnd64](../intrinsics/interlockedand-intrinsic-functions.md)||intrin.h|__int64 _InterlockedAnd64 (\__int64 volatile *,\__int64)|  
|[_InterlockedAnd64_HLEAcquire](../intrinsics/interlockedand-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedAnd64_HLEAcquire (\__int64 volatile *,\__int64)|  
|[_InterlockedAnd64_HLERelease](../intrinsics/interlockedand-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedAnd64_HLERelease (\__int64 volatile *,\__int64)|  
|[_InterlockedAnd64_np](../intrinsics/interlockedand-intrinsic-functions.md)||intrin.h|__int64 _InterlockedAnd64_np (\__int64 *,\__int64)|  
|[_InterlockedAnd8](../intrinsics/interlockedand-intrinsic-functions.md)||intrin.h|CHAR — _InterlockedAnd8 (char volatile *, char)|  
|[_InterlockedAnd8_np](../intrinsics/interlockedand-intrinsic-functions.md)||intrin.h|CHAR — _InterlockedAnd8_np (char *, char)|  
|[_interlockedbittestandreset](../intrinsics/interlockedbittestandreset-intrinsic-functions.md)||intrin.h|unsigned char _interlockedbittestandreset (Liczba długa *, długi b).|  
|[_interlockedbittestandreset_HLEAcquire](../intrinsics/interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin.h|unsigned char _interlockedbittestandreset_HLEAcquire (Liczba długa *, długi b).|  
|[_interlockedbittestandreset_HLERelease](../intrinsics/interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin.h|unsigned char _interlockedbittestandreset_HLERelease (Liczba długa *, długi b).|  
|[_interlockedbittestandreset64](../intrinsics/interlockedbittestandreset-intrinsic-functions.md)||intrin.h|_interlockedbittestandreset64 char bez znaku (\__int64 *,\__int64 b).|  
|[_interlockedbittestandreset64_HLEAcquire](../intrinsics/interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin.h|_interlockedbittestandreset64_HLEAcquire char bez znaku (\__int64 *,\__int64 b).|  
|[_interlockedbittestandreset64_HLERelease](../intrinsics/interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin.h|_interlockedbittestandreset64_HLERelease char bez znaku (\__int64 *,\__int64 b).|  
|[_interlockedbittestandset](../intrinsics/interlockedbittestandset-intrinsic-functions.md)||intrin.h|unsigned char _interlockedbittestandset (Liczba długa *, długi b).|  
|[_interlockedbittestandset_HLEAcquire](../intrinsics/interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin.h|unsigned char _interlockedbittestandset_HLEAcquire (Liczba długa *, długi b).|  
|[_interlockedbittestandset_HLERelease](../intrinsics/interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin.h|unsigned char _interlockedbittestandset_HLERelease (Liczba długa *, długi b).|  
|[_interlockedbittestandset64](../intrinsics/interlockedbittestandset-intrinsic-functions.md)||intrin.h|_interlockedbittestandset64 char bez znaku (\__int64 *,\__int64 b).|  
|[_interlockedbittestandset64_HLEAcquire](../intrinsics/interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin.h|_interlockedbittestandset64_HLEAcquire char bez znaku (\__int64 *,\__int64 b).|  
|[_interlockedbittestandset64_HLERelease](../intrinsics/interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin.h|_interlockedbittestandset64_HLERelease char bez znaku (\__int64 *,\__int64 b).|  
|[_InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)||intrin.h|długie _InterlockedCompareExchange (długo volatile *, długie, długie)|  
|[_InterlockedCompareExchange_HLEAcquire](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedCompareExchange_HLEAcquire (długo volatile *, długie, długie)|  
|[_InterlockedCompareExchange_HLERelease](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedCompareExchange_HLERelease (długo volatile *, długie, długie)|  
|[_InterlockedCompareExchange_np](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)||intrin.h|długie _InterlockedCompareExchange_np (długa *, długie, długi)|  
|[_InterlockedCompareExchange128](../intrinsics/interlockedcompareexchange128.md)||intrin.h|_InterlockedCompareExchange128 char bez znaku (\__int64 volatile *,\__int64,\__int64,\__int64\*)|  
|[_InterlockedCompareExchange128_np](../intrinsics/interlockedcompareexchange128.md)||intrin.h|_InterlockedCompareExchange128 char bez znaku (\__int64 volatile *,\__int64,\__int64,\__int64\*)|  
|[_InterlockedCompareExchange16](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)||intrin.h|krótki _InterlockedCompareExchange16 (krótki volatile * wzorzec krótkiej przeznaczenia, krótki Exchange)|  
|[_InterlockedCompareExchange16_np](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)||intrin.h|krótki _InterlockedCompareExchange16_np (krótki volatile * wzorzec krótkiej przeznaczenia, krótki Exchange)|  
|[_InterlockedCompareExchange64](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)||intrin.h|__int64 _InterlockedCompareExchange64 (\__int64 volatile *,\__int64,\__int64)|  
|[_InterlockedCompareExchange64_HLEAcquire](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedCompareExchange64_HLEAcquire (\__int64 volatile *,\__int64,\__int64)|  
|[_InterlockedCompareExchange64_HLERelease](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedCompareExchange64_HLERelease (\__int64 volatile *,\__int64,\__int64)|  
|[_InterlockedCompareExchange64_np](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)||intrin.h|__int64 _InterlockedCompareExchange64_np (\__int64 *,\__int64,\__int64)|  
|[_InterlockedCompareExchange8](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)||intrin.h|CHAR — _InterlockedCompareExchange8 (char volatile * przeznaczenia, char programu Exchange, char wzorzec)|  
|[_InterlockedCompareExchangePointer](../intrinsics/interlockedcompareexchangepointer-intrinsic-functions.md)||intrin.h|void * _InterlockedCompareExchangePointer (void \*volatile \*, void \*, void \*)|  
|[_InterlockedCompareExchangePointer_HLEAcquire](../intrinsics/interlockedcompareexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|void * _InterlockedCompareExchangePointer_HLEAcquire (void \*volatile \*, void \*, void \*)|  
|[_InterlockedCompareExchangePointer_HLERelease](../intrinsics/interlockedcompareexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|void * _InterlockedCompareExchangePointer_HLERelease (void \*volatile \*, void \*, void \*)|  
|[_InterlockedCompareExchangePointer_np](../intrinsics/interlockedcompareexchangepointer-intrinsic-functions.md)||intrin.h|void * _InterlockedCompareExchangePointer_np (void \* \*, void \*, void \*)|  
|[_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)||intrin.h|długie _InterlockedDecrement(long volatile *)|  
|[_InterlockedDecrement16](../intrinsics/interlockeddecrement-intrinsic-functions.md)||intrin.h|krótki _InterlockedDecrement16 (krótka volatile * składnik dodawania)|  
|[_InterlockedDecrement64](../intrinsics/interlockeddecrement-intrinsic-functions.md)||intrin.h|__int64 _InterlockedDecrement64 (\__int64 volatile *)|  
|[_InterlockedExchange](../intrinsics/interlockedexchange-intrinsic-functions.md)||intrin.h|długie _InterlockedExchange (długo volatile * długim)|  
|[_InterlockedExchange_HLEAcquire](../intrinsics/interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedExchange_HLEAcquire (długo volatile * długim)|  
|[_InterlockedExchange_HLERelease](../intrinsics/interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedExchange_HLERelease (długo volatile * długim)|  
|[_InterlockedExchange16](../intrinsics/interlockedexchange-intrinsic-functions.md)||intrin.h|krótki _InterlockedExchange16 (krótka volatile *, krótki)|  
|[_InterlockedExchange64](../intrinsics/interlockedexchange-intrinsic-functions.md)||intrin.h|__int64 _InterlockedExchange64 (\__int64 volatile *,\__int64)|  
|[_InterlockedExchange64_HLEAcquire](../intrinsics/interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedExchange64_HLEAcquire (\__int64 volatile *,\__int64)|  
|[_InterlockedExchange64_HLERelease](../intrinsics/interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedExchange64_HLERelease (\__int64 volatile *,\__int64)|  
|[_InterlockedExchange8](../intrinsics/interlockedexchange-intrinsic-functions.md)||intrin.h|CHAR — _InterlockedExchange8 (char volatile *, char)|  
|[_InterlockedExchangeAdd](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)||intrin.h|_InterlockedExchangeAdd długi (długo volatile * długim)|  
|[_InterlockedExchangeAdd_HLEAcquire](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin.h|_InterlockedExchangeAdd_HLEAcquire długi (długo volatile * długim)|  
|[_InterlockedExchangeAdd_HLERelease](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin.h|_InterlockedExchangeAdd_HLERelease długi (długo volatile * długim)|  
|[_InterlockedExchangeAdd16](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)||intrin.h|_InterlockedExchangeAdd16 krótkich (krótka volatile *, krótki)|  
|[_InterlockedExchangeAdd64](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)||intrin.h|__int64 _InterlockedExchangeAdd64 (\__int64 volatile *,\__int64)|  
|[_InterlockedExchangeAdd64_HLEAcquire](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedExchangeAdd64_HLEAcquire (\__int64 volatile *,\__int64)|  
|[_InterlockedExchangeAdd64_HLERelease](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedExchangeAdd64_HLERelease (\__int64 volatile *,\__int64)|  
|[_InterlockedExchangeAdd8](../intrinsics/interlockedexchangeadd-intrinsic-functions.md)||intrin.h|CHAR _InterlockedExchangeAdd8 (char volatile *, char)|  
|[_InterlockedExchangePointer](../intrinsics/interlockedexchangepointer-intrinsic-functions.md)||intrin.h|void * _InterlockedExchangePointer (void \*volatile \*, void \*)|  
|[_InterlockedExchangePointer_HLEAcquire](../intrinsics/interlockedexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|void * _InterlockedExchangePointer_HLEAcquire (void \*volatile \*, void \*)|  
|[_InterlockedExchangePointer_HLERelease](../intrinsics/interlockedexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|void * _InterlockedExchangePointer_HLERelease (void \*volatile \*, void \*)|  
|[_InterlockedIncrement](../intrinsics/interlockedincrement-intrinsic-functions.md)||intrin.h|długie _InterlockedIncrement(long volatile *)|  
|[_InterlockedIncrement16](../intrinsics/interlockedincrement-intrinsic-functions.md)||intrin.h|krótki _InterlockedIncrement16 (krótka volatile * składnik dodawania)|  
|[_InterlockedIncrement64](../intrinsics/interlockedincrement-intrinsic-functions.md)||intrin.h|__int64 _InterlockedIncrement64 (\__int64 volatile *)|  
|[_InterlockedOr](../intrinsics/interlockedor-intrinsic-functions.md)||intrin.h|długie _InterlockedOr (długo volatile * długim)|  
|[_InterlockedOr_HLEAcquire](../intrinsics/interlockedor-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedOr_HLEAcquire (długo volatile * długim)|  
|[_InterlockedOr_HLERelease](../intrinsics/interlockedor-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedOr_HLERelease (długo volatile * długim)|  
|[_InterlockedOr_np](../intrinsics/interlockedor-intrinsic-functions.md)||intrin.h|_InterlockedOr_np długa (Liczba długa * długim)|  
|[_InterlockedOr16](../intrinsics/interlockedor-intrinsic-functions.md)||intrin.h|krótki _InterlockedOr16 (krótka volatile *, krótki)|  
|[_InterlockedOr16_np](../intrinsics/interlockedor-intrinsic-functions.md)||intrin.h|krótki _InterlockedOr16_np (short *, krótki)|  
|[_InterlockedOr64](../intrinsics/interlockedor-intrinsic-functions.md)||intrin.h|__int64 _InterlockedOr64 (\__int64 volatile *,\__int64)|  
|[_InterlockedOr64_HLEAcquire](../intrinsics/interlockedor-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedOr64_HLEAcquire (\__int64 volatile *,\__int64)|  
|[_InterlockedOr64_HLERelease](../intrinsics/interlockedor-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedOr64_HLERelease (\__int64 volatile *,\__int64)|  
|[_InterlockedOr64_np](../intrinsics/interlockedor-intrinsic-functions.md)||intrin.h|__int64 _InterlockedOr64_np (\__int64 *,\__int64)|  
|[_InterlockedOr8](../intrinsics/interlockedor-intrinsic-functions.md)||intrin.h|CHAR — _InterlockedOr8 (char volatile *, char)|  
|[_InterlockedOr8_np](../intrinsics/interlockedor-intrinsic-functions.md)||intrin.h|CHAR — _InterlockedOr8_np (char *, char)|  
|[_InterlockedXor](../intrinsics/interlockedxor-intrinsic-functions.md)||intrin.h|długie _InterlockedXor (długo volatile * długim)|  
|[_InterlockedXor_HLEAcquire](../intrinsics/interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedXor_HLEAcquire (długo volatile * długim)|  
|[_InterlockedXor_HLERelease](../intrinsics/interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin.h|długie _InterlockedXor_HLERelease (długo volatile * długim)|  
|[_InterlockedXor_np](../intrinsics/interlockedxor-intrinsic-functions.md)||intrin.h|_InterlockedXor_np długa (Liczba długa * długim)|  
|[_InterlockedXor16](../intrinsics/interlockedxor-intrinsic-functions.md)||intrin.h|krótki _InterlockedXor16 (krótka volatile *, krótki)|  
|[_InterlockedXor16_np](../intrinsics/interlockedxor-intrinsic-functions.md)||intrin.h|krótki _InterlockedXor16_np (short *, krótki)|  
|[_InterlockedXor64](../intrinsics/interlockedxor-intrinsic-functions.md)||intrin.h|__int64 _InterlockedXor64 (\__int64 volatile *,\__int64)|  
|[_InterlockedXor64_HLEAcquire](../intrinsics/interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedXor64_HLEAcquire (\__int64 volatile *,\__int64)|  
|[_InterlockedXor64_HLERelease](../intrinsics/interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedXor64_HLERelease (\__int64 volatile *,\__int64)|  
|[_InterlockedXor64_np](../intrinsics/interlockedxor-intrinsic-functions.md)||intrin.h|__int64 _InterlockedXor64_np (\__int64 *,\__int64)|  
|[_InterlockedXor8](../intrinsics/interlockedxor-intrinsic-functions.md)||intrin.h|CHAR — _InterlockedXor8 (char volatile *, char)|  
|[_InterlockedXor8_np](../intrinsics/interlockedxor-intrinsic-functions.md)||intrin.h|CHAR — _InterlockedXor8_np (char *, char)|  
|[__invlpg](../intrinsics/invlpg.md)||intrin.h|void __invlpg(void*)|  
|[_invpcid](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INVPCID [2]|immintrin.h|void _invpcid (unsigned int, void *)|  
|[__inword](../intrinsics/inword.md)||intrin.h|niepodpisane krótki __inword (bez znaku krótkich Port)|  
|[__inwordstring](../intrinsics/inwordstring.md)||intrin.h|void __inwordstring (unsigned krótkich portu, bez znaku krótko * buforu, bez znaku liczba długa)|  
|_lgdt||intrin.h|void _lgdt(void*)|  
|[__lidt](../intrinsics/lidt.md)||intrin.h|void __lidt(void*)|  
|[__ll_lshift](../intrinsics/ll-lshift.md)||intrin.h|__int64 bez znaku [pascal/cdecl] \__ll_lshift (bez znaku \__int64, int)|  
|[__ll_rshift](../intrinsics/ll-rshift.md)||intrin.h|__int64 [pascal/cdecl] \__ll_rshift (\__int64, int)|  
|__llwpcb|LWP [1]|ammintrin.h|void __llwpcb(void *)|  
|_load_be_u16<br /><br /> [_loadbe_i16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i16&expand=3071)|MOVBE|immintrin.h|niepodpisane _load_be_u16 krótkich (void const *);<br /><br /> krótki _loadbe_i16 (void const\*); [3]|  
|_load_be_u32<br /><br /> [_loadbe_i32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i32&expand=3072)|MOVBE|immintrin.h|unsigned int _load_be_u32 (void const *);<br /><br /> int _loadbe_i32 (void const\*); [3]|  
|_load_be_u64<br /><br /> [_loadbe_i64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i64&expand=3073)|MOVBE|immintrin.h|niepodpisane __int64 _load_be_u64 (void const *);<br /><br /> \__int64 _loadbe_i64 (void const\*); [3]|  
|__lwpins32|LWP [1]|ammintrin.h|unsigned char __lwpins32 (unsigned int, int bez znaku, unsigned int)|  
|__lwpins64|LWP [1]|ammintrin.h|unsigned char __lwpins64 (bez znaku \__int64, unsigned int, unsigned int)|  
|__lwpval32|LWP [1]|ammintrin.h|void __lwpval32 (unsigned int, int bez znaku, unsigned int)|  
|__lwpval64|LWP [1]|ammintrin.h|void __lwpval64 (bez znaku \__int64, unsigned int, unsigned int)|  
|[__lzcnt](../intrinsics/lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin.h|__lzcnt(unsigned int) unsigned int|  
|[_lzcnt_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|_lzcnt_u32(unsigned int) unsigned int|  
|[_lzcnt_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|niepodpisane __int64 _lzcnt_u64 (bez znaku \__int64)|  
|[__lzcnt16](../intrinsics/lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin.h|__lzcnt16(unsigned short) krótkich bez znaku|  
|[__lzcnt64](../intrinsics/lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin.h|niepodpisane __int64 \__lzcnt64 (bez znaku \__int64)|  
|_m_prefetch|3DNOW|intrin.h|void _m_prefetch(void*)|  
|_m_prefetchw|3DNOW|intrin.h|void _m_prefetchw(void*)|  
|[_mm_abs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_abs_epi16 (\__m128i)|  
|[_mm_abs_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_abs_epi32 (\__m128i)|  
|[_mm_abs_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_abs_epi8 (\__m128i)|  
|[_mm_add_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_add_epi16 (\__m128i,\__m128i)|  
|[_mm_add_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_add_epi32 (\__m128i,\__m128i)|  
|[_mm_add_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_add_epi64 (\__m128i,\__m128i)|  
|[_mm_add_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_add_epi8 (\__m128i,\__m128i)|  
|[_mm_add_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_add_pd (\__m128d,\__m128d)|  
|[_mm_add_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_add_ps (\__m128,\__m128)|  
|[_mm_add_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_add_sd (\__m128d,\__m128d)|  
|[_mm_add_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_add_ss (\__m128,\__m128)|  
|[_mm_adds_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_adds_epi16 (\__m128i,\__m128i)|  
|[_mm_adds_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_adds_epi8 (\__m128i,\__m128i)|  
|[_mm_adds_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_adds_epu16 (\__m128i,\__m128i)|  
|[_mm_adds_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_adds_epu8 (\__m128i,\__m128i)|  
|[_mm_addsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128d _mm_addsub_pd (\__m128d,\__m128d)|  
|[_mm_addsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128 _mm_addsub_ps (\__m128,\__m128)|  
|[_mm_aesdec_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AESNI [2]|immintrin.h|__m128i _mm_aesdec_si128 ( \__m128i,\__m128i)|  
|[_mm_aesdeclast_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AESNI [2]|immintrin.h|__m128i _mm_aesdeclast_si128 ( \__m128i,\__m128i)|  
|[_mm_aesenc_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AESNI [2]|immintrin.h|__m128i _mm_aesenc_si128 ( \__m128i,\__m128i)|  
|[_mm_aesenclast_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AESNI [2]|immintrin.h|__m128i _mm_aesenclast_si128 ( \__m128i,\__m128i)|  
|[_mm_aesimc_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AESNI [2]|immintrin.h|__m128i _mm_aesimc_si128 (\__m128i)|  
|[_mm_aeskeygenassist_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AESNI [2]|immintrin.h|__m128i _mm_aeskeygenassist_si128 (\__m128i, const int)|  
|[_mm_alignr_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_alignr_epi8 (\__m128i,\__m128i, int)|  
|[_mm_and_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_and_pd (\__m128d,\__m128d)|  
|[_mm_and_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_and_ps (\__m128,\__m128)|  
|[_mm_and_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_and_si128 (\__m128i,\__m128i)|  
|[_mm_andnot_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_andnot_pd (\__m128d,\__m128d)|  
|[_mm_andnot_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_andnot_ps (\__m128,\__m128)|  
|[_mm_andnot_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_andnot_si128 (\__m128i,\__m128i)|  
|[_mm_avg_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_avg_epu16 (\__m128i,\__m128i)|  
|[_mm_avg_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_avg_epu8 (\__m128i,\__m128i)|  
|[_mm_blend_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_blend_epi16 (\__m128i,\__m128i, const int)|  
|[_mm_blend_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_blend_epi32 (\__m128i,\__m128i, const int)|  
|[_mm_blend_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128d _mm_blend_pd (\__m128d,\__m128d, const int)|  
|[_mm_blend_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128 _mm_blend_ps (\__m128,\__m128, const int)|  
|[_mm_blendv_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_blendv_epi8 (\__m128i,\__m128i,\__m128i)|  
|[_mm_blendv_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128d _mm_blendv_pd (\__m128d,\__m128d,\__m128d)|  
|[_mm_blendv_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128 _mm_blendv_ps (\__m128,\__m128,\__m128)|  
|[_mm_broadcast_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm_broadcast_ss(float const *)|  
|[_mm_broadcastb_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_broadcastb_epi8 (\__m128i)|  
|[_mm_broadcastd_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_broadcastd_epi32 (\__m128i)|  
|[_mm_broadcastq_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_broadcastq_epi64 (\__m128i)|  
|[_mm_broadcastsd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128d _mm_broadcastsd_pd (\__m128d)|  
|[_mm_broadcastss_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128 _mm_broadcastss_ps (\__m128)|  
|[_mm_broadcastw_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_broadcastw_epi16 (\__m128i)|  
|[_mm_castpd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128 _mm_castpd_ps (\__m128d)|  
|[_mm_castpd_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_castpd_si128 (\__m128d)|  
|[_mm_castps_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128d _mm_castps_pd (\__m128)|  
|[_mm_castps_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_castps_si128 (\__m128)|  
|[_mm_castsi128_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128d _mm_castsi128_pd (\__m128i)|  
|[_mm_castsi128_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128 _mm_castsi128_ps (\__m128i)|  
|[_mm_clflush](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_clflush(void const *)|  
|[_mm_clmulepi64_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|PCLMULQDQ [2]|immintrin.h|__m128i _mm_clmulepi64_si128 (\__m128i,\__m128i, const int)|  
|_mm_cmov_si128|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_cmov_si128 (\__m128i,\__m128i,\__m128i)|  
|[_mm_cmp_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128d _mm_cmp_pd (\__m128d,\__m128d, const int)|  
|[_mm_cmp_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm_cmp_ps (\__m128,\__m128, const int)|  
|[_mm_cmp_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128d _mm_cmp_sd (\__m128d,\__m128d, const int)|  
|[_mm_cmp_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm_cmp_ss (\__m128,\__m128, const int)|  
|[_mm_cmpeq_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmpeq_epi16 (\__m128i,\__m128i)|  
|[_mm_cmpeq_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmpeq_epi32 (\__m128i,\__m128i)|  
|[_mm_cmpeq_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cmpeq_epi64 (\__m128i,\__m128i)|  
|[_mm_cmpeq_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmpeq_epi8 (\__m128i,\__m128i)|  
|[_mm_cmpeq_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpeq_pd (\__m128d,\__m128d)|  
|[_mm_cmpeq_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpeq_ps (\__m128,\__m128)|  
|[_mm_cmpeq_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpeq_sd (\__m128d,\__m128d)|  
|[_mm_cmpeq_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpeq_ss (\__m128,\__m128)|  
|[_mm_cmpestra](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpestra (\__m128i, int,\__m128i, int, const int)|  
|[_mm_cmpestrc](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpestrc (\__m128i, int,\__m128i, int, const int)|  
|[_mm_cmpestri](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpestri (\__m128i, int,\__m128i, int, const int)|  
|[_mm_cmpestrm](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|__m128i _mm_cmpestrm (\__m128i, int,\__m128i, int, const int)|  
|[_mm_cmpestro](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpestro (\__m128i, int,\__m128i, int, const int)|  
|[_mm_cmpestrs](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpestrs (\__m128i, int,\__m128i, int, const int)|  
|[_mm_cmpestrz](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpestrz (\__m128i, int,\__m128i, int, const int)|  
|[_mm_cmpge_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpge_pd (\__m128d,\__m128d)|  
|[_mm_cmpge_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpge_ps (\__m128,\__m128)|  
|[_mm_cmpge_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpge_sd (\__m128d,\__m128d)|  
|[_mm_cmpge_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpge_ss (\__m128,\__m128)|  
|[_mm_cmpgt_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmpgt_epi16 (\__m128i,\__m128i)|  
|[_mm_cmpgt_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmpgt_epi32 (\__m128i,\__m128i)|  
|[_mm_cmpgt_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|__m128i _mm_cmpgt_epi64 (\__m128i,\__m128i)|  
|[_mm_cmpgt_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmpgt_epi8 (\__m128i,\__m128i)|  
|[_mm_cmpgt_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpgt_pd (\__m128d,\__m128d)|  
|[_mm_cmpgt_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpgt_ps (\__m128,\__m128)|  
|[_mm_cmpgt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpgt_sd (\__m128d,\__m128d)|  
|[_mm_cmpgt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpgt_ss (\__m128,\__m128)|  
|[_mm_cmpistra](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpistra (\__m128i,\__m128i, const int)|  
|[_mm_cmpistrc](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpistrc (\__m128i,\__m128i, const int)|  
|[_mm_cmpistri](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpistri (\__m128i,\__m128i, const int)|  
|[_mm_cmpistrm](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|__m128i _mm_cmpistrm (\__m128i,\__m128i, const int)|  
|[_mm_cmpistro](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpistro (\__m128i,\__m128i, const int)|  
|[_mm_cmpistrs](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpistrs (\__m128i,\__m128i, const int)|  
|[_mm_cmpistrz](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|int _mm_cmpistrz (\__m128i,\__m128i, const int)|  
|[_mm_cmple_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmple_pd (\__m128d,\__m128d)|  
|[_mm_cmple_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmple_ps (\__m128,\__m128)|  
|[_mm_cmple_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmple_sd (\__m128d,\__m128d)|  
|[_mm_cmple_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmple_ss (\__m128,\__m128)|  
|[_mm_cmplt_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmplt_epi16 (\__m128i,\__m128i)|  
|[_mm_cmplt_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmplt_epi32 (\__m128i,\__m128i)|  
|[_mm_cmplt_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cmplt_epi8 (\__m128i,\__m128i)|  
|[_mm_cmplt_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmplt_pd (\__m128d,\__m128d)|  
|[_mm_cmplt_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmplt_ps (\__m128,\__m128)|  
|[_mm_cmplt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmplt_sd (\__m128d,\__m128d)|  
|[_mm_cmplt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmplt_ss (\__m128,\__m128)|  
|[_mm_cmpneq_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpneq_pd (\__m128d,\__m128d)|  
|[_mm_cmpneq_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpneq_ps (\__m128,\__m128)|  
|[_mm_cmpneq_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpneq_sd (\__m128d,\__m128d)|  
|[_mm_cmpneq_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpneq_ss (\__m128,\__m128)|  
|[_mm_cmpnge_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpnge_pd (\__m128d,\__m128d)|  
|[_mm_cmpnge_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpnge_ps (\__m128,\__m128)|  
|[_mm_cmpnge_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpnge_sd (\__m128d,\__m128d)|  
|[_mm_cmpnge_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpnge_ss (\__m128,\__m128)|  
|[_mm_cmpngt_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpngt_pd (\__m128d,\__m128d)|  
|[_mm_cmpngt_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpngt_ps (\__m128,\__m128)|  
|[_mm_cmpngt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpngt_sd (\__m128d,\__m128d)|  
|[_mm_cmpngt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpngt_ss (\__m128,\__m128)|  
|[_mm_cmpnle_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpnle_pd (\__m128d,\__m128d)|  
|[_mm_cmpnle_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpnle_ps (\__m128,\__m128)|  
|[_mm_cmpnle_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpnle_sd (\__m128d,\__m128d)|  
|[_mm_cmpnle_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpnle_ss (\__m128,\__m128)|  
|[_mm_cmpnlt_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpnlt_pd (\__m128d,\__m128d)|  
|[_mm_cmpnlt_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpnlt_ps (\__m128,\__m128)|  
|[_mm_cmpnlt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpnlt_sd (\__m128d,\__m128d)|  
|[_mm_cmpnlt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpnlt_ss (\__m128,\__m128)|  
|[_mm_cmpord_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpord_pd (\__m128d,\__m128d)|  
|[_mm_cmpord_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpord_ps (\__m128,\__m128)|  
|[_mm_cmpord_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpord_sd (\__m128d,\__m128d)|  
|[_mm_cmpord_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpord_ss (\__m128,\__m128)|  
|[_mm_cmpunord_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpunord_pd (\__m128d,\__m128d)|  
|[_mm_cmpunord_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpunord_ps (\__m128,\__m128)|  
|[_mm_cmpunord_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cmpunord_sd (\__m128d,\__m128d)|  
|[_mm_cmpunord_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cmpunord_ss (\__m128,\__m128)|  
|_mm_com_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_com_epi16 (\__m128i,\__m128i, int)|  
|_mm_com_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_com_epi32 (\__m128i,\__m128i, int)|  
|_mm_com_epi64|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_com_epi32 (\__m128i,\__m128i, int)|  
|_mm_com_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_com_epi8 (\__m128i,\__m128i, int)|  
|_mm_com_epu16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_com_epu16 (\__m128i,\__m128i, int)|  
|_mm_com_epu32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_com_epu32 (\__m128i,\__m128i, int)|  
|_mm_com_epu64|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_com_epu32 (\__m128i,\__m128i, int)|  
|_mm_com_epu8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_com_epu8 (\__m128i,\__m128i, int)|  
|[_mm_comieq_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_comieq_sd (\__m128d,\__m128d)|  
|[_mm_comieq_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_comieq_ss (\__m128,\__m128)|  
|[_mm_comige_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_comige_sd (\__m128d,\__m128d)|  
|[_mm_comige_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_comige_ss (\__m128,\__m128)|  
|[_mm_comigt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_comigt_sd (\__m128d,\__m128d)|  
|[_mm_comigt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_comigt_ss (\__m128,\__m128)|  
|[_mm_comile_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_comile_sd (\__m128d,\__m128d)|  
|[_mm_comile_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_comile_ss (\__m128,\__m128)|  
|[_mm_comilt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_comilt_sd (\__m128d,\__m128d)|  
|[_mm_comilt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_comilt_ss (\__m128,\__m128)|  
|[_mm_comineq_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_comineq_sd (\__m128d,\__m128d)|  
|[_mm_comineq_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_comineq_ss (\__m128,\__m128)|  
|[_mm_crc32_u16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|unsigned int _mm_crc32_u16 (unsigned int, krótko bez znaku)|  
|[_mm_crc32_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|unsigned int _mm_crc32_u32 (unsigned int, int bez znaku)|  
|[_mm_crc32_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|niepodpisane __int64 _mm_crc32_u64 (bez znaku \__int64 niepodpisane \__int64)|  
|[_mm_crc32_u8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE42|intrin.h|unsigned int _mm_crc32_u8 (unsigned int, char bez znaku)|  
|[_mm_cvt_si2ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cvt_si2ss (\__m128, int)|  
|[_mm_cvt_ss2si](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_cvt_ss2si (\__m128)|  
|[_mm_cvtepi16_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepi16_epi32 (\__m128i)|  
|[_mm_cvtepi16_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepi16_epi64 (\__m128i)|  
|[_mm_cvtepi32_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepi32_epi64 (\__m128i)|  
|[_mm_cvtepi32_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cvtepi32_pd (\__m128i)|  
|[_mm_cvtepi32_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128 _mm_cvtepi32_ps (\__m128i)|  
|[_mm_cvtepi8_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepi8_epi16 (\__m128i)|  
|[_mm_cvtepi8_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepi8_epi32 (\__m128i)|  
|[_mm_cvtepi8_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepi8_epi64 (\__m128i)|  
|[_mm_cvtepu16_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepu16_epi32 (\__m128i)|  
|[_mm_cvtepu16_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepu16_epi64 (\__m128i)|  
|[_mm_cvtepu32_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepu32_epi64 (\__m128i)|  
|[_mm_cvtepu8_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepu8_epi16 (\__m128i)|  
|[_mm_cvtepu8_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepu8_epi32 (\__m128i)|  
|[_mm_cvtepu8_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_cvtepu8_epi64 (\__m128i)|  
|[_mm_cvtpd_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cvtpd_epi32 (\__m128d)|  
|[_mm_cvtpd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128 _mm_cvtpd_ps (\__m128d)|  
|[_mm_cvtph_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|F16C [2]|immintrin.h|__m128 _mm_cvtph_ps (\__m128i)|  
|[_mm_cvtps_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cvtps_epi32 (\__m128)|  
|[_mm_cvtps_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cvtps_pd (\__m128)|  
|[_mm_cvtps_ph](http://go.microsoft.com/fwlink/p/?LinkId=512130)|F16C [2]|immintrin.h|__m128i _mm_cvtps_ph (\__m128, const int)|  
|[_mm_cvtsd_f64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|Podwójna _mm_cvtsd_f64 (\__m128d)|  
|[_mm_cvtsd_si32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_cvtsd_si32 (\__m128d)|  
|[_mm_cvtsd_si64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__int64 _mm_cvtsd_si64 (\__m128d)|  
|[_mm_cvtsd_si64x](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__int64 _mm_cvtsd_si64x (\__m128d)|  
|[_mm_cvtsd_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128 _mm_cvtsd_ss (\__m128,\__m128d)|  
|[_mm_cvtsi128_si32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_cvtsi128_si32 (\__m128i)|  
|[_mm_cvtsi128_si64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__int64 _mm_cvtsi128_si64 (\__m128i)|  
|[_mm_cvtsi128_si64x](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__int64 _mm_cvtsi128_si64x (\__m128i)|  
|[_mm_cvtsi32_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cvtsi32_sd (\__m128d, int)|  
|[_mm_cvtsi32_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cvtsi32_si128(int)|  
|[_mm_cvtsi64_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cvtsi64_sd (\__m128d,\__int64)|  
|[_mm_cvtsi64_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cvtsi64_si128 (\__int64)|  
|[_mm_cvtsi64_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_cvtsi64_ss (\__m128,\__int64)|  
|[_mm_cvtsi64x_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cvtsi64x_sd (\__m128d,\__int64 b).|  
|[_mm_cvtsi64x_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cvtsi64x_si128 (\__int64)|  
|[_mm_cvtsi64x_ss](../intrinsics/mm-cvtsi64x-ss.md)|SSE2|intrin.h|__m128 _mm_cvtsi64x_ss (\__m128,\__int64 b).|  
|[_mm_cvtss_f32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|float _mm_cvtss_f32 (\__m128)|  
|[_mm_cvtss_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_cvtss_sd (\__m128d,\__m128)|  
|[_mm_cvtss_si64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__int64 _mm_cvtss_si64 (\__m128)|  
|[_mm_cvtss_si64x](../intrinsics/mm-cvtss-si64x.md)|SSE2|intrin.h|__int64 _mm_cvtss_si64x (\__m128)|  
|[_mm_cvtt_ss2si](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_cvtt_ss2si (\__m128)|  
|[_mm_cvttpd_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cvttpd_epi32 (\__m128d)|  
|[_mm_cvttps_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_cvttps_epi32 (\__m128)|  
|[_mm_cvttsd_si32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_cvttsd_si32 (\__m128d)|  
|[_mm_cvttsd_si64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__int64 _mm_cvttsd_si64 (\__m128d)|  
|[_mm_cvttsd_si64x](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__int64 _mm_cvttsd_si64x (\__m128d)|  
|[_mm_cvttss_si64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__int64 _mm_cvttss_si64 (\__m128)|  
|[_mm_cvttss_si64x](../intrinsics/mm-cvttss-si64x.md)|SSE2|intrin.h|__int64 _mm_cvttss_si64x (\__m128)|  
|[_mm_div_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_div_pd (\__m128d,\__m128d)|  
|[_mm_div_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_div_ps (\__m128,\__m128)|  
|[_mm_div_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_div_sd (\__m128d,\__m128d)|  
|[_mm_div_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_div_ss (\__m128,\__m128)|  
|[_mm_dp_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128d _mm_dp_pd (\__m128d,\__m128d, const int)|  
|[_mm_dp_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128 _mm_dp_ps (\__m128,\__m128, const int)|  
|[_mm_extract_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_extract_epi16 (\__m128i, int)|  
|[_mm_extract_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|int _mm_extract_epi32 (\__m128i, const int)|  
|[_mm_extract_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__int64 _mm_extract_epi64 (\__m128i, const int)|  
|[_mm_extract_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|int _mm_extract_epi8 (\__m128i, const int)|  
|[_mm_extract_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|int _mm_extract_ps (\__m128, const int)|  
|[_mm_extract_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)|SSE4a|intrin.h|__m128i _mm_extract_si64 (\__m128i,\__m128i)|  
|[_mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)|SSE4a|intrin.h|__m128i _mm_extracti_si64 (\__m128i, int, int)|  
|[_mm_fmadd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fmadd_pd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fmadd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fmadd_ps (\__m128,\__m128 b\__m128 c).|  
|[_mm_fmadd_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fmadd_sd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fmadd_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fmadd_ss (\__m128,\__m128 b\__m128 c).|  
|[_mm_fmaddsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fmaddsub_pd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fmaddsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fmaddsub_ps (\__m128,\__m128 b\__m128 c).|  
|[_mm_fmsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fmsub_pd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fmsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fmsub_ps (\__m128,\__m128 b\__m128 c).|  
|[_mm_fmsub_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fmsub_sd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fmsub_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fmsub_ss (\__m128,\__m128 b\__m128 c).|  
|[_mm_fmsubadd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fmsubadd_pd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fmsubadd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fmsubadd_ps (\__m128,\__m128 b\__m128 c).|  
|[_mm_fnmadd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fnmadd_pd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fnmadd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fnmadd_ps (\__m128,\__m128 b\__m128 c).|  
|[_mm_fnmadd_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fnmadd_sd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fnmadd_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fnmadd_ss (\__m128,\__m128 b\__m128 c).|  
|[_mm_fnmsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fnmsub_pd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fnmsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fnmsub_ps (\__m128,\__m128 b\__m128 c).|  
|[_mm_fnmsub_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128d _mm_fnmsub_sd (\__m128d,\__m128d b\__m128d c).|  
|[_mm_fnmsub_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m128 _mm_fnmsub_ss (\__m128,\__m128 b\__m128 c).|  
|_mm_frcz_pd|ELEMENT XOP [1]|ammintrin.h|__m128d _mm_frcz_pd (\__m128d)|  
|_mm_frcz_ps|ELEMENT XOP [1]|ammintrin.h|__m128 _mm_frcz_ps (\__m128)|  
|_mm_frcz_sd|ELEMENT XOP [1]|ammintrin.h|__m128d _mm_frcz_sd (\__m128d,\__m128d)|  
|_mm_frcz_ss|ELEMENT XOP [1]|ammintrin.h|__m128 _mm_frcz_ss (\__m128,\__m128)|  
|[_mm_getcsr](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|_mm_getcsr(void) unsigned int|  
|[_mm_hadd_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_hadd_epi16 (\__m128i,\__m128i)|  
|[_mm_hadd_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_hadd_epi32 (\__m128i,\__m128i)|  
|[_mm_hadd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128d _mm_hadd_pd (\__m128d,\__m128d)|  
|[_mm_hadd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128 _mm_hadd_ps (\__m128,\__m128)|  
|_mm_haddd_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddd_epi16 (\__m128i)|  
|_mm_haddd_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddd_epi8 (\__m128i)|  
|_mm_haddd_epu16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddd_epu16 (\__m128i)|  
|_mm_haddd_epu8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddd_epu8 (\__m128i)|  
|_mm_haddq_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddq_epi16 (\__m128i)|  
|_mm_haddq_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddq_epi32 (\__m128i)|  
|_mm_haddq_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddq_epi8 (\__m128i)|  
|_mm_haddq_epu16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddq_epu16 (\__m128i)|  
|_mm_haddq_epu32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddq_epu32 (\__m128i)|  
|_mm_haddq_epu8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddq_epu8 (\__m128i)|  
|[_mm_hadds_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_hadds_epi16 (\__m128i,\__m128i)|  
|_mm_haddw_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddw_epi8 (\__m128i)|  
|_mm_haddw_epu8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_haddw_epu8 (\__m128i)|  
|[_mm_hsub_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_hsub_epi16 (\__m128i,\__m128i)|  
|[_mm_hsub_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_hsub_epi32 (\__m128i,\__m128i)|  
|[_mm_hsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128d _mm_hsub_pd (\__m128d,\__m128d)|  
|[_mm_hsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128 _mm_hsub_ps (\__m128,\__m128)|  
|_mm_hsubd_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_hsubd_epi16 (\__m128i)|  
|_mm_hsubq_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_hsubq_epi32 (\__m128i)|  
|[_mm_hsubs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_hsubs_epi16 (\__m128i,\__m128i)|  
|_mm_hsubw_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_hsubw_epi8 (\__m128i)|  
|[_mm_i32gather_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_i32gather_epi32 (int const * elementu bazowego,\__m128i indeksu, const int skali)|  
|[_mm_i32gather_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_i32gather_epi64 (\__int64 const * podstawowej,\__m128i indeksu, const int skali)|  
|[_mm_i32gather_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128d _mm_i32gather_pd (dwa razy const * elementu bazowego,\__m128i indeksu, const int skali)|  
|[_mm_i32gather_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128 _mm_i32gather_ps (float const * elementu bazowego,\__m128i indeksu, const int skali)|  
|[_mm_i64gather_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_i64gather_epi32 (int const * elementu bazowego,\__m128i indeksu, const int skali)|  
|[_mm_i64gather_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_i64gather_epi64 (\__int64 const * podstawowej,\__m128i indeksu, const int skali)|  
|[_mm_i64gather_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128d _mm_i64gather_pd (dwa razy const * elementu bazowego,\__m128i indeksu, const int skali)|  
|[_mm_i64gather_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128 _mm_i64gather_ps (float const * elementu bazowego,\__m128i indeksu, const int skali)|  
|[_mm_insert_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_insert_epi16 (\__m128i, int, int)|  
|[_mm_insert_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_insert_epi32 (\__m128i, int, const int)|  
|[_mm_insert_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_insert_epi64 (\__m128i,\__int64, const int)|  
|[_mm_insert_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_insert_epi8 (\__m128i, int, const int)|  
|[_mm_insert_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128 _mm_insert_ps (\__m128,\__m128, const int)|  
|[_mm_insert_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)|SSE4a|intrin.h|__m128i _mm_insert_si64 (\__m128i,\__m128i)|  
|[_mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)|SSE4a|intrin.h|__m128i _mm_inserti_si64 (\__m128i,\__m128i, int, int)|  
|[_mm_lddqu_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128i _mm_lddqu_si128 (\__m128i const *)|  
|[_mm_lfence](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_lfence(void)|  
|[_mm_load_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_load_pd(double*)|  
|[_mm_load_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_load_ps(float*)|  
|[_mm_load_ps1](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_load_ps1(float*)|  
|[_mm_load_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_load_sd(double*)|  
|[_mm_load_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_load_si128 (\__m128i *)|  
|[_mm_load_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_load_ss(float*)|  
|[_mm_load1_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_load1_pd(double*)|  
|[_mm_loaddup_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128d _mm_loaddup_pd (dwa razy const *)|  
|[_mm_loadh_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_loadh_pd (\__m128d, double *)|  
|[_mm_loadh_pi](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_loadh_pi (\__m128,\_typu _m64 *)|  
|[_mm_loadl_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_loadl_epi64 (\__m128i *)|  
|[_mm_loadl_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_loadl_pd (\__m128d, double *)|  
|[_mm_loadl_pi](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_loadl_pi (\__m128,\_typu _m64 *)|  
|[_mm_loadr_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_loadr_pd(double*)|  
|[_mm_loadr_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_loadr_ps(float*)|  
|[_mm_loadu_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_loadu_pd(double*)|  
|[_mm_loadu_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_loadu_ps(float*)|  
|[_mm_loadu_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_loadu_si128 (\__m128i *)|  
|_mm_macc_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_macc_epi16 (\__m128i,\__m128i,\__m128i)|  
|_mm_macc_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_macc_epi32 (\__m128i,\__m128i,\__m128i)|  
|_mm_macc_pd|FMA4 [1]|ammintrin.h|__m128d _mm_macc_pd (\__m128d,\__m128d,\__m128d)|  
|_mm_macc_ps|FMA4 [1]|ammintrin.h|__m128 _mm_macc_ps (\__m128,\__m128,\__m128)|  
|_mm_macc_sd|FMA4 [1]|ammintrin.h|__m128d _mm_macc_sd (\__m128d,\__m128d,\__m128d)|  
|_mm_macc_ss|FMA4 [1]|ammintrin.h|__m128 _mm_macc_ss (\__m128,\__m128,\__m128)|  
|_mm_maccd_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_maccd_epi16 (\__m128i,\__m128i,\__m128i)|  
|_mm_macchi_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_macchi_epi32 (\__m128i,\__m128i,\__m128i)|  
|_mm_macclo_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_macclo_epi32 (\__m128i,\__m128i,\__m128i)|  
|_mm_maccs_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_maccs_epi16 (\__m128i,\__m128i,\__m128i)|  
|_mm_maccs_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_maccs_epi32 (\__m128i,\__m128i,\__m128i)|  
|_mm_maccsd_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_maccsd_epi16 (\__m128i,\__m128i,\__m128i)|  
|_mm_maccshi_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_maccshi_epi32 (\__m128i,\__m128i,\__m128i)|  
|_mm_maccslo_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_maccslo_epi32 (\__m128i,\__m128i,\__m128i)|  
|[_mm_madd_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_madd_epi16 (\__m128i,\__m128i)|  
|_mm_maddd_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_maddd_epi16 (\__m128i,\__m128i,\__m128i)|  
|_mm_maddsd_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_maddsd_epi16 (\__m128i,\__m128i,\__m128i)|  
|_mm_maddsub_pd|FMA4 [1]|ammintrin.h|__m128d _mm_maddsub_pd (\__m128d,\__m128d,\__m128d)|  
|_mm_maddsub_ps|FMA4 [1]|ammintrin.h|__m128 _mm_maddsub_ps (\__m128,\__m128,\__m128)|  
|[_mm_maddubs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_maddubs_epi16 (\__m128i,\__m128i)|  
|[_mm_mask_i32gather_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_mask_i32gather_epi32 (\__m128i src, int const * podstawowej,\_indeksu _m128i\__m128i maski, const int skali)|  
|[_mm_mask_i32gather_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_mask_i32gather_epi64 (\__m128i src\__int64 const * podstawowej,\_indeksu _m128i\__m128i maski, const int skali)|  
|[_mm_mask_i32gather_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128d _mm_mask_i32gather_pd (\__m128d src, double const * podstawowej,\_indeksu _m128i\__m128d maski, const int skali)|  
|[_mm_mask_i32gather_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128 _mm_mask_i32gather_ps (\__m128 src, float const * podstawowej,\_indeksu _m128i\__m128 maski, const int skali)|  
|[_mm_mask_i64gather_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_mask_i64gather_epi32 (\__m128i src, int const * podstawowej,\_indeksu _m128i\__m128i maski, const int skali)|  
|[_mm_mask_i64gather_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_mask_i64gather_epi64 (\__m128i src\__int64 const * podstawowej,\_indeksu _m128i\__m128i maski, const int skali)|  
|[_mm_mask_i64gather_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128d _mm_mask_i64gather_pd (\__m128d src, double const * podstawowej,\_indeksu _m128i\__m128d maski, const int skali)|  
|[_mm_mask_i64gather_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128 _mm_mask_i64gather_ps (\__m128 src, float const * podstawowej,\_indeksu _m128i\__m128 maski, const int skali)|  
|[_mm_maskload_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_maskload_epi32 (int const *,\__m128i)|  
|[_mm_maskload_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_maskload_epi64 ( \__int64 const *,\__m128i)|  
|[_mm_maskload_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128d _mm_maskload_pd (dwa razy const *,\__m128i)|  
|[_mm_maskload_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm_maskload_ps (float const *,\__m128i)|  
|[_mm_maskmoveu_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_maskmoveu_si128 (\__m128i,\__m128i, char *)|  
|[_mm_maskstore_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|void _mm_maskstore_epi32 (int *,\__m128i,\__m128i)|  
|[_mm_maskstore_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|void _mm_maskstore_epi64 (\__int64 *,\__m128i,\__m128i)|  
|[_mm_maskstore_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm_maskstore_pd (o podwójnej precyzji *,\__m128i,\__m128d)|  
|[_mm_maskstore_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm_maskstore_ps (float *,\__m128i,\__m128)|  
|[_mm_max_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_max_epi16 (\__m128i,\__m128i)|  
|[_mm_max_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_max_epi32 (\__m128i,\__m128i)|  
|[_mm_max_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_max_epi8 (\__m128i,\__m128i)|  
|[_mm_max_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_max_epu16 (\__m128i,\__m128i)|  
|[_mm_max_epu32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_max_epu32 (\__m128i,\__m128i)|  
|[_mm_max_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_max_epu8 (\__m128i,\__m128i)|  
|[_mm_max_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_max_pd (\__m128d,\__m128d)|  
|[_mm_max_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_max_ps (\__m128,\__m128)|  
|[_mm_max_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_max_sd (\__m128d,\__m128d)|  
|[_mm_max_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_max_ss (\__m128,\__m128)|  
|[_mm_mfence](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_mfence(void)|  
|[_mm_min_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_min_epi16 (\__m128i,\__m128i)|  
|[_mm_min_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_min_epi32 (\__m128i,\__m128i)|  
|[_mm_min_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_min_epi8 (\__m128i,\__m128i)|  
|[_mm_min_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_min_epu16 (\__m128i,\__m128i)|  
|[_mm_min_epu32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_min_epu32 (\__m128i,\__m128i)|  
|[_mm_min_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_min_epu8 (\__m128i,\__m128i)|  
|[_mm_min_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_min_pd (\__m128d,\__m128d)|  
|[_mm_min_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_min_ps (\__m128,\__m128)|  
|[_mm_min_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_min_sd (\__m128d,\__m128d)|  
|[_mm_min_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_min_ss (\__m128,\__m128)|  
|[_mm_minpos_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_minpos_epu16 (\__m128i)|  
|[_mm_monitor](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|void _mm_monitor (void const *, unsigned int, int bez znaku)|  
|[_mm_move_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_move_epi64 (\__m128i)|  
|[_mm_move_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_move_sd (\__m128d,\__m128d)|  
|[_mm_move_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_move_ss (\__m128,\__m128)|  
|[_mm_movedup_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128d _mm_movedup_pd (\__m128d)|  
|[_mm_movehdup_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128 _mm_movehdup_ps (\__m128)|  
|[_mm_movehl_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_movehl_ps (\__m128,\__m128)|  
|[_mm_moveldup_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|__m128 _mm_moveldup_ps (\__m128)|  
|[_mm_movelh_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_movelh_ps (\__m128,\__m128)|  
|[_mm_movemask_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_movemask_epi8 (\__m128i)|  
|[_mm_movemask_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_movemask_pd (\__m128d)|  
|[_mm_movemask_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_movemask_ps (\__m128)|  
|[_mm_mpsadbw_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_mpsadbw_epu8 (\__m128i s1\__m128i, const int)|  
|_mm_msub_pd|FMA4 [1]|ammintrin.h|__m128d _mm_msub_pd (\__m128d,\__m128d,\__m128d)|  
|_mm_msub_ps|FMA4 [1]|ammintrin.h|__m128 _mm_msub_ps (\__m128,\__m128,\__m128)|  
|_mm_msub_sd|FMA4 [1]|ammintrin.h|__m128d _mm_msub_sd (\__m128d,\__m128d,\__m128d)|  
|_mm_msub_ss|FMA4 [1]|ammintrin.h|__m128 _mm_msub_ss (\__m128,\__m128,\__m128)|  
|_mm_msubadd_pd|FMA4 [1]|ammintrin.h|__m128d _mm_msubadd_pd (\__m128d,\__m128d,\__m128d)|  
|_mm_msubadd_ps|FMA4 [1]|ammintrin.h|__m128 _mm_msubadd_ps (\__m128,\__m128,\__m128)|  
|[_mm_mul_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_mul_epi32 (\__m128i,\__m128i)|  
|[_mm_mul_epu32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_mul_epu32 (\__m128i,\__m128i)|  
|[_mm_mul_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_mul_pd (\__m128d,\__m128d)|  
|[_mm_mul_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_mul_ps (\__m128,\__m128)|  
|[_mm_mul_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_mul_sd (\__m128d,\__m128d)|  
|[_mm_mul_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_mul_ss (\__m128,\__m128)|  
|[_mm_mulhi_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_mulhi_epi16 (\__m128i,\__m128i)|  
|[_mm_mulhi_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_mulhi_epu16 (\__m128i,\__m128i)|  
|[_mm_mulhrs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_mulhrs_epi16 (\__m128i,\__m128i)|  
|[_mm_mullo_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_mullo_epi16 (\__m128i,\__m128i)|  
|[_mm_mullo_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_mullo_epi32 (\__m128i,\__m128i)|  
|[_mm_mwait](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE3|intrin.h|void _mm_mwait (unsigned int, int bez znaku)|  
|_mm_nmacc_pd|FMA4 [1]|ammintrin.h|__m128d _mm_nmacc_pd (\__m128d,\__m128d,\__m128d)|  
|_mm_nmacc_ps|FMA4 [1]|ammintrin.h|__m128 _mm_nmacc_ps (\__m128,\__m128,\__m128)|  
|_mm_nmacc_sd|FMA4 [1]|ammintrin.h|__m128d _mm_nmacc_sd (\__m128d,\__m128d,\__m128d)|  
|_mm_nmacc_ss|FMA4 [1]|ammintrin.h|__m128 _mm_nmacc_ss (\__m128,\__m128,\__m128)|  
|_mm_nmsub_pd|FMA4 [1]|ammintrin.h|__m128d _mm_nmsub_pd (\__m128d,\__m128d,\__m128d)|  
|_mm_nmsub_ps|FMA4 [1]|ammintrin.h|__m128 _mm_nmsub_ps (\__m128,\__m128,\__m128)|  
|_mm_nmsub_sd|FMA4 [1]|ammintrin.h|__m128d _mm_nmsub_sd (\__m128d,\__m128d,\__m128d)|  
|_mm_nmsub_ss|FMA4 [1]|ammintrin.h|__m128 _mm_nmsub_ss (\__m128,\__m128,\__m128)|  
|[_mm_or_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_or_pd (\__m128d,\__m128d)|  
|[_mm_or_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_or_ps (\__m128,\__m128)|  
|[_mm_or_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_or_si128 (\__m128i,\__m128i)|  
|[_mm_packs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_packs_epi16 (\__m128i,\__m128i)|  
|[_mm_packs_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_packs_epi32 (\__m128i,\__m128i)|  
|[_mm_packus_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_packus_epi16 (\__m128i,\__m128i)|  
|[_mm_packus_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_packus_epi32 (\__m128i,\__m128i)|  
|[_mm_pause](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_pause(void)|  
|_mm_perm_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_perm_epi8 (\__m128i,\__m128i,\__m128i)|  
|[_mm_permute_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128d _mm_permute_pd (\__m128d, int)|  
|[_mm_permute_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm_permute_ps (\__m128, int)|  
|_mm_permute2_pd|ELEMENT XOP [1]|ammintrin.h|__m128d _mm_permute2_pd (\__m128d,\__m128d,\__m128i, int)|  
|_mm_permute2_ps|ELEMENT XOP [1]|ammintrin.h|__m128 _mm_permute2_ps (\__m128,\__m128,\__m128i, int)|  
|[_mm_permutevar_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128d _mm_permutevar_pd (\__m128d,\__m128i)|  
|[_mm_permutevar_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm_permutevar_ps (\__m128,\__m128i)|  
|[_mm_popcnt_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|POPCNT|intrin.h|int _mm_popcnt_u32(unsigned int)|  
|[_mm_popcnt_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|POPCNT|intrin.h|__int64 _mm_popcnt_u64 (bez znaku \__int64)|  
|[_mm_prefetch](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_prefetch(char*,int)|  
|[_mm_rcp_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_rcp_ps (\__m128)|  
|[_mm_rcp_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_rcp_ss (\__m128)|  
|_mm_rot_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_rot_epi16 (\__m128i,\__m128i)|  
|_mm_rot_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_rot_epi32 (\__m128i,\__m128i)|  
|_mm_rot_epi64|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_rot_epi64 (\__m128i,\__m128i)|  
|_mm_rot_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_rot_epi8 (\__m128i,\__m128i)|  
|_mm_roti_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_rot_epi16 (\__m128i, int)|  
|_mm_roti_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_rot_epi32 (\__m128i, int)|  
|_mm_roti_epi64|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_rot_epi64 (\__m128i, int)|  
|_mm_roti_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_rot_epi8 (\__m128i, int)|  
|[_mm_round_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128d _mm_round_pd (\__m128d, const int)|  
|[_mm_round_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128 _mm_round_ps (\__m128, const int)|  
|[_mm_round_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128d _mm_round_sd (\__m128d,\__m128d, const int)|  
|[_mm_round_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128 _mm_round_ss (\__m128,\__m128, const int)|  
|[_mm_rsqrt_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_rsqrt_ps (\__m128)|  
|[_mm_rsqrt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_rsqrt_ss (\__m128)|  
|[_mm_sad_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sad_epu8 (\__m128i,\__m128i)|  
|[_mm_set_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_set_epi16(short,short,short,short,short,short,short,short)|  
|[_mm_set_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_set_epi32(int,int,int,int)|  
|[_mm_set_epi64x](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_set_epi64x (\__int64 i1\__int64 i0)|  
|[_mm_set_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_set_epi8(char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char)|  
|[_mm_set_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_set_pd(double,double)|  
|[_mm_set_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_set_ps(float,float,float,float)|  
|[_mm_set_ps1](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_set_ps1(float)|  
|[_mm_set_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_set_sd(double)|  
|[_mm_set_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_set_ss(float)|  
|[_mm_set1_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_set1_epi16(short)|  
|[_mm_set1_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_set1_epi32(int)|  
|[_mm_set1_epi64x](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_set1_epi64x (\__int64 i)|  
|[_mm_set1_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_set1_epi8(char)|  
|[_mm_set1_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_set1_pd(double)|  
|[_mm_setcsr](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_setcsr(unsigned int)|  
|_mm_setl_epi64|SSE2|intrin.h|__m128i _mm_setl_epi64 (\__m128i)|  
|[_mm_setr_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_setr_epi16(short,short,short,short,short,short,short,short)|  
|[_mm_setr_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_setr_epi32(int,int,int,int)|  
|[_mm_setr_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_setr_epi8(char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char)|  
|[_mm_setr_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_setr_pd(double,double)|  
|[_mm_setr_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_setr_ps(float,float,float,float)|  
|[_mm_setzero_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_setzero_pd(void)|  
|[_mm_setzero_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_setzero_ps(void)|  
|[_mm_setzero_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_setzero_si128(void)|  
|[_mm_sfence](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_sfence(void)|  
|_mm_sha_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_sha_epi16 (\__m128i,\__m128i)|  
|_mm_sha_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_sha_epi32 (\__m128i,\__m128i)|  
|_mm_sha_epi64|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_sha_epi64 (\__m128i,\__m128i)|  
|_mm_sha_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_sha_epi8 (\__m128i,\__m128i)|  
|_mm_shl_epi16|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_shl_epi16 (\__m128i,\__m128i)|  
|_mm_shl_epi32|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_shl_epi32 (\__m128i,\__m128i)|  
|_mm_shl_epi64|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_shl_epi64 (\__m128i,\__m128i)|  
|_mm_shl_epi8|ELEMENT XOP [1]|ammintrin.h|__m128i _mm_shl_epi8 (\__m128i,\__m128i)|  
|[_mm_shuffle_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_shuffle_epi32 (\__m128i, int)|  
|[_mm_shuffle_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_shuffle_epi8 (\__m128i,\__m128i)|  
|[_mm_shuffle_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_shuffle_pd (\__m128d,\__m128d, int)|  
|[_mm_shuffle_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_shuffle_ps (\__m128,\__m128, unsigned int)|  
|[_mm_shufflehi_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_shufflehi_epi16 (\__m128i, int)|  
|[_mm_shufflelo_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_shufflelo_epi16 (\__m128i, int)|  
|[_mm_sign_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_sign_epi16 (\__m128i,\__m128i)|  
|[_mm_sign_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_sign_epi32 (\__m128i,\__m128i)|  
|[_mm_sign_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|INSTRUKCJI SSSE3|intrin.h|__m128i _mm_sign_epi8 (\__m128i,\__m128i)|  
|[_mm_sll_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sll_epi16 (\__m128i,\__m128i)|  
|[_mm_sll_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sll_epi32 (\__m128i,\__m128i)|  
|[_mm_sll_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sll_epi64 (\__m128i,\__m128i)|  
|[_mm_slli_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_slli_epi16 (\__m128i, int)|  
|[_mm_slli_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_slli_epi32 (\__m128i, int)|  
|[_mm_slli_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_slli_epi64 (\__m128i, int)|  
|[_mm_slli_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_slli_si128 (\__m128i, int)|  
|[_mm_sllv_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_sllv_epi32 (\__m128i,\__m128i)|  
|[_mm_sllv_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_sllv_epi64 (\__m128i,\__m128i)|  
|[_mm_sqrt_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_sqrt_pd (\__m128d)|  
|[_mm_sqrt_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_sqrt_ps (\__m128)|  
|[_mm_sqrt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_sqrt_sd (\__m128d,\__m128d)|  
|[_mm_sqrt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_sqrt_ss (\__m128)|  
|[_mm_sra_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sra_epi16 (\__m128i,\__m128i)|  
|[_mm_sra_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sra_epi32 (\__m128i,\__m128i)|  
|[_mm_srai_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srai_epi16 (\__m128i, int)|  
|[_mm_srai_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srai_epi32 (\__m128i, int)|  
|[_mm_srav_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_srav_epi32 (\__m128i,\__m128i)|  
|[_mm_srl_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srl_epi16 (\__m128i,\__m128i)|  
|[_mm_srl_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srl_epi32 (\__m128i,\__m128i)|  
|[_mm_srl_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srl_epi64 (\__m128i,\__m128i)|  
|[_mm_srli_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srli_epi16 (\__m128i, int)|  
|[_mm_srli_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srli_epi32 (\__m128i, int)|  
|[_mm_srli_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srli_epi64 (\__m128i, int)|  
|[_mm_srli_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_srli_si128 (\__m128i, int)|  
|[_mm_srlv_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_srlv_epi32 (\__m128i,\__m128i)|  
|[_mm_srlv_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm_srlv_epi64 (\__m128i,\__m128i)|  
|[_mm_store_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_store_pd (o podwójnej precyzji *\__m128d)|  
|[_mm_store_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_store_ps (float *\__m128)|  
|[_mm_store_ps1](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_store_ps1 (float *\__m128)|  
|[_mm_store_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_store_sd (o podwójnej precyzji *\__m128d)|  
|[_mm_store_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_store_si128 (\__m128i *\__m128i)|  
|[_mm_store_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_store_ss (float *\__m128)|  
|[_mm_store1_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_store1_pd (o podwójnej precyzji *\__m128d)|  
|[_mm_storeh_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_storeh_pd (o podwójnej precyzji *\__m128d)|  
|[_mm_storeh_pi](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_storeh_pi (\_typu _m64 *\__m128)|  
|[_mm_storel_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_storel_epi64 (\__m128i *\__m128i)|  
|[_mm_storel_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_storel_pd (o podwójnej precyzji *\__m128d)|  
|[_mm_storel_pi](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_storel_pi (\_typu _m64 *\__m128)|  
|[_mm_storer_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_storer_pd (o podwójnej precyzji *\__m128d)|  
|[_mm_storer_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_storer_ps (float *\__m128)|  
|[_mm_storeu_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_storeu_pd (o podwójnej precyzji *\__m128d)|  
|[_mm_storeu_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_storeu_ps (float *\__m128)|  
|[_mm_storeu_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_storeu_si128 (\__m128i *\__m128i)|  
|[_mm_stream_load_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|__m128i _mm_stream_load_si128 (\__m128i *)|  
|[_mm_stream_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_stream_pd (o podwójnej precyzji *\__m128d)|  
|[_mm_stream_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|void _mm_stream_ps (float *\__m128)|  
|[_mm_stream_sd](../intrinsics/mm-stream-sd.md)|SSE4a|intrin.h|void _mm_stream_sd (o podwójnej precyzji *\__m128d)|  
|[_mm_stream_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_stream_si128 (\__m128i *\__m128i)|  
|[_mm_stream_si32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|void _mm_stream_si32(int*,int)|  
|[_mm_stream_si64x](../intrinsics/mm-stream-si64x.md)|SSE2|intrin.h|void _mm_stream_si64x (\__int64 *,\__int64)|  
|[_mm_stream_ss](../intrinsics/mm-stream-ss.md)|SSE4a|intrin.h|void _mm_stream_ss (float *\__m128)|  
|[_mm_sub_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sub_epi16 (\__m128i,\__m128i)|  
|[_mm_sub_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sub_epi32 (\__m128i,\__m128i)|  
|[_mm_sub_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sub_epi64 (\__m128i,\__m128i)|  
|[_mm_sub_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_sub_epi8 (\__m128i,\__m128i)|  
|[_mm_sub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_sub_pd (\__m128d,\__m128d)|  
|[_mm_sub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_sub_ps (\__m128,\__m128)|  
|[_mm_sub_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_sub_sd (\__m128d,\__m128d)|  
|[_mm_sub_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_sub_ss (\__m128,\__m128)|  
|[_mm_subs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_subs_epi16 (\__m128i,\__m128i)|  
|[_mm_subs_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_subs_epi8 (\__m128i,\__m128i)|  
|[_mm_subs_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_subs_epu16 (\__m128i,\__m128i)|  
|[_mm_subs_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_subs_epu8 (\__m128i,\__m128i)|  
|[_mm_testc_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm_testc_pd (\__m128d,\__m128d)|  
|[_mm_testc_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm_testc_ps (\__m128,\__m128)|  
|[_mm_testc_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|int _mm_testc_si128 (\__m128i,\__m128i)|  
|[_mm_testnzc_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm_testnzc_pd (\__m128d,\__m128d)|  
|[_mm_testnzc_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm_testnzc_ps (\__m128,\__m128)|  
|[_mm_testnzc_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|int _mm_testnzc_si128 (\__m128i,\__m128i)|  
|[_mm_testz_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm_testz_pd (\__m128d,\__m128d)|  
|[_mm_testz_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm_testz_ps (\__m128,\__m128)|  
|[_mm_testz_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE41|intrin.h|int _mm_testz_si128 (\__m128i,\__m128i)|  
|[_mm_ucomieq_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_ucomieq_sd (\__m128d,\__m128d)|  
|[_mm_ucomieq_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_ucomieq_ss (\__m128,\__m128)|  
|[_mm_ucomige_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_ucomige_sd (\__m128d,\__m128d)|  
|[_mm_ucomige_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_ucomige_ss (\__m128,\__m128)|  
|[_mm_ucomigt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_ucomigt_sd (\__m128d,\__m128d)|  
|[_mm_ucomigt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_ucomigt_ss (\__m128,\__m128)|  
|[_mm_ucomile_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_ucomile_sd (\__m128d,\__m128d)|  
|[_mm_ucomile_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_ucomile_ss (\__m128,\__m128)|  
|[_mm_ucomilt_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_ucomilt_sd (\__m128d,\__m128d)|  
|[_mm_ucomilt_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_ucomilt_ss (\__m128,\__m128)|  
|[_mm_ucomineq_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|int _mm_ucomineq_sd (\__m128d,\__m128d)|  
|[_mm_ucomineq_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|int _mm_ucomineq_ss (\__m128,\__m128)|  
|[_mm_unpackhi_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_unpackhi_epi16 (\__m128i,\__m128i)|  
|[_mm_unpackhi_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_unpackhi_epi32 (\__m128i,\__m128i)|  
|[_mm_unpackhi_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_unpackhi_epi64 (\__m128i,\__m128i)|  
|[_mm_unpackhi_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_unpackhi_epi8 (\__m128i,\__m128i)|  
|[_mm_unpackhi_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_unpackhi_pd (\__m128d,\__m128d)|  
|[_mm_unpackhi_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_unpackhi_ps (\__m128,\__m128)|  
|[_mm_unpacklo_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_unpacklo_epi16 (\__m128i,\__m128i)|  
|[_mm_unpacklo_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_unpacklo_epi32 (\__m128i,\__m128i)|  
|[_mm_unpacklo_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_unpacklo_epi64 (\__m128i,\__m128i)|  
|[_mm_unpacklo_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_unpacklo_epi8 (\__m128i,\__m128i)|  
|[_mm_unpacklo_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_unpacklo_pd (\__m128d,\__m128d)|  
|[_mm_unpacklo_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_unpacklo_ps (\__m128,\__m128)|  
|[_mm_xor_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128d _mm_xor_pd (\__m128d,\__m128d)|  
|[_mm_xor_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE|intrin.h|__m128 _mm_xor_ps (\__m128,\__m128)|  
|[_mm_xor_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|SSE2|intrin.h|__m128i _mm_xor_si128 (\__m128i,\__m128i)|  
|[_mm256_abs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_abs_epi16 (\__m256i)|  
|[_mm256_abs_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_abs_epi32 (\__m256i)|  
|[_mm256_abs_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_abs_epi8 (\__m256i)|  
|[_mm256_add_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_add_epi16 (\__m256i,\__m256i)|  
|[_mm256_add_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_add_epi32 (\__m256i,\__m256i)|  
|[_mm256_add_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_add_epi64 (\__m256i,\__m256i)|  
|[_mm256_add_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_add_epi8 (\__m256i,\__m256i)|  
|[_mm256_add_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_add_pd (\__m256d,\__m256d)|  
|[_mm256_add_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_add_ps (\__m256,\__m256)|  
|[_mm256_adds_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_adds_epi16 (\__m256i,\__m256i)|  
|[_mm256_adds_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_adds_epi8 (\__m256i,\__m256i)|  
|[_mm256_adds_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_adds_epu16 (\__m256i,\__m256i)|  
|[_mm256_adds_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_adds_epu8 (\__m256i,\__m256i)|  
|[_mm256_addsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_addsub_pd (\__m256d,\__m256d)|  
|[_mm256_addsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_addsub_ps (\__m256,\__m256)|  
|[_mm256_alignr_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_alignr_epi8 (\__m256i,\__m256i, const int)|  
|[_mm256_and_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_and_pd (\__m256d,\__m256d)|  
|[_mm256_and_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_and_ps (\__m256,\__m256)|  
|[_mm256_and_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_and_si256 (\__m256i,\__m256i)|  
|[_mm256_andnot_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_andnot_pd (\__m256d,\__m256d)|  
|[_mm256_andnot_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_andnot_ps (\__m256,\__m256)|  
|[_mm256_andnot_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_andnot_si256 (\__m256i,\__m256i)|  
|[_mm256_avg_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_avg_epu16 (\__m256i,\__m256i)|  
|[_mm256_avg_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_avg_epu8 (\__m256i,\__m256i)|  
|[_mm256_blend_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_blend_epi16 (\__m256i,\__m256i, const int)|  
|[_mm256_blend_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_blend_epi32 (\__m256i,\__m256i, const int)|  
|[_mm256_blend_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_blend_pd (\__m256d,\__m256d, const int)|  
|[_mm256_blend_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_blend_ps (\__m256,\__m256, const int)|  
|[_mm256_blendv_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_blendv_epi8 (\__m256i,\__m256i,\__m256i)|  
|[_mm256_blendv_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_blendv_pd (\__m256d,\__m256d,\__m256d)|  
|[_mm256_blendv_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_blendv_ps (\__m256,\__m256,\__m256)|  
|[_mm256_broadcast_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_broadcast_pd (\__m128d const *)|  
|[_mm256_broadcast_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_broadcast_ps (\__m128 const *)|  
|[_mm256_broadcast_sd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_broadcast_sd(double const *)|  
|[_mm256_broadcast_ss](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_broadcast_ss(float const *)|  
|[_mm256_broadcastb_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastb_epi8 (\__m128i)|  
|[_mm256_broadcastd_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastd_epi32 (\__m128i)|  
|[_mm256_broadcastq_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastq_epi64 (\__m128i)|  
|[_mm256_broadcastsd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256d _mm256_broadcastsd_pd (\__m128d)|  
|[_mm256_broadcastsi128_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastsi128_si256 (\__m128i)|  
|[_mm256_broadcastss_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256 _mm256_broadcastss_ps (\__m128)|  
|[_mm256_broadcastw_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastw_epi16 (\__m128i)|  
|[_mm256_castpd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_castpd_ps (\__m256d)|  
|[_mm256_castpd_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_castpd_si256 (\__m256d)|  
|[_mm256_castpd128_pd256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_castpd128_pd256 (\__m128d)|  
|[_mm256_castpd256_pd128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128d _mm256_castpd256_pd128 (\__m256d)|  
|[_mm256_castps_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_castps_pd (\__m256)|  
|[_mm256_castps_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_castps_si256 (\__m256)|  
|[_mm256_castps128_ps256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_castps128_ps256 (\__m128)|  
|[_mm256_castps256_ps128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm256_castps256_ps128 (\__m256)|  
|[_mm256_castsi128_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_castsi128_si256 (\__m128i)|  
|[_mm256_castsi256_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_castsi256_pd (\__m256i)|  
|[_mm256_castsi256_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_castsi256_ps (\__m256i)|  
|[_mm256_castsi256_si128](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128i _mm256_castsi256_si128 (\__m256i)|  
|_mm256_cmov_si256|ELEMENT XOP [1]|ammintrin.h|__m256i _mm256_cmov_si256 (\__m256i,\__m256i,\__m256i)|  
|[_mm256_cmp_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_cmp_pd (\__m256d,\__m256d, const int)|  
|[_mm256_cmp_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_cmp_ps (\__m256,\__m256, const int)|  
|[_mm256_cmpeq_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpeq_epi16 (\__m256i,\__m256i)|  
|[_mm256_cmpeq_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpeq_epi32 (\__m256i,\__m256i)|  
|[_mm256_cmpeq_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpeq_epi64 (\__m256i,\__m256i)|  
|[_mm256_cmpeq_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpeq_epi8 (\__m256i,\__m256i)|  
|[_mm256_cmpgt_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpgt_epi16 (\__m256i,\__m256i)|  
|[_mm256_cmpgt_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpgt_epi32 (\__m256i,\__m256i)|  
|[_mm256_cmpgt_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpgt_epi64 (\__m256i,\__m256i)|  
|[_mm256_cmpgt_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpgt_epi8 (\__m256i,\__m256i)|  
|[_mm256_cvtepi16_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi16_epi32 (\__m128i)|  
|[_mm256_cvtepi16_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi16_epi64 (\__m128i)|  
|[_mm256_cvtepi32_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi32_epi64 (\__m128i)|  
|[_mm256_cvtepi32_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_cvtepi32_pd (\__m128i)|  
|[_mm256_cvtepi32_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_cvtepi32_ps (\__m256i)|  
|[_mm256_cvtepi8_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi8_epi16 (\__m128i)|  
|[_mm256_cvtepi8_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi8_epi32 (\__m128i)|  
|[_mm256_cvtepi8_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi8_epi64 (\__m128i)|  
|[_mm256_cvtepu16_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu16_epi32 (\__m128i)|  
|[_mm256_cvtepu16_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu16_epi64 (\__m128i)|  
|[_mm256_cvtepu32_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu32_epi64 (\__m128i)|  
|[_mm256_cvtepu8_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu8_epi16 (\__m128i)|  
|[_mm256_cvtepu8_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu8_epi32 (\__m128i)|  
|[_mm256_cvtepu8_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu8_epi64 (\__m128i)|  
|[_mm256_cvtpd_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128i _mm256_cvtpd_epi32 (\__m256d)|  
|[_mm256_cvtpd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm256_cvtpd_ps (\__m256d)|  
|[_mm256_cvtph_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|F16C [2]|immintrin.h|__m256 _mm256_cvtph_ps (\__m128i)|  
|[_mm256_cvtps_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_cvtps_epi32 (\__m256)|  
|[_mm256_cvtps_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_cvtps_pd (\__m128)|  
|[_mm256_cvtps_ph](http://go.microsoft.com/fwlink/p/?LinkId=512130)|F16C [2]|immintrin.h|__m128i _mm256_cvtps_ph (\__m256, const int)|  
|[_mm256_cvttpd_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128i _mm256_cvttpd_epi32 (\__m256d)|  
|[_mm256_cvttps_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_cvttps_epi32 (\__m256)|  
|[_mm256_div_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_div_pd (\__m256d,\__m256d)|  
|[_mm256_div_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_div_ps (\__m256,\__m256)|  
|[_mm256_dp_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_dp_ps (\__m256,\__m256, const int)|  
|[_mm256_extractf128_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128d _mm256_extractf128_pd (\__m256d, const int)|  
|[_mm256_extractf128_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128 _mm256_extractf128_ps (\__m256, const int)|  
|[_mm256_extractf128_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m128i _mm256_extractf128_si256 (\__m256i, const int)|  
|[_mm256_extracti128_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm256_extracti128_si256 (\__m256i, int offset)|  
|[_mm256_fmadd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256d _mm256_fmadd_pd (\__m256d,\__m256d b\__m256d c).|  
|[_mm256_fmadd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256 _mm256_fmadd_ps (\__m256,\__m256 b\__m256 c).|  
|[_mm256_fmaddsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256d _mm256_fmaddsub_pd (\__m256d,\__m256d b\__m256d c).|  
|[_mm256_fmaddsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256 _mm256_fmaddsub_ps (\__m256,\__m256 b\__m256 c).|  
|[_mm256_fmsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256d _mm256_fmsub_pd (\__m256d,\__m256d b\__m256d c).|  
|[_mm256_fmsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256 _mm256_fmsub_ps (\__m256,\__m256 b\__m256 c).|  
|[_mm256_fmsubadd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256d _mm256_fmsubadd_pd (\__m256d,\__m256d b\__m256d c).|  
|[_mm256_fmsubadd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256 _mm256_fmsubadd_ps (\__m256,\__m256 b\__m256 c).|  
|[_mm256_fnmadd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256d _mm256_fnmadd_pd (\__m256d,\__m256d b\__m256d c).|  
|[_mm256_fnmadd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256 _mm256_fnmadd_ps (\__m256,\__m256 b\__m256 c).|  
|[_mm256_fnmsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256d _mm256_fnmsub_pd (\__m256d,\__m256d b\__m256d c).|  
|[_mm256_fnmsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FMA [2]|immintrin.h|__m256 _mm256_fnmsub_ps (\__m256,\__m256 b\__m256 c).|  
|_mm256_frcz_pd|ELEMENT XOP [1]|ammintrin.h|__m256d _mm256_frcz_pd (\__m256d)|  
|_mm256_frcz_ps|ELEMENT XOP [1]|ammintrin.h|__m256 _mm256_frcz_ps (\__m256)|  
|[_mm256_hadd_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_hadd_epi16 (\__m256i,\__m256i)|  
|[_mm256_hadd_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_hadd_epi32 (\__m256i,\__m256i)|  
|[_mm256_hadd_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_hadd_pd (\__m256d,\__m256d)|  
|[_mm256_hadd_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_hadd_ps (\__m256,\__m256)|  
|[_mm256_hadds_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_hadds_epi16 (\__m256i,\__m256i)|  
|[_mm256_hsub_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_hsub_epi16 (\__m256i,\__m256i)|  
|[_mm256_hsub_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_hsub_epi32 (\__m256i,\__m256i)|  
|[_mm256_hsub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_hsub_pd (\__m256d,\__m256d)|  
|[_mm256_hsub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_hsub_ps (\__m256,\__m256)|  
|[_mm256_hsubs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_hsubs_epi16 (\__m256i,\__m256i)|  
|[_mm256_i32gather_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_i32gather_epi32 (int const * elementu bazowego,\__m256i indeksu, const int skali)|  
|[_mm256_i32gather_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_i32gather_epi64 (\__int64 const * podstawowej,\__m128i indeksu, const int skali)|  
|[_mm256_i32gather_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256d _mm256_i32gather_pd (dwa razy const * elementu bazowego,\__m128i indeksu, const int skali)|  
|[_mm256_i32gather_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256 _mm256_i32gather_ps (float const * elementu bazowego,\__m256i indeksu, const int skali)|  
|[_mm256_i64gather_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_i64gather_epi32 (int const * elementu bazowego,\__m256i indeksu, const int skali)|  
|[_mm256_i64gather_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_i64gather_epi64 (\__int64 const * podstawowej,\__m256i indeksu, const int skali)|  
|[_mm256_i64gather_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256d _mm256_i64gather_pd (dwa razy const * elementu bazowego,\__m256i indeksu, const int skali)|  
|[_mm256_i64gather_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128 _mm256_i64gather_ps (float const * elementu bazowego,\__m256i indeksu, const int skali)|  
|[_mm256_insertf128_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_insertf128_pd (\__m256d,\__m128d, int)|  
|[_mm256_insertf128_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_insertf128_ps (\__m256,\__m128, int)|  
|[_mm256_insertf128_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_insertf128_si256 (\__m256i,\__m128i, int)|  
|[_mm256_inserti128_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_inserti128_si256 (\__m256i,\__m128i, int)|  
|[_mm256_lddqu_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_lddqu_si256 (\__m256i *)|  
|[_mm256_load_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_load_pd(double const *)|  
|[_mm256_load_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_load_ps(float const *)|  
|[_mm256_load_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_load_si256 (\__m256i *)|  
|[_mm256_loadu_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_loadu_pd(double const *)|  
|[_mm256_loadu_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_loadu_ps(float const *)|  
|[_mm256_loadu_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_loadu_si256 (\__m256i *)|  
|_mm256_macc_pd|FMA4 [1]|ammintrin.h|__m256d _mm_macc_pd (\__m256d,\__m256d,\__m256d)|  
|_mm256_macc_ps|FMA4 [1]|ammintrin.h|__m256 _mm_macc_ps (\__m256,\__m256,\__m256)|  
|[_mm256_madd_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_madd_epi16 (\__m256i,\__m256i)|  
|_mm256_maddsub_pd|FMA4 [1]|ammintrin.h|__m256d _mm_maddsub_pd (\__m256d,\__m256d,\__m256d)|  
|_mm256_maddsub_ps|FMA4 [1]|ammintrin.h|__m256 _mm_maddsub_ps (\__m256,\__m256,\__m256)|  
|[_mm256_maddubs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_maddubs_epi16 (\__m256i,\__m256i)|  
|[_mm256_mask_i32gather_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mask_i32gather_epi32 (\__m256i src, int const * podstawowej,\_indeksu _m256i\__m256i maski, const int skali)|  
|[_mm256_mask_i32gather_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mask_i32gather_epi64 (\__m256i src\__int64 const * podstawowej,\_indeksu _m128i\__m256i maski, const int skali)|  
|[_mm256_mask_i32gather_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256d _mm256_mask_i32gather_pd (\__m256d src, double const * podstawowej,\_indeksu _m128i\__m256d maski, const int skali)|  
|[_mm256_mask_i32gather_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256 _mm256_mask_i32gather_ps (\__m256 src, float const * podstawowej,\_indeksu _m256i\__m256 maski, const int skali)|  
|[_mm256_mask_i64gather_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128i _mm256_mask_i64gather_epi32 (\__m128i src, int const * podstawowej,\_indeksu _m256i\__m128i maski, const int skali)|  
|[_mm256_mask_i64gather_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mask_i64gather_epi64 (\__m256i src\__int64 const * podstawowej,\_indeksu _m256i\__m256i maski, const int skali)|  
|[_mm256_mask_i64gather_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256d _mm256_mask_i64gather_pd (\__m256d src, double const * podstawowej,\_indeksu _m256i\__m256d maski, const int skali)|  
|[_mm256_mask_i64gather_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m128 _mm256_mask_i64gather_ps (\__m128 src, float const * podstawowej,\_indeksu _m256i\__m128 maski, const int skali)|  
|[_mm256_maskload_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_maskload_epi32 (int const *,\__m256i)|  
|[_mm256_maskload_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_maskload_epi64 ( \__int64 const *,\__m256i)|  
|[_mm256_maskload_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_maskload_pd (dwa razy const *,\__m256i)|  
|[_mm256_maskload_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_maskload_ps (float const *,\__m256i)|  
|[_mm256_maskstore_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|void _mm256_maskstore_epi32 (int *,\__m256i,\__m256i)|  
|[_mm256_maskstore_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|void _mm256_maskstore_epi64 (\__int64 *,\__m256i,\__m256i)|  
|[_mm256_maskstore_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_maskstore_pd (o podwójnej precyzji *,\__m256i,\__m256d)|  
|[_mm256_maskstore_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_maskstore_ps (float *,\__m256i,\__m256)|  
|[_mm256_max_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epi16 (\__m256i,\__m256i)|  
|[_mm256_max_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epi32 (\__m256i,\__m256i)|  
|[_mm256_max_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epi8 (\__m256i,\__m256i)|  
|[_mm256_max_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epu16 (\__m256i,\__m256i)|  
|[_mm256_max_epu32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epu32 (\__m256i,\__m256i)|  
|[_mm256_max_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epu8 (\__m256i,\__m256i)|  
|[_mm256_max_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_max_pd (\__m256d,\__m256d)|  
|[_mm256_max_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_max_ps (\__m256,\__m256)|  
|[_mm256_min_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epi16 (\__m256i,\__m256i)|  
|[_mm256_min_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epi32 (\__m256i,\__m256i)|  
|[_mm256_min_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epi8 (\__m256i,\__m256i)|  
|[_mm256_min_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epu16 (\__m256i,\__m256i)|  
|[_mm256_min_epu32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epu32 (\__m256i,\__m256i)|  
|[_mm256_min_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epu8 (\__m256i,\__m256i)|  
|[_mm256_min_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_min_pd (\__m256d,\__m256d)|  
|[_mm256_min_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_min_ps (\__m256,\__m256)|  
|[_mm256_movedup_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_movedup_pd (\__m256d)|  
|[_mm256_movehdup_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_movehdup_ps (\__m256)|  
|[_mm256_moveldup_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_moveldup_ps (\__m256)|  
|[_mm256_movemask_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|int _mm256_movemask_epi8 (\__m256i)|  
|[_mm256_movemask_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_movemask_pd (\__m256d)|  
|[_mm256_movemask_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_movemask_ps (\__m256)|  
|[_mm256_mpsadbw_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mpsadbw_epu8 (\__m256i,\__m256i, const int)|  
|_mm256_msub_pd|FMA4 [1]|ammintrin.h|__m256d _mm_msub_pd (\__m256d,\__m256d,\__m256d)|  
|_mm256_msub_ps|FMA4 [1]|ammintrin.h|__m256 _mm_msub_ps (\__m256,\__m256,\__m256)|  
|_mm256_msubadd_pd|FMA4 [1]|ammintrin.h|__m256d _mm_msubadd_pd (\__m256d,\__m256d,\__m256d)|  
|_mm256_msubadd_ps|FMA4 [1]|ammintrin.h|__m256 _mm_msubadd_ps (\__m256,\__m256,\__m256)|  
|[_mm256_mul_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mul_epi32 (\__m256i,\__m256i)|  
|[_mm256_mul_epu32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mul_epu32 (\__m256i,\__m256i)|  
|[_mm256_mul_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_mul_pd (\__m256d,\__m256d)|  
|[_mm256_mul_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_mul_ps (\__m256,\__m256)|  
|[_mm256_mulhi_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mulhi_epi16 (\__m256i,\__m256i)|  
|[_mm256_mulhi_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mulhi_epu16 (\__m256i,\__m256i)|  
|[_mm256_mulhrs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mulhrs_epi16 (\__m256i,\__m256i)|  
|[_mm256_mullo_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mullo_epi16 (\__m256i,\__m256i)|  
|[_mm256_mullo_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_mullo_epi32 (\__m256i,\__m256i)|  
|_mm256_nmacc_pd|FMA4 [1]|ammintrin.h|__m256d _mm_nmacc_pd (\__m256d,\__m256d,\__m256d)|  
|_mm256_nmacc_ps|FMA4 [1]|ammintrin.h|__m256 _mm_nmacc_ps (\__m256,\__m256,\__m256)|  
|_mm256_nmsub_pd|FMA4 [1]|ammintrin.h|__m256d _mm_nmsub_pd (\__m256d,\__m256d,\__m256d)|  
|_mm256_nmsub_ps|FMA4 [1]|ammintrin.h|__m256 _mm_nmsub_ps (\__m256,\__m256,\__m256)|  
|[_mm256_or_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_or_pd (\__m256d,\__m256d)|  
|[_mm256_or_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_or_ps (\__m256,\__m256)|  
|[_mm256_or_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_or_si256 (\__m256i,\__m256i)|  
|[_mm256_packs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_packs_epi16 (\__m256i,\__m256i)|  
|[_mm256_packs_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_packs_epi32 (\__m256i,\__m256i)|  
|[_mm256_packus_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_packus_epi16 (\__m256i,\__m256i)|  
|[_mm256_packus_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_packus_epi32 (\__m256i,\__m256i)|  
|[_mm256_permute_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_permute_pd (\__m256d, int)|  
|[_mm256_permute_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_permute_ps (\__m256, int)|  
|_mm256_permute2_pd|ELEMENT XOP [1]|ammintrin.h|__m256d _mm256_permute2_pd (\__m256d,\__m256d,\__m256i, int)|  
|_mm256_permute2_ps|ELEMENT XOP [1]|ammintrin.h|__m256 _mm256_permute2_ps (\__m256,\__m256,\__m256i, int)|  
|[_mm256_permute2f128_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_permute2f128_pd (\__m256d,\__m256d, int)|  
|[_mm256_permute2f128_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_permute2f128_ps (\__m256,\__m256, int)|  
|[_mm256_permute2f128_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_permute2f128_si256 (\__m256i,\__m256i, int)|  
|[_mm256_permute2x128_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_permute2x128_si256 (\__m256i,\__m256i, const int)|  
|[_mm256_permute4x64_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_permute4x64_epi64 (\__m256i, const int)|  
|[_mm256_permute4x64_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256d _mm256_permute4x64_pd (\__m256d, const int)|  
|[_mm256_permutevar_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_permutevar_pd (\__m256d,\__m256i)|  
|[_mm256_permutevar_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_permutevar_ps (\__m256,\__m256i)|  
|[_mm256_permutevar8x32_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_permutevar8x32_epi32 (\__m256i,\__m256i)|  
|[_mm256_permutevar8x32_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256 _mm256_permutevar8x32_ps (\__m256,\__m256i)|  
|[_mm256_rcp_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_rcp_ps (\__m256)|  
|[_mm256_round_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_round_pd (\__m256d, int)|  
|[_mm256_round_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_round_ps (\__m256, int)|  
|[_mm256_rsqrt_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_rsqrt_ps (\__m256)|  
|[_mm256_sad_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sad_epu8 (\__m256i,\__m256i)|  
|[_mm256_set_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|(__m256i _mm256_set_epi16 (krótki|  
|[_mm256_set_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_set_epi32(int,int,int,int,int,int,int,int)|  
|[_mm256_set_epi64x](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|_mm256_set_epi64x __m256i (długi czas, długi czas, długi czas, długi czas)|  
|[_mm256_set_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_set_epi8(char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char,char)|  
|[_mm256_set_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_set_pd(double,double,double,double)|  
|[_mm256_set_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_set_ps(float,float,float,float,float,float,float,float)|  
|[_mm256_set1_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi16(short)|  
|[_mm256_set1_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi32(int)|  
|[_mm256_set1_epi64x](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|_mm256_set1_epi64x __m256i (long long)|  
|[_mm256_set1_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi8(char)|  
|[_mm256_set1_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_set1_pd(double)|  
|[_mm256_set1_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_set1_ps(float)|  
|[_mm256_setr_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|(__m256i _mm256_setr_epi16 (krótki|  
|[_mm256_setr_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_setr_epi32(int,int,int,int,int,int,int,int)|  
|[_mm256_setr_epi64x](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|_mm256_setr_epi64x __m256i (długi czas, długi czas, długi czas, długi czas)|  
|[_mm256_setr_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|(__m256i _mm256_setr_epi8 (char|  
|[_mm256_setr_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_setr_pd(double,double,double,double)|  
|[_mm256_setr_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_setr_ps(float,float,float,float,float,float,float,float)|  
|[_mm256_setzero_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_setzero_pd(void)|  
|[_mm256_setzero_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_setzero_ps(void)|  
|[_mm256_setzero_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256i _mm256_setzero_si256(void)|  
|[_mm256_shuffle_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_shuffle_epi32 (\__m256i, const int)|  
|[_mm256_shuffle_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_shuffle_epi8 (\__m256i,\__m256i)|  
|[_mm256_shuffle_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_shuffle_pd (\__m256d,\__m256d, const int)|  
|[_mm256_shuffle_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_shuffle_ps (\__m256,\__m256, const int)|  
|[_mm256_shufflehi_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_shufflehi_epi16 (\__m256i, const int)|  
|[_mm256_shufflelo_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_shufflelo_epi16 (\__m256i, const int)|  
|[_mm256_sign_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sign_epi16 (\__m256i,\__m256i)|  
|[_mm256_sign_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sign_epi32 (\__m256i,\__m256i)|  
|[_mm256_sign_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sign_epi8 (\__m256i,\__m256i)|  
|[_mm256_sll_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sll_epi16 (\__m256i,\__m128i)|  
|[_mm256_sll_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sll_epi32 (\__m256i,\__m128i)|  
|[_mm256_sll_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sll_epi64 (\__m256i,\__m128i)|  
|[_mm256_slli_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_slli_epi16 (\__m256i, int)|  
|[_mm256_slli_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_slli_epi32 (\__m256i, int)|  
|[_mm256_slli_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_slli_epi64 (\__m256i, int)|  
|[_mm256_slli_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_slli_si256 (\__m256i, int)|  
|[_mm256_sllv_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sllv_epi32 (\__m256i,\__m256i)|  
|[_mm256_sllv_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sllv_epi64 (\__m256i,\__m256i)|  
|[_mm256_sqrt_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_sqrt_pd (\__m256d)|  
|[_mm256_sqrt_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_sqrt_ps (\__m256)|  
|[_mm256_sra_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sra_epi16 (\__m256i,\__m128i)|  
|[_mm256_sra_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sra_epi32 (\__m256i,\__m128i)|  
|[_mm256_srai_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srai_epi16 (\__m256i, int)|  
|[_mm256_srai_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srai_epi32 (\__m256i, int)|  
|[_mm256_srav_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srav_epi32 (\__m256i,\__m256i)|  
|[_mm256_srl_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srl_epi16 (\__m256i,\__m128i)|  
|[_mm256_srl_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srl_epi32 (\__m256i,\__m128i)|  
|[_mm256_srl_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srl_epi64 (\__m256i,\__m128i)|  
|[_mm256_srli_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srli_epi16 (\__m256i, int)|  
|[_mm256_srli_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srli_epi32 (\__m256i, int)|  
|[_mm256_srli_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srli_epi64 (\__m256i, int)|  
|[_mm256_srli_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srli_si256 (\__m256i, int)|  
|[_mm256_srlv_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srlv_epi32 (\__m256i,\__m256i)|  
|[_mm256_srlv_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_srlv_epi64 (\__m256i,\__m256i)|  
|[_mm256_store_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_store_pd (o podwójnej precyzji *,\__m256d)|  
|[_mm256_store_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_store_ps (float *,\__m256)|  
|[_mm256_store_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_store_si256 (\__m256i *,\__m256i)|  
|[_mm256_storeu_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_storeu_pd (o podwójnej precyzji *,\__m256d)|  
|[_mm256_storeu_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_storeu_ps (float *,\__m256)|  
|[_mm256_storeu_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_storeu_si256 (\__m256i *,\__m256i)|  
|[_mm256_stream_load_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_stream_load_si256 (\__m256i const *)|  
|[_mm256_stream_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void __mm256_stream_pd (o podwójnej precyzji *,\__m256d)|  
|[_mm256_stream_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_stream_ps (float * p,\__m256)|  
|[_mm256_stream_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void __mm256_stream_si256 (\__m256i *,\__m256i)|  
|[_mm256_sub_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sub_epi16 (\__m256i,\__m256i)|  
|[_mm256_sub_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sub_epi32 (\__m256i,\__m256i)|  
|[_mm256_sub_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sub_epi64 (\__m256i,\__m256i)|  
|[_mm256_sub_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_sub_epi8 (\__m256i,\__m256i)|  
|[_mm256_sub_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_sub_pd (\__m256d,\__m256d)|  
|[_mm256_sub_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_sub_ps (\__m256,\__m256)|  
|[_mm256_subs_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_subs_epi16 (\__m256i,\__m256i)|  
|[_mm256_subs_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_subs_epi8 (\__m256i,\__m256i)|  
|[_mm256_subs_epu16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_subs_epu16 (\__m256i,\__m256i)|  
|[_mm256_subs_epu8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_subs_epu8 (\__m256i,\__m256i)|  
|[_mm256_testc_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testc_pd (\__m256d,\__m256d)|  
|[_mm256_testc_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testc_ps (\__m256,\__m256)|  
|[_mm256_testc_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testc_si256 (\__m256i,\__m256i)|  
|[_mm256_testnzc_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testnzc_pd (\__m256d,\__m256d)|  
|[_mm256_testnzc_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testnzc_ps (\__m256,\__m256)|  
|[_mm256_testnzc_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testnzc_si256 (\__m256i,\__m256i)|  
|[_mm256_testz_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testz_pd (\__m256d,\__m256d)|  
|[_mm256_testz_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testz_ps (\__m256,\__m256)|  
|[_mm256_testz_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|int _mm256_testz_si256 (\__m256i,\__m256i)|  
|[_mm256_unpackhi_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_unpackhi_epi16 (\__m256i,\__m256i)|  
|[_mm256_unpackhi_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_unpackhi_epi32 (\__m256i,\__m256i)|  
|[_mm256_unpackhi_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_unpackhi_epi64 (\__m256i,\__m256i)|  
|[_mm256_unpackhi_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_unpackhi_epi8 (\__m256i,\__m256i)|  
|[_mm256_unpackhi_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_unpackhi_pd (\__m256d,\__m256d)|  
|[_mm256_unpackhi_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_unpackhi_ps (\__m256,\__m256)|  
|[_mm256_unpacklo_epi16](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_unpacklo_epi16 (\__m256i,\__m256i)|  
|[_mm256_unpacklo_epi32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_unpacklo_epi32 (\__m256i,\__m256i)|  
|[_mm256_unpacklo_epi64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_unpacklo_epi64 (\__m256i,\__m256i)|  
|[_mm256_unpacklo_epi8](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_unpacklo_epi8 (\__m256i,\__m256i)|  
|[_mm256_unpacklo_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_unpacklo_pd (\__m256d,\__m256d)|  
|[_mm256_unpacklo_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_unpacklo_ps (\__m256,\__m256)|  
|[_mm256_xor_pd](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256d _mm256_xor_pd (\__m256d,\__m256d)|  
|[_mm256_xor_ps](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|__m256 _mm256_xor_ps (\__m256,\__m256)|  
|[_mm256_xor_si256](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX2 [2]|immintrin.h|__m256i _mm256_xor_si256 (\__m256i,\__m256i)|  
|[_mm256_zeroall](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_zeroall(void)|  
|[_mm256_zeroupper](http://go.microsoft.com/fwlink/p/?LinkId=512130)|AVX [2]|immintrin.h|void _mm256_zeroupper(void)|  
|[__movsb](../intrinsics/movsb.md)||intrin.h|VOID __movsb (IN PBYTE, BAJTÓW w const *, IN SIZE_T)|  
|[__movsd](../intrinsics/movsd.md)||intrin.h|VOID __movsd (IN PDWORD, DWORD w const *, IN SIZE_T)|  
|[__movsq](../intrinsics/movsq.md)||intrin.h|VOID __movsq (IN PDWORD64, IN DWORD64 const *, IN SIZE_T)|  
|[__movsw](../intrinsics/movsw.md)||intrin.h|VOID __movsw (PWORD w, WORD w const *, IN SIZE_T)|  
|[_mul128](../intrinsics/mul128.md)||intrin.h|__int64 _mul128 (\_mnożnik _int64\__int64 multiplicand\__int64 * highproduct)|  
|[__mulh](../intrinsics/mulh.md)||intrin.h|__int64 \__mulh (\__int64,\__int64)|  
|_mulx_u32|BMI [2]|immintrin.h|unsigned int _mulx_u32 (unsigned int, unsigned int, int bez znaku *)|  
|_mulx_u64|BMI [2]|immintrin.h|niepodpisane __int64 _mulx_u64 (bez znaku \__int64 niepodpisane \__int64 niepodpisane \__int64 *)|  
|[__nop](../intrinsics/nop.md)||intrin.h|void __nop(void)|  
|__nvreg_restore_fence||intrin.h|void __nvreg_restore_fence(void)|  
|__nvreg_save_fence||intrin.h|void __nvreg_save_fence(void)|  
|[__outbyte](../intrinsics/outbyte.md)||intrin.h|void __outbyte (bez znaku portu krótkich, bez znaku char danych)|  
|[__outbytestring](../intrinsics/outbytestring.md)||intrin.h|void __outbytestring (bez znaku portu krótkich, unsigned char * buforu, bez znaku liczba długa)|  
|[__outdword](../intrinsics/outdword.md)||intrin.h|void __outdword (bez znaku krótkich portu, danych unsigned long)|  
|[__outdwordstring](../intrinsics/outdwordstring.md)||intrin.h|void __outdwordstring (unsigned portu krótkie, unsigned long * buforu, bez znaku liczba długa)|  
|[__outword](../intrinsics/outword.md)||intrin.h|void __outword (bez znaku Port krótkie, krótki danych bez podpisu)|  
|[__outwordstring](../intrinsics/outwordstring.md)||intrin.h|void __outwordstring (unsigned krótkich portu, bez znaku krótko * buforu, bez znaku liczba długa)|  
|[_pdep_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI [2]|immintrin.h|unsigned int _pdep_u32 (unsigned int, int bez znaku)|  
|[_pdep_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI [2]|immintrin.h|niepodpisane __int64 _pdep_u64 (bez znaku \__int64 niepodpisane \__int64)|  
|[_pext_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI [2]|immintrin.h|unsigned int _pext_u32 (unsigned int, int bez znaku)|  
|[_pext_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI [2]|immintrin.h|niepodpisane __int64 _pext_u64 (bez znaku \__int64 niepodpisane \__int64)|  
|[__popcnt](../intrinsics/popcnt16-popcnt-popcnt64.md)|POPCNT|intrin.h|__popcnt(unsigned int) unsigned int|  
|[__popcnt16](../intrinsics/popcnt16-popcnt-popcnt64.md)|POPCNT|intrin.h|__popcnt16(unsigned short) krótkich bez znaku|  
|[__popcnt64](../intrinsics/popcnt16-popcnt-popcnt64.md)|POPCNT|intrin.h|niepodpisane __int64 \__popcnt64 (bez znaku \__int64)|  
|[_rdrand16_step](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RDRAND [2]|immintrin.h|int _rdrand16_step(unsigned short *)|  
|[_rdrand32_step](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RDRAND [2]|immintrin.h|int _rdrand32_step(unsigned int *)|  
|[_rdrand64_step](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RDRAND [2]|immintrin.h|int _rdrand64_step (bez znaku \__int64 *)|  
|[_rdseed16_step](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RDSEED [2]|immintrin.h|int _rdseed16_step(unsigned short *)|  
|[_rdseed32_step](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RDSEED [2]|immintrin.h|int _rdseed32_step(unsigned int *)|  
|[_rdseed64_step](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RDSEED [2]|immintrin.h|int _rdseed64_step (bez znaku \__int64 *)|  
|[__rdtsc](../intrinsics/rdtsc.md)||intrin.h|niepodpisane __int64 \__rdtsc(void)|  
|[__rdtscp](../intrinsics/rdtscp.md)|RDTSCP|intrin.h|niepodpisane __int64 \__rdtscp (unsigned int *)|  
|[_ReadBarrier](../intrinsics/readbarrier.md)||intrin.h|void _ReadBarrier(void)|  
|[__readcr0](../intrinsics/readcr0.md)||intrin.h|niepodpisane __int64 \__readcr0(void)|  
|[__readcr2](../intrinsics/readcr2.md)||intrin.h|niepodpisane __int64 \__readcr2(void)|  
|[__readcr3](../intrinsics/readcr3.md)||intrin.h|niepodpisane __int64 \__readcr3(void)|  
|[__readcr4](../intrinsics/readcr4.md)||intrin.h|niepodpisane __int64 \__readcr4(void)|  
|[__readcr8](../intrinsics/readcr8.md)||intrin.h|niepodpisane __int64 \__readcr8(void)|  
|[__readdr](../intrinsics/readdr.md)||intrin.h|niepodpisane __int64 \__readdr(unsigned)|  
|[__readeflags](../intrinsics/readeflags.md)||intrin.h|niepodpisane __int64 \__readeflags(void)|  
|[_readfsbase_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FSGSBASE [2]|immintrin.h|_readfsbase_u32(void) unsigned int|  
|[_readfsbase_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FSGSBASE [2]|immintrin.h|_readfsbase_u64(void) __int64 bez znaku|  
|[_readgsbase_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FSGSBASE [2]|immintrin.h|_readgsbase_u32(void) unsigned int|  
|[_readgsbase_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FSGSBASE [2]|immintrin.h|_readgsbase_u64(void) __int64 bez znaku|  
|[__readgsbyte](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)||intrin.h|__readgsbyte char bez znaku (przesunięcie długa bez znaku)|  
|[__readgsdword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)||intrin.h|niepodpisane __readgsdword długi (przesunięcie długa bez znaku)|  
|[__readgsqword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)||intrin.h|niepodpisane __int64 \__readgsqword (przesunięcie długa bez znaku)|  
|[__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)||intrin.h|niepodpisane krótki __readgsword (przesunięcie długa bez znaku)|  
|[__readmsr](../intrinsics/readmsr.md)||intrin.h|niepodpisane __int64 \__readmsr (unsigned long)|  
|[__readpmc](../intrinsics/readpmc.md)||intrin.h|niepodpisane __int64 \__readpmc(unsigned long a)|  
|[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)||intrin.h|void _ReadWriteBarrier(void)|  
|[_ReturnAddress](../intrinsics/returnaddress.md)||intrin.h|void * _ReturnAddress(void)|  
|_rorx_u32|BMI [2]|immintrin.h|unsigned int _rorx_u32 (unsigned int, const unsigned int)|  
|_rorx_u64|BMI [2]|immintrin.h|niepodpisane __int64 _rorx_u64 (bez znaku \__int64, const unsigned int)|  
|[_rotl16](../intrinsics/rotl8-rotl16.md)||intrin.h|niepodpisane _rotl16 krótkich (krótszej wartości bez znaku, shift char bez znaku)|  
|[_rotl8](../intrinsics/rotl8-rotl16.md)||intrin.h|unsigned char _rotl8 (wartość char bez znaku, shift char bez znaku)|  
|[_rotr16](../intrinsics/rotr8-rotr16.md)||intrin.h|niepodpisane _rotr16 krótkich (krótszej wartości bez znaku, shift char bez znaku)|  
|[_rotr8](../intrinsics/rotr8-rotr16.md)||intrin.h|unsigned char _rotr8 (wartość char bez znaku, shift char bez znaku)|  
|_rsm||intrin.h|void _rsm(void)|  
|_sarx_i32|BMI [2]|immintrin.h|int _sarx_i32 (int, int bez znaku)|  
|_sarx_i64|BMI [2]|immintrin.h|__int64 _sarx_i64 (\__int64, unsigned int)|  
|[__segmentlimit](../intrinsics/segmentlimit.md)||intrin.h|unsigned long __segmentlimit(unsigned long a)|  
|_sgdt||intrin.h|void _sgdt(void*)|  
|[__shiftleft128](../intrinsics/shiftleft128.md)||intrin.h|niepodpisane __int64 \__shiftleft128 (bez znaku \_LowPart _int64, bez znaku \__int64 HighPart unsigned char Shift)|  
|[__shiftright128](../intrinsics/shiftright128.md)||intrin.h|niepodpisane __int64 \__shiftright128 (bez znaku \_LowPart _int64, bez znaku \__int64 HighPart unsigned char Shift)|  
|_shlx_u32|BMI [2]|immintrin.h|unsigned int _shlx_u32 (unsigned int, int bez znaku)|  
|_shlx_u64|BMI [2]|immintrin.h|niepodpisane __int64 _shlx_u64 (bez znaku \__int64, unsigned int)|  
|_shrx_u32|BMI [2]|immintrin.h|unsigned int _shrx_u32 (unsigned int, int bez znaku)|  
|_shrx_u64|BMI [2]|immintrin.h|niepodpisane __int64 _shrx_u64 (bez znaku \__int64, unsigned int)|  
|[__sidt](../intrinsics/sidt.md)||intrin.h|void __sidt(void*)|  
|__slwpcb|LWP [1]|ammintrin.h|void *__slwpcb(void)|  
|_stac|SMAP|intrin.h|void _stac(void)|  
|_store_be_u16<br /><br /> [_storebe_i16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i16&expand=5141)|MOVBE|immintrin.h|void _store_be_u16 (void * bez znaku krótko);<br /><br /> void _storebe_i16 (void \*, krótki); [3]|  
|_store_be_u32<br /><br /> [_storebe_i32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i32&expand=5142)|MOVBE|immintrin.h|void _store_be_u32 (void *, unsigned int);<br /><br /> void _storebe_i32 (void \*, int); [3]|  
|_store_be_u64<br /><br /> [_storebe_i64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i64&expand=5143)|MOVBE|immintrin.h|void _store_be_u64 (void * bez znaku \__int64);<br /><br /> void _storebe_i64 (void \*, \__int64); [3]|  
|_Store_HLERelease|HLE [2]|immintrin.h|void _Store_HLERelease (długo volatile * długim)|  
|_Store64_HLERelease|HLE [2]|immintrin.h|void _Store64_HLERelease (\__int64 volatile *,\__int64)|  
|_StorePointer_HLERelease|HLE [2]|immintrin.h|void _StorePointer_HLERelease (void * volatile \*, void \*)|  
|[__stosb](../intrinsics/stosb.md)||intrin.h|void __stosb (PBYTE IN, BAJTÓW w IN SIZE_T)|  
|[__stosd](../intrinsics/stosd.md)||intrin.h|void __stosd (PDWORD IN, DWORD w IN SIZE_T)|  
|[__stosq](../intrinsics/stosq.md)||intrin.h|void __stosq (IN PDWORD64, IN DWORD64 w SIZE_T)|  
|[__stosw](../intrinsics/stosw.md)||intrin.h|void __stosw (PWORD w, WORD w IN SIZE_T)|  
|_subborrow_u16||intrin.h|unsigned char _subborrow_u16 (unsigned char b_in, niepodpisane src1 krótkich, niepodpisane src2 krótkie, bez znaku krótko * diff)|  
|[_subborrow_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)||intrin.h|unsigned char _subborrow_u32 (unsigned char b_in, src1 unsigned int, src2 unsigned int, int bez znaku * diff)|  
|[_subborrow_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)||intrin.h|unsigned char _subborrow_u64 (unsigned char b_in, bez znaku \_src1 _int64, bez znaku \_src2 _int64, bez znaku \__int64 * diff)|  
|_subborrow_u8||intrin.h|unsigned char _subborrow_u8 (unsigned char b_in, src1 char bez znaku, src2 unsigned char unsigned char * diff)|  
|[__svm_clgi](../intrinsics/svm-clgi.md)||intrin.h|void __svm_clgi(void)|  
|[__svm_invlpga](../intrinsics/svm-invlpga.md)||intrin.h|void __svm_invlpga(void*,int)|  
|[__svm_skinit](../intrinsics/svm-skinit.md)||intrin.h|void __svm_skinit(int)|  
|[__svm_stgi](../intrinsics/svm-stgi.md)||intrin.h|void __svm_stgi(void)|  
|[__svm_vmload](../intrinsics/svm-vmload.md)||intrin.h|void __svm_vmload(size_t)|  
|[__svm_vmrun](../intrinsics/svm-vmrun.md)||intrin.h|void __svm_vmrun(size_t)|  
|[__svm_vmsave](../intrinsics/svm-vmsave.md)||intrin.h|void __svm_vmsave(size_t)|  
|_t1mskc_u32|ABM [1]|ammintrin.h|_t1mskc_u32(unsigned int) unsigned int|  
|_t1mskc_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _t1mskc_u64 (bez znaku \__int64)|  
|[_tzcnt_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|_tzcnt_u32(unsigned int) unsigned int|  
|[_tzcnt_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|BMI|ammintrin.h, immintrin.h|niepodpisane __int64 _tzcnt_u64 (bez znaku \__int64)|  
|_tzmsk_u32|ABM [1]|ammintrin.h|_tzmsk_u32(unsigned int) unsigned int|  
|_tzmsk_u64|ABM [1]|ammintrin.h|niepodpisane __int64 _tzmsk_u64 (bez znaku \__int64)|  
|[__ud2](../intrinsics/ud2.md)||intrin.h|void __ud2(void)|  
|[__ull_rshift](../intrinsics/ull-rshift.md)||intrin.h|__int64 bez znaku [pascal/cdecl] \__ull_rshift (bez znaku \__int64, int)|  
|[_umul128](../intrinsics/umul128.md)||intrin.h|niepodpisane __int64 _umul128 (bez znaku \_mnożnik _int64, bez znaku \_multiplicand _int64, bez znaku \__int64 * highproduct)|  
|[__umulh](../intrinsics/umulh.md)||intrin.h|niepodpisane __int64 \__umulh (bez znaku \__int64 niepodpisane \__int64)|  
|[__vmx_off](../intrinsics/vmx-off.md)||intrin.h|void __vmx_off(void)|  
|[__vmx_on](../intrinsics/vmx-on.md)||intrin.h|unsigned char __vmx_on (bez znaku \__int64 *)|  
|[__vmx_vmclear](../intrinsics/vmx-vmclear.md)||intrin.h|unsigned char __vmx_vmclear (bez znaku \__int64 *)|  
|[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)||intrin.h|__vmx_vmlaunch(void) char bez znaku|  
|[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)||intrin.h|unsigned char __vmx_vmptrld (bez znaku \__int64 *)|  
|[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)||intrin.h|void __vmx_vmptrst (bez znaku \__int64 *)|  
|[__vmx_vmread](../intrinsics/vmx-vmread.md)||intrin.h|__vmx_vmread(size_t,size_t*) char bez znaku|  
|[__vmx_vmresume](../intrinsics/vmx-vmresume.md)||intrin.h|__vmx_vmresume(void) char bez znaku|  
|[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)||intrin.h|__vmx_vmwrite(size_t,size_t) char bez znaku|  
|[__wbinvd](../intrinsics/wbinvd.md)||intrin.h|void __wbinvd(void)|  
|[_WriteBarrier](../intrinsics/writebarrier.md)||intrin.h|void _WriteBarrier(void)|  
|[__writecr0](../intrinsics/writecr0.md)||intrin.h|void __writecr0 (bez znaku \__int64)|  
|[__writecr3](../intrinsics/writecr3.md)||intrin.h|void __writecr3 (bez znaku \__int64)|  
|[__writecr4](../intrinsics/writecr4.md)||intrin.h|void __writecr4 (bez znaku \__int64)|  
|[__writecr8](../intrinsics/writecr8.md)||intrin.h|void __writecr8 (bez znaku \__int64)|  
|[__writedr](../intrinsics/writedr.md)||intrin.h|void __writedr (bez znaku, bez znaku \__int64)|  
|[__writeeflags](../intrinsics/writeeflags.md)||intrin.h|void __writeeflags (bez znaku \__int64)|  
|[_writefsbase_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FSGSBASE [2]|immintrin.h|void _writefsbase_u32(unsigned int)|  
|[_writefsbase_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FSGSBASE [2]|immintrin.h|void _writefsbase_u64 (bez znaku \__int64)|  
|[_writegsbase_u32](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FSGSBASE [2]|immintrin.h|void _writegsbase_u32(unsigned int)|  
|[_writegsbase_u64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|FSGSBASE [2]|immintrin.h|void _writegsbase_u64 (bez znaku \__int64)|  
|[__writegsbyte](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)||intrin.h|void __writegsbyte (bez znaku długo przesunięcie, unsigned char danych)|  
|[__writegsdword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)||intrin.h|void __writegsdword (bez znaku długo przesunięcie, bez znaku danych long)|  
|[__writegsqword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)||intrin.h|void __writegsqword (unsigned przesunięcie długie, bez znaku \__int64 danych)|  
|[__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)||intrin.h|void __writegsword (bez znaku długo przesunięcie, bez znaku krótkich danych)|  
|[__writemsr](../intrinsics/writemsr.md)||intrin.h|void __writemsr (unsigned long, bez znaku \__int64)|  
|[_xabort](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RTM [2]|immintrin.h|void _xabort(unsigned int)|  
|[_xbegin](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RTM [2]|immintrin.h|_xbegin(void) bez znaku|  
|[_xend](http://go.microsoft.com/fwlink/p/?LinkId=512130)|RTM [2]|immintrin.h|void _xend(void)|  
|[_xgetbv](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XSAVE [2]|immintrin.h|_xgetbv(unsigned int) __int64 bez znaku|  
|[_xrstor](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XSAVE [2]|immintrin.h|void _xrstor (void const *, bez znaku \__int64)|  
|[_xrstor64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XSAVE [2]|immintrin.h|void _xrstor64 (void const *, bez znaku \__int64)|  
|[_xsave](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XSAVE [2]|immintrin.h|void _xsave (void *, bez znaku \__int64)|  
|[_xsave64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XSAVE [2]|immintrin.h|void _xsave64 (void *, bez znaku \__int64)|  
|[_xsaveopt](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XSAVEOPT [2]|immintrin.h|void _xsaveopt (void *, bez znaku \__int64)|  
|[_xsaveopt64](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XSAVEOPT [2]|immintrin.h|void _xsaveopt64 (void *, bez znaku \__int64)|  
|[_xsetbv](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XSAVE [2]|immintrin.h|void _xsetbv (unsigned int, bez znaku \__int64)|  
|[_xtest](http://go.microsoft.com/fwlink/p/?LinkId=512130)|XTEST [2]|immintrin.h|_xtest(void) char bez znaku|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Funkcje wewnętrzne ARM](../intrinsics/arm-intrinsics.md)   
 [x86 funkcje wewnętrzne](../intrinsics/x86-intrinsics-list.md)