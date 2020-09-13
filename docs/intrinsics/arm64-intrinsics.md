---
title: Funkcje wewnętrzne ARM64
description: Lista odwołań wewnętrznych elementów ARM64 obsługiwanych przez kompilator języka Microsoft C++ w programie Visual Studio.
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
helpviewer_keywords:
- __break ARM64 intrinsic
- __addx18byte ARM64 intrinsic
- __addx18word ARM64 intrinsic
- __addx18dword ARM64 intrinsic
- __addx18qword ARM64 intrinsic
- __cas8 ARM64 intrinsic
- __cas16 ARM64 intrinsic
- __cas32 ARM64 intrinsic
- __cas64 ARM64 intrinsic
- __casa8 ARM64 intrinsic
- __casa16 ARM64 intrinsic
- __casa32 ARM64 intrinsic
- __casa64 ARM64 intrinsic
- __casl8 ARM64 intrinsic
- __casl16 ARM64 intrinsic
- __casl32 ARM64 intrinsic
- __casl64 ARM64 intrinsic
- __casal8 ARM64 intrinsic
- __casal16 ARM64 intrinsic
- __casal32 ARM64 intrinsic
- __casal64 ARM64 intrinsic
- __crc32b ARM64 intrinsic
- __crc32h ARM64 intrinsic
- __crc32w ARM64 intrinsic
- __crc32d ARM64 intrinsic
- __crc32cb ARM64 intrinsic
- __crc32ch ARM64 intrinsic
- __crc32cw ARM64 intrinsic
- __crc32cd ARM64 intrinsic
- __getReg ARM64 intrinsic
- __getRegFp ARM64 intrinsic
- __getCallerReg ARM64 intrinsic
- __getCallerRegFp ARM64 intrinsic
- __hlt ARM64 intrinsic
- __incx18byte ARM64 intrinsic
- __incx18word ARM64 intrinsic
- __incx18dword ARM64 intrinsic
- __incx18qword ARM64 intrinsic
- __ldar8 ARM64 intrinsic
- __ldar16 ARM64 intrinsic
- __ldar32 ARM64 intrinsic
- __ldar64 ARM64 intrinsic
- __ldapr8 ARM64 intrinsic
- __ldapr16 ARM64 intrinsic
- __ldapr32 ARM64 intrinsic
- __ldapr64 ARM64 intrinsic
- __prefetch2 ARM64 intrinsic
- __readx18byte ARM64 intrinsic
- __readx18word ARM64 intrinsic
- __readx18dword ARM64 intrinsic
- __readx18qword ARM64 intrinsic
- __setReg ARM64 intrinsic
- __setRegFp ARM64 intrinsic
- __setCallerReg ARM64 intrinsic
- __setCallerRegFp ARM64 intrinsic
- __stlr8 ARM64 intrinsic
- __stlr16 ARM64 intrinsic
- __stlr32 ARM64 intrinsic
- __stlr64 ARM64 intrinsic
- __swp8 ARM64 intrinsic
- __swp16 ARM64 intrinsic
- __swp32 ARM64 intrinsic
- __swp64 ARM64 intrinsic
- __swpa8 ARM64 intrinsic
- __swpa16 ARM64 intrinsic
- __swpa32 ARM64 intrinsic
- __swpa64 ARM64 intrinsic
- __swpl8 ARM64 intrinsic
- __swpl16 ARM64 intrinsic
- __swpl32 ARM64 intrinsic
- __swpl64 ARM64 intrinsic
- __swpal8 ARM64 intrinsic
- __swpal16 ARM64 intrinsic
- __swpal32 ARM64 intrinsic
- __swpal64 ARM64 intrinsic
- __sys ARM64 intrinsic
- __svc ARM64 intrinsic
- __writex18byte ARM64 intrinsic
- __writex18word ARM64 intrinsic
- __writex18dword ARM64 intrinsic
- __writex18qword ARM64 intrinsic
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 13358458bf9abcf0bc6e38ca115b537abc99300a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039758"
---
# <a name="arm64-intrinsics"></a>Funkcje wewnętrzne ARM64

