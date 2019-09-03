---
title: __fastfail
ms.date: 09/02/2019
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: 34198409c6a57eb494bfe819b367b71405a84e64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222196"
---
# <a name="__fastfail"></a>__fastfail

**Microsoft Specific**

Natychmiast kończy proces wywołujący z minimalnym obciążeniem.

## <a name="syntax"></a>Składnia

```C
void __fastfail(unsigned int code);
```

### <a name="parameters"></a>Parametry

*kodu*\
podczas `FAST_FAIL_<description>` Symboliczna stała z pliku Winnt. h lub WDM. h, która wskazuje przyczynę zakończenia procesu.

## <a name="return-value"></a>Wartość zwracana

`__fastfail` Wewnętrzna nie zwraca.

## <a name="remarks"></a>Uwagi

Wewnętrznie udostępnia mechanizm szybkiego żądania niepowodzenia — sposób, w jaki proces potencjalnie uszkodzony może zażądać natychmiastowego zakończenia procesu. `__fastfail` Krytyczne błędy, które mogą mieć uszkodzony stan programu i stosu poza odzyskiwaniem, nie mogą być obsługiwane przez funkcję regularnego obsługi wyjątków. Użyj `__fastfail` , aby przerwać proces przy użyciu minimalnego obciążenia.

Wewnętrznie program `__fastfail` jest implementowany przy użyciu kilku mechanizmów specyficznych dla architektury:

|Architektura|Instrukcja|Lokalizacja argumentu kodu|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|`ecx`|
|X64|int 0x29|`rcx`|
|ARM|0xDEFB kodu operacji|`r0`|
|ARM64|0xF003 kodu operacji|`x0`|

Szybkie żądanie niepowodzenia jest samodzielne i zwykle wymaga wykonania tylko dwóch instrukcji. Po wykonaniu szybkiego żądania niepowodzenia jądro podejmuje odpowiednie działanie. W kodzie trybu użytkownika nie ma żadnych zależności pamięci poza wskaźnikiem instrukcji, gdy zostanie zgłoszone zdarzenie szybkiego błędu. To maksymalizuje swoją niezawodność, nawet w przypadku poważnych uszkodzeń pamięci.

Argument, jeden `FAST_FAIL_<description>` ze stałych symbolicznych z Winnt. h lub WDM. h, opisuje typ warunku niepowodzenia. `code` Jest on włączany do raportów o błędach w sposób specyficzny dla środowiska.

Szybkie błędy w trybie użytkownika są wyświetlane jako wyjątek, który nie jest ciągły, z kodem wyjątku 0xC0000409 oraz co najmniej jeden parametr wyjątku. Pierwszy parametr wyjątku jest `code` wartością. Ten kod wyjątku wskazuje na Raportowanie błędów systemu Windows (raportowanie błędów) i infrastrukturę debugowania, że proces jest uszkodzony, a w odpowiedzi na awarię należy podjąć minimalne akcje w procesie. Żądania szybkiego niepowodzenia w trybie jądra są implementowane przy użyciu dedykowanego kodu `KERNEL_SECURITY_CHECK_FAILURE` wykrywania (0x139). W obu przypadkach nie są wywoływane programy obsługi wyjątków, ponieważ oczekuje się, że program jest w stanie uszkodzenia. Jeśli jest obecny debuger, ma możliwość sprawdzenia stanu programu przed zakończeniem.

Obsługa natywnego, wbudowanego mechanizmu awarii systemu Windows 8. Systemy operacyjne Windows, które nie obsługują instrukcji Fast Fail, natywnie zazwyczaj traktują szybkie żądanie niepowodzenia jako naruszenie zasad dostępu lub jako `UNEXPECTED_KERNEL_MODE_TRAP` dane wykrywania. W takich przypadkach program jest nadal zakończony, ale nie musi być szybko.

`__fastfail`jest dostępny tylko jako wewnętrzny.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__fastfail`|x86, x64, ARM, ARM64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
