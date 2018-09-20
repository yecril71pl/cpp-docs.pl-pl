---
title: __fastfail | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6699585db899fc2601ac4945c4b2c57edbf5f309
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379180"
---
# <a name="fastfail"></a>__fastfail

**Microsoft Specific**

Natychmiast kończy proces wywołujący osiąga obciążenie.

## <a name="syntax"></a>Składnia

```
void __fastfail(unsigned int code);
```

#### <a name="parameters"></a>Parametry

*Kod*<br/>
[in] A `FAST_FAIL_<description>` symboliczna stała z pliku winnt.h lub wdm.h, która oznacza powód zakończenia procesu.

## <a name="return-value"></a>Wartość zwracana

`__fastfail` Wewnętrzne nie zwraca.

## <a name="remarks"></a>Uwagi

`__fastfail` Wewnętrzne udostępnia mechanizm *szybkie niepowodzenie* żądania — potencjalnie uszkodzony procesu sposób zakończenia procesu natychmiastowego żądania. Błędy krytyczne, które może spowodować uszkodzenie stan programu i stos poza odzyskiwania nie może być obsługiwane przez obsługi funkcji regularnych wyjątków. Użyj `__fastfail` aby zakończyć proces, korzystając z minimalne obciążenie.

Wewnętrznie `__fastfail` jest implementowany przy użyciu kilku mechanizmów architektury:

|Architektura|Instrukcja|Lokalizacja kodu argumentu|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|ecx|
|X64|int 0x29|rcx|
|ARM|OpCode 0xDEFB|r0|

Żądanie szybkiego niepowodzenie jest niezależna i zazwyczaj wymaga zaledwie dwóch instrukcji do wykonania. Po awarii szybkie żądanie zostało wykonane przez jądro następnie podejmuje odpowiednie działanie. W kodzie w trybie użytkownika występują żadne zależności pamięci poza wskaźnika instrukcji, sam, gdy zostanie wywołane zdarzenie szybkie kończyć się niepowodzeniem. Maksymalizuje jej niezawodności, nawet jeśli pamięci poważne uszkodzenie.

`code` Argument — jeden z `FAST_FAIL_<description>` należy stosować stałe symboliczne z pliku winnt.h lub wdm.h—describes typ warunku błędu i jest włączony do raportów o awarii w sposób specyficznymi dla środowiska.

Żądania szybkie awarii trybu użytkownika są wyświetlane jako drugiej szansy nie można kontynuować wyjątek z kod wyjątku 0xC0000409 i parametrów co najmniej jeden wyjątek. Pierwszy parametr wyjątku ma `code` wartość. Ten kod wyjątku wskazuje raportowania błędów Windows (WER) i debugowania infrastruktury, że proces jest uszkodzony, a minimalny działania w trakcie powinny zostać podjęte w odpowiedzi na błąd. Żądania szybkie kończyć się niepowodzeniem w trybie jądra są implementowane przy użyciu kodu bugcheck dedykowanych, `KERNEL_SECURITY_CHECK_FAILURE` (0x139). W obu przypadkach brak obsługi wyjątków są wywoływane, ponieważ program powinien być w stanie uszkodzenia. Jeśli jest obecny debuger, otrzymuje możliwość sprawdzenia stanu programu przed zakończeniem działania.

Obsługa mechanizmu natywnej awarii szybkie rozpoczął się w systemie Windows 8. Systemy operacyjne Windows, które nie obsługują natywnie instrukcji szybkie kończyć się niepowodzeniem zazwyczaj traktują szybkie Niepowodzenie żądania jako naruszenie zasad dostępu, lub `UNEXPECTED_KERNEL_MODE_TRAP` wyniki operacji. W takich przypadkach program jest nadal zakończone, ale nie musi tak szybko.

`__fastfail` jest dostępna tylko wewnętrznie.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__fastfail`|x86 x 64, ARM|

**Plik nagłówkowy** \<intrin.h >

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)