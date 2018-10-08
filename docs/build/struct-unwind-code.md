---
title: Struktura UNWIND_CODE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5bccddd2ddd5c0f9dfbc828a7da3a66fa13339d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861723"
---
# <a name="struct-unwindcode"></a>struktura UNWIND_CODE

Tablica kodu odwijania jest używana do rejestrowania sekwencji operacji w prologu, na które wpływają na nieulotnej rejestrów i RSP. Każdy element kodu ma następujący format:

|||
|-|-|
|UBYTE|Przesunięcie w prologu|
|UBYTE: 4|Kod operacji unwind|
|UBYTE: 4|Informacje o operacji|

Tablica jest posortowana według malejącej przesunięcie w prologu.

## <a name="offset-in-prolog"></a>Przesunięcie w prologu

Przesunięcie od początku prologu końca instrukcji, która wykonuje tę operację powiększoną o 1 (czyli Przesunięcie początku następnej instrukcji).

## <a name="unwind-operation-code"></a>Kod operacji unwind

Uwaga: Niektóre kody operacji wymagają niepodpisane przesunięcie wartości w ramce stosu lokalnego. Jest to przesunięcie od początku alokacji stosu stałych (najniższy adres). Jeśli pole zarejestrować ramki UNWIND_INFO wynosi zero, to przesunięcie pochodzi z RSP. Jeśli pole zarejestrować ramki jest różna od zera, to przesunięcie, z którym RSP znajdował się w przypadku FP reg zostało ustanowione. To jest równe reg FP minus przesunięcie reg FP (16 \* skalowanych ramki zarejestrować przesunięcie w UNWIND_INFO). Jeśli reg FP jest używany, następnie jakiegokolwiek kodu unwind biorąc przesunięcia może być używana tylko po nawiązaniu FP reg w prologu.

Dla wszystkich rozkazów z wyjątkiem `UWOP_SAVE_XMM128` i `UWOP_SAVE_XMM128_FAR`, przesunięcie będzie zawsze wielokrotnością liczby 8, ponieważ wszystkie stosu interesujących wartości są przechowywane w granicach 8 bajtów (stosu, sam jest zawsze 16-bajtowy wyrównane). Kody operacji, które przyjmują krótki przesunięcie (mniej niż 512K) końcowy USHORT w węzłach dla tego kodu przechowuje przesunięcie podzielić przez 8. Dla kodów operacji, które przyjmują długie przesunięcie (512 KB < = przesunięcie < 4GB), końcowy dwa węzły USHORT ten kod przechowywania przesunięcie (w formacie little-endian).

Aby uzyskać rozkazów `UWOP_SAVE_XMM128` i `UWOP_SAVE_XMM128_FAR`, przesunięcie będzie zawsze wielokrotnością liczby 16, ponieważ wszystkie operacje XMM 128-bitowego musi przypadać na 16-bajtowy wyrównanej pamięci. W związku z tym, współczynnik skali 16 służy do `UWOP_SAVE_XMM128`, pozwalające przesunięcia mniej niż 1 mln.

Kod operacji odwijania jest jedną z następujących czynności:

`UWOP_PUSH_NONVOL` (0) 1 węzeł

Wypchnij nieulotnej całkowitoliczbowym, zmniejszanie RSP przez 8. Informacje o operacji są numer rejestru. Należy zauważyć, że ze względu na ograniczenia dotyczące epilogs, `UWOP_PUSH_NONVOL` kodów unwind musi występować jako pierwszy w prologu i odpowiednio ostatni w tablicy kodu unwind. Względne uporządkowanie ma zastosowanie do wszystkich innych kodów odwijania, z wyjątkiem `UWOP_PUSH_MACHFRAME`.

`UWOP_ALLOC_LARGE` (1) 2 lub 3 węzłów

Przydziel obszar o dużych rozmiarach na stosie. Istnieją dwie formy. Jeśli informacje o operacji jest równa 0, a następnie rozmiar alokacji podzielona przez 8 są rejestrowane w następnym gniazda, umożliwiając alokacji maksymalnie 512 K - 8. Jeśli informacje o operacji jest równa 1, a następnie nieskalowanego rozmiar alokacji jest rejestrowana w następnych dwóch miejsc w formacie little-endian, dzięki czemu alokacji do 4GB - 8.

`UWOP_ALLOC_SMALL` (2) 1 węzeł

Przydziel obszar małe na stosie. Rozmiar alokacji to pola informacje o operacji \* 8 + 8, dzięki czemu alokacje od 8 do 128.

Kod unwind alokacji stosu zawsze należy używać w możliwie najkrótszym możliwe kodowanie:

|**Rozmiar alokacji**|**Kodzie operacji unwind**|
|-|-|
|8 do 128 bajtów|`UWOP_ALLOC_SMALL`|
|136 do 512-8 kilobajtów|`UWOP_ALLOC_LARGE`, informacje o operacji = 0|
|512 KB do 4G - 8 bajtów|`UWOP_ALLOC_LARGE`, informacje o operacji = 1|

