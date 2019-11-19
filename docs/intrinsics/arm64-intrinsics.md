---
title: ARM64 wewnętrzne
description: Lista elementów wewnętrznych ARM64 obsługiwanych przez kompilator firmy Microsoft C++ .
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
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 30881c2b45714f91bf9035819b11ae41322b7086
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163672"
---
# <a name="arm64-intrinsics"></a>ARM64 wewnętrzne

Kompilator firmy C++ Microsoft (MSVC) udostępnia następujące elementy wewnętrzne architektury arm64. Aby uzyskać więcej informacji na temat usługi ARM, zobacz sekcje architektury i narzędzi programistycznych dla deweloperów w witrynie sieci Web usługi [ARM](https://developer.arm.com/docs) .

## <a name="top"></a>NEON

Rozszerzenia zestawu instrukcji wektora NEON dla ARM64 zapewniają możliwości Single Instruction Multiple Data (SIMD). Są one podobne do tych w zestawach wektorowych MMX i SSE, które są wspólne dla procesorów architektury x86 i x64.

Elementy wewnętrzne NEONu są obsługiwane, jak to przedstawiono w pliku nagłówkowym *arm64_neon. h*. Obsługa MSVC dla wewnętrznych elementów jest podobna do kompilatora ARM64, który jest udokumentowany w [wewnętrznej referencji ARM](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) w witrynie ARM InfoCenter.

##  <a name="A"></a>Lista elementów wewnętrznych specyficznych dla ARM64

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
|__dmb|DMB|void __dmb (niepodpisane `_Type`int)<br /><br /> Wstawia operację bariery pamięci do strumienia instrukcji. Parametr `_Type` określa rodzaj ograniczeń wymuszanych przez barierę.<br /><br /> Aby uzyskać więcej informacji na temat rodzajów ograniczeń, które można wymusić, zobacz [ograniczenia dotyczące bariery pamięci](#BarrierRestrictions).|
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
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatile \__int16 \*)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const volatile \__int32 \*)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (const volatile \__int64 \*)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const volatile \__int8 \*)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16 (nietrwałe \__int16 \*, \__int16)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32 (nietrwałe \__int32 \*, \__int32)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void __iso_volatile_store64 (nietrwałe \__int64 \*, \__int64)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8 (nietrwałe \__int8 \*, \__int8)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load wewnętrzne/Store](#IsoVolatileLoadStore).|
|__ldar8|LDARB|niepodpisane __ldar8 __int8 (unsigned __int8 volatile * _Target)|
|__ldar16|LDARH|niepodpisane __ldar16 __int16 (unsigned __int16 volatile * _Target)|
|__ldar32|LDAR|niepodpisane __ldar32 __int32 (unsigned __int32 volatile * _Target)|
|__ldar64|LDAR|niepodpisane __ldar64 __int64 (unsigned __int64 volatile * _Target)|
|__ldapr8|LDAPRB|niepodpisane __ldapr8 __int8 (unsigned __int8 volatile * _Target)|
|__ldapr16|LDAPRH|niepodpisane __ldapr16 __int16 (unsigned __int16 volatile * _Target)|
|__ldapr32|Protokół LDAP|niepodpisane __ldapr32 __int32 (unsigned __int32 volatile * _Target)|
|__ldapr64|Protokół LDAP|niepodpisane __ldapr64 __int64 (unsigned __int64 volatile * _Target)|
|__mulh||\__int64 __mulh (\__int64, \__int64)|
|__prefetch|PRFM|void __cdecl \__prefetch (const void \*)<br /><br /> Zapewnia `PRFM` wskazówkę z `PLDL1KEEP` operacji pobierania z wyprzedzeniem do systemu, w którym można szybko uzyskać dostęp do pamięci w określonym adresie lub w bliskiej jego lokalizacji. Niektóre systemy mogą zoptymalizować ten wzorzec dostępu do pamięci, aby zwiększyć wydajność środowiska uruchomieniowego. Jednakże z punktu widzenia C++ języka funkcja nie ma zauważalnego efektu i może nic nie robić.|
|__prefetch2|PRFM|void __cdecl \__prefetch (const void \*, uint8_t prfop)<br /><br /> Zapewnia wskazówkę `PRFM` Memory z podaną operacją pobierania z wyprzedzeniem w systemie, w której może zostać wkrótce uzyskany dostęp do pamięci w określonym adresie lub w bliskiej lokalizacji. Niektóre systemy mogą zoptymalizować ten wzorzec dostępu do pamięci, aby zwiększyć wydajność środowiska uruchomieniowego. Jednakże z punktu widzenia C++ języka funkcja nie ma zauważalnego efektu i może nic nie robić.|
|__readx18byte||niepodpisany znak __readx18byte (liczba bez znaku)|
|__readx18word||krótkie __readx18word bez znaku (bez znaku)|
|__readx18dword||niepodpisane długie __readx18dword (liczba bez znaku)|
|__readx18qword||niepodpisane __readx18qword __int64 (liczba bez znaku)|
|__setReg||void __setReg (int, unsigned __int64)|
|__setRegFp||void __setRegFp (int, Double)|
|__setCallerReg||void __setCallerReg (int, unsigned __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, Double)|
|__sev|WAŻNOŚĆ|void __sev (void)|
|__static_assert||void __static_assert (int, const char \*)|
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
|__wfe|WFE|void __wfe (void)|
|__wfi|WFI|void __wfi (void)|
|__writex18byte||void __writex18byte (unsigned long, znak bez znaku)|
|__writex18word||void __writex18word (Long unsigned unsigned Short)|
|__writex18dword||void __writex18dword (Long bez znaku, Long unsigned)|
|__writex18qword||void __writex18qword (Long unsigned, unsigned __int64)|
|__umulh||niepodpisane \__int64 __umulh (bez znaku \__int64, bez znaku \_)|
|_CopyDoubleFromInt64||podwójne _CopyDoubleFromInt64 (\__int64)|
|_CopyFloatFromInt32||_CopyFloatFromInt32 zmiennoprzecinkowe (\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat (float)|
|_CopyInt64FromDouble||_CopyInt64FromDouble __int64 (Double)|
|_CountLeadingOnes||niepodpisane _CountLeadingOnes int (liczba bez znaku)|
|_CountLeadingOnes64||niepodpisane _CountLeadingOnes64 int (niepodpisane \__int64)|
|_CountLeadingSigns||niepodpisane _CountLeadingSigns int (Long)|
|_CountLeadingSigns64||niepodpisane _CountLeadingSigns64 int (\__int64)|
|_CountLeadingZeros||niepodpisane _CountLeadingZeros int (liczba bez znaku)|
|_CountLeadingZeros64||niepodpisane _CountLeadingZeros64 int (niepodpisane \__int64)|
|_ReadStatusReg|Marta|\__int64 _ReadStatusReg (int)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, \__int64)|

[[Wróć do początku](#top)]

###  <a name="BarrierRestrictions"></a>Ograniczenia dotyczące barier pamięci

Funkcje wewnętrzne `__dmb` (bariera pamięci danych), `__dsb` (bariera synchronizacji danych) i `__isb` (bariera synchronizacji instrukcji) używają następujących wstępnie zdefiniowanych wartości do określenia ograniczenia dotyczącego bariery pamięci w zakresie domeny udostępniania i rodzaju dostępu, na który ma wpływ operacja.

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

W przypadku `__isb` wewnętrznego jedynym aktualnie prawidłowym ograniczeniem jest _ARM64_BARRIER_SY; wszystkie inne wartości są zarezerwowane przez architekturę.

###  <a name="IsoVolatileLoadStore"></a>__iso_volatile_load wewnętrzne/Store

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

\ *lokalizacji*
Adres lokalizacji pamięci, z której ma zostać odczytany lub zapisany.

\ *wartości*
Wartość do zapisu w określonej lokalizacji pamięci (tylko elementy wewnętrzne sklepu).

#### <a name="return-value-load-intrinsics-only"></a>Wartość zwracana (tylko wewnętrzne obciążenia)

Wartość lokalizacji pamięci, która jest określona przez *lokalizację*.

#### <a name="remarks"></a>Uwagi

Za pomocą `__iso_volatile_load8/16/32/64` i `__iso_volatile_store8/16/32/64` wewnętrznych można jawnie wykonywać dostęp do pamięci, które nie podlegają optymalizacji kompilatora. Kompilator nie może usunąć, synthetize ani zmienić względnej kolejności tych operacji. Nie generują one jednak niejawnych barier pamięci sprzętowej. W związku z tym sprzęt może nadal zmienić kolejność zauważalnych dostępów do pamięci w wielu wątkach. Dokładniej te elementy wewnętrzne są równoważne następującym wyrażeniem, które zostały skompilowane w obszarze **/volatile: ISO**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Zwróć uwagę, że elementy wewnętrzne przyjmują nietrwałe wskaźniki, aby pomieścić zmienne lotne. Jednakże nie jest wymagane ani zalecenie, aby użyć nietrwałych wskaźników jako argumentów. Semantyka tych operacji jest dokładnie taka sama, jeśli jest używany zwykły, nietrwały typ.

Aby uzyskać więcej informacji na temat argumentu wiersza polecenia **/volatile: ISO** , zobacz [/volatile (interpretacja słowa kluczowego volatile)](../build/reference/volatile-volatile-keyword-interpretation.md).

##  <a name="I"></a>Obsługa ARM64 wewnętrznych z innych architektur

Poniższa tabela zawiera listę funkcji wewnętrznych z innych architektur, które są obsługiwane na platformach ARM64. W przypadku, gdy zachowanie elementu wewnętrznego na ARM64 różni się od zachowania w przypadku innych architektur sprzętowych, należy zauważyć dodatkowe szczegóły.

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|__assume|void __assume (int)|
|__code_seg|void __code_seg (stała char \*)|
|__debugbreak|void __cdecl \__debugbreak (void)|
|__fastfail|__declspec (noreturn) void \__fastfail (bez znaku int)|
|__nop|void __nop (void)|
|__yield|void __yield (void) **Uwaga:** na platformach arm64 ta funkcja GENERUJE instrukcję Yield. Ta instrukcja wskazuje, że wątek wykonuje zadanie, które może być tymczasowo zawieszone przed wykonaniem — na przykład struktury spinlock — bez negatywnego wpływu na program. Umożliwia PROCESORowi wykonywanie innych zadań podczas cyklów wykonywania, które w przeciwnym razie byłyby tracone.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void)|
|_BitScanForward|niepodpisany znak _BitScanForward (niepodpisane długie \* _Index, niepodpisane długie _Mask)|
|_BitScanForward64|niepodpisane _BitScanForward64 znakowe (niepodpisane długie \* _Index, niepodpisane __int64 _Mask)|
|_BitScanReverse|niepodpisany znak _BitScanReverse (niepodpisane długie \* _Index, niepodpisane długie _Mask)|
|_BitScanReverse64|niepodpisane _BitScanReverse64 znakowe (niepodpisane długie \* _Index, niepodpisane __int64 _Mask)|
|_bittest|niepodpisany znak _bittest (Long const \*, Long)|
|_bittest64|niepodpisany znak _bittest64 (__int64 stała \*, __int64)|
|_bittestandcomplement|niepodpisany znak _bittestandcomplement (Long \*, Long)|
|_bittestandcomplement64|niepodpisany znak _bittestandcomplement64 (__int64 \*, __int64)|
|_bittestandreset|niepodpisany znak _bittestandreset (Long \*, Long)|
|_bittestandreset64|niepodpisany znak _bittestandreset64 (__int64 \*, __int64)|
|_bittestandset|niepodpisany znak _bittestandset (Long \*, Long)|
|_bittestandset64|niepodpisany znak _bittestandset64 (__int64 \*, __int64)|
|_byteswap_uint64|niepodpisane __int64 \__cdecl _byteswap_uint64 (niepodpisane \__int64)|
|_byteswap_ulong|niepodpisane długie __cdecl _byteswap_ulong (bez znaku)|
|_byteswap_ushort|niepodpisane krótkie __cdecl _byteswap_ushort (krótkie bez znaku)|
|_disable|void __cdecl _disable (void) **Uwaga:** na platformach arm64 ta funkcja generuje instrukcję `MSR DAIFCLR,#2`; jest on dostępny tylko jako wewnętrzny.|
|_enable|void __cdecl _enable (void) **Uwaga:** na platformach arm64 ta funkcja generuje instrukcję `MSR DAIFSET,#2`; jest on dostępny tylko jako wewnętrzny.|
|_lrotl|niepodpisane długie __cdecl _lrotl (Long, int)|
|_lrotr|niepodpisane długie __cdecl _lrotr (Long, int)|
|_ReadBarrier|void _ReadBarrier (void)|
|_ReadWriteBarrier|void _ReadWriteBarrier (void)|
|_ReturnAddress|void \* _ReturnAddress (void)|
|_rotl|niepodpisane _rotl int __cdecl (niepodpisane _Value int, int _Shift)|
|_rotl16|niepodpisane krótkie _rotl16 (krótkie _Shift _Value niepodpisanego znaku)|
|_rotl64|niepodpisane __int64 \__cdecl _rotl64 (bez znaku \__int64 _Value, int _Shift)|
|_rotl8|niepodpisany znak _rotl8 (znak bez znaku _Value, niepodpisany znak _Shift)|
|_rotr|niepodpisane _rotr int __cdecl (niepodpisane _Value int, int _Shift)|
|_rotr16|niepodpisane krótkie _rotr16 (krótkie _Shift _Value niepodpisanego znaku)|
|_rotr64|niepodpisane __int64 \__cdecl _rotr64 (bez znaku \__int64 _Value, int _Shift)|
|_rotr8|niepodpisany znak _rotr8 (znak bez znaku _Value, niepodpisany znak _Shift)|
|_setjmpex|_setjmpex int __cdecl (jmp_buf)|
|_WriteBarrier|void _WriteBarrier (void)|

[[Wróć do początku](#top)]

## <a name="interlocked-intrinsics"></a>Blokady wewnętrzne

Wbudowane elementy wewnętrzne są zestawem wewnętrznych, które są używane do wykonywania niepodzielnych operacji odczytu i zapisu. Niektóre z nich są wspólne dla wszystkich platform. Są one wyświetlane osobno w tym miejscu, ponieważ istnieje duża liczba. Ze względu na to, że ich definicje są najczęściej nadmiarowe, łatwiej jest myśleć o nich w ogólnych warunkach. Ich nazwy mogą służyć do uzyskania dokładnych zachowań.

Poniższa tabela zawiera podsumowanie obsługi ARM64, które nie są Zablokowani. Każda komórka w tabeli odnosi się do nazwy, która jest tworzona przez dołączenie nazwy operacji w lewej górnej komórce wiersza i nazwy typu w górnej komórce kolumny do `_Interlocked`. Na przykład, komórka na przecięciu wiersza `Xor` i kolumny `8` odpowiada `_InterlockedXor8` i jest w pełni obsługiwany. Większość obsługiwanych funkcji oferuje następujące opcjonalne sufiksy: `_acq`, `_rel`i `_nf`. Sufiks `_acq` wskazuje semantykę "pozyskiwania", a sufiks `_rel` wskazuje semantykę "Release". Sufiks `_nf` lub "No ogrodzenia" jest unikatowy dla ARM i ARM64 i został omówiony w następnej sekcji.

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Dodaj|Brak|Brak|Pełne|Pełne|Brak|Brak|
|Lub|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|CompareExchange|Pełne|Pełne|Pełne|Pełne|Pełne|Pełne|
|Dekrementacji|Brak|Pełne|Pełne|Pełne|Brak|Brak|
|Program Exchange|Pełne|Pełne|Pełne|Pełne|Brak|Pełne|
|ExchangeAdd|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|Pełny|Brak|Pełne|Pełne|Pełne|Brak|Brak|
|Lub|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|XOR|Pełne|Pełne|Pełne|Pełne|Brak|Brak|

Głównych

- **Pełna**: obsługuje formularze zwykłe, `_acq`, `_rel`i `_nf`.

- **Brak**: nieobsługiwane

###  <a name="nf_suffix"></a>sufiks _nf (bez ogrodzenia)

Sufiks `_nf` lub "No ogrodzenia" wskazuje, że operacja nie zachowuje się jako żadnego rodzaju bariery pamięci, w przeciwieństwie do innych trzech form (zwykłych, `_acq`i `_rel`), które działają w przypadku niektórych rodzajów barier. Jednym z możliwych użycia formularzy `_nf` jest zachowanie licznika statystyk, który jest aktualizowany przez wiele wątków w tym samym czasie, ale którego wartość nie jest używana w przypadku wykonywania wielu wątków.

### <a name="list-of-interlocked-intrinsics"></a>Lista zablokowanych elementów wewnętrznych

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|_InterlockedAdd|długi _InterlockedAdd (Long _volatile \*, Long)|
|_InterlockedAdd64|_InterlockedAdd64 __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_acq|_InterlockedAdd64_acq __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_nf|_InterlockedAdd64_nf __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_rel|_InterlockedAdd64_rel __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedAdd_acq|długi _InterlockedAdd_acq (długa nietrwała \*, Long)|
|_InterlockedAdd_nf|długi _InterlockedAdd_nf (długa nietrwała \*, Long)|
|_InterlockedAdd_rel|długi _InterlockedAdd_rel (długa nietrwała \*, Long)|
|_InterlockedAnd|długi _InterlockedAnd (długa nietrwała \*, Long)|
|_InterlockedAnd16|krótkie _InterlockedAnd16 (krótkie \*nietrwałe, krótkie)|
|_InterlockedAnd16_acq|krótkie _InterlockedAnd16_acq (krótkie \*nietrwałe, krótkie)|
|_InterlockedAnd16_nf|krótkie _InterlockedAnd16_nf (krótkie \*nietrwałe, krótkie)|
|_InterlockedAnd16_rel|krótkie _InterlockedAnd16_rel (krótkie \*nietrwałe, krótkie)|
|_InterlockedAnd64|_InterlockedAnd64 __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_acq|_InterlockedAnd64_acq __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_nf|_InterlockedAnd64_nf __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_rel|_InterlockedAnd64_rel __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedAnd8|znak _InterlockedAnd8 (znak nietrwały \*, Char)|
|_InterlockedAnd8_acq|znak _InterlockedAnd8_acq (znak nietrwały \*, Char)|
|_InterlockedAnd8_nf|znak _InterlockedAnd8_nf (znak nietrwały \*, Char)|
|_InterlockedAnd8_rel|znak _InterlockedAnd8_rel (znak nietrwały \*, Char)|
|_InterlockedAnd_acq|długi _InterlockedAnd_acq (długa nietrwała \*, Long)|
|_InterlockedAnd_nf|długi _InterlockedAnd_nf (długa nietrwała \*, Long)|
|_InterlockedAnd_rel|długi _InterlockedAnd_rel (długa nietrwała \*, Long)|
|_InterlockedCompareExchange|długi __cdecl _InterlockedCompareExchange (Long volatile \*, Long, Long)|
|_InterlockedCompareExchange_acq|długi _InterlockedCompareExchange_acq (długa nietrwała \*, Long, Long)|
|_InterlockedCompareExchange_nf|długi _InterlockedCompareExchange_nf (długa nietrwała \*, Long, Long)|
|_InterlockedCompareExchange_rel|długi _InterlockedCompareExchange_rel (długa nietrwała \*, Long, Long)|
|_InterlockedCompareExchange16|krótkie _InterlockedCompareExchange16 (krótkie nietrwałe \*, krótkie, krótkie)|
|_InterlockedCompareExchange16_acq|krótkie _InterlockedCompareExchange16_acq (krótkie nietrwałe \*, krótkie, krótkie)|
|_InterlockedCompareExchange16_nf|krótkie _InterlockedCompareExchange16_nf (krótkie nietrwałe \*, krótkie, krótkie)|
|_InterlockedCompareExchange16_rel|krótkie _InterlockedCompareExchange16_rel (krótkie nietrwałe \*, krótkie, krótkie)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange8|znak _InterlockedCompareExchange8 (znak nietrwały \*, char, Char)|
|_InterlockedCompareExchange8_acq|znak _InterlockedCompareExchange8_acq (znak nietrwały \*, char, Char)|
|_InterlockedCompareExchange8_nf|znak _InterlockedCompareExchange8_nf (znak nietrwały \*, char, Char)|
|_InterlockedCompareExchange8_rel|znak _InterlockedCompareExchange8_rel (znak nietrwały \*, char, Char)|
|_InterlockedCompareExchangePointer|_InterlockedCompareExchangePointer \* void (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_acq|_InterlockedCompareExchangePointer_acq \* void (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_nf|_InterlockedCompareExchangePointer_nf \* void (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchangePointer_rel|_InterlockedCompareExchangePointer_rel \* void (void \* volatile \*, void \*, void \*)|
|_InterlockedCompareExchange128|niepodpisany znak _InterlockedCompareExchange128 (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_acq|niepodpisany znak _InterlockedCompareExchange128_acq (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|niepodpisany znak _InterlockedCompareExchange128_nf (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|niepodpisany znak _InterlockedCompareExchange128_rel (\__int64 volatile \* _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedDecrement|długi __cdecl _InterlockedDecrement (Long volatile \*)|
|_InterlockedDecrement16|krótkie _InterlockedDecrement16 (krótkie \*nietrwałe)|
|_InterlockedDecrement16_acq|krótkie _InterlockedDecrement16_acq (krótkie \*nietrwałe)|
|_InterlockedDecrement16_nf|krótkie _InterlockedDecrement16_nf (krótkie \*nietrwałe)|
|_InterlockedDecrement16_rel|krótkie _InterlockedDecrement16_rel (krótkie \*nietrwałe)|
|_InterlockedDecrement64|_InterlockedDecrement64 __int64 (\__int64 volatile \*)|
|_InterlockedDecrement64_acq|_InterlockedDecrement64_acq __int64 (\__int64 volatile \*)|
|_InterlockedDecrement64_nf|_InterlockedDecrement64_nf __int64 (\__int64 volatile \*)|
|_InterlockedDecrement64_rel|_InterlockedDecrement64_rel __int64 (\__int64 volatile \*)|
|_InterlockedDecrement_acq|długi _InterlockedDecrement_acq (Long volatile \*)|
|_InterlockedDecrement_nf|długi _InterlockedDecrement_nf (Long volatile \*)|
|_InterlockedDecrement_rel|długi _InterlockedDecrement_rel (Long volatile \*)|
|_InterlockedExchange|długi __cdecl _InterlockedExchange (Long volatile \* _Target, Long)|
|_InterlockedExchange_acq|długi _InterlockedExchange_acq (Long volatile \* _Target, Long)|
|_InterlockedExchange_nf|długi _InterlockedExchange_nf (Long volatile \* _Target, Long)|
|_InterlockedExchange_rel|długi _InterlockedExchange_rel (Long volatile \* _Target, Long)|
|_InterlockedExchange16|krótkie _InterlockedExchange16 (krótkie \* nietrwałe _Target, krótkie)|
|_InterlockedExchange16_acq|krótkie _InterlockedExchange16_acq (krótkie \* nietrwałe _Target, krótkie)|
|_InterlockedExchange16_nf|krótkie _InterlockedExchange16_nf (krótkie \* nietrwałe _Target, krótkie)|
|_InterlockedExchange16_rel|krótkie _InterlockedExchange16_rel (krótkie \* nietrwałe _Target, krótkie)|
|_InterlockedExchange64|__int64 _InterlockedExchange64 (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (znak nietrwały \* _Target, Char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (znak nietrwały \* _Target, Char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (znak nietrwały \* _Target, Char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (znak nietrwały \* _Target, Char)|
|_InterlockedExchangeAdd|długi __cdecl _InterlockedExchangeAdd (Long volatile \*Long)|
|_InterlockedExchangeAdd16|krótkie _InterlockedExchangeAdd16 (krótkie \*nietrwałe, krótkie)|
|_InterlockedExchangeAdd16_acq|krótkie _InterlockedExchangeAdd16_acq (krótkie \*nietrwałe, krótkie)|
|_InterlockedExchangeAdd16_nf|krótkie _InterlockedExchangeAdd16_nf (krótkie \*nietrwałe, krótkie)|
|_InterlockedExchangeAdd16_rel|krótkie _InterlockedExchangeAdd16_rel (krótkie \*nietrwałe, krótkie)|
|_InterlockedExchangeAdd64|_InterlockedExchangeAdd64 __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_acq|_InterlockedExchangeAdd64_acq __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_nf|_InterlockedExchangeAdd64_nf __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_rel|_InterlockedExchangeAdd64_rel __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd8|znak _InterlockedExchangeAdd8 (znak nietrwały \*, Char)|
|_InterlockedExchangeAdd8_acq|znak _InterlockedExchangeAdd8_acq (znak nietrwały \*, Char)|
|_InterlockedExchangeAdd8_nf|znak _InterlockedExchangeAdd8_nf (znak nietrwały \*, Char)|
|_InterlockedExchangeAdd8_rel|znak _InterlockedExchangeAdd8_rel (znak nietrwały \*, Char)|
|_InterlockedExchangeAdd_acq|długi _InterlockedExchangeAdd_acq (długa nietrwała \*, Long)|
|_InterlockedExchangeAdd_nf|długi _InterlockedExchangeAdd_nf (długa nietrwała \*, Long)|
|_InterlockedExchangeAdd_rel|długi _InterlockedExchangeAdd_rel (długa nietrwała \*, Long)|
|_InterlockedExchangePointer|_InterlockedExchangePointer \* void (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_acq|_InterlockedExchangePointer_acq \* void (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_nf|_InterlockedExchangePointer_nf \* void (void \* volatile \* _Target, void \*)|
|_InterlockedExchangePointer_rel|_InterlockedExchangePointer_rel \* void (void \* volatile \* _Target, void \*)|
|_InterlockedIncrement|długi __cdecl _InterlockedIncrement (Long volatile \*)|
|_InterlockedIncrement16|krótkie _InterlockedIncrement16 (krótkie \*nietrwałe)|
|_InterlockedIncrement16_acq|krótkie _InterlockedIncrement16_acq (krótkie \*nietrwałe)|
|_InterlockedIncrement16_nf|krótkie _InterlockedIncrement16_nf (krótkie \*nietrwałe)|
|_InterlockedIncrement16_rel|krótkie _InterlockedIncrement16_rel (krótkie \*nietrwałe)|
|_InterlockedIncrement64|_InterlockedIncrement64 __int64 (\__int64 volatile \*)|
|_InterlockedIncrement64_acq|_InterlockedIncrement64_acq __int64 (\__int64 volatile \*)|
|_InterlockedIncrement64_nf|_InterlockedIncrement64_nf __int64 (\__int64 volatile \*)|
|_InterlockedIncrement64_rel|_InterlockedIncrement64_rel __int64 (\__int64 volatile \*)|
|_InterlockedIncrement_acq|długi _InterlockedIncrement_acq (Long volatile \*)|
|_InterlockedIncrement_nf|długi _InterlockedIncrement_nf (Long volatile \*)|
|_InterlockedIncrement_rel|długi _InterlockedIncrement_rel (Long volatile \*)|
|_InterlockedOr|długi _InterlockedOr (długa nietrwała \*, Long)|
|_InterlockedOr16|krótkie _InterlockedOr16 (krótkie \*nietrwałe, krótkie)|
|_InterlockedOr16_acq|krótkie _InterlockedOr16_acq (krótkie \*nietrwałe, krótkie)|
|_InterlockedOr16_nf|krótkie _InterlockedOr16_nf (krótkie \*nietrwałe, krótkie)|
|_InterlockedOr16_rel|krótkie _InterlockedOr16_rel (krótkie \*nietrwałe, krótkie)|
|_InterlockedOr64|_InterlockedOr64 __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_acq|_InterlockedOr64_acq __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_nf|_InterlockedOr64_nf __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_rel|_InterlockedOr64_rel __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedOr8|znak _InterlockedOr8 (znak nietrwały \*, Char)|
|_InterlockedOr8_acq|znak _InterlockedOr8_acq (znak nietrwały \*, Char)|
|_InterlockedOr8_nf|znak _InterlockedOr8_nf (znak nietrwały \*, Char)|
|_InterlockedOr8_rel|znak _InterlockedOr8_rel (znak nietrwały \*, Char)|
|_InterlockedOr_acq|długi _InterlockedOr_acq (długa nietrwała \*, Long)|
|_InterlockedOr_nf|długi _InterlockedOr_nf (długa nietrwała \*, Long)|
|_InterlockedOr_rel|długi _InterlockedOr_rel (długa nietrwała \*, Long)|
|_InterlockedXor|długi _InterlockedXor (długa nietrwała \*, Long)|
|_InterlockedXor16|krótkie _InterlockedXor16 (krótkie \*nietrwałe, krótkie)|
|_InterlockedXor16_acq|krótkie _InterlockedXor16_acq (krótkie \*nietrwałe, krótkie)|
|_InterlockedXor16_nf|krótkie _InterlockedXor16_nf (krótkie \*nietrwałe, krótkie)|
|_InterlockedXor16_rel|krótkie _InterlockedXor16_rel (krótkie \*nietrwałe, krótkie)|
|_InterlockedXor64|_InterlockedXor64 __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_acq|_InterlockedXor64_acq __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_nf|_InterlockedXor64_nf __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_rel|_InterlockedXor64_rel __int64 (\__int64 volatile \*, \__int64)|
|_InterlockedXor8|znak _InterlockedXor8 (znak nietrwały \*, Char)|
|_InterlockedXor8_acq|znak _InterlockedXor8_acq (znak nietrwały \*, Char)|
|_InterlockedXor8_nf|znak _InterlockedXor8_nf (znak nietrwały \*, Char)|
|_InterlockedXor8_rel|znak _InterlockedXor8_rel (znak nietrwały \*, Char)|
|_InterlockedXor_acq|długi _InterlockedXor_acq (długa nietrwała \*, Long)|
|_InterlockedXor_nf|długi _InterlockedXor_nf (długa nietrwała \*, Long)|
|_InterlockedXor_rel|długi _InterlockedXor_rel (długa nietrwała \*, Long)|

[[Wróć do początku](#top)]

### <a name="_interlockedbittest-intrinsics"></a>elementy wewnętrzne _interlockedbittest

Wewnętrzne testy bitowe z blokadą są wspólne dla wszystkich platform. ARM64 dodaje `_acq`, `_rel`i `_nf` wariantów, które po prostu modyfikują semantykę bariery operacji, zgodnie z opisem w temacie [_nf (brak ogranicznika)](#nf_suffix) wcześniej w tym artykule.

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|_interlockedbittestandreset|niepodpisany znak _interlockedbittestandreset (długa nietrwała \*, Long)|
|_interlockedbittestandreset_acq|niepodpisany znak _interlockedbittestandreset_acq (długa nietrwała \*, Long)|
|_interlockedbittestandreset_nf|niepodpisany znak _interlockedbittestandreset_nf (długa nietrwała \*, Long)|
|_interlockedbittestandreset_rel|niepodpisany znak _interlockedbittestandreset_rel (długa nietrwała \*, Long)|
|_interlockedbittestandreset64|niepodpisany znak _interlockedbittestandreset64 (__int64 nietrwałe \*, __int64)|
|_interlockedbittestandreset64_acq|niepodpisany znak _interlockedbittestandreset64_acq (__int64 nietrwałe \*, __int64)|
|_interlockedbittestandreset64_nf|niepodpisany znak _interlockedbittestandreset64_nf (__int64 nietrwałe \*, __int64)|
|_interlockedbittestandreset64_rel|niepodpisany znak _interlockedbittestandreset64_rel (__int64 nietrwałe \*, __int64)|
|_interlockedbittestandset|niepodpisany znak _interlockedbittestandset (długa nietrwała \*, Long)|
|_interlockedbittestandset_acq|niepodpisany znak _interlockedbittestandset_acq (długa nietrwała \*, Long)|
|_interlockedbittestandset_nf|niepodpisany znak _interlockedbittestandset_nf (długa nietrwała \*, Long)|
|_interlockedbittestandset_rel|niepodpisany znak _interlockedbittestandset_rel (długa nietrwała \*, Long)|
|_interlockedbittestandset64|niepodpisany znak _interlockedbittestandset64 (__int64 nietrwałe \*, __int64)|
|_interlockedbittestandset64_acq|niepodpisany znak _interlockedbittestandset64_acq (__int64 nietrwałe \*, __int64)|
|_interlockedbittestandset64_nf|niepodpisany znak _interlockedbittestandset64_nf (__int64 nietrwałe \*, __int64)|
|_interlockedbittestandset64_rel|niepodpisany znak _interlockedbittestandset64_rel (__int64 nietrwałe \*, __int64)|

[[Wróć do początku](#top)]

## <a name="see-also"></a>Zobacz także

\ [Wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
\ [wewnętrzne ARM](arm-intrinsics.md)
[Odwołanie asemblera ARM](../assembler/arm/arm-assembler-reference.md)\
[C++Dokumentacja języka](../cpp/cpp-language-reference.md)
