---
title: Funkcje wewnętrzne ARM64
description: Lista odwołań do wewnętrznych arm64 obsługiwanych przez kompilator Microsoft C++ w programie Visual Studio.
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
ms.openlocfilehash: 27325df55d128337a45e76bbf5387508a523f57c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754524"
---
# <a name="arm64-intrinsics"></a>Funkcje wewnętrzne ARM64

Kompilator Microsoft C++ (MSVC) udostępnia następujące elementy wewnętrzne w architekturze ARM64. Aby uzyskać więcej informacji na temat usługi ARM, zobacz sekcje Architektury i narzędzi programistycznych w [witrynie ARM Developer Documentation](https://developer.arm.com/docs) w sieci Web.

## <a name="neon"></a><a name="top"></a>Neon

Rozszerzenia zestawu instrukcji wektorowych NEON dla ARM64 zapewniają funkcje pojedynczej instrukcji wielokrotnego przesyłania danych (SIMD). Przypominają one te w zestawach instrukcji wektorowych MMX i SSE, które są wspólne dla procesorów architektury x86 i x64.

Neon intrinsics są obsługiwane, jak przewidziano w pliku nagłówka *arm64_neon.h*. Obsługa msvc dla neonu wewnętrznego przypomina kompilator ARM64, który jest udokumentowany w [ARM NEON Intrinsic Reference](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) w arm infocenter stronie internetowej.

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a>Lista wewnętrzną specyficzna dla ARM64

|Nazwa funkcji|Instrukcja|Prototyp funkcji|
|-------------------|-----------------|------------------------|
|__break|Brk|nieważne __break(int)|
|__addx18byte||void __addx18byte (niepodpisany długi, niepodpisany znak)|
|__addx18word||void __addx18word (niepodpisane długie, niepodpisane krótkie)|
|__addx18dword||void __addx18dword (niepodpisane długie, niepodpisane długie)|
|__addx18qword||void __addx18qword (niepodpisane długie, niepodpisane __int64)|
|__cas8|Casb ( CASB )|niepodpisane __cas8 __int8 (niepodpisane __int8 lotne* _Target, niepodpisane __int8 _Comp, niepodpisane __int8 _Value)|
|__cas16|Gotówki|niepodpisane __cas16 __int16 (niepodpisane __int16 lotne* _Target, niepodpisane _Comp __int16, niepodpisane __int16 _Value)|
|__cas32|CAS|niepodpisane __cas32 __int32 (niepodpisane __int32 _Target lotne*, niepodpisane _Comp __int32, niepodpisane _Value __int32)|
|__cas64|CAS|niepodpisane __cas64 __int64 (niepodpisane __int64 lotne* _Target, niepodpisane _Comp __int64, niepodpisane __int64 _Value)|
|__casa8|CASAB ( CASAB )|niepodpisane __int8 __casa8(niepodpisane __int8 lotne* _Target, niepodpisane _Comp __int8, niepodpisane __int8 _Value)|
|__casa16|Casah ( CASAH )|niepodpisane __casa16 __int16 (niepodpisane __int16 lotne* _Target, niepodpisane __int16 _Comp, niepodpisane __int16 _Value)|
|__casa32|Casa|niepodpisane __casa32 __int32 (niepodpisane _Target lotne* __int32, niepodpisane _Comp __int32, _Value __int32 niepodpisane)|
|__casa64|Casa|niepodpisane __int64 __casa64 (niepodpisane __int64 lotne* _Target, niepodpisane _Comp __int64, niepodpisane __int64 _Value)|
|__casl8|CASLB (własówk|niepodpisane __int8 __casl8 (niepodpisane __int8 lotne* _Target, niepodpisane _Comp __int8, niepodpisane __int8 _Value)|
|__casl16|CASLH (włas ie)|niepodpisane __casl16 __int16 (niepodpisane __int16 lotne* _Target, niepodpisane __int16 _Comp, niepodpisane __int16 _Value)|
|__casl32|CASL (włas ie|niepodpisane __casl32 __int32 (niepodpisane __int32 lotne* _Target, niepodpisane _Comp __int32, niepodpisane __int32 _Value)|
|__casl64|CASL (włas ie|niepodpisane __int64 __casl64 (niepodpisane __int64 lotne* _Target, niepodpisane _Comp __int64, niepodpisane __int64 _Value)|
|__casal8|CASALB (właso.|niepodpisane __int8 __casal8 __casal8 (niepodpisane __int8 lotne* _Target, niepodpisane __int8 _Comp, niepodpisane __int8 _Value)|
|__casal16|CASALH ( CASALH )|niepodpisane __casal16 __int16(niepodpisane __int16 lotne* _Target, niepodpisane _Comp __int16, niepodpisane __int16 _Value)|
|__casal32|Casal|niepodpisane __casal32 __int32 (niepodpisane __int32 lotne* _Target, niepodpisane _Comp __int32, niepodpisane _Value __int32)|
|__casal64|Casal|niepodpisane __casal64 __int64 (niepodpisane __int64 lotne* _Target, niepodpisane _Comp __int64, niepodpisane _Value __int64)|
|__crc32b|CRC32B|__crc32b niepodpisanych __int32 (__int32 niepodpisanych, niepodpisanych __int32)|
|__crc32h|CRC32H|__crc32h __int32 bez podpisu (__int32 niepodpisany, niepodpisany __int32)|
|__crc32w|CRC32W|__crc32w niepodpisanych __int32 (__int32 niepodpisanych, niepodpisanych __int32)|
|__crc32d|CRC32X|__crc32d niepodpisanych __int32 (__int32 niepodpisanych, niepodpisanych __int64)|
|__crc32cb|CRC32CB|__crc32cb __int32 bez podpisu (__int32 bez podpisu, __int32 bez podpisu)|
|__crc32ch|CRC32CH ( CRC32CH )|__int32 __crc32ch __int32 (__int32 niepodpisane, niepodpisane __int32)|
|__crc32cw|CRC32CW|__crc32cw __int32 bez podpisu (__int32 bez podpisu, __int32 bez podpisu)|
|__crc32cd|CRC32CX|__crc32cd __int32 bez podpisu (__int32 niepodpisany, __int64 niepodpisane)|
|__dmb|Dmb|void __dmb(unsigned int) `_Type`<br /><br /> Wstawia operację bariery pamięci do strumienia instrukcji. Parametr `_Type` określa rodzaj ograniczenia, który wymusza barierę.<br /><br /> Aby uzyskać więcej informacji na temat rodzajów ograniczeń, które mogą być egzekwowane, zobacz [Ograniczenia bariery pamięci](#BarrierRestrictions).|
|__dsb|Dsb|void __dsb (niepodpisane int _Type)<br /><br /> Wstawia operację bariery pamięci do strumienia instrukcji. Parametr `_Type` określa rodzaj ograniczenia, który wymusza barierę.<br /><br /> Aby uzyskać więcej informacji na temat rodzajów ograniczeń, które mogą być egzekwowane, zobacz [Ograniczenia bariery pamięci](#BarrierRestrictions).|
|__isb|Isb|void __isb (niepodpisane int _Type)<br /><br /> Wstawia operację bariery pamięci do strumienia instrukcji. Parametr `_Type` określa rodzaj ograniczenia, który wymusza barierę.<br /><br /> Aby uzyskać więcej informacji na temat rodzajów ograniczeń, które mogą być egzekwowane, zobacz [Ograniczenia bariery pamięci](#BarrierRestrictions).|
|__getReg||niepodpisane __int64 __getReg(int)|
|__getRegFp||podwójne __getRegFp(int)|
|__getCallerReg||niepodpisane __int64 __getCallerReg(int)|
|__getCallerRegFp||podwójne __getCallerRegFp(int)|
|__hvc|Hvc|unsigned int __hvc(unsigned int, ...)|
|__hlt|Hlt|int __hlt(unsigned int, ...)|
|__incx18byte||void __incx18byte (niepodpisane długo)|
|__incx18word||void __incx18word (niepodpisane długo)|
|__incx18dword||void __incx18dword (niepodpisane długo)|
|__incx18qword||void __incx18qword (niepodpisane długo)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatile \_ \*_int16)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load/magazynu wewnętrznego](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32(const volatile \_ \*_int32)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load/magazynu wewnętrznego](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (const volatile \_ \*_int64)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load/magazynu wewnętrznego](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const volatile \_ \*_int8)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load/magazynu wewnętrznego](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16(lotny \__int16 \*, \__int16)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load/magazynu wewnętrznego](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32(lotny \__int32 \*, \__int32)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load/magazynu wewnętrznego](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void __iso_volatile_store64(lotny \__int64 \*, \__int64)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load/magazynu wewnętrznego](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8(lotny \__int8 \*, \__int8)<br /><br /> Aby uzyskać więcej informacji, zobacz [__iso_volatile_load/magazynu wewnętrznego](#IsoVolatileLoadStore).|
|__ldar8|LDARB ( LDARB )|niepodpisane __ldar8 __int8 (niepodpisane __int8 lotne* _Target)|
|__ldar16|LDARH ( LDARH )|niepodpisane __int16 __ldar16 (niepodpisane __int16 lotne* _Target)|
|__ldar32|LDAR ( LDAR )|niepodpisane __int32 __ldar32 (niepodpisane __int32 lotne* _Target)|
|__ldar64|LDAR ( LDAR )|niepodpisane __ldar64 __int64 (niepodpisane __int64 lotne* _Target)|
|__ldapr8|LDAPRB ( LDAPRB )|niepodpisane __ldapr8 __int8 (niepodpisane __int8 lotne* _Target)|
|__ldapr16|LDAPRH ( LDAPRH )|niepodpisane __int16 __ldapr16 (niepodpisane __int16 lotne* _Target)|
|__ldapr32|LDAPR (LDAPR)|niepodpisane __ldapr32 __int32 (niepodpisane __int32 lotne* _Target)|
|__ldapr64|LDAPR (LDAPR)|niepodpisane __ldapr64 __int64 (niepodpisane __int64 lotne* _Target)|
|__mulh||\__int64 __mulh(\__int64, \__int64)|
|__prefetch|ŚR|void __cdecl \__prefetch(const void) \*<br /><br /> Zawiera `PRFM` wskazówkę dotyczącą pamięci z `PLDL1KEEP` operacją wstępnego dostępu do systemu, do których można wkrótce uzyskać dostęp do pamięci pod określonym adresem lub w pobliżu określonego adresu. Niektóre systemy mogą zoptymalizować dla tego wzorca dostępu do pamięci, aby zwiększyć wydajność środowiska uruchomieniowego. Jednak z punktu widzenia języka C++ funkcja nie ma zauważalnego efektu i może nic nie robić.|
|__prefetch2|ŚR|void __cdecl \__prefetch(const void \*, uint8_t prfop)<br /><br /> Zawiera `PRFM` wskazówkę dotyczącą pamięci z dostarczoną operacją wstępnego dostępu do systemu, do których można wkrótce uzyskać dostęp do pamięci pod określonym adresem lub w pobliżu określonego adresu. Niektóre systemy mogą zoptymalizować dla tego wzorca dostępu do pamięci, aby zwiększyć wydajność środowiska uruchomieniowego. Jednak z punktu widzenia języka C++ funkcja nie ma zauważalnego efektu i może nic nie robić.|
|__readx18byte||niepodpisany znak __readx18byte(niepodpisany długi)|
|__readx18word||niepodpisane krótkie __readx18word (niepodpisane długie)|
|__readx18dword||niepodpisane długie __readx18dword (niepodpisane długie)|
|__readx18qword||niepodpisane __readx18qword __int64 (niepodpisane długo)|
|__setReg||nieważne __setReg (int, niepodpisane __int64)|
|__setRegFp||void __setRegFp (int, double)|
|__setCallerReg||nieważne __setCallerReg (int, niepodpisane __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, double)|
|__sev|Sev|void __sev(void)|
|__static_assert||void __static_assert(int, const \*char)|
|__stlr8|STLRB ( STLRB )|void __stlr8(niepodpisane __int8 lotne* _Target, niepodpisane __int8 _Value)|
|__stlr16|STLRH ( STLRH )|void __stlr16(niepodpisane __int16 lotne* _Target, niepodpisane __int16 _Value)|
|__stlr32|Okręg wyborczy STLR|void __stlr32(niepodpisane __int32 lotne* _Target, niepodpisane __int32 _Value)|
|__stlr64|Okręg wyborczy STLR|void __stlr64(niepodpisane __int64 lotne* _Target, niepodpisane __int64 _Value)|
|__swp8|SWPB (właśc.|niepodpisane __swp8 __int8 (niepodpisane __int8 lotne* _Target, niepodpisane __int8 _Value)|
|__swp16|Swph ( swph )|niepodpisane __swp16 __int16 (niepodpisane __int16 lotne* _Target, niepodpisane __int16 _Value)|
|__swp32|Swp|niepodpisane __swp32 __int32 (niepodpisane __int32 lotne* _Target, niepodpisane __int32 _Value)|
|__swp64|Swp|niepodpisane __swp64 __int64 (niepodpisane __int64 lotne* _Target, niepodpisane __int64 _Value)|
|__swpa8|SWPAB ( SWPAB )|niepodpisane __swpa8 __int8 (niepodpisane __int8 lotne* _Target, niepodpisane __int8 _Value)|
|__swpa16|SWPAH (swpah)|niepodpisane __int16 __swpa16 (niepodpisane __int16 lotne* _Target, niepodpisane __int16 _Value)|
|__swpa32|Swpa ( SWPA )|niepodpisane __int32 __swpa32 (niepodpisane __int32 lotne* _Target, niepodpisane __int32 _Value)|
|__swpa64|Swpa ( SWPA )|niepodpisane __int64 __swpa64 (niepodpisane __int64 lotne* _Target, niepodpisane __int64 _Value)|
|__swpl8|SWPLB ( SWPLB )|niepodpisane __int8 __swpl8 (niepodpisane __int8 lotne* _Target, niepodpisane __int8 _Value)|
|__swpl16|SWPLH ( SWPLH )|niepodpisane __swpl16 __int16 (niepodpisane __int16 lotne* _Target, niepodpisane __int16 _Value)|
|__swpl32|SWPL ( SWPL )|niepodpisane __int32 __swpl32 (niepodpisane __int32 lotne* _Target, niepodpisane __int32 _Value)|
|__swpl64|SWPL ( SWPL )|niepodpisane __swpl64 __int64 (niepodpisane __int64 lotne* _Target, niepodpisane __int64 _Value)|
|__swpal8|SWPALB ( SWPALB )|niepodpisane __int8 __swpal8 (niepodpisane __int8 lotne* _Target, niepodpisane __int8 _Value)|
|__swpal16|SWPALH ( SWPALH )|niepodpisane __int16 __swpal16 (niepodpisane __int16 lotne* _Target, niepodpisane __int16 _Value)|
|__swpal32|Swpal|niepodpisane __int32 __swpal32 (niepodpisane __int32 lotne* _Target, niepodpisane __int32 _Value)|
|__swpal64|Swpal|niepodpisane __int64 __swpal64 (niepodpisane __int64 lotne* _Target, niepodpisane __int64 _Value)|
|__sys|Sys|unsigned int __sys(int, __int64)|
|__svc|Svc|unsigned int __svc(unsigned int, ...)|
|__wfe|Fronton internetowy|void __wfe(void)|
|__wfi|Wfi|void __wfi(void)|
|__writex18byte||void __writex18byte(niepodpisany długi, niepodpisany znak)|
|__writex18word||void __writex18word (niepodpisane długie, niepodpisane krótkie)|
|__writex18dword||void __writex18dword (niepodpisane długie, niepodpisane długie)|
|__writex18qword||void __writex18qword (niepodpisane długie, niepodpisane __int64)|
|__umulh||\___umulh _int64 bez podpisu \_(_int64 bez podpisu, _int64 niepodpisane) \_|
|_CopyDoubleFromInt64||podwójne _CopyDoubleFromInt64(\__int64)|
|_CopyFloatFromInt32||_CopyFloatFromInt32 pływakowa(\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(pływak)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(podwójne)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(niepodpisane długo)|
|_CountLeadingOnes64||niepodpisane _CountLeadingOnes64 int (niepodpisane \__int64)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||unsigned int _CountLeadingSigns64(\__int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(niepodpisane długo)|
|_CountLeadingZeros64||niepodpisane int _CountLeadingZeros64 (niepodpisane \__int64)|
|_ReadStatusReg|Pani|\__int64 _ReadStatusReg(int)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, \__int64)|

[[Powrót do góry](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>Ograniczenia barierowe pamięci

Funkcje `__dmb` wewnętrzne (bariera pamięci `__dsb` danych), (bariera `__isb` synchronizacji danych) i (bariera synchronizacji instrukcji) używają następujących wstępnie zdefiniowanych wartości, aby określić ograniczenie bariery pamięci pod względem domeny udostępniania i rodzaju dostępu, na który ma wpływ operacja.

|Wartość ograniczenia|Opis|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Pełny system, odczyty i zapisy.|
|_ARM64_BARRIER_ST|Pełny system, zapisuje tylko.|
|_ARM64_BARRIER_LD|Pełny system, tylko do odczytu.|
|_ARM64_BARRIER_ISH|Wewnętrzna sharable, odczytuje i pisze.|
|_ARM64_BARRIER_ISHST|Wewnętrzna sharable, pisze tylko.|
|_ARM64_BARRIER_ISHLD|Wewnętrzna sharable, tylko do odczytu.|
|_ARM64_BARRIER_NSH|Niezbywalne, odczytuje i pisze.|
|_ARM64_BARRIER_NSHST|Nie sharable, zapisuje tylko.|
|_ARM64_BARRIER_NSHLD|Niezbywalne, tylko do odczytu.|
|_ARM64_BARRIER_OSH|Zewnętrzna sharable, odczytuje i zapisuje.|
|_ARM64_BARRIER_OSHST|Zewnętrzna sharable, zapisuje tylko.|
|_ARM64_BARRIER_OSHLD|Zewnętrzne sharable, tylko do odczytu.|

W `__isb` przypadku wewnętrznych jedynym ograniczeniem, które jest obecnie ważne, jest _ARM64_BARRIER_SY; wszystkie inne wartości są zarezerwowane przez architekturę.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/magazyn

Te funkcje wewnętrzne jawnie wykonywać obciążenia i magazyny, które nie podlegają optymalizacji kompilatora.

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

*Lokalizacji*\
Adres lokalizacji pamięci do odczytu lub zapisu.

*Wartość*\
Wartość do zapisu do określonej lokalizacji pamięci (magazyn tylko wewnętrzne).

#### <a name="return-value-load-intrinsics-only"></a>Wartość zwracana (tylko wykastowe obciążenie)

Wartość lokalizacji pamięci określonej przez *Location*.

#### <a name="remarks"></a>Uwagi

Można użyć `__iso_volatile_load8/16/32/64` i `__iso_volatile_store8/16/32/64` intrinsics jawnie wykonywać dostępy do pamięci, które nie podlegają optymalizacji kompilatora. Kompilator nie można usunąć, syntetyzować lub zmienić względną kolejność tych operacji. Jednak nie generuje niejawne bariery pamięci sprzętowej. W związku z tym sprzęt może nadal ponownie zasądzać zauważalne dostępy do pamięci w wielu wątkach. Dokładniej, te elementy wewnętrzne są równoważne następującym wyrażeniom skompilowanym w **/volatile:iso**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Należy zauważyć, że wewnętrzne wskaźniki wziąć volatile wskaźniki w celu uwzględnienia zmiennych lotnych. Jednak nie ma żadnych wymagań lub zalecenia, aby użyć wskaźników nietrwałych jako argumenty. Semantyka tych operacji są dokładnie takie same, jeśli używany jest typ zwykły, nieulotny.

Aby uzyskać więcej informacji na temat argumentu wiersza polecenia **/volatile:iso,** zobacz [/volatile (volatile keyword interpretation)](../build/reference/volatile-volatile-keyword-interpretation.md).

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>Obsługa ARM64 dla wewnętrznego z innych architektur

W poniższej tabeli wymieniono elementy wewnętrzne innych architektur, które są obsługiwane na platformach ARM64. Gdy zachowanie wewnętrznej na ARM64 różni się od jego zachowania na innych architekturach sprzętu, dodatkowe szczegóły są zauważyć.

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|__assume|nieważne __assume(int)|
|__code_seg|void __code_seg(const char) \*|
|__debugbreak|void __cdecl \__debugbreak(void)|
|__fastfail|__declspec(noreturn) void \__fastfail(unsigned int)|
|__nop|void __nop(void)|
|__yield|void __yield(void) **Uwaga:** Na platformach ARM64 ta funkcja generuje instrukcję YIELD. Ta instrukcja wskazuje, że wątek wykonuje zadanie, które może być tymczasowo zawieszone w wykonaniu — na przykład spinlock — bez negatywnego wpływu na program. Umożliwia procesorowi CPU wykonywanie innych zadań podczas cykli wykonywania, które w przeciwnym razie zostałyby zmarnowane.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress(void)|
|_BitScanForward|niepodpisane _BitScanForward char (niepodpisane długie \* _Index, niepodpisane długie _Mask)|
|_BitScanForward64|niepodpisane _BitScanForward64 char (niepodpisane _Index długie, \* niepodpisane __int64 _Mask)|
|_BitScanReverse|niepodpisane _BitScanReverse char (niepodpisane długie \* _Index, niepodpisane długie _Mask)|
|_BitScanReverse64|niepodpisane _BitScanReverse64 char (niepodpisane _Index długie, \* niepodpisane __int64 _Mask)|
|_bittest|niepodpisany znak _bittest (długi \*const, długi)|
|_bittest64|niepodpisane _bittest64 char(__int64 const \*, __int64)|
|_bittestandcomplement|niepodpisany znak _bittestandcomplement (długi, \*długi)|
|_bittestandcomplement64|niepodpisane _bittestandcomplement64 char(__int64 \*, __int64)|
|_bittestandreset|niepodpisany znak _bittestandreset \*(długi, długi)|
|_bittestandreset64|niepodpisane _bittestandreset64 char(__int64 \*, __int64)|
|_bittestandset|niepodpisany znak _bittestandset (długi, \*długi)|
|_bittestandset64|niepodpisane _bittestandset64 char(__int64 \*, __int64)|
|_byteswap_uint64|niepodpisane __int64 \__byteswap_uint64 _cdecl (_int64 niepodpisane) \_|
|_byteswap_ulong|niepodpisane długie __cdecl _byteswap_ulong (niepodpisane długie)|
|_byteswap_ushort|niepodpisane krótkie _byteswap_ushort __cdecl (niepodpisane krótkie)|
|_disable|void __cdecl _disable(void) **Uwaga:** Na platformach ARM64 ta funkcja generuje `MSR DAIFCLR,#2`instrukcję; jest dostępny tylko jako nieodłączny element.|
|_enable|void __cdecl _enable(void) **Uwaga:** Na platformach ARM64 ta funkcja generuje `MSR DAIFSET,#2`instrukcję; jest dostępny tylko jako nieodłączny element.|
|_lrotl|niepodpisane długie __cdecl _lrotl (niepodpisane długie, int)|
|_lrotr|niepodpisane długie __cdecl _lrotr (niepodpisane długie, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress(void)|
|_rotl|unsigned int __cdecl _rotl (unsigned int _Value, int _Shift)|
|_rotl16|niepodpisane krótkie _rotl16 (niepodpisane krótkie _Value, niepodpisane _Shift char)|
|_rotl64|niepodpisane __int64 \__cdecl _rotl64 (_Value _int64 niepodpisane, \_int _Shift)|
|_rotl8|niepodpisane _rotl8 char(niepodpisane _Value char, niepodpisane char _Shift)|
|_rotr|unsigned int __cdecl _rotr (unsigned int _Value, int _Shift)|
|_rotr16|niepodpisane krótkie _rotr16 (niepodpisane krótkie _Value, niepodpisane _Shift char)|
|_rotr64|niepodpisane __int64 \__cdecl _rotr64 (_Value _int64 niepodpisane, \_int _Shift)|
|_rotr8|niepodpisane _rotr8 char(niepodpisane _Value char, niepodpisane char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[Powrót do góry](#top)]

## <a name="interlocked-intrinsics"></a>Zablokowane środki wewnętrzne

Interlocked intrinsics to zestaw wewnętrznych, które są używane do wykonywania operacji atomowego odczytu i modyfikowania zapisu. Niektóre z nich są wspólne dla wszystkich platform. Są one wymienione oddzielnie tutaj, ponieważ istnieje duża liczba z nich. Ponieważ ich definicje są w większości zbędne, łatwiej jest myśleć o nich w kategoriach ogólnych. Ich nazwy mogą służyć do wyprowadzania dokładnych zachowań.

W poniższej tabeli podsumowano obsługę ARM64 nie-bittest zablokowane wewnętrzne. Każda komórka w tabeli odpowiada nazwie, która jest pochodną przez dołączenie nazwy operacji w lewej komórce wiersza i nazwy `_Interlocked`typu w komórce najwyższej wielkości kolumny do . Na przykład komórka na przecięciu `Xor` `8` wiersza i `_InterlockedXor8` kolumny odpowiada i jest w pełni obsługiwana. Większość obsługiwanych funkcji oferuje te opcjonalne `_acq`przyrostki: , `_rel`, i `_nf`. Sufiks `_acq` wskazuje semantyczne "nabyć", `_rel` a sufiks oznacza semantyczną "release". Przyrostek `_nf` "bez ogrodzenia" jest unikatowy dla ARM i ARM64 i jest omówiony w następnej sekcji.

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Dodaj|Brak|Brak|Pełne|Pełne|Brak|Brak|
|And|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|Compareexchange|Pełne|Pełne|Pełne|Pełne|Pełne|Pełne|
|Zmniejszyć|Brak|Pełne|Pełne|Pełne|Brak|Brak|
|Exchange|Pełne|Pełne|Pełne|Pełne|Brak|Pełne|
|Wymiana Addd|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|Przyrost|Brak|Pełne|Pełne|Pełne|Brak|Brak|
|Lub|Pełne|Pełne|Pełne|Pełne|Brak|Brak|
|Xor|Pełne|Pełne|Pełne|Pełne|Brak|Brak|

Klucz:

- **Pełna**: obsługuje `_acq` `_rel`zwykły, `_nf` , i formy.

- **Brak:** Nie obsługiwane

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>przyrostek _nf (bez ogrodzenia)

Sufiks `_nf` "bez ogrodzenia" wskazuje, że operacja nie zachowuje się jak żadna bariera pamięci, `_acq`w `_rel`przeciwieństwie do pozostałych trzech form (zwykły, i ), które zachowują się jak pewnego rodzaju bariera. Jednym z możliwych `_nf` zastosowań formularzy jest obsługa licznika statystyk, który jest aktualizowany przez wiele wątków w tym samym czasie, ale którego wartość nie jest używana w inny sposób podczas wykonywania wielu wątków.

### <a name="list-of-interlocked-intrinsics"></a>Lista zablokowanych wewnętrznych

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|_InterlockedAdd|długi _InterlockedAdd (długi \*_volatile, długi)|
|_InterlockedAdd64|__int64 _InterlockedAdd64(\__int64 lotny \*, \__int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq _int64 _int64\_lotnych \* \_|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf(\__int64 lotny \*, \__int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel(\__int64 lotny, \* \__int64)|
|_InterlockedAdd_acq|długi _InterlockedAdd_acq (długi lotny, \*długi)|
|_InterlockedAdd_nf|długi _InterlockedAdd_nf (długi lotny, \*długi)|
|_InterlockedAdd_rel|długi _InterlockedAdd_rel (długi lotny, \*długi)|
|_InterlockedAnd|długi _InterlockedAnd (długi lotny, \*długi)|
|_InterlockedAnd16|krótki _InterlockedAnd16 (krótki lotny, \*krótki)|
|_InterlockedAnd16_acq|krótki _InterlockedAnd16_acq (krótki lotny, \*krótki)|
|_InterlockedAnd16_nf|krótki _InterlockedAnd16_nf (krótki \*lotny, krótki)|
|_InterlockedAnd16_rel|krótki _InterlockedAnd16_rel (krótki \*lotny, krótki)|
|_InterlockedAnd64|__int64 _InterlockedAnd64(\__int64 lotny \*, \__int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq _int64 _int64\__int64 \* \_|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf(\__int64 lotny \*, \__int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel(\__int64 lotny \*, \__int64)|
|_InterlockedAnd8|char _InterlockedAnd8(char volatile \*, char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq(char volatile \*, char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf(char volatile \*, char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel(char volatile \*, char)|
|_InterlockedAnd_acq|długi _InterlockedAnd_acq (długi lotny, \*długi)|
|_InterlockedAnd_nf|długi _InterlockedAnd_nf (długi lotny, \*długi)|
|_InterlockedAnd_rel|długi _InterlockedAnd_rel (długi lotny, \*długi)|
|_InterlockedCompareExchange|długi __cdecl _InterlockedCompareExchange (długi lotny, \*długi, długi)|
|_InterlockedCompareExchange_acq|długi _InterlockedCompareExchange_acq (długi lotny, \*długi, długi)|
|_InterlockedCompareExchange_nf|długi _InterlockedCompareExchange_nf (długi lotny, \*długi, długi)|
|_InterlockedCompareExchange_rel|długi _InterlockedCompareExchange_rel (długi lotny, \*długi, długi)|
|_InterlockedCompareExchange16|krótki _InterlockedCompareExchange16 (krótki lotny, \*krótki, krótki)|
|_InterlockedCompareExchange16_acq|krótki _InterlockedCompareExchange16_acq (krótki \*lotny, krótki, krótki)|
|_InterlockedCompareExchange16_nf|krótki _InterlockedCompareExchange16_nf (krótki lotny, \*krótki, krótki)|
|_InterlockedCompareExchange16_rel|krótki _InterlockedCompareExchange16_rel (krótki lotny, \*krótki, krótki)|
|_InterlockedCompareExchange64|\___int64 _InterlockedCompareExchange64( _int64 \*lotny, \__int64, \__int64)|
|_InterlockedCompareExchange64_acq|\___int64 _InterlockedCompareExchange64_acq( _int64 \*lotny, \__int64, \__int64)|
|_InterlockedCompareExchange64_nf|\___int64 _InterlockedCompareExchange64_nf( _int64 \*lotny, \__int64, \__int64)|
|_InterlockedCompareExchange64_rel|\___int64 _InterlockedCompareExchange64_rel( _int64 \*lotny, \__int64, \__int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8(char volatile \*, char, char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq(char volatile, \*char, char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf(char volatile \*, char, char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel(char volatile \*, char, char)|
|_InterlockedCompareExchangePointer|void \* \* _InterlockedCompareExchangePointer(void volatile \*, \*void \*, void )|
|_InterlockedCompareExchangePointer_acq|void \* \* _InterlockedCompareExchangePointer_acq(void volatile \*, \*void \*, void )|
|_InterlockedCompareExchangePointer_nf|void \* \* _InterlockedCompareExchangePointer_nf(void volatile \*, \*void \*, void )|
|_InterlockedCompareExchangePointer_rel|void \* \* _InterlockedCompareExchangePointer_rel(void volatile \*, \*void \*, void )|
|_InterlockedCompareExchange128|_InterlockedCompareExchange128\__int64 \* lotnych, \__Destination _ExchangeHigh _int64 _int64 _ExchangeLow \__int64, \_ \* _int64 _ComparandResult)|
|_InterlockedCompareExchange128_acq|\__InterlockedCompareExchange128_acq \* _int64 lotnych, \__Destination _ExchangeHigh _int64 _int64 _ExchangeLow \__int64, \_ \* _int64 _ComparandResult.|
|_InterlockedCompareExchange128_nf|_InterlockedCompareExchange128_nf _Destination\__int64 _ExchangeHigh _int64 \* \__int64, \__ExchangeLow _int64 \__int64 _int64 \* _ComparandResult.|
|_InterlockedCompareExchange128_rel|\__InterlockedCompareExchange128_rel _int64 lotnych, \* \__Destination _int64 _ExchangeHigh \__int64 _ExchangeLow, \__int64 \* _ComparandResult.|
|_InterlockedDecrement|długi __cdecl _InterlockedDecrement (długi lotny) \*|
|_InterlockedDecrement16|krótki _InterlockedDecrement16 (krótki lotny) \*|
|_InterlockedDecrement16_acq|krótki _InterlockedDecrement16_acq (krótki lotny) \*|
|_InterlockedDecrement16_nf|krótki _InterlockedDecrement16_nf (krótki \*lotny)|
|_InterlockedDecrement16_rel|krótki _InterlockedDecrement16_rel (krótki lotny) \*|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64(\__int64 lotny) \*|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq(\__int64 lotny) \*|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf(\__int64 lotny) \*|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel(\__int64 lotny) \*|
|_InterlockedDecrement_acq|długi _InterlockedDecrement_acq (długi lotny) \*|
|_InterlockedDecrement_nf|długi _InterlockedDecrement_nf(długi lotny) \*|
|_InterlockedDecrement_rel|długi _InterlockedDecrement_rel(długi lotny) \*|
|_InterlockedExchange|długi __cdecl _InterlockedExchange (długi lotny \* _Target, długi)|
|_InterlockedExchange_acq|długi _InterlockedExchange_acq (długi \* lotny _Target, długi)|
|_InterlockedExchange_nf|długi _InterlockedExchange_nf (długi \* lotny _Target, długi)|
|_InterlockedExchange_rel|długi _InterlockedExchange_rel (długi lotny \* _Target, długi)|
|_InterlockedExchange16|krótki _InterlockedExchange16 (krótki lotny \* _Target, krótki)|
|_InterlockedExchange16_acq|krótki _InterlockedExchange16_acq (krótki lotny \* _Target, krótki)|
|_InterlockedExchange16_nf|krótki _InterlockedExchange16_nf (krótki lotny \* _Target, krótki)|
|_InterlockedExchange16_rel|krótki _InterlockedExchange16_rel (krótki lotny \* _Target, krótki)|
|_InterlockedExchange64|__int64 _InterlockedExchange64(\__int64 lotnych \* _Target, \__int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq(\__int64 lotny \* _Target, \__int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf(\__int64 lotnych \* _Target, \__int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel(\__int64 lotnych \* _Target, \__int64)|
|_InterlockedExchange8|char _InterlockedExchange8(char volatile \* _Target, char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq(char volatile \* _Target, char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf(char volatile \* _Target, char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel(char volatile \* _Target, char)|
|_InterlockedExchangeAdd|długi __cdecl _InterlockedExchangeAdd (długi lotny, \*długi)|
|_InterlockedExchangeAdd16|krótki _InterlockedExchangeAdd16 (krótki lotny, \*krótki)|
|_InterlockedExchangeAdd16_acq|krótki _InterlockedExchangeAdd16_acq (krótki lotny, \*krótki)|
|_InterlockedExchangeAdd16_nf|krótki _InterlockedExchangeAdd16_nf (krótki \*lotny, krótki)|
|_InterlockedExchangeAdd16_rel|krótki _InterlockedExchangeAdd16_rel (krótki \*lotny, krótki)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64(\__int64 lotny \*, \__int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq(\__int64 lotny \*, \__int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf(\__int64 lotny \*, \__int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel(\__int64 lotny \*, \__int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8(char volatile \*, char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq(char volatile \*, char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf(char volatile \*, char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel(char volatile \*, char)|
|_InterlockedExchangeAdd_acq|długi _InterlockedExchangeAdd_acq (długi lotny, \*długi)|
|_InterlockedExchangeAdd_nf|długi _InterlockedExchangeAdd_nf (długi lotny, \*długi)|
|_InterlockedExchangeAdd_rel|długi _InterlockedExchangeAdd_rel (długi lotny, \*długi)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer(void \* volatile \* _Target, void) \*|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq(void \* volatile \* _Target, void) \*|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf(void \* volatile \* _Target, void) \*|
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel(void \* volatile \* _Target, void) \*|
|_InterlockedIncrement|długi __cdecl _InterlockedIncrement (długo lotny) \*|
|_InterlockedIncrement16|krótki _InterlockedIncrement16 (krótki lotny) \*|
|_InterlockedIncrement16_acq|krótki _InterlockedIncrement16_acq (krótki lotny) \*|
|_InterlockedIncrement16_nf|krótki _InterlockedIncrement16_nf (krótki \*lotny)|
|_InterlockedIncrement16_rel|krótki _InterlockedIncrement16_rel (krótki lotny) \*|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64(\__int64 lotny) \*|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq(\__int64 lotny) \*|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf(\__int64 lotny) \*|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel(\__int64 lotny) \*|
|_InterlockedIncrement_acq|długi _InterlockedIncrement_acq (długi lotny) \*|
|_InterlockedIncrement_nf|długi _InterlockedIncrement_nf(długi lotny) \*|
|_InterlockedIncrement_rel|długi _InterlockedIncrement_rel (długi lotny) \*|
|_InterlockedOr|długi _InterlockedOr (długi lotny, \*długi)|
|_InterlockedOr16|krótki _InterlockedOr16 (krótki \*lotny, krótki)|
|_InterlockedOr16_acq|krótki _InterlockedOr16_acq (krótki lotny, \*krótki)|
|_InterlockedOr16_nf|krótki _InterlockedOr16_nf (krótki lotny, \*krótki)|
|_InterlockedOr16_rel|krótki _InterlockedOr16_rel (krótki lotny, \*krótki)|
|_InterlockedOr64|__int64 _InterlockedOr64(\__int64 lotny, \* \__int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq(\__int64 lotny \*, \__int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf _int64(\__int64 lotny) \* \_|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel(\__int64 lotny \*, \__int64)|
|_InterlockedOr8|char _InterlockedOr8(char volatile \*, char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq(char volatile \*, char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf(char volatile \*, char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel(char volatile \*, char)|
|_InterlockedOr_acq|długi _InterlockedOr_acq (długi lotny, \*długi)|
|_InterlockedOr_nf|długi _InterlockedOr_nf (długi lotny, \*długi)|
|_InterlockedOr_rel|długi _InterlockedOr_rel (długi lotny, \*długi)|
|_InterlockedXor|długi _InterlockedXor (długi \*lotny, długi)|
|_InterlockedXor16|krótki _InterlockedXor16 (krótki lotny, \*krótki)|
|_InterlockedXor16_acq|krótki _InterlockedXor16_acq (krótki \*lotny, krótki)|
|_InterlockedXor16_nf|krótki _InterlockedXor16_nf (krótki lotny, \*krótki)|
|_InterlockedXor16_rel|krótki _InterlockedXor16_rel (krótki \*lotny, krótki)|
|_InterlockedXor64|__int64 _InterlockedXor64(\__int64 lotny, \* \__int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq _int64 _int64 lotnych(\__int64 \*lotnych) \_|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf(\__int64 lotny \*, \__int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel(\__int64 lotny \*, \__int64)|
|_InterlockedXor8|char _InterlockedXor8(char volatile \*, char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq(char volatile \*, char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf(char volatile \*, char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel(char volatile \*, char)|
|_InterlockedXor_acq|długi _InterlockedXor_acq (długi lotny, \*długi)|
|_InterlockedXor_nf|długi _InterlockedXor_nf (długi \*lotny, długi)|
|_InterlockedXor_rel|długi _InterlockedXor_rel (długi lotny, \*długi)|

[[Powrót do góry](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest wewnętrzną

Wywiązuje się ze zwykłych powiązanych obrażeń testowych bitów są wspólne dla wszystkich platform. ARM64 `_acq`dodaje `_rel`, `_nf` i warianty, które po prostu zmodyfikować semantykę bariery operacji, jak opisano w [_nf (bez ogrodzenia) Sufiks](#nf_suffix) wcześniej w tym artykule.

|Nazwa funkcji|Prototyp funkcji|
|-------------------|------------------------|
|_interlockedbittestandreset|niepodpisany znak _interlockedbittestandreset (długi \*lotny, długi)|
|_interlockedbittestandreset_acq|niepodpisany znak _interlockedbittestandreset_acq (długi \*lotny, długi)|
|_interlockedbittestandreset_nf|niepodpisany znak _interlockedbittestandreset_nf (długi \*lotny, długi)|
|_interlockedbittestandreset_rel|niepodpisany znak _interlockedbittestandreset_rel (długi \*lotny, długi)|
|_interlockedbittestandreset64|niepodpisane _interlockedbittestandreset64 char(__int64 lotny, \*__int64)|
|_interlockedbittestandreset64_acq|niepodpisane _interlockedbittestandreset64_acq char(__int64 lotny, \*__int64)|
|_interlockedbittestandreset64_nf|niepodpisane _interlockedbittestandreset64_nf char(__int64 lotny, \*__int64)|
|_interlockedbittestandreset64_rel|niepodpisane _interlockedbittestandreset64_rel char(__int64 lotny, \*__int64)|
|_interlockedbittestandset|niepodpisany znak _interlockedbittestandset (długi \*lotny, długi)|
|_interlockedbittestandset_acq|niepodpisany znak _interlockedbittestandset_acq (długi \*lotny, długi)|
|_interlockedbittestandset_nf|niepodpisany znak _interlockedbittestandset_nf (długi \*lotny, długi)|
|_interlockedbittestandset_rel|niepodpisany znak _interlockedbittestandset_rel (długi \*lotny, długi)|
|_interlockedbittestandset64|niepodpisane _interlockedbittestandset64 char(__int64 lotny, \*__int64)|
|_interlockedbittestandset64_acq|niepodpisane _interlockedbittestandset64_acq char(__int64 lotny, \*__int64)|
|_interlockedbittestandset64_nf|niepodpisane _interlockedbittestandset64_nf char(__int64 lotny, \*__int64)|
|_interlockedbittestandset64_rel|niepodpisane _interlockedbittestandset64_rel char(__int64 lotny, \*__int64)|

[[Powrót do góry](#top)]

## <a name="see-also"></a>Zobacz też

[Wewnętrzne właściwości kompilatora](../intrinsics/compiler-intrinsics.md)\
[Wewnętrzne właściwości arm](arm-intrinsics.md)\
[Odniesienie do asemblera ARM](../assembler/arm/arm-assembler-reference.md)\
[Odwołanie do języka C++](../cpp/cpp-language-reference.md)
