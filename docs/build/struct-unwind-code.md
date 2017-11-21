---
title: Struktura UNWIND_CODE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 40b47b2b04d73c30e6c876199dbd98483490f4f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="struct-unwindcode"></a>struktura UNWIND_CODE
Tablica kodu unwind jest używana do rejestrowania sekwencja operacji w prologu, które mają wpływ na nieulotnej rejestrów i źródło. Każdy element kodu ma następujący format:  
  
|||  
|-|-|  
|UBYTE|Przesunięcie w prologu|  
|UBYTE: 4|Kod operacji unwind|  
|UBYTE: 4|Informacje o operacji|  
  
 Tablica jest sortowana według malejącej przesunięcie w prologu.  
  
 **Przesunięcie w prologu**  
 Przesunięcie od początku prologu końca instrukcji, które wykonuje tę operację, a także 1 (to znaczy Przesunięcie początku następną instrukcję).  
  
 **Kod operacji unwind**  
 Uwaga: Niektóre kody operacji wymaga niepodpisane przesunięcie wartości w ramce stosu lokalnego. Jest to przesunięcie od początku alokacji stosu stałego (najniższym adresem). Jeśli pole zarejestrować ramki w UNWIND_INFO wynosi zero, to przesunięcie jest źródło. Jeśli pole zarejestrować ramki jest różna od zera, to przesunięcie, z którym źródło znajdował się, gdy FP reg zostało ustanowione. To jest równe reg FP minus przesunięcie reg FP (16 * skalowana ramki zarejestrować przesunięcie w UNWIND_INFO). Jeśli używana jest reg FP, następnie dowolny kod unwind biorąc przesunięcia może być używana tylko po ustanowieniu FP reg w prologu.  
  
 Dla wszystkich opcodes z wyjątkiem UWOP_SAVE_XMM128 i UWOP_SAVE_XMM128_FAR przesunięcie będą zawsze miały wielokrotnością liczby 8, ponieważ wszystkie wartości stosu istotnych znajdują się na granice 8 bajtów (stosu sam jest zawsze 16-bajtowych wyrównane). Kodów operacji, które przyjmują krótkich przesunięcie (mniej niż 512 KB) końcowych USHORT w węzłach tego kodu przechowuje przesunięcie podzielić przez 8. Dla kody operacji, które przyjmują długi przesunięcie (512 KB < = przesunięcie < 4GB), końcowego dwa węzły USHORT dla tego kodu utrzymywanie przesunięcie (w formacie little endian).  
  
 Dla opcodes UWOP_SAVE_XMM128 i UWOP_SAVE_XMM128_FAR przesunięcie będą zawsze miały wielokrotnością 16, ponieważ wszystkie operacje XMM 128-bitowego musi wystąpić 16-bajtowych wyrównany pamięci. W związku z tym współczynnik skali, 16 jest używana do UWOP_SAVE_XMM128 umożliwiający przesunięcia mniej niż 1M.  
  
 Kod operacji unwind jest jednym z następujących czynności:  
  
 UWOP_PUSH_NONVOL (0) 1 węzła  
  
 Wypchnij rejestru nieulotnej liczba całkowita, dekrementacja źródło przez 8. Informacje o operacji jest numer rejestru. Zauważ, że, ze względu na ograniczenia dotyczące epilogs, kody unwind UWOP_PUSH_NONVOL musi występować jako pierwszy w prologu i odpowiednio ostatni w tablicy unwind kodu. Względne uporządkowanie ma zastosowanie do wszystkich innych kodów unwind z wyjątkiem UWOP_PUSH_MACHFRAME.  
  
 UWOP_ALLOC_LARGE (1) węzły 2 lub 3  
  
 Przydziel obszar dużych na stosie. Istnieją dwie formy. Jeśli informacje o operacji jest równa 0, a następnie rozmiar alokacji podzielona przez 8 jest rejestrowany w gnieździe dalej stosowanie alokacji maksymalnie 512 KB - 8. Jeśli informacje o operacji jest równa 1, a następnie nieskalowanego rozmiar alokacji jest rejestrowana w kolejnych dwóch miejsc w formacie little endian, dzięki czemu alokacje do 4GB - 8.  
  
 UWOP_ALLOC_SMALL (2) 1 węzła  
  
 Przydziel obszar małe na stosie. Rozmiar alokacji to pola informacje o operacji * 8 + 8, umożliwiając alokacji od 8 do 128.  
  
 Kod unwind alokacji stosu zawsze należy używać najmniejszej kodowanie możliwe:  
  