Kompilator języka Microsoft C++ (MSVC) udostępnia następujące elementy wewnętrzne architektury ARM64. Aby uzyskać więcej informacji na temat usługi ARM, zobacz sekcje architektury i narzędzi programistycznych dla deweloperów w witrynie sieci Web usługi [ARM](https://developer.arm.com/docs) .

## <a name="neon"></a><a name="top"></a> NEON

Rozszerzenia zestawu instrukcji wektora NEON dla ARM64 zapewniają możliwości Single Instruction Multiple Data (SIMD). Są one podobne do tych w zestawach wektorowych MMX i SSE, które są wspólne dla procesorów architektury x86 i x64.

Elementy wewnętrzne NEONu są obsługiwane, jak to przedstawiono w pliku nagłówkowym *arm64_neon. h*. Obsługa MSVC dla wewnętrznych elementów jest podobna do kompilatora ARM64, który jest udokumentowany w [wewnętrznej referencji ARM](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) w witrynie ARM InfoCenter.

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a> Lista elementów wewnętrznych specyficznych dla ARM64

|Nazwa funkcji|Instrukcja|Prototyp funkcji|
|-------------------|-----------------|------------------------|
|__break|BRK|void __break (int)|
|__addx18byte||void __addx18byte (unsigned long, znak bez znaku)|
|__addx18word||void __addx18word (Long unsigned unsigned Short)|
|__addx18dword||void __addx18dword (Long bez znaku, Long unsigned)|
|__addx18qword||void __addx18qword (Long unsigned, unsigned __int64)|
|__cas8|CASB|niepodpisane __int8 __cas8 (bez znaku __int8 volatile * _Target, bez znaku __int8 _Comp, bez znaku __int8 _Value)|
|__cas16|PIENIĘDZY|niepodpisane __int16 __cas16 (bez znaku __int16 volatile * _Target, bez znaku __int16 _Comp, bez znaku __int16 _Value)|
|__cas32|CAS|niepodpisane __int32 __cas32 (bez znaku __int32 volatile * _Target, bez znaku __int32 _Comp, bez znaku __int32 _Value)|
|__cas64|CAS|niepodpisane __int64 __cas64 (bez znaku __int64 volatile * _Target, bez znaku __int64 _Comp, bez znaku __int64 _Value)|
|__casa8|CASAB|niepodpisane __int8 __casa8 (bez znaku __int8 volatile * _Target, bez znaku __int8 _Comp, bez znaku __int8 _Value)|
|__casa16|CASAH|niepodpisane __int16 __casa16 (bez znaku __int16 volatile * _Target, bez znaku __int16 _Comp, bez znaku __int16 _Value)|
|__casa32|CASA|niepodpisane __int32 __casa32 (bez znaku __int32 volatile * _Target, bez znaku __int32 _Comp, bez znaku __int32 _Value)|
|__casa64|CASA|niepodpisane __int64 __casa64 (bez znaku __int64 volatile * _Target, bez znaku __int64 _Comp, bez znaku __int64 _Value)|
|__casl8|CASLB|niepodpisane __int8 __casl8 (bez znaku __int8 volatile * _Target, bez znaku __int8 _Comp, bez znaku __int8 _Value)|
|__casl16|CASLH|niepodpisane __int16 __casl16 (bez znaku __int16 volatile * _Target, bez znaku __int16 _Comp, bez znaku __int16 _Value)|
|__casl32|CASL|niepodpisane __int32 __casl32 (bez znaku __int32 volatile * _Target, bez znaku __int32 _Comp, bez znaku __int32 _Value)|
|__casl64|CASL|niepodpisane __int64 __casl64 (bez znaku __int64 volatile * _Target, bez znaku __int64 _Comp, bez znaku __int64 _Value)|
|__casal8|CASALB|niepodpisane __int8 __casal8 (bez znaku __int8 volatile * _Target, bez znaku __int8 _Comp, bez znaku __int8 _Value)|
|__casal16|CASALH|niepodpisane __int16 __casal16 (bez znaku __int16 volatile * _Target, bez znaku __int16 _Comp, bez znaku __int16 _Value)|
|__casal32|CASAL|niepodpisane __int32 __casal32 (bez znaku __int32 volatile * _Target, bez znaku __int32 _Comp, bez znaku __int32 _Value)|
|__casal64|CASAL|niepodpisane __int64 __casal64 (bez znaku __int64 volatile * _Target, bez znaku __int64 _Comp, bez znaku __int64 _Value)|
|__crc32b|CRC32B|niepodpisane __int32 __crc32b (niepodpisane __int32, niepodpisane __int32)|
|__crc32h|CRC32H|niepodpisane __int32 __crc32h (niepodpisane __int32, niepodpisane __int32)|
|__crc32w|CRC32W|niepodpisane __int32 __crc32w (niepodpisane __int32, niepodpisane __int32)|
|__crc32d|CRC32X|niepodpisane __int32 __crc32d (niepodpisane __int32, niepodpisane __int64)|
|__crc32cb|CRC32CB|niepodpisane __int32 __crc32cb (niepodpisane __int32, niepodpisane __int32)|
|__crc32ch|CRC32CH|niepodpisane __int32 __crc32ch (niepodpisane __int32, niepodpisane __int32)|
|__crc32cw|CRC32CW|niepodpisane __int32 __crc32cw (niepodpisane __int32, niepodpisane __int32)|
|__crc32cd|CRC32CX|niepodpisane __int32 __crc32cd (niepodpisane __int32, niepodpisane __int64)|
|__dmb|DMB|void __dmb (bez znaku int `_Type` )<br /><br /> Wstawia operację bariery pamięci do strumienia instrukcji. Parametr `_Type` określa rodzaj ograniczeń wymuszanych przez barierę.<br /><br /> Aby uzyskać więcej informacji na temat rodzajów ograniczeń, które można wymusić, zobacz [ograniczenia dotyczące bariery pamięci](#BarrierRestrictions).|
|__dsb|TEŻ|void __dsb (niepodpisane _Type int)<br /><br /> Wstawia operację bariery pamięci do strumienia instrukcji. Parametr `_Type` określa rodzaj ograniczeń wymuszanych przez barierę.<br /><br /> Aby uzyskać więcej informacji na temat rodzajów ograniczeń, które można wymusić, zobacz [ograniczenia dotyczące bariery pamięci](#BarrierRestrictions).|
|__isb|ISB|void __isb (niepodpisane _Type int)<br /><br /> Wstawia operację bariery pamięci do strumienia instrukcji. Parametr `_Type` określa rodzaj ograniczeń wymuszanych przez barierę.<br /><br /> Aby uzyskać więcej informacji na temat rodzajów ograniczeń, które można wymusić, zobacz [ograniczenia dotyczące bariery pamięci](#BarrierRestrictions).|
|__getReg||niepodpisane __getReg __int64 (int)|
|__getRegFp||podwójne __getRegFp (int)|
|__getCallerReg||niepodpisane __getCallerReg __int64 (int)|
|__getCallerRegFp||podwójne __getCallerRegFp (int)|
|__hvc|HVC|niepodpisane __hvc int (int bez znaku,...)|
|__hlt|INSTRUKCJI|int __hlt (bez znaku int,...)|
|__incx18byte||void __incx18byte (liczba bez znaku)|
|__incx18word||void __incx18word (liczba bez znaku)|
|__incx18dword||void __incx18dword (liczba bez znaku)|
|__incx18qword||void __incx18qword (liczba bez znaku)|
|__iso_volatile_load16||\__iso_volatile_load16 __int16 (const volatile \_ _int16 \* )<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load32||\__iso_volatile_load32 __int32 (const volatile \_ _int32 \* )<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load64||\__iso_volatile_load64 __int64 (const volatile \_ _int64 \* )<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load8||\__iso_volatile_load8 __int8 (const volatile \_ _int8 \* )<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16 (nietrwały \_ _int16 \* , \_ _int16)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32 (nietrwały \_ _int32 \* , \_ _int32)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void __iso_volatile_store64 (nietrwały \_ _int64 \* , \_ _int64)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8 (nietrwały \_ _int8 \* , \_ _int8)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__ldar8|LDARB|niepodpisane __ldar8 __int8 (unsigned __int8 volatile * _Target)|
|__ldar16|LDARH|niepodpisane __ldar16 __int16 (unsigned __int16 volatile * _Target)|
|__ldar32|LDAR|niepodpisane __ldar32 __int32 (unsigned __int32 volatile * _Target)|
|__ldar64|LDAR|niepodpisane __ldar64 __int64 (unsigned __int64 volatile * _Target)|
|__ldapr8|LDAPRB|niepodpisane __ldapr8 __int8 (unsigned __int8 volatile * _Target)|
|__ldapr16|LDAPRH|niepodpisane __ldapr16 __int16 (unsigned __int16 volatile * _Target)|
|__ldapr32|Protokół LDAP|niepodpisane __ldapr32 __int32 (unsigned __int32 volatile * _Target)|
|__ldapr64|Protokół LDAP|niepodpisane __ldapr64 __int64 (unsigned __int64 volatile * _Target)|
|__mulh||\___mulh _int64 ( \_ _int64, \_ _int64)|
|__prefetch|PRFM|_prefetch __cdecl void \_ (const void \* )<br /><br /> Udostępnia `PRFM` wskazówkę dotyczącą pamięci z operacją pobierania z wyprzedzeniem `PLDL1KEEP` do systemu, w którym można uzyskać dostęp do pamięci w określonym lub bliskim podanym adresie. Niektóre systemy mogą zoptymalizować ten wzorzec dostępu do pamięci, aby zwiększyć wydajność środowiska uruchomieniowego. Jednak z punktu widzenia języka C++ funkcja nie ma zauważalnego efektu i może nic nie robić.|
|__prefetch2|PRFM|_prefetch __cdecl void \_ (const void \* , uint8_t prfop)<br /><br /> Zapewnia `PRFM` wskazówkę dotyczącą pamięci z podaną operacją pobierania z wyprzedzeniem w systemie, do której można uzyskać dostęp do pamięci w określonym lub bliskim podanym adresie. Niektóre systemy mogą zoptymalizować ten wzorzec dostępu do pamięci, aby zwiększyć wydajność środowiska uruchomieniowego. Jednak z punktu widzenia języka C++ funkcja nie ma zauważalnego efektu i może nic nie robić.|
|__readx18byte||niepodpisany znak __readx18byte (liczba bez znaku)|
|__readx18word||krótkie __readx18word bez znaku (bez znaku)|
|__readx18dword||niepodpisane długie __readx18dword (liczba bez znaku)|
|__readx18qword||niepodpisane __readx18qword __int64 (liczba bez znaku)|
|__setReg||void __setReg (int, unsigned __int64)|
|__setRegFp||void __setRegFp (int, Double)|
|__setCallerReg||void __setCallerReg (int, unsigned __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, Double)|
|__sev|WAŻNOŚĆ|void __sev (void)|
|__static_assert||void __static_assert (int, const char \* )|
|__stlr8|STLRB|void __stlr8 (bez znaku __int8 volatile * _Target, bez znaku __int8 _Value)|
|__stlr16|STLRH|void __stlr16 (bez znaku __int16 volatile * _Target, bez znaku __int16 _Value)|
|__stlr32|STLR|void __stlr32 (bez znaku __int32 volatile * _Target, bez znaku __int32 _Value)|
|__stlr64|STLR|void __stlr64 (bez znaku __int64 volatile * _Target, bez znaku __int64 _Value)|
|__swp8|SWPB|niepodpisane __swp8 __int8 (unsigned __int8 volatile * _Target, bez znaku __int8)|
|__swp16|SWPH|niepodpisane __swp16 __int16 (unsigned __int16 volatile * _Target, bez znaku __int16)|
|__swp32|SWP|niepodpisane __swp32 __int32 (unsigned __int32 volatile * _Target, bez znaku __int32)|
|__swp64|SWP|niepodpisane __swp64 __int64 (unsigned __int64 volatile * _Target, bez znaku __int64)|
|__swpa8|SWPAB|niepodpisane __swpa8 __int8 (unsigned __int8 volatile * _Target, bez znaku __int8)|
|__swpa16|SWPAH|niepodpisane __swpa16 __int16 (unsigned __int16 volatile * _Target, bez znaku __int16)|
|__swpa32|SWPA|niepodpisane __swpa32 __int32 (unsigned __int32 volatile * _Target, bez znaku __int32)|
|__swpa64|SWPA|niepodpisane __swpa64 __int64 (unsigned __int64 volatile * _Target, bez znaku __int64)|
|__swpl8|SWPLB|niepodpisane __swpl8 __int8 (unsigned __int8 volatile * _Target, bez znaku __int8)|
|__swpl16|SWPLH|niepodpisane __swpl16 __int16 (unsigned __int16 volatile * _Target, bez znaku __int16)|
|__swpl32|SWPL|niepodpisane __swpl32 __int32 (unsigned __int32 volatile * _Target, bez znaku __int32)|
|__swpl64|SWPL|niepodpisane __swpl64 __int64 (unsigned __int64 volatile * _Target, bez znaku __int64)|
|__swpal8|SWPALB|niepodpisane __swpal8 __int8 (unsigned __int8 volatile * _Target, bez znaku __int8)|
|__swpal16|SWPALH|niepodpisane __swpal16 __int16 (unsigned __int16 volatile * _Target, bez znaku __int16)|
|__swpal32|SWPAL|niepodpisane __swpal32 __int32 (unsigned __int32 volatile * _Target, bez znaku __int32)|
|__swpal64|SWPAL|niepodpisane __swpal64 __int64 (unsigned __int64 volatile * _Target, bez znaku __int64)|
|__sys|WIDOKU|niepodpisane __sys int (int, __int64)|
|__svc|SVC|niepodpisane __svc int (int bez znaku,...)|
|__wfe|Fronton internetowy|void __wfe (void)|
|__wfi|WFI|void __wfi (void)|
|__writex18byte||void __writex18byte (unsigned long, znak bez znaku)|
|__writex18word||void __writex18word (Long unsigned unsigned Short)|
|__writex18dword||void __writex18dword (Long bez znaku, Long unsigned)|
|__writex18qword||void __writex18qword (Long unsigned, unsigned __int64)|
|__umulh||niepodpisane \_ _int64 __umulh (niepodpisane \_ _int64, niepodpisane \_ _int64)|
|_CopyDoubleFromInt64||podwójne _CopyDoubleFromInt64 ( \_ _int64)|
|_CopyFloatFromInt32||_CopyFloatFromInt32 zmiennoprzecinkowe ( \_ _int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat (float)|
|_CopyInt64FromDouble||_CopyInt64FromDouble __int64 (Double)|
|_CountLeadingOnes||niepodpisane _CountLeadingOnes int (liczba bez znaku)|
|_CountLeadingOnes64||niepodpisane _CountLeadingOnes64 int (niepodpisane \_ _int64)|
|_CountLeadingSigns||niepodpisane _CountLeadingSigns int (Long)|
|_CountLeadingSigns64||niepodpisane _CountLeadingSigns64 int ( \_ _int64)|
|_CountLeadingZeros||niepodpisane _CountLeadingZeros int (liczba bez znaku)|
|_CountLeadingZeros64||niepodpisane _CountLeadingZeros64 int (niepodpisane \_ _int64)|
|_ReadStatusReg|Marta|\__ReadStatusReg _int64 (int)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, \_ _int64)|

[[Wróć do początku](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a> Ograniczenia dotyczące barier pamięci

Funkcje wewnętrzne `__dmb` (bariera pamięci danych), `__dsb` (bariera synchronizacji danych) i `__isb` (bariera synchronizacji instrukcji) używają następujących wstępnie zdefiniowanych wartości do określenia ograniczenia dotyczącego bariery pamięci w zakresie domeny udostępniania i rodzaju dostępu, którego dotyczy operacja.

|Wartość ograniczenia|Opis|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Pełny system, Odczyt i zapis.|
|_ARM64_BARRIER_ST|Pełny system, tylko zapisy.|
|_ARM64_BARRIER_LD|Pełny system, tylko do odczytu.|
|_ARM64_BARRIER_ISH|Wewnętrzne, które można udostępniać, odczyty i zapisy.|
|_ARM64_BARRIER_ISHST|Wewnętrzny, udostępniony, tylko zapis.|
|_ARM64_BARRIER_ISHLD|Wewnętrzny udostępniony, tylko do odczytu.|
|_ARM64_BARRIER_NSH|Nie można udostępniać, odczytów i zapisów.|
|_ARM64_BARRIER_NSHST|Nie można udostępniać, tylko zapisy.|
|_ARM64_BARRIER_NSHLD|Nie można udostępniać, tylko do odczytu.|
|_ARM64_BARRIER_OSH|Zewnętrzny, udostępniony, Odczyt i zapis.|
|_ARM64_BARRIER_OSHST|Zewnętrzny, udostępniony, tylko zapis.|
|_ARM64_BARRIER_OSHLD|Zewnętrzny, udostępniony, tylko do odczytu.|

W przypadku `__isb` wewnętrznego jedynym aktualnie prawidłowym ograniczeniem jest _ARM64_BARRIER_SY. wszystkie inne wartości są zarezerwowane przez architekturę.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a> __iso_volatile_load wewnętrzne/Store

Te funkcje wewnętrzne jawnie wykonują obciążenia i magazyny, które nie podlegają optymalizacji kompilatora.

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>Parametry

*Przeniesienie*\
Adres lokalizacji pamięci, z której ma zostać odczytany lub zapisany.

*Wartościami*\
Wartość do zapisu w określonej lokalizacji pamięci (tylko elementy wewnętrzne sklepu).

#### <a name="return-value-load-intrinsics-only"></a>Wartość zwracana (tylko wewnętrzne obciążenia)

Wartość lokalizacji pamięci, która jest określona przez *lokalizację*.

#### <a name="remarks"></a>Uwagi

Można użyć elementów `__iso_volatile_load8/16/32/64` i, `__iso_volatile_store8/16/32/64` Aby jawnie wykonywać dostęp do pamięci, które nie podlegają optymalizacji kompilatora. Kompilator nie może usunąć, synthetize ani zmienić względnej kolejności tych operacji. Nie generują one jednak niejawnych barier pamięci sprzętowej. W związku z tym sprzęt może nadal zmienić kolejność zauważalnych dostępów do pamięci w wielu wątkach. Dokładniej te elementy wewnętrzne są równoważne następującym wyrażeniem, które zostały skompilowane w obszarze **/volatile: ISO**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Zwróć uwagę, że elementy wewnętrzne przyjmują nietrwałe wskaźniki, aby pomieścić zmienne lotne. Jednakże nie jest wymagane ani zalecenie, aby użyć nietrwałych wskaźników jako argumentów. Semantyka tych operacji jest dokładnie taka sama, jeśli jest używany zwykły, nietrwały typ.

Aby uzyskać więcej informacji na temat argumentu wiersza polecenia **/volatile: ISO** , zobacz [/volatile (interpretacja słowa kluczowego volatile)](../build/reference/volatile-volatile-keyword-interpretation.md).

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a> Obsługa ARM64 wewnętrznych z innych architektur

Poniższa tabela zawiera listę funkcji wewnętrznych z innych architektur, które są obsługiwane na platformach ARM64. W przypadku, gdy zachowanie elementu wewnętrznego na ARM64 różni się od zachowania w przypadku innych architektur sprzętowych, należy zauważyć dodatkowe szczegóły.

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|__assume|void __assume (int)|
|__code_seg|void __code_seg (const char \* )|
|__debugbreak|void __cdecl \_ _debugbreak (void)|
|__fastfail|__declspec (noreturn) void \_ _fastfail (bez znaku int)|
|__nop|void __nop (void)|
|__yield|void __yield (void) **Uwaga:**  na platformach arm64 ta funkcja GENERUJE instrukcję Yield. Ta instrukcja wskazuje, że wątek wykonuje zadanie, które może być tymczasowo zawieszone przed wykonaniem — na przykład struktury spinlock — bez negatywnego wpływu na program. Umożliwia PROCESORowi wykonywanie innych zadań podczas cyklów wykonywania, które w przeciwnym razie byłyby tracone.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void)|
|_BitScanForward|niepodpisany znak _BitScanForward (Long długi \* _index, długi _Mask bez znaku)|
|_BitScanForward64|niepodpisany znak _BitScanForward64 (Long długi \* _index, bez znaku __int64 _Mask)|
|_BitScanReverse|niepodpisany znak _BitScanReverse (Long długi \* _index, długi _Mask bez znaku)|
|_BitScanReverse64|niepodpisany znak _BitScanReverse64 (Long długi \* _index, bez znaku __int64 _Mask)|
|_bittest|niepodpisany znak _bittest (Long const \* , Long)|
|_bittest64|niepodpisany znak _bittest64 (__int64 const \* , __int64)|
|_bittestandcomplement|niepodpisany znak _bittestandcomplement (Long \* , Long)|
|_bittestandcomplement64|niepodpisany znak _bittestandcomplement64 (__int64 \* , __int64)|
|_bittestandreset|niepodpisany znak _bittestandreset (Long \* , Long)|
|_bittestandreset64|niepodpisany znak _bittestandreset64 (__int64 \* , __int64)|
|_bittestandset|niepodpisany znak _bittestandset (Long \* , Long)|
|_bittestandset64|niepodpisany znak _bittestandset64 (__int64 \* , __int64)|
|_byteswap_uint64|niepodpisane __int64 \_ _cdecl _byteswap_uint64 (bez znaku \_ _int64)|
|_byteswap_ulong|niepodpisane długie __cdecl _byteswap_ulong (bez znaku)|
|_byteswap_ushort|niepodpisane krótkie __cdecl _byteswap_ushort (krótkie bez znaku)|
|_disable|void __cdecl _disable (void) **Uwaga:**  na platformach arm64 ta funkcja generuje instrukcję `MSR DAIFCLR,#2` . jest ona dostępna tylko jako wewnętrzna.|
|_enable|void __cdecl _enable (void) **Uwaga:**  na platformach arm64 ta funkcja generuje instrukcję `MSR DAIFSET,#2` . jest ona dostępna tylko jako wewnętrzna.|
|_lrotl|niepodpisane długie __cdecl _lrotl (Long, int)|
|_lrotr|niepodpisane długie __cdecl _lrotr (Long, int)|
|_ReadBarrier|void _ReadBarrier (void)|
|_ReadWriteBarrier|void _ReadWriteBarrier (void)|
|_ReturnAddress|void \* _ReturnAddress (void)|
|_rotl|niepodpisane _rotl int __cdecl (niepodpisane _Value int, int _Shift)|
|_rotl16|niepodpisane krótkie _rotl16 (krótkie _Shift _Value niepodpisanego znaku)|
|_rotl64|niepodpisane __int64 \_ _cdecl _rotl64 (bez znaku \_ _int64 _Value, int _Shift)|
|_rotl8|niepodpisany znak _rotl8 (znak bez znaku _Value, niepodpisany znak _Shift)|
|_rotr|niepodpisane _rotr int __cdecl (niepodpisane _Value int, int _Shift)|
|_rotr16|niepodpisane krótkie _rotr16 (krótkie _Shift _Value niepodpisanego znaku)|
|_rotr64|niepodpisane __int64 \_ _cdecl _rotr64 (bez znaku \_ _int64 _Value, int _Shift)|
|_rotr8|niepodpisany znak _rotr8 (znak bez znaku _Value, niepodpisany znak _Shift)|
|_setjmpex|_setjmpex int __cdecl (jmp_buf)|
|_WriteBarrier|void _WriteBarrier (void)|

[[Wróć do początku](#top)]

## <a name="interlocked-intrinsics"></a>Blokady wewnętrzne

Wbudowane elementy wewnętrzne są zestawem wewnętrznych, które są używane do wykonywania niepodzielnych operacji odczytu i zapisu. Niektóre z nich są wspólne dla wszystkich platform. Są one wyświetlane osobno w tym miejscu, ponieważ istnieje duża liczba. Ze względu na to, że ich definicje są najczęściej nadmiarowe, łatwiej jest myśleć o nich w ogólnych warunkach. Ich nazwy mogą służyć do uzyskania dokładnych zachowań.

Poniższa tabela zawiera podsumowanie obsługi ARM64, które nie są Zablokowani. Każda komórka w tabeli odnosi się do nazwy, która jest tworzona przez dołączenie nazwy operacji w lewym górnym rogu wiersza i nazwy typu w górnej komórce kolumny do `_Interlocked` . Na przykład komórka na przecięciu `Xor` wiersza i `8` kolumny odpowiada `_InterlockedXor8` i jest w pełni obsługiwana. Większość obsługiwanych funkcji oferuje następujące opcjonalne sufiksy: `_acq` , `_rel` , i `_nf` . `_acq`Sufiks wskazuje semantykę "pozyskiwania", a `_rel` sufiks wskazuje "Release". `_nf`Sufiks lub "No ogrodzenia" jest unikatowy dla ARM i arm64 i został omówiony w następnej sekcji.

|Operacja|8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Dodaj|Brak|Brak|Pełne|Pełne|Brak|Brak|
|And|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|CompareExchange|Pełne|Pełne|Pełne|Pełne|Pełne|Pełne|
|Dekrementacji|Brak|Pełne|Pełne|Pełne|Brak|Brak|
|Exchange|Pełne|Pełne|Pełne|Pełne|Brak|Pełne|
|ExchangeAdd|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|Przyrost|Brak|Pełne|Pełne|Pełne|Brak|Brak|
|Lub|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|Xor|Pełne|Pełne|Pełne|Pełne|Brak|Brak|

Klucz:

- **Pełna**: obsługuje proste, `_acq` , `_rel` , i `_nf` formularze.

- **Brak**: nieobsługiwane

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a> sufiks _nf (bez ogrodzenia)

`_nf`Sufiks lub "No ogrodzenia" wskazuje, że operacja nie zachowuje się jako jakikolwiek rodzaj bariery pamięci, w przeciwieństwie do innych trzech form (zwykłych, `_acq` i `_rel` ), które działają jako niektóre przeszkody. Jednym z możliwych użycia `_nf` formularzy jest zachowywanie licznika statystyk, który jest aktualizowany przez wiele wątków w tym samym czasie, ale którego wartość nie jest używana w inny sposób podczas wykonywania wielu wątków.

### <a name="list-of-interlocked-intrinsics"></a>Lista zablokowanych elementów wewnętrznych

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|_InterlockedAdd|długi _InterlockedAdd (Long _volatile \* , Long)|
|_InterlockedAdd64|_InterlockedAdd64 __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_acq|_InterlockedAdd64_acq __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_nf|_InterlockedAdd64_nf __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_rel|_InterlockedAdd64_rel __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd_acq|długi _InterlockedAdd_acq (Long volatile \* , Long)|
|_InterlockedAdd_nf|długi _InterlockedAdd_nf (Long volatile \* , Long)|
|_InterlockedAdd_rel|długi _InterlockedAdd_rel (Long volatile \* , Long)|
|_InterlockedAnd|długi _InterlockedAnd (Long volatile \* , Long)|
|_InterlockedAnd16|Krótki _InterlockedAnd16 (krótki nietrwały \* , krótki)|
|_InterlockedAnd16_acq|Krótki _InterlockedAnd16_acq (krótki nietrwały \* , krótki)|
|_InterlockedAnd16_nf|Krótki _InterlockedAnd16_nf (krótki nietrwały \* , krótki)|
|_InterlockedAnd16_rel|Krótki _InterlockedAnd16_rel (krótki nietrwały \* , krótki)|
|_InterlockedAnd64|_InterlockedAnd64 __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_acq|_InterlockedAnd64_acq __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_nf|_InterlockedAnd64_nf __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_rel|_InterlockedAnd64_rel __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd8|char _InterlockedAnd8 (Char volatile \* , Char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq (Char volatile \* , Char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (Char volatile \* , Char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel (Char volatile \* , Char)|
|_InterlockedAnd_acq|długi _InterlockedAnd_acq (Long volatile \* , Long)|
|_InterlockedAnd_nf|długi _InterlockedAnd_nf (Long volatile \* , Long)|
|_InterlockedAnd_rel|długi _InterlockedAnd_rel (Long volatile \* , Long)|
|_InterlockedCompareExchange|długi __cdecl _InterlockedCompareExchange (Long volatile \* , Long, Long)|
|_InterlockedCompareExchange_acq|długi _InterlockedCompareExchange_acq (Long volatile \* , Long, Long)|
|_InterlockedCompareExchange_nf|długi _InterlockedCompareExchange_nf (Long volatile \* , Long, Long)|
|_InterlockedCompareExchange_rel|długi _InterlockedCompareExchange_rel (Long volatile \* , Long, Long)|
|_InterlockedCompareExchange16|krótkie _InterlockedCompareExchange16 (krótkie nietrwałe \* , krótkie, krótkie)|
|_InterlockedCompareExchange16_acq|krótkie _InterlockedCompareExchange16_acq (krótkie nietrwałe \* , krótkie, krótkie)|
|_InterlockedCompareExchange16_nf|krótkie _InterlockedCompareExchange16_nf (krótkie nietrwałe \* , krótkie, krótkie)|
|_InterlockedCompareExchange16_rel|krótkie _InterlockedCompareExchange16_rel (krótkie nietrwałe \* , krótkie, krótkie)|
|_InterlockedCompareExchange64|_InterlockedCompareExchange64 __int64 ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_acq|_InterlockedCompareExchange64_acq __int64 ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_nf|_InterlockedCompareExchange64_nf __int64 ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_rel|_InterlockedCompareExchange64_rel __int64 ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (Char, char \* , Char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (Char, char \* , Char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf (Char, char \* , Char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel (Char, char \* , Char)|
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchange128|niepodpisany znak _InterlockedCompareExchange128 ( \_ _int64 nietrwałe \* _Destination, \_ _int64 _ExchangeHigh, \_ _int64 _ExchangeLow, \_ _int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_acq|niepodpisany znak _InterlockedCompareExchange128_acq ( \_ _int64 nietrwałe \* _Destination, \_ _int64 _ExchangeHigh, \_ _int64 _ExchangeLow, \_ _int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|niepodpisany znak _InterlockedCompareExchange128_nf ( \_ _int64 nietrwałe \* _Destination, \_ _int64 _ExchangeHigh, \_ _int64 _ExchangeLow, \_ _int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|niepodpisany znak _InterlockedCompareExchange128_rel ( \_ _int64 nietrwałe \* _Destination, \_ _int64 _ExchangeHigh, \_ _int64 _ExchangeLow, \_ _int64 \* _ComparandResult)|
|_InterlockedDecrement|długi __cdecl _InterlockedDecrement (Long volatile \* )|
|_InterlockedDecrement16|krótkie _InterlockedDecrement16 (Short volatile \* )|
|_InterlockedDecrement16_acq|krótkie _InterlockedDecrement16_acq (Short volatile \* )|
|_InterlockedDecrement16_nf|krótkie _InterlockedDecrement16_nf (Short volatile \* )|
|_InterlockedDecrement16_rel|krótkie _InterlockedDecrement16_rel (Short volatile \* )|
|_InterlockedDecrement64|_InterlockedDecrement64 __int64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_acq|_InterlockedDecrement64_acq __int64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_nf|_InterlockedDecrement64_nf __int64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_rel|_InterlockedDecrement64_rel __int64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement_acq|długi _InterlockedDecrement_acq (Long volatile \* )|
|_InterlockedDecrement_nf|długi _InterlockedDecrement_nf (Long volatile \* )|
|_InterlockedDecrement_rel|długi _InterlockedDecrement_rel (Long volatile \* )|
|_InterlockedExchange|długi __cdecl _InterlockedExchange (Long volatile \* _Target Long)|
|_InterlockedExchange_acq|długi _InterlockedExchange_acq (długa nietrwała \* _Target, Long)|
|_InterlockedExchange_nf|długi _InterlockedExchange_nf (długa nietrwała \* _Target, Long)|
|_InterlockedExchange_rel|długi _InterlockedExchange_rel (długa nietrwała \* _Target, Long)|
|_InterlockedExchange16|krótkie _InterlockedExchange16 (krótkie _Target nietrwałe \* , krótkie)|
|_InterlockedExchange16_acq|krótkie _InterlockedExchange16_acq (krótkie _Target nietrwałe \* , krótkie)|
|_InterlockedExchange16_nf|krótkie _InterlockedExchange16_nf (krótkie _Target nietrwałe \* , krótkie)|
|_InterlockedExchange16_rel|krótkie _InterlockedExchange16_rel (krótkie _Target nietrwałe \* , krótkie)|
|_InterlockedExchange64|_InterlockedExchange64 __int64 ( \_ _int64 volatile \* _Target, \_ _int64)|
|_InterlockedExchange64_acq|_InterlockedExchange64_acq __int64 ( \_ _int64 volatile \* _Target, \_ _int64)|
|_InterlockedExchange64_nf|_InterlockedExchange64_nf __int64 ( \_ _int64 volatile \* _Target, \_ _int64)|
|_InterlockedExchange64_rel|_InterlockedExchange64_rel __int64 ( \_ _int64 volatile \* _Target, \_ _int64)|
|_InterlockedExchange8|znak _InterlockedExchange8 (znak nietrwały \* _Target, Char)|
|_InterlockedExchange8_acq|znak _InterlockedExchange8_acq (znak nietrwały \* _Target, Char)|
|_InterlockedExchange8_nf|znak _InterlockedExchange8_nf (znak nietrwały \* _Target, Char)|
|_InterlockedExchange8_rel|znak _InterlockedExchange8_rel (znak nietrwały \* _Target, Char)|
|_InterlockedExchangeAdd|długi __cdecl _InterlockedExchangeAdd (Long volatile \* , Long)|
|_InterlockedExchangeAdd16|Krótki _InterlockedExchangeAdd16 (krótki nietrwały \* , krótki)|
|_InterlockedExchangeAdd16_acq|Krótki _InterlockedExchangeAdd16_acq (krótki nietrwały \* , krótki)|
|_InterlockedExchangeAdd16_nf|Krótki _InterlockedExchangeAdd16_nf (krótki nietrwały \* , krótki)|
|_InterlockedExchangeAdd16_rel|Krótki _InterlockedExchangeAdd16_rel (krótki nietrwały \* , krótki)|
|_InterlockedExchangeAdd64|_InterlockedExchangeAdd64 __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_acq|_InterlockedExchangeAdd64_acq __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_nf|_InterlockedExchangeAdd64_nf __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_rel|_InterlockedExchangeAdd64_rel __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8 (Char volatile \* , Char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq (Char volatile \* , Char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf (Char volatile \* , Char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel (Char volatile \* , Char)|
|_InterlockedExchangeAdd_acq|długi _InterlockedExchangeAdd_acq (Long volatile \* , Long)|
|_InterlockedExchangeAdd_nf|długi _InterlockedExchangeAdd_nf (Long volatile \* , Long)|
|_InterlockedExchangeAdd_rel|długi _InterlockedExchangeAdd_rel (Long volatile \* , Long)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* volatile \* _Target, void \* )|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq (void \* volatile \* _Target, void \* )|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* volatile \* _Target, void \* )|
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel (void \* volatile \* _Target, void \* )|
|_InterlockedIncrement|długi __cdecl _InterlockedIncrement (Long volatile \* )|
|_InterlockedIncrement16|krótkie _InterlockedIncrement16 (Short volatile \* )|
|_InterlockedIncrement16_acq|krótkie _InterlockedIncrement16_acq (Short volatile \* )|
|_InterlockedIncrement16_nf|krótkie _InterlockedIncrement16_nf (Short volatile \* )|
|_InterlockedIncrement16_rel|krótkie _InterlockedIncrement16_rel (Short volatile \* )|
|_InterlockedIncrement64|_InterlockedIncrement64 __int64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_acq|_InterlockedIncrement64_acq __int64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_nf|_InterlockedIncrement64_nf __int64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_rel|_InterlockedIncrement64_rel __int64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement_acq|długi _InterlockedIncrement_acq (Long volatile \* )|
|_InterlockedIncrement_nf|długi _InterlockedIncrement_nf (Long volatile \* )|
|_InterlockedIncrement_rel|długi _InterlockedIncrement_rel (Long volatile \* )|
|_InterlockedOr|długi _InterlockedOr (Long volatile \* , Long)|
|_InterlockedOr16|Krótki _InterlockedOr16 (krótki nietrwały \* , krótki)|
|_InterlockedOr16_acq|Krótki _InterlockedOr16_acq (krótki nietrwały \* , krótki)|
|_InterlockedOr16_nf|Krótki _InterlockedOr16_nf (krótki nietrwały \* , krótki)|
|_InterlockedOr16_rel|Krótki _InterlockedOr16_rel (krótki nietrwały \* , krótki)|
|_InterlockedOr64|_InterlockedOr64 __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_acq|_InterlockedOr64_acq __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_nf|_InterlockedOr64_nf __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_rel|_InterlockedOr64_rel __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr8|char _InterlockedOr8 (Char volatile \* , Char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq (Char volatile \* , Char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf (Char volatile \* , Char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel (Char volatile \* , Char)|
|_InterlockedOr_acq|długi _InterlockedOr_acq (Long volatile \* , Long)|
|_InterlockedOr_nf|długi _InterlockedOr_nf (Long volatile \* , Long)|
|_InterlockedOr_rel|długi _InterlockedOr_rel (Long volatile \* , Long)|
|_InterlockedXor|długi _InterlockedXor (Long volatile \* , Long)|
|_InterlockedXor16|Krótki _InterlockedXor16 (krótki nietrwały \* , krótki)|
|_InterlockedXor16_acq|Krótki _InterlockedXor16_acq (krótki nietrwały \* , krótki)|
|_InterlockedXor16_nf|Krótki _InterlockedXor16_nf (krótki nietrwały \* , krótki)|
|_InterlockedXor16_rel|Krótki _InterlockedXor16_rel (krótki nietrwały \* , krótki)|
|_InterlockedXor64|_InterlockedXor64 __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_acq|_InterlockedXor64_acq __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_nf|_InterlockedXor64_nf __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_rel|_InterlockedXor64_rel __int64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor8|char _InterlockedXor8 (Char volatile \* , Char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq (Char volatile \* , Char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf (Char volatile \* , Char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel (Char volatile \* , Char)|
|_InterlockedXor_acq|długi _InterlockedXor_acq (Long volatile \* , Long)|
|_InterlockedXor_nf|długi _InterlockedXor_nf (Long volatile \* , Long)|
|_InterlockedXor_rel|długi _InterlockedXor_rel (Long volatile \* , Long)|

[[Wróć do początku](#top)]

### <a name="_interlockedbittest-intrinsics"></a>elementy wewnętrzne _interlockedbittest

Wewnętrzne testy bitowe z blokadą są wspólne dla wszystkich platform. ARM64 dodaje `_acq` , `_rel` i `_nf` warianty, które po prostu modyfikują semantykę bariery operacji, zgodnie z opisem w [_nf (bez ogrodzenia) sufiks](#nf_suffix) wcześniej w tym artykule.

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|_interlockedbittestandreset|niepodpisany znak _interlockedbittestandreset (Long volatile \* , Long)|
|_interlockedbittestandreset_acq|niepodpisany znak _interlockedbittestandreset_acq (Long volatile \* , Long)|
|_interlockedbittestandreset_nf|niepodpisany znak _interlockedbittestandreset_nf (Long volatile \* , Long)|
|_interlockedbittestandreset_rel|niepodpisany znak _interlockedbittestandreset_rel (Long volatile \* , Long)|
|_interlockedbittestandreset64|niepodpisany znak _interlockedbittestandreset64 (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_acq|niepodpisany znak _interlockedbittestandreset64_acq (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_nf|niepodpisany znak _interlockedbittestandreset64_nf (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_rel|niepodpisany znak _interlockedbittestandreset64_rel (__int64 volatile \* , __int64)|
|_interlockedbittestandset|niepodpisany znak _interlockedbittestandset (Long volatile \* , Long)|
|_interlockedbittestandset_acq|niepodpisany znak _interlockedbittestandset_acq (Long volatile \* , Long)|
|_interlockedbittestandset_nf|niepodpisany znak _interlockedbittestandset_nf (Long volatile \* , Long)|
|_interlockedbittestandset_rel|niepodpisany znak _interlockedbittestandset_rel (Long volatile \* , Long)|
|_interlockedbittestandset64|niepodpisany znak _interlockedbittestandset64 (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_acq|niepodpisany znak _interlockedbittestandset64_acq (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_nf|niepodpisany znak _interlockedbittestandset64_nf (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_rel|niepodpisany znak _interlockedbittestandset64_rel (__int64 volatile \* , __int64)|

[[Wróć do początku](#top)]

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Funkcje wewnętrzne ARM](arm-intrinsics.md)\
[Dokumentacja asemblera ARM](../assembler/arm/arm-assembler-reference.md)\
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)