`UWOP_SET_FPREG` (3) 1 węzeł

Przez ustawienie rejestru na niektórych przesunięcie bieżącego RSP, należy ustanowić rejestr wskaźnika ramki. Przesunięcie jest równa zarejestrować ramki (skalowanych) pole przesunięcia UNWIND_INFO \* 16, dzięki czemu przesunięcia z zakresu od 0 do 240. Zezwala na użycie przesunięcie, ustanawiania wskaźnik ramki, który wskazuje na środku alokacji stosu stały, pomagając gęstość kodu, umożliwiając więcej uzyskuje dostęp do używania formularzy krótkich instrukcji. Należy zauważyć, że pola informacje o operacji jest zarezerwowany i nie powinna być używana.

`UWOP_SAVE_NONVOL` (4) 2 węzły

Zapisz nieulotnej całkowitoliczbowym na stosie przy użyciu MOV zamiast powiadomienie WYPYCHANE. To jest używany głównie dla shrink-wrapping, gdzie nieulotnej rejestru są zapisywane na stos w stanie, która była przydzielona wcześniej. Informacje o operacji są numer rejestru. Przesunięcie skalowany przy 8 stosu są zapisywane w następnej operacji unwind miejsca kod operacji zgodnie z opisem w powyższej Uwaga.

`UWOP_SAVE_NONVOL_FAR` (5) 3 węzły

Zapisz nieulotnej całkowitoliczbowym na stosie z przesunięciem długie, użycie MOV zamiast powiadomienie WYPYCHANE. To jest używany głównie dla shrink-wrapping, gdzie nieulotnej rejestru są zapisywane na stos w stanie, która była przydzielona wcześniej. Informacje o operacji są numer rejestru. Przesunięcie nieskalowanego stosu jest rejestrowana w ciągu następnych dwóch miejsc kod operacji unwind zgodnie z opisem w powyższej Uwaga.

`UWOP_SAVE_XMM128` (8) węzłów 2

Zapisz wszystkie 128 bitów nieulotnej, zarejestruj XMM na stosie. Informacje o operacji są numer rejestru. Przesunięcie stosu skalowany przy 16 są rejestrowane w gnieździe dalej.

`UWOP_SAVE_XMM128_FAR` (9) 3 węzły

Zapisz wszystkie 128 bitów nieulotnej, zarejestruj XMM na stosie z przesunięciem długie. Informacje o operacji są numer rejestru. Przesunięcie nieskalowanego stosu jest rejestrowana w dwóch następnych miejsc.

`UWOP_PUSH_MACHFRAME` (10) 1 węzeł

Wypchnij ramki maszyny.  Służy do rejestrowania efekt sprzętu, przerwania lub wyjątku. Istnieją dwie formy. Jeśli informacje o operacji jest równa 0, że zostało wypchnięte na stosie:

|||
|-|-|
|RSP + 32|SS|
|RSP + 24|Stary RSP|
|RSP + 16|EFLAGS|
|RSP + 8|CS|
|RSP|PROTOKÓŁ RIP|

Jeśli o operacji jest równa 1, a następnie wypchnięto zamiast tego następujące:

|||
|-|-|
|RSP + 40|SS|
|RSP + 32|Stary RSP|
|RSP + 24|EFLAGS|
|RSP + 16|CS|
|RSP + 8|PROTOKÓŁ RIP|
|RSP|Kod błędu:|

Ten kod unwind zawsze pojawi się w prologu fikcyjnego z rolą, która faktycznie nigdy nie jest wykonywane, ale zamiast tego jest umieszczany przed punktu wejścia rzeczywistych procedury przerwań i istnieje tylko po to, aby zapewnić miejsce, aby zasymulować wypychania ramki maszyny. `UWOP_PUSH_MACHFRAME` rejestruje symulacji i wskazuje, że komputer ma pod względem koncepcyjnym wykonać następujące czynności:

1. Adres zwrotny RIP z góry stosu do POP *Temp*

1. Wypychanie SS

1. Stary RSP wypychania

1. Wypychanie EFLAGS

1. CS wypychania

1. Wypychanie *Temp*

1. Wypychanie kodu błędu (Jeśli informacje o operacji jest równa 1)

Symulowane `UWOP_PUSH_MACHFRAME` operacji zmniejsza RSP przez 40 (op informacji jest równa 0) lub 48 (op informacji jest równa 1).

## <a name="operation-info"></a>Informacje o operacji

Znaczenie tych 4 bitów zależy od kodu operacji. Do zakodowania rejestru ogólnego przeznaczenia (liczba całkowita), służy następujące mapowania:

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8-15|R8 do R15|

## <a name="see-also"></a>Zobacz też

[Dane operacji Unwind dla obsługi wyjątków, obsługa debugera](../build/unwind-data-for-exception-handling-debugger-support.md)
