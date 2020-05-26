---
title: Obsługa wyjątków ARM64
description: Opisuje konwencje obsługi wyjątków i dane używane przez system Windows w systemie ARM64.
ms.date: 11/19/2018
ms.openlocfilehash: abc77aa683e73a2740c71ffbd7ddead07f91ff7d
ms.sourcegitcommit: 5bb421fdf61d290cac93a03e16a6a80959accf6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83854830"
---
# <a name="arm64-exception-handling"></a>Obsługa wyjątków ARM64

System Windows on ARM64 używa tego samego mechanizmu obsługi wyjątków strukturalnych dla asynchronicznie generowanych przez sprzęt wyjątków i synchronicznych wyjątków generowanych przez oprogramowanie. Obsługa wyjątków specyficznych dla języka jest tworzona w oparciu o obsługę wyjątków strukturalnych systemu Windows przy użyciu funkcji pomocnika języka. W tym dokumencie opisano obsługę wyjątków w systemie Windows na ARM64 oraz pomocników języka używanych przez kod generowany przez asembler Microsoft ARM i kompilator MSVC.

## <a name="goals-and-motivation"></a>Cele i motywacja

Wyjątkiem są konwencje danych dotyczące odwinięcia wyjątku, a ten opis ma na celu:

1. Podaj wystarczającą ilość opisu, aby zezwolić na odwracanie bez kodu w każdym przypadku.

   - Analizowanie kodu wymaga, aby kod był stronicowany. Zapobiega to występowaniu w niektórych sytuacjach, gdy jest to przydatne (śledzenie, próbkowanie, debugowanie).

   - Analizowanie kodu jest złożone; kompilator należy zachować ostrożność, aby generować tylko instrukcje, które może zdekodować niewietrzer.

   - Jeśli nie można w pełni opisać odwinięcia przy użyciu kodów operacji unwind, wówczas w niektórych przypadkach musi on wrócić do dekodowania instrukcji. Powoduje to zwiększenie ogólnej złożoności i zaleca się uniknięcie tego.

1. Obsługa rozwinięcia w funkcjach MID i epilogu.

   - Odmowa jest używana w systemie Windows na potrzeby więcej niż obsługi wyjątków. Niezwykle ważne jest, aby kod mógł zostać rozwinięcia dokładnie nawet wtedy, gdy w środku sekwencji kodu prolog lub epilogu.

1. Zapoznaj się z minimalną ilością miejsca.

   - Kody operacji unwind nie mogą być zagregowane w celu znacznego zwiększenia rozmiaru binarnego.

   - Ze względu na to, że kody operacji unwind mogą być blokowane w pamięci, niewielki wpływ zapewnia minimalne obciążenie dla każdego załadowanego pliku binarnego.

## <a name="assumptions"></a>Założenia

Te założenia są wprowadzane w opisie obsługi wyjątków:

1. Zarejestrowanie i epilogs w celu zaplanowania dublowania. Korzystając z zalet tej typowej cechy, rozmiar metadanych koniecznych do opisania odwinięcia może być znacznie zmniejszony. W treści funkcji nie ma znaczenia, czy operacje prologu są cofnięte lub operacje epilogu są wykonywane w sposób do przodu. Oba powinny generować identyczne wyniki.

1. Funkcje w całości są stosunkowo małe. Kilka optymalizacji dla miejsca polega na tym fakcie, aby osiągnąć najbardziej wydajne pakowanie danych.

1. Brak kodu warunkowego w epilogs.

1. Rejestr dedykowanych wskaźników ramki: Jeśli Sp zostanie zapisany w innym rejestrze (x29) w prologu, ten rejestr pozostanie nienaruszony w całej funkcji. Oznacza to, że oryginalny Sp można odzyskać w dowolnym momencie.

1. Jeśli SP nie zostanie zapisany w innym rejestrze, wszystkie manipulowanie wskaźnikiem stosu odbywa się wyłącznie w prologu i epilogu.

1. Układ ramki stosu jest zorganizowany zgodnie z opisem w następnej sekcji.

## <a name="arm64-stack-frame-layout"></a>Układ ramki stosu ARM64

![Układ ramki stosu](media/arm64-exception-handling-stack-frame.png "Układ ramki stosu")

W przypadku funkcji łańcucha ramek FP i LR można zapisać w dowolnym miejscu w obszarze zmiennej lokalnej, w zależności od kwestii optymalizacji. Celem jest maksymalizacja liczby miejsc, do których można uzyskać dostęp za pomocą jednej instrukcji na podstawie wskaźnika ramki (x29) lub wskaźnika stosu (SP). Jednak w przypadku `alloca` funkcji musi być łańcuchem, a x29 musi wskazywać na dół stosu. Aby umożliwić lepsze pokrycie w trybie par rejestracji, nielotne obszary zapisywania są umieszczane w górnej części stosu lokalnego. Poniżej przedstawiono przykłady ilustrujące kilka najbardziej wydajnych sekwencji prologu. W celu zapewnienia przejrzystości i lepszej lokalizacji pamięci podręcznej kolejność przechowywania zapisywanych rejestrów we wszystkich kanonicznych dziennikach jest w kolejności "rosnąco". `#framesz`poniżej przedstawia rozmiar całego stosu (z wyłączeniem obszaru alloca). `#localsz`i `#outsz` należy zauważyć, że rozmiar lokalnego obszaru (w tym obszar zapisu dla \< pary x29, LR>) i wyjściowy rozmiar parametru jest odpowiednio.