|||  
|-|-|  
|**Rozmiar alokacji**|**Kodzie operacji unwind**|  
|8 – 128 bajtów|UWOP_ALLOC_SMALL|  
|136 do 512-8 KB|UWOP_ALLOC_LARGE, informacje o operacji = 0|  
|512 KB do 4G - 8 bajtów|UWOP_ALLOC_LARGE, informacje o operacji = 1|  
  
 (3) UWOP_SET_FPREG węzła 1  
  
 Rejestr wskaźnika ramki należy ustanowić przez ustawienie rejestru do niektórych przesunięcie bieżące źródło. Przesunięcie jest równa zarejestrować ramki (skalowanie) pole przesunięcia UNWIND_INFO * 16, dzięki czemu przesunięcia od 0 do 240. Przesunięcie pozwala ustanawianie wskaźnika ramki, wskazujące środka alokacji stosu stały, ułatwienia gęstość kodu, zezwalając więcej uzyskuje dostęp do używania formularzy krótkie instrukcje. Należy pamiętać, że w polu informacje o operacji jest zarezerwowany i nie powinna być używana.  
  
 UWOP_SAVE_NONVOL (4) węzły 2  
  
 Zapisz rejestru nieulotnej całkowitą na stosie za pomocą MOV zamiast WYPYCHANIA. To jest używany głównie dla shrink-wrapping, której jest zapisywany nieulotnej rejestru do stosu w pozycji, która była przydzielona wcześniej. Informacje o operacji jest numer rejestru. Przesunięcie skalowana przez 8 stosu jest rejestrowany w następnej operacji unwind gniazda kod operacji, zgodnie z opisem w powyższej Uwaga.  
  
 UWOP_SAVE_NONVOL_FAR (5) węzły 3  
  
 Zapisz rejestru nieulotnej całkowitą na stosie z przesunięciem długie, użycie MOV zamiast WYPYCHANIA. To jest używany głównie dla shrink-wrapping, której jest zapisywany nieulotnej rejestru do stosu w pozycji, która była przydzielona wcześniej. Informacje o operacji jest numer rejestru. Przesunięcie nieskalowanego stosu jest rejestrowany w ciągu następnych dwóch miejsc kod operacji unwind zgodnie z opisem w powyższej Uwaga.  
  
 UWOP_SAVE_XMM128 (8) węzły 2  
  
 Zapisz wszystkie 128 bitów nieulotnej, zarejestruj XMM na stosie. Informacje o operacji jest numer rejestru. Przesunięcie stosu skalowany przy 16 jest rejestrowana w gnieździe dalej.  
  
 UWOP_SAVE_XMM128_FAR (9) węzły 3  
  
 Zapisz wszystkie 128 bitów nieulotnej, zarejestruj XMM na stosie z przesunięciem długo. Informacje o operacji jest numer rejestru. Przesunięcie nieskalowanego stosu jest rejestrowana w kolejnych dwóch miejsc.  
  
 UWOP_PUSH_MACHFRAME (10) 1 węzła  
  
 Wypchnij ramki maszyny.  Służy do rejestrowania przerwań sprzętowych lub wyjątek. Istnieją dwie formy. Jeśli informacje o operacji równa 0, następujące ma został naciśnięty na stosie:  
  
|||  
|-|-|  
|ŹRÓDŁO + 32|SS|  
|ŹRÓDŁO + 24|Stary źródło|  
|ŹRÓDŁO + 16|EFLAGS|  
|ŹRÓDŁO + 8|CS|  
|ŹRÓDŁO|PROTOKÓŁ RIP|  
  
 Jeśli informacje o operacji jest równa 1, a następnie następujące ma zamiast tego wypychana:  
  
|||  
|-|-|  
|ŹRÓDŁO + 40|SS|  
|ŹRÓDŁO + 32|Stary źródło|  
|ŹRÓDŁO + 24|EFLAGS|  
|ŹRÓDŁO + 16|CS|  
|ŹRÓDŁO + 8|PROTOKÓŁ RIP|  
|ŹRÓDŁO|Kod błędu:|  
  
 Ten kod unwind zawsze będą wyświetlane w prologu fikcyjny, co faktycznie nigdy nie jest wykonywana, ale zamiast tego jest umieszczany przed punkt wejścia rzeczywistych procedury przerwań i istnieje tylko w celu zapewnienia miejsca do symulowania wypychania ramki maszyny. UWOP_PUSH_MACHFRAME rejestruje tego symulacji, co oznacza, że maszynie koncepcyjnie wykonaniu następujących czynności:  
  
 POP RIP Adres zwrotny z góry stosu w *Temp*  
  
 Wypychanie SS  
  
 Źródło starego wypychania  
  
 Wypychanie EFLAGS  
  
 CS wypychania  
  
 Wypychanie *Temp*  
  
 Wypychanie kodu błędu (Jeśli informacje o op jest równa 1)  
  
 Symulowane UWOP_PUSH_MACHFRAME operacji zmniejsza źródło przez 40 (informacje o op równe 0) lub 48 (op informacji jest równa 1).  
  
 **Informacje o operacji**  
 Znaczenie te 4 bity zależy od kodu operacji. Aby zakodować rejestru ogólnego przeznaczenia (liczba całkowita), służy następującego mapowania:  
  
|||  
|-|-|  
|0|RAX|  
|1|RCX|  
|2|RDX|  
|3|RBX|  
|4|ŹRÓDŁO|  
|5|RBP|  
|6|RSI|  
|7|RDI|  
|8 – 15|R8 do R15|  
  
## <a name="see-also"></a>Zobacz też  
 [Dane operacji unwind dla obsługi wyjątków, obsługa debugera](../build/unwind-data-for-exception-handling-debugger-support.md)