1. Łańcuchy, #localsz \< = 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        stp    x29,lr,[sp,#-localsz]!   // save <x29,lr> at bottom of local area
        mov    x29,sp                   // x29 points to bottom of local
        sub    sp,sp,#outsz             // (optional for #outsz != 0)
    ```

1. Łańcuchy, #localsz > 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        sub    sp,sp,#(localsz+outsz)   // allocate remaining frame
        stp    x29,lr,[sp,#outsz]       // save <x29,lr> at bottom of local area
        add    x29,sp,#outsz            // setup x29 points to bottom of local area
    ```

1. Niełańcuchowe, funkcje liścia (LR Unsaved)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]
        str    x23,[sp,#32]
        stp    d8,d9,[sp,#40]           // save FP regs (optional)
        stp    d10,d11,[sp,#56]
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Wszystkie elementy lokalne są dostępne w oparciu o SP. \<x29, LR> wskazuje na poprzednią ramkę. Dla ramki size \< = 512, "Sub SP,..." można je zoptymalizować w przypadku przeniesienia zapisanego obszaru REGS na dół stosu. Minusem polega na tym, że nie jest on spójny z innymi układami powyżej, i zapisano REGS wziąć część zakresu dla trybu parowania z funkcją para-regs i indeksem wstępnym i indeksowanym.

1. Niełańcuchowe funkcje, które nie są typu liść (LR są zapisywane w obszarze zapisanym int)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Lub, z parzystą liczbą Zapisano rejestry int,

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Tylko x19 zapisane:

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \*Alokacja obszaru zapisu reg nie jest przedstawiona w STP, ponieważ wstępnie indeksowana wartość STP reg-LR nie może być reprezentowana przy użyciu kodów unwind.

   Wszystkie elementy lokalne są dostępne w oparciu o SP. \<x29> wskazuje na poprzednią ramkę.

1. Łańcuchy, #framesz \< = 512, #outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   W porównaniu do pierwszego przykładu prologu powyżej warto skorzystać z tej możliwości, że wszystkie instrukcje dotyczące zapisu rejestru są gotowe do wykonania po tylko jednej instrukcji alokacji stosu. Oznacza to, że nie istnieje żadne przeciwdziałanie na poziomie SP, które uniemożliwia równoległość poziomu instrukcji.

1. Łańcuchy, rozmiar ramki > 512 (opcjonalnie dla funkcji bez alokacji)

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   W celu optymalizacji x29 można umieścić w dowolnym miejscu w obszarze lokalnym, aby zapewnić lepszy zakres dla "reg-para" i tryb adresowania przesunięcia poprzedzającego/post-Indexed. Elementy lokalne poniżej wskaźników ramki są dostępne na podstawie SP.

1. Łańcuchy, rozmiar ramki > 4K, z lub bez alloca (),

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        mov    x15,#(framesz/16)
        bl     __chkstk
        sub    sp,sp,x15,lsl#4              // allocate remaining frame
                                            // end of prolog
        ...
        sub    sp,sp,#alloca                // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,x29                       // sp points to top of local area
        ldp    d10,d11,[sp,#64]
        ...
        ldp    x29,lr,[sp],#80              // post-indexed, reload <x29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>Informacje dotyczące obsługi wyjątków ARM64

### <a name="pdata-records"></a>rekordy. pdata

Rekordy. pdata to uporządkowana Tablica elementów o stałej długości, która opisuje każdą funkcję manipulowania stosem w pliku binarnym środowiska PE. Fraza "manipulowanie stosem" jest istotna: funkcje liścia, które nie wymagają żadnego magazynu lokalnego i nie muszą zapisywać/przywracać rejestrów nietrwałych, nie wymagają rekordu. pdata. Aby zaoszczędzić miejsce, należy jawnie pominąć te rekordy. Odwinięcie z jednej z tych funkcji może uzyskać adres zwrotny bezpośrednio z LR, aby przenieść się do obiektu wywołującego.

Każdy rekord. pData dla ARM64 ma długość 8 bajtów. Ogólny format każdego rekordu umieszcza 32-bitowy adres RVA funkcji uruchamianej w pierwszym wyrazie, po którym następuje drugi wyraz, który zawiera wskaźnik do xdata bloku o zmiennej długości lub spakowanym słowie opisującym nieprzewijanie sekwencji funkcji kanonicznej.

![Układ rekordu. pdata](media/arm64-exception-handling-pdata-record.png "Układ rekordu. pdata")

Pola są następujące:

- **Początkowy adres RVA funkcji** to 32-bitowy adres RVA początku funkcji.

- **Flaga** to pole 2-bitowe, które wskazuje, jak interpretować pozostałe 30 bitów drugiego. pdata. Jeśli **Flaga** ma wartość 0, pozostałe bity tworzą **adres RVA informacji o wyjątku** (z dwoma najniższymi bitami niejawnie 0). Jeśli **Flaga** jest różna od zera, pozostałe bity tworzą **spakowaną strukturę danych unwind** .

- **Informacje o wyjątku adres RVA** jest adresem struktury informacji o wyjątku o zmiennej długości przechowywanej w sekcji. xdata. Te dane muszą być wyrównane 4-bajtowo.

- **Spakowane dane unwind** to skompresowany opis operacji wymaganych do odwinięcia z funkcji, przy założeniu, że forma kanoniczna. W takim przypadku nie jest wymagany żaden rekord. xdata.

### <a name="xdata-records"></a>rekordy. xdata

Gdy spakowany format unwindy jest niewystarczający do opisania odwinięcia funkcji, należy utworzyć rekord o zmiennej długości. xdata. Adres tego rekordu jest przechowywany w drugim słowie rekordu. pdata. Format XData jest spakowanym zestawem wyrazów o zmiennej długości:

![Układ rekordu. xdata](media/arm64-exception-handling-xdata-record.png "Układ rekordu. xdata")

Te dane są podzielone na cztery sekcje:

1. Nagłówek 1 lub 2-Word opisujący ogólny rozmiar struktury i udostępniający dane funkcji klucza. Drugi wyraz jest obecny tylko wtedy, gdy zarówno **Liczba epilogu** , jak i **słowa kodu** są ustawione na 0. Nagłówek zawiera następujące pola bitowe:

   a. **Długość funkcji** to pole 18-bitowe. Wskazuje łączną długość funkcji w bajtach podzieloną przez 4. Jeśli funkcja jest większa niż 1M, do opisania funkcji należy użyć wielu rekordów. pdata i. xdata. Aby uzyskać więcej informacji, zobacz sekcję [duże funkcje](#large-functions) .

   b. Wartość **odwrotna** to pole 2-bitowe. Opisuje on wersję pozostałej. xdata. Obecnie tylko wersja 0 jest zdefiniowana, więc wartości 1-3 nie są dozwolone.

   c. **X** to pole 1-bitowe. Wskazuje obecność (1) lub nieobecność (0) danych wyjątku.

   d. **E** to pole 1-bitowe. Wskazuje, że informacje opisujące pojedynczy epilogu są pakowane do nagłówka (1), a nie wymagają dodatkowych słów Scope w dalszej części (0).

   e. **Epilogu Count** to pole 5-bitowe, które ma dwa średnie, w zależności od stanu **E** bitowej:

      1. Jeśli **E** jest 0, określa liczbę całkowitej liczby zakresów epilogu opisanych w sekcji 2. Jeśli w funkcji istnieje więcej niż 31 zakresów, pole **słowa Code** musi mieć wartość 0, aby wskazać, że wymagane jest słowo rozszerzenia.

      2. Jeśli **E** to 1, to pole określa indeks pierwszego kodu unwindy, który opisuje ten i tylko epilogu.

   f. **Słowa kodu** to pole 5-bitowe, które określa liczbę 32-bitowych wyrazów, które muszą zawierać wszystkie kody operacji unwind w sekcji 3. Jeśli wymagane są więcej niż 31 wyrazów (to oznacza, że jeśli istnieje więcej niż 124 bajtów kodu wywinięcia), to pole musi mieć wartość 0, aby wskazać, że wymagane jest słowo rozszerzenia.

   g. **Rozszerzona liczba epilogu** i **rozszerzone słowa kodu** są odpowiednio 16-bitowymi i 8-bitowymi polami. Zapewniają one więcej miejsca do kodowania nietypowo dużej liczby epilogs lub nietypowo dużą liczbę słów kodu unwind. Słowo Extension zawierające te pola jest obecne tylko wtedy, gdy zarówno pole **Count epilogu** , jak i **słowa Code** w pierwszym nagłówku, ma wartość 0.

1. Jeśli **Liczba epilogu** nie jest równa zero, lista informacji o zakresach epilogu, spakowanych jeden do wyrazu, znajduje się po nagłówku i opcjonalnym rozszerzonym nagłówku. Są one przechowywane w kolejności rosnącego przesunięcia początkowego. Każdy zakres zawiera następujące bity:

   a. **Epilogu rozpoczęcia przesunięcia** to pole 18-bitowe, które ma przesunięcie w bajtach, podzieloną przez 4 epilogu względem początku funkcji.

   b. **Res** to pole 4-bitowe zarezerwowane do użytku w przyszłości. Wartość musi być równa 0.

   c. **Indeks początkowy epilogu** jest polem 10-bitowym (2 więcej bitów niż **rozszerzone słowa kodu**). Wskazuje on indeks bajtów pierwszego kodu unwind, który opisuje ten epilogu.

1. Po liście zakresów epilogu jest tablicą bajtów, które zawierają kody wyłączania, opisane szczegółowo w dalszej części. Ta tablica jest dopełniana na końcu do najbliższej pełnej granicy słowa. Kody operacji unwind są zapisywane w tej tablicy. Zaczynają się one od najbliższej treści funkcji i są przesuwane do krawędzi funkcji. Bajty dla każdego kodu unwindy są przechowywane w kolejności big-endian, aby można je było pobrać bezpośrednio, rozpoczynając od najbardziej znaczącego bajtu, który identyfikuje operację i długość reszty kodu.

1. Na koniec po bajtach kodu unwind, jeśli bit **X** w nagłówku został ustawiony na 1, nastąpi informacje dotyczące obsługi wyjątków. Składa się z jednego adresu **RVA procedury obsługi wyjątku** , który udostępnia adres samej procedury obsługi wyjątków. Następuje to bezpośrednio przez zmienną długość danych wymaganą przez program obsługi wyjątków.

Rekord. xdata został zaprojektowany tak, aby można było pobrać pierwsze 8 bajtów i użyć ich do obliczenia pełnego rozmiaru rekordu, pomniejszonej o długość danych wyjątków o zmiennej wielkości poniżej. Poniższy fragment kodu oblicza rozmiar rekordu:

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 27) != 0) {
        Size = 4;
        EpilogScopes = (Xdata[0] >> 22) & 0x1f;
        UnwindWords = (Xdata[0] >> 27) & 0x0f;
    } else {
        Size = 8;
        EpilogScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    Size += 4 * EpilogScopes;
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;        // exception handler RVA
    }
    return Size;
}
```

Chociaż Prolog i każdy epilogu ma swój własny indeks w kodach unwind, tabela jest udostępniana między nimi. Jest to w pełni możliwe (i nierzadko występujące), które mogą współdzielić te same kody. (Aby zapoznać się z przykładem, zobacz przykład 2 w sekcji [przykłady](#examples) ). Autorzy kompilatora powinni zoptymalizować w tym przypadku, w szczególności, ponieważ największy indeks, który może być określony, to 255, który ogranicza łączną liczbę kodów operacji unwind dla określonej funkcji.

### <a name="unwind-codes"></a>Kody operacji unwind

Tablica kodów operacji unwind jest pulą sekwencji, które opisują dokładnie sposób cofania efektów prologu, przechowywane w tym samym porządku, których operacje muszą zostać cofnięte. Kody operacji unwind można traktować jako mały zestaw instrukcji zakodowany jako ciąg bajtów. Po zakończeniu wykonywania, adres zwrotny do wywołania funkcji znajduje się w rejestrze LR. Wszystkie nietrwałe rejestry są przywracane do ich wartości w momencie wywołania funkcji.

Jeśli wyjątki były gwarantowane tylko w obrębie treści funkcji i nigdy w prologu lub jakimkolwiek epilogu, konieczne będzie tylko pojedyncze sekwencje. Jednak model unwindy dla systemu Windows wymaga, aby kod mógł zostać nieprzeprowadzony z poziomu częściowo wykonanego prologu lub epilogu. Aby spełnić to wymaganie, kody operacji unwind zostały starannie zaprojektowane, aby jednoznacznie mapować 1:1 do każdego odpowiedniego kodu operacji w prologu i epilogu. Ten projekt ma kilka implikacji:

1. Zliczając liczbę kodów operacji unwind, można obliczyć długość prologu i epilogu.

1. Zliczając liczbę instrukcji poza początkiem zakresu epilogu, można pominąć równoważną liczbę kodów unwind. Następnie możemy wykonać pozostałą część sekwencji, aby zakończyć częściowe wykonywanie operacji unwind wykonanej przez epilogu.

1. Zliczając liczbę instrukcji przed końcem prologu, można pominąć równoważną liczbę kodów unwind. Następnie możemy wykonać resztę sekwencji, aby cofnąć tylko te części prologu, które zakończyły wykonywanie.

Kody operacji unwind są kodowane zgodnie z poniższą tabelą. Wszystkie kody operacji unwind są pojedynczym/podwójnym bajtem, z wyjątkiem tego, który alokuje duży stos. Całkowicie ma 21 kod operacji unwind. Każdy kod operacji unwind mapuje dokładnie jedną instrukcję w prologu/epilogu, aby umożliwić odwinięcie częściowo wykonanych dzienników i epilogs.

|Kod unwind|Bity i interpretacja|
|-|-|
|`alloc_s`|000XXXXX: Przydziel mały stos z rozmiarem \< 512 (2 ^ 5 * 16).|
|`save_r19r20_x`|    001zzzzz: Zapisz \< parę x19, x20> w `[sp-#Z*8]!` , wstępnie indeksowanym przesunięciu >=-248 |
|`save_fplr`|        01zzzzzz: Save \< x29, lr> par w `[sp+#Z*8]` , offset \< = 504. |
|`save_fplr_x`|        10zzzzzz: Zapisz \< parę x29, lr> w `[sp-(#Z+1)*8]!` , wstępnie indeksowanym przesunięciu >=-512 |
|`alloc_m`|        11000xxx'xxxxxxxx: Przydziel duży stos o rozmiarze \< 16 KB (2 ^ 11 * 16). |
|`save_regp`|        110010xx'xxzzzzzz: Zapisz parę x (19 + #X) w `[sp+#Z*8]` , offset \< = 504 |
|`save_regp_x`|        110011xx'xxzzzzzz: Zapisz parę x (19 + #X) w `[sp-(#Z+1)*8]!` , wstępnie indeksowanym przesunięciu >=-512 |
|`save_reg`|        110100xx'xxzzzzzz: Zapisz reg x (19 + #X) o `[sp+#Z*8]` , offset \< = 504 |
|`save_reg_x`|        1101010x'xxxzzzzz: Zapisz reg x (19 + #X) w `[sp-(#Z+1)*8]!` , wstępnie indeksowanym przesunięciu >=-256 |
|`save_lrpair`|         1101011x'xxzzzzzz: Zapisz parę \< x (19 + 2 * #X), lr> o `[sp+#Z*8]` , offset \< = 504 |
|`save_fregp`|        1101100x'xxzzzzzz: Zapisz parę d (8 + #X) o `[sp+#Z*8]` , offset \< = 504 |
|`save_fregp_x`|        1101101x'xxzzzzzz: Zapisz parę d (8 + #X) w `[sp-(#Z+1)*8]!` , wstępnie indeksowanym przesunięciu >=-512 |
|`save_freg`|        1101110x'xxzzzzzz: Zapisz reg d (8 + #X) o `[sp+#Z*8]` , offset \< = 504 |
|`save_freg_x`|        11011110 ' xxxzzzzz: Zapisz reg d (8 + #X) o `[sp-(#Z+1)*8]!` , wstępnie indeksowanym przesunięciu >=-256 |
|`alloc_l`|         11100000 "xxxxxxxx'xxxxxxxx'xxxxxxxx: Przydziel duży stos o rozmiarze \< 256M (2 ^ 24 * 16) |
|`set_fp`|        11100001: Skonfiguruj x29: w:`mov x29,sp` |
|`add_fp`|        11100010 ' XXXXXXXX: Skonfiguruj x29 przy użyciu:`add x29,sp,#x*8` |
|`nop`|            11100011: nie jest wymagana żadna operacja operacji unwind. |
|`end`|            11100100: koniec kodu unwind. Oznacza RET w epilogu. |
|`end_c`|        11100101: koniec kodu unwind w bieżącym zakresie łańcucha. |
|`save_next`|        11100110: Zapisz następną parę rejestrów int lub FP. |
| |            11100111: zarezerwowane |
| |              11101xxx: zarezerwowane dla niestandardowych przypadków sterty poniżej wygenerowane tylko dla procedur ASM |
| |              11101000: niestandardowy stos dla MSFT_OP_TRAP_FRAME |
| |              11101001: niestandardowy stos dla MSFT_OP_MACHINE_FRAME |
| |              11101010: niestandardowy stos dla MSFT_OP_CONTEXT |
| |              11101100: niestandardowy stos dla MSFT_OP_CLEAR_UNWOUND_TO_CALL |
| |              1111xxxx: zarezerwowane |

W instrukcji z dużymi wartościami obejmującymi wiele bajtów, najbardziej znaczące bity są przechowywane jako pierwsze. Ten projekt umożliwia znalezienie łącznego rozmiaru w bajtach kodu unwind przez wyszukanie tylko pierwszego bajtu kodu. Ponieważ każdy kod operacji unwind jest dokładnie mapowany do instrukcji w prologu lub epilogu, można obliczyć rozmiar prologu lub epilogu. Możesz sprawdzić od początku sekwencji do końca i użyć tabeli odnośników lub podobnego urządzenia, aby określić, jak długo jest odpowiedni opcode.

Adresowanie przesunięcia indeksowanego po indeksie nie jest dozwolone w prologu. Wszystkie zakresy przesunięcia (#Z) pasują do kodowania wartości STP/STR Addressing, z wyjątkiem `save_r19r20_x` , w których 248 jest wystarczająca dla wszystkich obszarów zapisu (10 int rejestrów + 8 FP rejestrów wejściowych + 8).

`save_next`należy przestrzegać pary rejestrowania nietrwałej int lub FP: `save_regp` ,,,, `save_regp_x` `save_fregp` `save_fregp_x` `save_r19r20_x` lub innej `save_next` . Zapisuje następną parę rejestru w następnym 16-bajtowym gnieździe w kolejności "rosnąco". A `save_next` odnosi się do pierwszej pary rejestrów FP, gdy następuje po `save-next` tej wartości, która wskazuje ostatnią parę rejestrów int.

Ponieważ rozmiar i instrukcje regularnego powrotu i przeskoku są takie same, nie ma potrzeby rozdzielnego `end` kodu unwind dla scenariuszy wywołania tail.

`end_c`jest przeznaczony do obsługi fragmentów funkcji niesąsiadujących na potrzeby optymalizacji. `end_c`A wskazujące na zakończenie kodów operacji unwind w bieżącym zakresie musi następować inna seria kodu operacji unwind z rzeczywistą `end` . Kody operacji unwind między `end_c` i `end` reprezentują operacje prologu w regionie nadrzędnym (prologu).  Więcej szczegółów i przykładów opisano w sekcji poniżej.

### <a name="packed-unwind-data"></a>Spakowane dane operacji unwind

W przypadku funkcji, których dzienniki i epilogs są zgodne z formularzem kanonicznym opisanym poniżej, można użyć spakowanych danych operacji unwind. Eliminuje to konieczność całkowitego użycia rekordu. xdata i znacząco zmniejsza koszt udostępniania danych unwind. Kanoniczne dzienniki i epilogs zostały zaprojektowane tak, aby spełniały typowe wymagania prostej funkcji: takie, które nie wymaga obsługi wyjątków, i który wykonuje jego konfigurację i operacje usuwania w kolejności standardowej.

Format rekordu. pdata z zapakowanymi danymi unwind wygląda następująco:

![rekord. pdata z zapakowanymi danymi unwind](media/arm64-exception-handling-packed-unwind-data.png "rekord. pdata z zapakowanymi danymi unwind")

Pola są następujące:

- **Początkowy adres RVA funkcji** to 32-bitowy adres RVA początku funkcji.
- **Flaga** jest polem 2-bitowym, jak opisano powyżej, z następującymi znaczeniami:
  - 00 = spakowane dane operacji unwind nie są używane; pozostałe bity wskazują na rekord. xdata
  - 01 = spakowane dane operacji unwind używane z pojedynczym prologem i epilogu na początku i na końcu zakresu
  - 10 = spakowane dane operacji unwind używane dla kodu bez jakichkolwiek Prolog i epilogu. Przydatne do opisywania segmentów funkcji rozdzielonych
  - 11 = zarezerwowane.
- **Długość funkcji** jest polem 11-bitowym dostarczającym długość całej funkcji w bajtach podzieloną przez 4. Jeśli funkcja jest większa niż 8k, zamiast tego należy użyć pełnego rekordu. xdata.
- **Rozmiar ramki** to pole 9-bitowe wskazujące liczbę bajtów stosu przydzielonego dla tej funkcji, podzieloną przez 16. Funkcje, które przydzielą większe niż (8k-16) bajty stosu, muszą używać pełnego rekordu. xdata. Obejmuje obszar zmiennych lokalnych, obszar parametrów wychodzących, zapisywany obszar int i FP oraz obszar parametrów macierzystych, ale wyklucza obszar alokacji dynamicznej.
- **CR** jest flagą 2-bitową wskazującą, czy funkcja zawiera dodatkowe instrukcje dotyczące konfigurowania łańcucha ramek i łącza zwrotnego:
  - 00 = Funkcja, \< x29, LR> para nie jest zapisywana w stosie.
  - 01 = funkcja niełańcuchowa, \< lr> jest zapisywana w stosie
  - 10 = zarezerwowane;
  - 11 = funkcja łańcuchowa, instrukcja magazynu/pary ładowania jest używana w prologu/epilogu \< x29, lr>
- **H** jest flagą 1-bitową wskazującą, czy funkcja jest domachowa do rejestrów parametrów liczb całkowitych (x0-120) przez przechowywanie ich na bardzo rozpoczęciu funkcji. (0 = nie zawiera rejestrów domowych, 1 = Rejestr domy).
- **RegI** to pole 4-bitowe wskazujące liczbę rejestrów nietrwałych int (x19-x28) zapisanych w lokalizacji stosu kanonicznego.
- **RegF** to pole 3-bitowe wskazujące liczbę rejestrów nietrwałych FP (D8-D15) zapisanych w lokalizacji stosu kanonicznego. (RegF = 0: nie zapisano żadnego rejestru FP; RegF>0: rejestry RegF + 1 FP są zapisywane). Spakowane dane unwind nie mogą być używane dla funkcji, która zapisuje tylko jeden rejestr FP.

Dzienniki kanoniczne, które znajdują się w kategoriach 1, 2 (bez wychodzącego obszaru parametrów), 3 i 4 w powyższej sekcji mogą być reprezentowane przez spakowany format unwind.  Epilogs dla funkcji kanonicznych podążają za podobnym formularzem, z wyjątkiem **H** nie ma wpływu, `set_fp` instrukcja zostanie pominięta, a porządek kroków i instrukcje w każdym kroku są odwrócone w epilogu. Algorytm spakowanej. xdata wykonuje następujące kroki, szczegółowo w poniższej tabeli:

Krok 0: wstępne Obliczanie rozmiaru każdego obszaru.

Krok 1. zapisywanie rejestrów zapisanych w liczbie int.

Krok 2. ten krok jest specyficzny dla typu 4 w wczesnych sekcjach. LR jest zapisywana na końcu obszaru int.

Krok 3. zapisywanie zapisywanych rejestrów FP.

Krok 4. zapisywanie argumentów wejściowych w obszarze parametru macierzystego.

Krok 5. przydzielanie pozostałych stosów, w tym obszaru lokalnego, \< x29, lr> i wychodzącego obszaru parametrów. 5a odnosi się do typu kanonicznego 1. 5B i 5c są dla typu kanonicznego 2. 5D i 5e są dla obu typów 3 i 4.

Czynności #|Oflaguj wartości|Liczba instrukcji|Kod operacji|Kod unwind
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **RegI** <= 10|RegI/2 + **RegI** %2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**= = 01 *|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** <= 7|(RegF + 1)/2 +<br/>(RegF + 1) %2)|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** = = 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** = = 11 &&  # locsz<br/> <= 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5B|**CR** = = 11 &&<br/>512 < #locsz <= 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** = = 11 &&  # locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5D|(**CR** = = 00 \| \| **CR**= = 01)  &&<br/>#locsz <= 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** = = 00 \| \| **CR**= = 01)  &&<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\*Jeśli **CR** = = 01 i **RegI** jest liczbą nieparzystą, krok 2 i ostatni save_rep w kroku 1 są scalone w jeden save_regp.

\*\*Jeśli **RegI**  ==  **CR** = = 0, a **RegF** ! = 0, pierwsza wartość STP dla zmiennoprzecinkowego wykonuje wstępne zmniejszenie.

\*\*\*Żadne instrukcje nie `mov x29,sp` są obecne w epilogu. Nie można użyć spakowanych danych operacji unwind, jeśli funkcja wymaga przywrócenia elementu Sp z x29.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Likwidacja częściowych dzienników i epilogs

Najbardziej powszechną sytuacją odwinięcia jest taka, w której wystąpił wyjątek lub wywołanie w treści funkcji, z dala od prologu i wszystkich epilogs. W takiej sytuacji odmowa jest prosta: po prostu rozpoczyna wykonywanie kodów w tablicy unwinds Zaczynając od indeksu 0 i kontynuuje do momentu wykrycia końcowego kodu operacji.

W przypadku, gdy wystąpi wyjątek lub przerwanie w czasie wykonywania prologu lub epilogu, trudniejsze jest prawidłowe odwinięcie. W takich sytuacjach Ramka stosu jest tylko częściowo skonstruowana. Problem polega na określeniu dokładnie tego, co zostało zrobione, aby prawidłowo go cofnąć.

Na przykład Wypełnij ten Prolog i sekwencję epilogu:

```asm
0000:    stp    x29,lr,[sp,#-256]!          // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,#224]             // save_fregp 0, 224
0008:    stp    x19,x20,[sp,#240]           // save_regp 0, 240
000c:    mov    x29,sp                      // set_fp
         ...
0100:    mov    sp,x29                      // set_fp
0104:    ldp    x19,x20,[sp,#240]           // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    x29,lr,[sp],#256            // save_fplr_x  256 (post-indexed load)
0110:    ret    lr                          // end
```

Obok każdego kodu operacji jest odpowiednim kodem unwind opisującym tę operację. Można zobaczyć, jak seria kodów operacji unwind dla prologu jest dokładnym obrazem lustrzanym kodów unwind dla epilogu (nie zliczanie końcowej instrukcji epilogu). Jest to typowa sytuacja i dlatego zawsze przyjmujemy, że kody operacji unwind dla prologu są przechowywane w odwrotnej kolejności od kolejności wykonywania prologu.

Dlatego w przypadku Prolog i epilogu pozostawiamy wspólny zestaw kodów operacji unwind:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

Przypadek epilogu jest prosty, ponieważ jest w normalnej kolejności. Rozpoczynając od przesunięcia 0 w epilogu (które zaczyna się od przesunięcia 0x100 w funkcji), oczekujemy na wykonanie pełnej sekwencji unwindy, ponieważ nie zostało jeszcze wykonane żadne oczyszczanie. Jeśli znajdziesz wypróbujemy jedną instrukcję (w przesunięciu 2 w epilogu), możemy pomyślnie wyłączać je, pomijając pierwszy kod operacji unwind. Możemy uogólnić tę sytuację i założyć 1:1 mapowanie między opcodemi i kodami unwind. Następnie, aby rozpocząć odwinięcie od instrukcji *n* w epilogu, należy pominąć pierwsze *n* kodów i rozpocząć od tej operacji.

Powoduje to, że podobna logika działa dla prologu, z wyjątkiem odwrotnej. Jeśli zaczniemy odwracać od przesunięcia 0 w prologu, chcemy wykonać nic. W przypadku nieprzewinięcia z przesunięcia 2, który jest jedną instrukcją w programie, chcemy rozpocząć wykonywanie sekwencji operacji unwindy po kodzie od końca. (Pamiętaj, że kody są przechowywane w odwrotnej kolejności). W tym miejscu możemy również uogólnić: Jeśli zaczniemy odwinąć od instrukcji n w prologu, należy rozpocząć wykonywanie n kodów nieprzedziałania na końcu listy kodów.

Nie zawsze dzieje się tak, że kody Prolog i epilogu pasują do siebie. Dlatego tablica operacji unwind może potrzebować kilku sekwencji kodów. Aby określić przesunięcie lokalizacji, w której mają zostać rozpoczęte przetwarzanie kodów, użyj następującej logiki:

1. W przypadku odwinięcia od treści funkcji Rozpocznij wykonywanie kodów unwind przy użyciu indeksu 0 i Kontynuuj do momentu osiągnięcia "End" kodu operacji.

1. W przypadku odwinięcia z epilogu należy użyć początkowego indeksu epilogu dostarczonego z zakresem epilogu jako punktu początkowego. Oblicz, ile bajtów danego komputera pochodzi z początku epilogu. Następnie przejdź dalej do kolejnych kodów unwind, pomijając kody operacji unwind, dopóki nie zostaną uwzględnione wszystkie już wykonywane instrukcje. Następnie wykonaj od tego momentu.

1. Jeśli jest to rozwinięcia z poziomu prologu, Użyj indeksu 0 jako punktu początkowego. Oblicz długość kodu prologu z sekwencji, a następnie Oblicz, ile bajtów danego komputera jest od końca prologu. Następnie przejdź dalej do kolejnych kodów unwind, pomijając kody operacji unwind, dopóki nie zostaną uwzględnione wszystkie instrukcje, które nie zostały jeszcze wykonane. Następnie wykonaj od tego momentu.

Te reguły oznaczają kody operacji unwind dla prologu muszą zawsze być pierwszym w tablicy. I, są również kodami używanymi do rozwinięcia w ogólnym przypadku odwracania od wewnątrz treści. Wszelkie sekwencje kodu specyficzne dla epilogu powinny być od razu po.

### <a name="function-fragments"></a>Fragmenty funkcji

W celu optymalizacji kodu i innych powodów warto podzielić funkcję na fragmenty rozdzielone (nazywane również regionami). Po podzieleniu każdy wynikający z nich fragment funkcji wymaga własnego rekordu pData (i prawdopodobnie xdata).

Dla każdego rozdzielonego pomocniczego fragmentu, który ma własne Prolog, oczekuje się, że żadne dostosowanie stosu nie jest wykonywane w prologu. Wszystkie miejsca na stosie wymagane przez region pomocniczy muszą być wstępnie przydzielone przez jego region nadrzędny (lub nazywany regionem hosta). Pozwala to na zachowanie wskaźnika stosu wyłącznie w pierwotnym prologu funkcji.

Typowym przypadkiem fragmentów funkcji jest "separacja kodu" z tym kompilatorem może przenosić region kodu z funkcji hosta. Istnieją trzy nietypowe przypadki, które mogą być spowodowane rozdzieleniem kodu.

#### <a name="example"></a>Przykład

- (region 1: początek)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (region 1: koniec)

- (region 3: początek)

    ```asm
        ...
    ```

- (region 3: koniec)

- (region 2: początek)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (region 2: koniec)

1. Tylko prolog (region 1: wszystkie epilogs znajdują się w regionach oddzielonych):

   Należy opisać tylko Prolog. Nie można go przedstawić w formacie Compact. pdata. W pełnej xdata przypadku może być reprezentowane przez ustawienie epilogu Count = 0. Zobacz region 1 w powyższym przykładzie.

   Kody operacji unwind: `set_fp` , `save_regp 0,240` , `save_fplr_x_256` , `end` .

1. Tylko epilogs (region 2: Prolog znajduje się w regionie hosta)

   Przyjmuje się, że przez kontrolkę czas przeskoczy do tego regionu, wszystkie kody prologu zostały wykonane. Częściowe odwinięcie może wystąpić w epilogs w taki sam sposób jak w przypadku normalnej funkcji. Tego typu regionu nie można reprezentować przez Compact. pdata. W pełnym rekordzie. xdata może być zakodowana przy użyciu prologu "fantomu", który jest poddany przez `end_c` `end` parę kodu i.  Interlinia `end_c` wskazuje rozmiar prologu równy zero. Epilogu początkowy indeks pojedynczych punktów epilogu do `set_fp` .

   Kod unwind dla regionu 2:,,,, `end_c` `set_fp` `save_regp 0,240` `save_fplr_x_256` `end` .

1. Brak dzienników lub epilogs (region 3: zarejestrowanie i wszystkie epilogs znajdują się w innych fragmentach):

   Format Compact. pdata można zastosować za pośrednictwem flagi ustawień = 10. W przypadku pełnego rekordu. xdata liczba epilogu = 1. Kod unwind jest taki sam jak kod dla regionu 2, ale indeks początkowy epilogu wskazuje również na `end_c` . Częściowe odwinięcie nie będzie nigdy wykonywane w tym regionie kodu.

Innym bardziej skomplikowanym przypadkiem fragmentów funkcji jest "Zmniejsz Zawijanie". Kompilator może zdecydować się na opóźnienie zapisywania niedozwolonych, zapisywanych rejestrów, aż poza funkcją prologu wejścia funkcji.

- (region 1: początek)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (region 2: początek)

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- (region 2: koniec)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (region 1: koniec)

W prologu regionu 1 przestrzeń stosu jest wstępnie przypisana. Zobaczysz, że region 2 będzie miał ten sam kod operacji unwindy nawet wtedy, gdy jego funkcja hosta została przeniesiona.

Region 1: `set_fp` ,,, `save_regp 0,240` `save_fplr_x_256` `end` z indeksem początkowym epilogu, wskazuje na `set_fp` jak zwykle.

Region 2:,,,, `save_regp 2, 224` `end_c` `set_fp` `save_regp 0,240` `save_fplr_x_256` `end` . Epilogu początkowy Indeks wskazuje na pierwszy kod operacji unwind `save_regp 2, 224` .

### <a name="large-functions"></a>Duże funkcje

Fragmenty mogą służyć do opisywania funkcji większych niż limit 1M narzucony przez pola bitowe w nagłówku. xdata. Aby opisać bardzo dużą funkcję podobną do tej, należy podzielić ją na fragmenty mniejsze niż 1M. Każdy fragment powinien zostać dostosowany, aby nie dzielił epilogu na wiele elementów.

Tylko pierwszy fragment funkcji będzie zawierać Prolog; wszystkie inne fragmenty są oznaczone jako nieposiadające prologu. W zależności od liczby epilogs, każdy fragment może zawierać zero lub więcej epilogs. Należy pamiętać, że każdy zakres epilogu w fragmencie określa jego Przesunięcie początkowe względem początku fragmentu, a nie na początku funkcji.

Jeśli fragment nie ma prologu i nie epilogu, nadal wymaga własnego rekordu. pdata (i prawdopodobnie. xdata), aby opisać sposób odwinięcia z wewnątrz treści funkcji.

## <a name="examples"></a>Przykłady

### <a name="example-1-frame-chained-compact-form"></a>Przykład 1: łańcuch ramek, kompaktowy — formularz

```asm
|Foo|     PROC
|$LN19|
    str     x19,[sp,#-0x10]!        // save_reg_x
    sub     sp,sp,#0x810            // alloc_m
    stp     fp,lr,[sp]              // save_fplr
    mov     fp,sp                   // set_fp
                                    //  end of prolog
    ...

|$pdata$Foo|
    DCD     imagerel     |$LN19|
    DCD     0x416101ed
    ;Flags[SingleProEpi] functionLength[492] RegF[0] RegI[1] H[0] frameChainReturn[Chained] frameSize[2080]
```

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Przykład 2: łańcuch z ramkami, Pełna forma z Prologem & epilogu

```asm
|Bar|     PROC
|$LN19|
    stp     x19,x20,[sp,#-0x10]!    // save_regp_x
    stp     fp,lr,[sp,#-0x90]!      // save_fplr_x
    mov     fp,sp                   // set_fp
                                    // end of prolog
    ...
                                    // begin of epilog, a mirror sequence of Prolog
    mov     sp,fp
    ldp     fp,lr,[sp],#0x90
    ldp     x19,x20,[sp],#0x10
    ret     lr

|$pdata$Bar|
    DCD     imagerel     |$LN19|
    DCD     imagerel     |$unwind$cse2|
|$unwind$Bar|
    DCD     0x1040003d
    DCD     0x1000038
    DCD     0xe42291e1
    DCD     0xe42291e1
    ;Code Words[2], Epilog Count[1], E[0], X[0], Function Length[6660]
    ;Epilog Start Index[0], Epilog Start Offset[56]
    ;set_fp
    ;save_fplr_x
    ;save_r19r20_x
    ;end
```

Indeks początkowy epilogu [0] wskazuje tę samą sekwencję kodu unwindy prologu.

### <a name="example-3-variadic-unchained-function"></a>Przykład 3: wariadyczne funkcja niełańcuchowa

```asm
|Delegate| PROC
|$LN4|
    sub     sp,sp,#0x50
    stp     x19,lr,[sp]
    stp     x0,x1,[sp,#0x10]        // save incoming register to home area
    stp     x2,x3,[sp,#0x20]        // ...
    stp     x4,x5,[sp,#0x30]
    stp     x6,x7,[sp,#0x40]        // end of prolog
    ...
    ldp     x19,lr,[sp]             // beginning of epilog
    add     sp,sp,#0x50
    ret     lr

    AREA    |.pdata|, PDATA
|$pdata$Delegate|
    DCD     imagerel |$LN4|
    DCD     imagerel |$unwind$Delegate|

    AREA    |.xdata|, DATA
|$unwind$Delegate|
    DCD     0x18400012
    DCD     0x200000f
    DCD     0xe3e3e3e3
    DCD     0xe40500d6
    DCD     0xe40500d6
    ;Code Words[3], Epilog Count[1], E[0], X[0], Function Length[18]
    ;Epilog Start Index[4], Epilog Start Offset[15]
    ;nop        // nop for saving in home area
    ;nop        // ditto
    ;nop        // ditto
    ;nop        // ditto
    ;save_lrpair
    ;alloc_s
    ;end
```

Indeks początkowy epilogu (4) wskazuje na środek kodu unwindy prologu (częściowo ponownie używany tablicę operacji unwind).

## <a name="see-also"></a>Zobacz także

[Przegląd konwencji ABI ARM64](arm64-windows-abi-conventions.md)<br/>
[Obsługa wyjątków ARM](arm-exception-handling.md)
