---
title: Obsługa wyjątków ARM64
ms.date: 11/19/2018
ms.openlocfilehash: 921029704e4bf5adabfbe0a82387dadc911b9036
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816155"
---
# <a name="arm64-exception-handling"></a>Obsługa wyjątków ARM64

Windows dla procesorów ARM64 używa tego samego strukturalnej obsługi wyjątków mechanizm asynchroniczne wyjątki generowane przez sprzęt i synchroniczne wyjątki generowane przez oprogramowanie. Programy obsługi wyjątków specyficzne dla języka są tworzone na podstawie Windows obsługi przy użyciu języka funkcji pomocnika wyjątków strukturalnych. W tym dokumencie opisano obsługę wyjątków w Windows ARM64 i pomocników język używany przez kod, który jest generowany przez asemblera ARM firmy Microsoft oraz za pomocą kompilatora MSVC.

## <a name="goals-and-motivation"></a>Cele i motywację

Konwencje danych z odwijania wyjątek, a ten opis są przeznaczone do:

1. Podaj wystarczająco dużo opis, aby umożliwić odwijanie bez konieczności pisania kodu, sondowanie we wszystkich przypadkach.

   - Analizowanie kodu wymaga kodu, które ma być stronicowana w. Zapobiega to odwijanie w niektórych sytuacjach, w których jest użyteczny (śledzenie próbkowania, debugowanie).

   - Analizowanie kodu jest złożone, Kompilator należy uważać, aby generować jedynie instrukcje unwinder jest w stanie dekodowania.

   - Jeśli nie jest w pełni opisane za pomocą kodów unwind odwijanie, następnie w niektórych przypadkach go należy wrócić do dekodowania instrukcji. Zwiększa ogólną złożoności i najlepiej będzie należy unikać.

1. Obsługa odwijania w środku prologu i epilogu pośredniej.

   - Odwijanie jest używany w Windows przez więcej niż obsługa wyjątków, więc krytyczne, że będziemy mogli wykonać dokładne unwind nawet środku sekwencji kodu prologu i epilogu.

1. Zająć minimalnej ilości miejsca.

   - Kody unwind nie agregacji znacznie zwiększyć rozmiar binarnego.

   - Ponieważ kody unwind prawdopodobnie może być zablokowana w pamięci, o niewielkich rozmiarach zapewnia minimalne obciążenie dla każdego załadowanego pliku binarnego.

## <a name="assumptions"></a>Założenia

Poniżej przedstawiono założeniom w opis obsługi wyjątków:

1. Prologs i epilogs zwykle albo innych duplikatów. Przez, korzystając z tego wspólne cechy można znacznie zmniejszyć rozmiar metadane potrzebne do opisania rozwinięcia. W treści funkcji nie ma znaczenia, czy operacje prologu zostaną cofnięte, epilogu operacje są wykonywane w sposób do przodu. Obie powinny być takie same wyniki.

1. Funkcje dla całego zwykle jest stosunkowo mały. Wprowadzono kilka optymalizacji dla miejsca zależy to w celu osiągnięcia najbardziej efektywny sposób pakowania danych.

1. Brak warunkowego kodu w epilogs.

1. Rejestr wskaźnika ramki dedykowanej: Jeśli PS zostanie zapisany w innym rejestru (r29) w prologu, który zarejestrował pozostają niezmienione w całej funkcji, dzięki czemu oryginalne sp może zostać odzyskana w dowolnym momencie.

1. Chyba że PS jest zapisywany w rejestrze innego, wszystkie operacje na wskaźnik stosu występuje wyłącznie w prologu i epilogu.

1. Układ ramki stosu jest zorganizowana zgodnie z opisem w następnej sekcji.

## <a name="arm64-stack-frame-layout"></a>Układ ramki stosu ARM64

![Ramka stosu — układ](media/arm64-exception-handling-stack-frame.png "układ ramki stosu")

Dla funkcji ramki łańcuchowa parę fp i lr można zapisać w dowolnym miejscu w zmiennej lokalnej w zależności od zagadnienia dotyczące optymalizacji. Celem jest, aby zmaksymalizować liczbę zmiennych lokalnych, które można osiągnąć przez jeden pojedynczej instrukcji, w oparciu o wskaźnik ramki (r29) lub wskaźnik stosu (sp). Jednak dla `alloca` funkcji, muszą być powiązane i r29 musi wskazywać na dole stosu. Aby umożliwić lepsze pokrycie rejestru pary adresowanie trybu, nieulotnej zarejestrować aave, które obszary są umieszczone na górze stosu sieci lokalnej. Poniżej przedstawiono przykłady ilustrujące kilka najbardziej efektywny sposób sekwencji prologu. Dla jasności i lepsze lokalność pamięci podręcznej kolejność przechowywania zapisane wywoływanego rejestrów w wszystkich prologs canonical jest w kolejności "rosnącą się". `#framesz` poniżej reprezentuje rozmiar całego stosu (z wyjątkiem obszaru alloca). `#localsz` i `#outsz` oznaczają rozmiar lokalnego (Zapisz w tym obszar \<r29, lr > pary) i odpowiednio wychodzące rozmiar parametru.

1. Tworzenie łańcucha #localsz \<= 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        stp    r29, lr, [sp, -#localsz]!    // save <r29,lr> at bottom of local area
        mov    r29,sp                   // r29 points to bottom of local
        sub    sp, #outsz               // (optional for #outsz != 0)
    ```

1. Tworzenie łańcucha #localsz > 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        sub    sp,#localsz+#outsz       // allocate remaining frame
        stp    r29, lr, [sp, #outsz]    // save <r29,lr> at bottom of local area
        add    r29,sp, #outsz           // setup r29 points to bottom of local area
    ```

1. Unchained, funkcje liścia (lr niezapisane)

    ```asm
        stp    r19,r20,[sp, -72]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp, 16]
        str    r23 [sp,32]
        stp    d8,d9,[sp,40]            // save FP regs (optional)
        stp    d10,d11,[sp,56]
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   Wszystkie zmienne lokalne są dostępne w oparciu o SP. \<R29, lr > wskazuje na poprzedniej ramki. Rozmiar ramki \<= 512, "Sub-sp,..." może być w celu optymalizacji gdy obszar regs zapisany jest przenoszony do dolnej części stosu. Wadą tego jest nie jest spójna z innymi układów powyżej i zapisane regs brać zakresu dla pary regs i przed i po indeksowanych przesunięcia Tryb adresowania.

1. Funkcje unchained, elementu członkowskiego typu liść (lr został zapisany w obszarze zapisane Int)

    ```asm
        stp    r19,r20,[sp,-80]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        stp    r23, lr,[sp, 32]         // save last Int reg and lr
        stp    d8,d9,[sp, 48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,64]          // ...
        sub    sp,#framesz-80           // allocate the remaining local area
    ```

   Lub z parzystą liczbą zapisane rejestrów Int

    ```asm
        stp    r19,r20,[sp,-72]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        str    lr,[sp, 32]              // save lr
        stp    d8,d9,[sp, 40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,56]          // ...
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   Tylko r19 zapisane:

    ```asm
        sub    sp, sp, #16              // reg save area allocation*
        stp    r19,lr,[sp,0]            // save r19, lr
        sub    sp,#framesz-16           // allocate the remaining local area
    ```

   \* Reg Zapisz alokację obszaru nie jest składane do stp, ponieważ stp wstępnie indeksowanych lr reg nie może być reprezentowana z kodami unwind.

   Wszystkie zmienne lokalne są dostępne w oparciu o SP. \<R29 > wskazuje na poprzedniej ramki.

1. Tworzenie łańcucha #framesz \<= 512, #outsz = 0

    ```asm
        stp    r29, lr, [sp, -#framesz]!    // pre-indexed, save <r29,lr>
        mov    r29,sp                       // r29 points to bottom of stack
        stp    r19,r20,[sp, #framesz -32]   // save INT pair
        stp    d8,d9,[sp, #framesz -16]     // save FP pair
    ```

   Porównanie z prologu #1 powyżej, zaletą jest możliwość wszystkich rejestru Zapisz instrukcje gotowe do wykonania od razu po tylko jeden stosu przydzielanie instrukcji. W związku z tym ma zapobieganie zależności na jest dodatkiem, który uniemożliwia równoległości poziomu instrukcji.

1. Tworzenie łańcucha, rozmiar ramki > 512 (opcjonalnie na potrzeby funkcji, które nie alloca)

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        sub    sp,#framesz-80               // allocate the remaining local area
    ```

   W celu optymalizacji r29 można umieścić w dowolnym miejscu w sieci lokalnej w celu zapewnienia lepszego pokrycia "reg pary" i wstępnie przygotowany/odniesienie-indexed przesunięcie Tryb adresowania. Zmienne lokalne poniżej wskaźników ramek można uzyskać dostęp w oparciu SP.

1. Powiązane, rozmiar ramki > 4K, z lub bez alloca(),

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        mov    r8, #framesz/16
        bl     chkstk
        sub    sp, r8*16                    // allocate remaining frame
                                            // end of prolog
        ...
        sp = alloca                         // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,r29                       // sp points to top of local area
        ldp    d10,d11, [sp,64],
        ...
        ldp    r29, lr, [sp], -80           // post-indexed, reload <r29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>Informacje o obsługi wyjątku ARM64

### <a name="pdata-records"></a>rekordy .pdata

Rekordy .pdata są uporządkowanej tablicy elementów o stałej długości, które opisują co manipulowanie stosu funkcji w pliku binarnym środowiska PE. Należy dokładnie frazę "stosu — manipulowanie": funkcje typu liść, nie wymagają żadnych Magazyn lokalny i które nie potrzebują zapisać/przywrócić rejestrów trwałej nie wymagają rekordu .pdata te należy jawnie pominąć, aby zaoszczędzić miejsce. Odwijanie od jednej z tych funkcji można po prostu uzyskiwanie adres zwrotny LR, aby przenieść do obiektu wywołującego.

Każdy rekord .pdata dla architektury ARM64 jest 8 bajtów długości. Ogólny format każdego miejsca rekordu RVA 32-bitowych funkcji uruchamiania w pierwszy wyraz, następuje chwilę, korzystając z niego zawiera wskaźnik do bloku .xdata o zmiennej długości lub upakowaną słowo opisujące sekwencję odwijania kanonicznej funkcji.

![Układ rekordu .pdata](media/arm64-exception-handling-pdata-record.png "układ rekordu .pdata")

Dostępne są następujące pola:

- **Funkcja Start RVA** jest RVA 32-bitowych uruchomienia funkcji.

- **Flaga** jest polem 2-bitowy, która wskazuje, jak interpretować pozostałych bitów 30 drugi wyrazu, .pdata. Jeśli **flagi** wynosi 0, a następnie pozostałe bits formularza **RVA informacje o wyjątku** (za pomocą niski dwa bity niejawnie 0). Jeśli **flagi** jest różna od zera, pozostałe bits formularza **spakowane dane operacji Unwind** struktury.

- **Adres RVA informacje o wyjątku** to adres struktury informacji o zmiennej długości wyjątek, przechowywane w sekcji .xdata. Musi to być 4-bajtowego wyrównania.

- **Spakowane dane operacji Unwind** jest skompresowany opis operacji wymaganych do rozwijają się od funkcji, zakładając, że forma kanoniczna. W tym przypadku żadnego rekordu .xdata jest wymagany.

### <a name="xdata-records"></a>rekordy .xdata

Format upakowaną odwijania jest niewystarczający do opisania rozwinięcia funkcji, rekord o zmiennej długości .xdata musi zostać utworzona. Adres ten rekord jest przechowywany w drugim słowie rekordu .pdata. Format .xdata jest spakowany zestaw znaków o zmiennej długości słowa:

![Układ rekordu .xdata](media/arm64-exception-handling-xdata-record.png ".xdata rekordu układu")

Tych danych jest dzielony na cztery sekcje:

1. 1 lub 2-word nagłówka opisujące całkowity rozmiar struktury i dostarcza dane kluczowa funkcja. Drugi programu word będzie on wyświetlany, jeśli obie **liczba epilogu** i **wyrazów** pola są ustawione na 0. Są to pola bitowe w nagłówku:

   a. **Funkcja długość** jest polem 18-bitowe, wskazując całkowita długość tej funkcji w bajtach, podzielona przez 4. Jeśli funkcja jest większy niż 1 mln, wiele rekordów pdata i xdata musi używane do opisywania tej funkcji. Zobacz [duże funkcje](#large-functions) sekcji, aby uzyskać więcej informacji.

   b. **Sterowniki** jest polem 2-bitowy, opisujący wersję pozostałe xdata. Na chwilę obecną, wersja 0 jest zdefiniowana, a zatem nie są dozwolone wartości 1 – 3.

   c. **X** jest polem 1-bitowego wskazujący obecność (1) lub dane wyjątku braku (0).

   d. **E** jest pole bitowe co oznacza, że informacji opisujących pojedynczego epilogu są pakowane w nagłówku (1) zamiast konieczności dodatkowego zakresu wyrazów nowszej (0).

   e. **Liczba epilogu** jest polem 5-bitowy, który ma dwa znaczenia, w zależności od stanu **E** bitowych:

      1. Jeśli **E** jest ustawiona na 0: Określa liczbę całkowita liczba zakresów wyjątek opisane w sekcji 2. Jeśli istnieje więcej niż 31-zakresami, w funkcji, a następnie **wyrazów** pola musi być równa 0 Aby wskazać, że wymagane jest słowo rozszerzenia.

      2. Jeśli **E** jest ustawiona na 1, w tym polu określa indeks pierwszego kodu odwijania, opisujący jeden i tylko epilogu.

   f. **Wyrazy kodu** jest polem 5-bitowy, określająca liczbę 32-bitowych słów potrzebne ma zawierać wszystkie kody unwind w sekcji 4. Jeśli wymaganych jest więcej niż 31 wyrazów (czyli więcej niż 124 operacji unwind bajty kodu), a następnie to pole musi być równa 0 Aby wskazać, że wymagane jest rozszerzenie programu word.

   g. **Rozszerzony liczba epilogu** i **rozszerzone wyrazów** są odpowiednio pola 16-bitowych i 8-bitowych, które zapewniają więcej miejsca na potrzeby kodowania niezwykle dużą liczbę epilogs lub nietypowo dużej liczby operacji unwind wyrazów. Rozszerzenia programu word, zawierające te pola będzie on wyświetlany, jeśli oba **liczba epilogu** i **wyrazów** pól w pierwszy wyraz nagłówka są ustawione na 0.

1. Po wyjątku Jeśli **liczba epilogu** nie jest równa zero, listę informacji o zakresach epilogu spakowane do programu word i przechowywane w celu zwiększenia początkowe przesunięcie. Każdy zakres zawiera następujące usługi bits:

   a. **Przesunięcie Start epilogu** jest polem 18-bitowe przesunięcie w bajtach, podzielona przez 4 epilogu względem początku funkcji opisujące

   b. **Res** jest 4-bitowe pole zarezerwowane dla przyszłego rozszerzenia. Musi wynosić 0.

   c. **Indeks Start epilogu** jest 10-bitowy (2 bity więcej niż **rozszerzone wyrazów**) pola wskazujący indeks bajtu pierwszego unwind kod, który opisuje to epilogu.

1. Po listy zakresów epilogu zawiera tablicę bajtów, które zawierają kody odwijania, opisano szczegółowo w dalszej części tego tematu. Ta tablica jest uzupełniana na końcu do najbliższej granicy pełny wyraz. Bajty są przechowywane w kolejności little-endian, dzięki czemu mogą być bezpośrednio pobierane w trybie little-endian.

1. Na koniec, po bajty kodu unwind (i, jeśli **X** bit w nagłówku został ustawiony na wartość 1) zawiera informacje o program obsługi wyjątku. Ten krok składa się z pojedynczej **RVA obsługi wyjątków** podając adres obsługi wyjątków, a następnie natychmiast o zmiennej długości ilość danych wymaganych przez program obsługi wyjątków.

Rekord .xdata powyżej zaprojektowano w taki sposób, że istnieje możliwość pobrania pierwsze 8 bajtów i przy jego użyciu obliczeń w pełnym rozmiarze rekordu (minus długość danych wyjątku o zmiennym rozmiarze, który następuje po). Poniższy fragment kodu oblicza rozmiar rekordu:

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

Należy zauważyć, że chociaż prologu i epilogu każdy ma własny indeks na kody odwijania, tabela jest współużytkowana przez je i jest przepływności (i nie jest całkowicie rzadko), wszystkie udostępniają te same kody (Zobacz przykład 2 w załączniku A poniżej). Twórcom kompilatorów powinien optymalizować generowany dla tego przypadku, w szczególności ponieważ największego indeksu, który może być określony wynosi 255, co ogranicza łączną liczbę kodów unwind dla danej funkcji.

### <a name="unwind-codes"></a>Kodów odwinięcia

Tablica kodów odwijania jest pula sekwencji, które opisują dokładnie, jak cofnąć skutki prologu, w kolejności, w którym trzeba można cofnąć operacji. Kody unwind można traktować jako zestaw instrukcji mini zakodowany jako ciąg bajtów. Po zakończeniu wykonywania adres zwrotny wywołania funkcji znajduje się w rejestrze lr, a wszystkie rejestrów trwałej zostaną przywrócone do ich wartości w czasie, gdy wywołana została funkcja.

Jeśli wyjątki były tylko musi wystąpić w treści funkcji (i nigdy nie przy użyciu prologu i epilogu wszelkie), a następnie konieczna może być tylko jednej sekwencji. Model odwijania Windows wymaga jednak, że firma Microsoft można wykonać operacji odwinięcia z w ramach częściowo wykonane prologu i epilogu. Aby spełnić to wymaganie, kody unwind zostały dokładnie zaprojektowane tak, aby jednoznacznie mapują 1:1 do każdego odpowiedni kod operacji w prologu i epilogu. To ma wpływ kilka:

1. Przez liczenie unwind kodów, jest można obliczyć długość prologu i epilogu.

1. Przez liczenie instrukcji po uruchomieniu zakresu epilogu, jest możliwe, aby pominąć równoważną liczbę kodów unwind i wykonania pozostałej części sekwencji, aby ukończyć częściowo wykonywane unwind działał epilogu.

1. Przez liczenie instrukcji przed zakończeniem prologu, jest możliwe, aby pominąć równoważną liczbę kodów unwind i wykonania pozostałej części sekwencji, aby cofnąć tylko te części prologu, które zostaną ukończone.

Kody unwind są kodowane zgodnie z poniższą tabelą. Wszystkie kodów odwinięcia są pojedynczy/podwójny bajt, z wyjątkiem tego, który przydziela dużego stosu. Są całkowicie 21 kodu unwind. Każdy unwind kodu mapy dokładnie jeden instrukcji w prologu/epilogu w celu umożliwienia odwijanie prologs częściowo wykonane i epilogs.

|Kodzie operacji unwind|Usługa BITS i interpretacji|
|-|-|
|`alloc_s`|000xxxxx: przydzielić mały stos o rozmiarze \< 512 (2 ^ 5 * 16).|
|`save_r19r20_x`|    001zzzzz: Zapisz \<r19, 20 > pary w [Z dodatkiem sp # * 8]!, wstępnie indeksowanych przesunięcie > =-248 |
|`save_fplr`|        01zzzzzz: Zapisz \<r29, lr > pair u [sp + #Z * 8], offset \<= 504. |
|`save_fplr_x`|        10zzzzzz: Zapisz \<r29, lr > pair w [sp-(#Z + 1) * 8]!, wstępnie indeksowanych przesunięcie > =-512 |
|`alloc_m`|        11000xxx "xxxxxxxx: alokacji stosu dużych o rozmiarze \< 16 KB (2 ^ 11 * 16). |
|`save_regp`|        110010xx "xxzzzzzz: Zapisz pary r(19+#X) u [sp + #Z * 8], offset \<= 504 |
|`save_regp_x`|        110011xx'xxzzzzzz: save pair r(19+#X) at [sp-(#Z+1)*8]!, pre-indexed offset >= -512 |
|`save_reg`|        110100xx "xxzzzzzz: Zapisz r(19+#X) reg w [sp + #Z * 8], offset \<= 504 |
|`save_reg_x`|        1101010 x "xxxzzzzz: Zapisz r(19+#X) reg w [sp-(#Z + 1) * 8]!, wstępnie indeksowanych przesunięcie > =-256 |
|`save_lrpair`|         1101011x'xxzzzzzz: save pair \<r19+2 *#X,lr> at [sp+#Z*8], offset \<= 504 |
|`save_fregp`|        1101100x'xxzzzzzz: save pair d(8+#X) at [sp+#Z*8], offset \<= 504 |
|`save_fregp_x`|        1101101x'xxzzzzzz: save pair d(8+#X), at [sp-(#Z+1)*8]!, pre-indexed offset >= -512 |
|`save_freg`|        1101110 x "xxzzzzzz: Zapisz d(8+#X) reg w [sp + #Z * 8], offset \<= 504 |
|`save_freg_x`|        11011110'xxxzzzzz: save reg d(8+#X) at [sp-(#Z+1)*8]!, pre-indexed offset >= -256 |
|`alloc_l`|         xxxxxxxx "xxxxxxxx" xxxxxxxx 11100000': alokacji stosu dużych o rozmiarze \< 256 M (2 ^ 24 * 16) |
|`set_fp`|        11100001: Konfigurowanie r29: za pomocą: mov r29 sp |
|`add_fp`|        11100010' xxxxxxxx: Konfigurowanie r29 z: Dodawanie r29 sp #x * 8 |
|`nop`|            11100011: nie operacji unwind operacji jest wymagany. |
|`end`|            11100100: koniec unwind kodu. Oznacza ret w epilogu. |
|`end_c`|        11100101: koniec unwind kodu w bieżącym zakresie łańcuchowych. |
|`save_next`|        11100110: Zapisz dalej trwałej Int lub FP Zarejestruj pary. |
|`arithmetic(add)`|    11100111' 000zxxxx: Dodaj reg(z) pliku cookie do lr (0 = x28, 1 = sp); Dodawanie lr, lr, reg(z) |
|`arithmetic(sub)`|    11100111' 001zxxxx: sub reg(z) pliku cookie z lr (0 = x28, 1 = sp); Sub-lr, lr, reg(z) |
|`arithmetic(eor)`|    11100111' 010zxxxx: lr równorzędną za pomocą plików cookie reg(z) (0 = x28, 1 = sp); równorzędną lr, lr, reg(z) |
|`arithmetic(rol)`|    11100111' 0110xxxx: symulowane roli programu lr za pomocą plików cookie reg (x28); xip0 = minus x28; RoR lr, xip0 |
|`arithmetic(ror)`|    11100111' 100zxxxx: lr ror za pomocą plików cookie reg(z) (0 = x28, 1 = sp); RoR lr, lr, reg(z) |
| |            11100111: xxxz---:---zarezerwowane |
| |              11101xxx: zarezerwowane dla niestandardowych stosu przypadki przedstawione poniżej generowane tylko dla procedur asm |
| |              11101001: Niestandardowe stos MSFT_OP_TRAP_FRAME |
| |              11101010: Niestandardowe stos MSFT_OP_MACHINE_FRAME |
| |              11101011: Niestandardowe stos MSFT_OP_CONTEXT |
| |              1111xxxx: zarezerwowane |

W instrukcjach o dużych wartościach obejmujących wiele bajtów najbardziej znaczące bity są przechowywane najpierw. Kody unwind powyżej zaprojektowano tak, po prostu wyszukiwanie do pierwszego bajtu kodu to możliwość sprawdzenia, całkowity rozmiar w bajtach kodu unwind. Biorąc pod uwagę, że każdy kod unwind dokładnie jest mapowany na instrukcję w prologu i epilogu, do obliczenia rozmiaru prologu i epilogu, należy wykonać jest przeprowadzenie od samego początku sekwencji-to-end, przy użyciu tabeli odnośników lub podobne urządzenie, aby określić, jak długo Core jest opcode działa prawidłowo.

Należy pamiętać, że po wprowadzeniu indeksowanych adresowania przesunięcia jest niedozwolone w prologu. Wszystkie zakresy przesunięcia (#Z) odpowiadać metodzie kodowania STP/STR adresowania z wyjątkiem `save_r19r20_x` w których 248 jest wystarczająca dla Zapisz wszystkie obszary (10 rejestrów Int + 8 rejestrów FP + 8 rejestrów wejściowego).

`save_next` należy wykonać zapisywania int lub FP volatile zarejestrować pary: `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x`, lub inne `save_next`. Następna para rejestru w następnej miejscu 16-bajtowy zapisuje w kolejności "rośnie". `save-next` następujące `save_next` , oznacza ostatnią parę rejestr Int odwołuje się do pierwszej pary rejestr FP.

Ponieważ rozmiar zwykłych wróć i szybkie instrukcje są takie same, nie ma potrzeby o rozdzielonych `end` kodzie operacji unwind dla scenariuszy wywołanie tail.

`end_c` przeznaczony do obsługi funkcji nieciągłego fragmentów do celów optymalizacji. A `end_c` wskazuje koniec unwind kodów w bieżącym zakresie musi następować innej serii unwind kodu zakończyła się z liczbą rzeczywistą `end`. Kody unwind między `end_c` i `end` reprezentują operacje prologu w regionie nadrzędnego (prologu "fantomu").  Bardziej szczegółowe informacje i przykłady zostały opisane w poniższej sekcji.

### <a name="packed-unwind-data"></a>Spakowane dane operacji unwind

Dla operacji unwind funkcje pakowane którego prologs i epilogs postępuj zgodnie z forma kanoniczna opisane poniżej, dane mogą być używane, eliminując konieczność łączenia się rekord .xdata całkowicie i znacznemu ograniczeniu kosztów związanych z udostępnianiem dane operacji unwind. Canonical prologs i epilogs są przeznaczone do typowych wymagań prostej funkcji, który nie wymaga obsługi wyjątków, a który wykonuje jej operacje instalacji i usuwania w standardowej kolejności.

Format rekordu .pdata z upakowaną unwind danych wygląda następująco:

![dane operacji unwind .pdata rekordu z upakowaną](media/arm64-exception-handling-packed-unwind-data.png ".pdata rekordu z spakowane dane operacji unwind")

Dostępne są następujące pola:

- **Funkcja Start RVA** jest RVA 32-bitowych uruchomienia funkcji.
- **Flaga** jest polem bitowym 2, jak opisano powyżej, mają następujące znaczenie:
  - 00 = upakowaną nie jest używany; dane operacji unwind pozostałych bitów wskazują rekord .xdata poniżej
  - 01 = spakowane dane używane zgodnie z poniższym opisem za pomocą pojedynczego prologu i epilogu na początku i na końcu zakresu operacji unwind
  - 10 = upakowaną używane zgodnie z poniższym opisem dla kodu bez żadnych prologu i epilogu; dane operacji unwind jest to przydatne do opisywania segmentów rozdzielonych funkcji.
  - 11 = zastrzeżone;
- **Funkcja długość** jest polem 11-bitowy, zapewniając długość całej funkcji w bajtach, podzielona przez 4. Funkcja jest większa niż 8 kilobajtów, zamiast tego należy użyć rekordu pełną .xdata.
- **Rozmiar ramki** jest polem 9-bitową określającą liczbę bajtów stosu, który jest przydzielony dla tej funkcji, podzielona przez 16. Funkcje, które alokują przekracza (KB 8 – 16) bajtów stosu, należy użyć rekordu pełną .xdata. W tym sieci lokalnej zmiennej, wychodzące w obszarze parametrów, zapisane wywoływanego Int i FP obszaru i obszaru głównego parametru, ale z wyłączeniem obszaru dynamicznej alokacji.
- **CR** jest flaga 2-bitowy, wskazującą, czy funkcja obejmuje dodatkowe instrukcje dotyczące konfigurowania z łańcuchem ramki i zwracany łącza:
  - 00 = unchained funkcji \<r29, lr > parę nie jest zapisywana w stosie.
  - 01 = unchained funkcji \<lr > jest zapisywany w stos
  - 10 = zastrzeżone;
  - 11 = łańcuchowych funkcji instrukcji pary magazynu/obciążenia jest używana w prologu i epilogu \<r29, lr >
- **H** jest 1-bitowego flagę wskazującą, czy funkcja homes parametru liczby całkowitej rejestruje (r0 r7), umieszczając je na samym początku funkcji. (0 = nie główna rejestrów, 1 = rejestrów domów).
- **RegI** pole 4-bitowy, określającą liczbę rejestrów INT-volatile (r19 r28) zapisywane w lokalizacji canonical stosu.
- **RegF** jest polem 3-bitową określającą liczbę rejestrów FP-volatile (d8 d15) zapisywane w lokalizacji canonical stosu. (0 = nie FP jest zapisywane w rejestrze, m > 0: m + 1 rejestrów FP są zapisywane). Dla funkcji zapisywania tylko jeden rejestr FP, pakowane unwind danych nie można zastosować.

Canonical prologs, które można podzielić na kategorie 1, 2 (bez wychodzących obszaru parametrów), 3 i 4 w powyższej sekcji może być reprezentowany przez format upakowaną unwind.  Epilogs funkcje canonical postępuj zgodnie z formularza bardzo podobne, z wyjątkiem **H** nie ma wpływu, `set_fp` instrukcji zostanie pominięty, a kolejność kroków, jak również instrukcje w każdym kroku zostały cofnięte w epilogu. Algorytm upakowaną xdata obejmuje następujące kroki, szczegółowo opisane w poniższej tabeli:

Krok 0: Wykonaj wstępne obliczania rozmiaru każdego obszaru.

Krok 1. Zapisz Int zapisane wywoływanego rejestrów.

Krok 2. Ten krok jest specyficzny dla typu 4 na początku sekcji. LR zostanie zapisany pod koniec Int obszaru.

Krok 3. Zapisz FP zapisane wywoływanego rejestrów.

Krok 4. Zapisz argumentów wejściowych w obszarze parametrów macierzystego.

Krok 5. Przydziel pozostałe stosu, takich jak lokalny obszar \<r29, lr > pary i wychodzących obszarze parametrów. 5a odnosi się do typu canonical 1. 5b i 5c odpowiadają kanoniczna typu 2. 5d 5e dotyczą zarówno typ 3 i 4 typu.

Krok #|Wartości flagi|Liczba instrukcji|OpCode|Kodzie operacji unwind
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **regI** < = 10|RegI / 2 + **RegI** % 2|`stp r19,r20,[sp,#savsz]!`<br/>`stp r21,r22,[sp,16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**==01*|1|`str lr,[sp, #intsz-8]`\*|`save_reg`
3|0 < **RegF** < = 7|(RegF + 1) / 2 +<br/>(RegF + 1) % 2).|`stp d8,d9,[sp, #intsz]`\*\*<br/>`stp d10,d11,[sp, #intsz+16]`<br/>`...`<br/>`str d(8+RegF),[sp, #intsz+#fpsz-8]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** == 1|4|`stp r0,r1,[sp, #intsz+#fpsz]`<br/>`stp r2,r3,[sp, #intsz+#fpsz+16]`<br/>`stp r4,r5,[sp, #intsz+#fpsz+32]`<br/>`stp r6,r7,[sp, #intsz+#fpsz+48]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** == 11 & & #locsz<br/> <= 512|2|`stp r29,lr,[sp,-#locsz]!`<br/>`mov r29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** == 11 &AMP; &AMP;<br/>512 < #locsz < = 4088|3|`sub sp,sp, #locsz`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** == 11 & & #locsz > 4088|4|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|(**CR** == 00 \| \| **CR**== 01) &AMP; &AMP;<br/>#locsz < = 4088|1|`sub sp,sp, #locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \| \| **CR**== 01) &AMP; &AMP;<br/>#locsz > 4088|2|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* Jeśli **CR** == 01 i **RegI** jest liczbą nieparzystą kroku 2, a ostatni save_rep w kroku 1 są scalane w jeden save_regp.

\*\* Jeśli **RegI** == **CR** == 0, a **RegF** ! = 0 i pierwszy stp dla liczb zmiennoprzecinkowych jest operacja predekrementacji.

\*\*\* Nie instrukcji odpowiadający `mov r29, sp` znajduje się w epilogu. Jeśli funkcja wymaga przywracaniem SP z r29, wówczas nie możemy korzystać z spakowane dane operacji unwind.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Odwijania prologs częściowe i epilogs

Najbardziej typowe odwijania sytuacja jest jeden, w którym wystąpił wyjątek lub wywołania w treści funkcji prologu i epilogs wszystkich. W takiej sytuacji odwijanie jest proste: unwinder po prostu rozpoczęcia wykonywania operacji kody w unwind tablicy, zaczynając od indeksu 0 i kontynuować, dopóki nie zostanie wykryty kod zakończenia operacji.

Jest trudniejsze na odpoczynek, prawidłowo w przypadku, gdy wystąpi wyjątek lub przerwania występuje podczas wykonywania kodu prologu i epilogu. W takich sytuacjach ramka stosu jest tylko częściowo wykonane, a lewy ma na celu określenie, dokładnie co zostało zrobione w celu poprawnie cofnąć tę operację.

Na przykład wykonaj tę sekwencję prologu i epilogu:

```asm
0000:    stp    r29, lr, [sp, -256]!        // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,224]              // save_fregp 0, 224
0008:    stp    r19,r20,[sp,240]            // save_regp 0, 240
000c:    mov    r29,sp                      // set_fp
         ...
0100:    mov    sp,r29                      // set_fp
0104:    ldp    r19,r20,[sp,240]            // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    r29, lr, [sp, -256]!        // save_fplr_x  256 (post-indexed load)
0110:    ret     lr                         // end
```

Obok każdego opcode jest kod odpowiednie odwijania, opisujący tej operacji. Pierwszą rzeczą, którą należy pamiętać, jest serii unwind kodów prologu dokładny obraz lustrzany kody unwind epilogu (bez uwzględnienia końcowej instrukcji epilogu). Jest to sytuacja typowe i z tego powodu unwind kodów prologu są zawsze zakłada, że mają być przechowywane w odwrotnej kolejności w prologu kolejność wykonywania.

W związku z tym zarówno dla kodu prologu i epilogu, firma Microsoft są pozostawiane z wspólny zestaw kodów unwind:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

Począwszy od przypadku epilogu (więcej utrudnione, ponieważ jest w normalnej kolejności), przy przesunięciu 0 w ramach epilogu, (która rozpoczyna się od przesunięcia 0x100 w funkcji), czy oczekujemy do wykonania sekwencji pełne rozwinięcie, ponieważ żadne Oczyszczanie jeszcze nie przeprowadzono. Firma Microsoft jesteśmy jednej instrukcji w (przesunięciem 2 w epilogu), firma Microsoft może pomyślnie unwind przez pominięcie pierwszy kod unwind. Uogólnianie tę sytuację, zakładając, że mapowanie 1:1 między rozkazów i operacji unwind kodów, firma Microsoft stanu, że jeśli firma Microsoft nie są odwijanie od n instrukcji w epilogu, należy pominąć pierwszy kody n unwind i rozpocząć wykonywanie skryptu w tym miejscu.

Okazuje się, że podobnej logiki działa w ramach prologu, z wyjątkiem w odwrotnej kolejności. Firma Microsoft nie są odwijanie od przesunięcia 0 w prologu, czy chcemy wykonania nic. Jeśli firma Microsoft odwinięty od przesunięcia 2, czyli pojedynczej instrukcji w, a następnie chcemy uruchomić wykonywanie unwind sekwencji jednego unwind kodu na końcu (Pamiętaj, że kody są przechowywane w odwrotnej kolejności). I tu zbyt możemy uogólnić Jeśli firma Microsoft nie są odwijanie od n instrukcji w prologu, firma Microsoft powinien rozpocząć wykonywanie kody n odwijanie od końca listy kodów.

Teraz nie zawsze jest przypadek, który kodów prologu i epilogu dokładnie pasować. Z tego powodu unwind tablicy może być konieczne zawierać kilka sekwencje kodów. Aby określić przesunięcie miejsca rozpocząć przetwarzanie kodów, użyj logiki poniższym:

1. Odwijanie od w treści funkcji, wystarczy rozpocząć wykonywanie skryptu kody unwind pod indeksem 0 i kontynuować do momentu osiągnięcia opcode "koniec".

1. Jeśli odwijanie od w ramach epilogu, należy użyć konkretnego epilogu indeks początkowy wyposażone w zakresie epilogu jako punktu wyjścia. Obliczenia, liczbę bajtów w danym Komputerem jest od początku epilogu. Następnie przejdź do przodu, za pomocą kodów odwijania, pomijanie unwind kodów, dopóki wszystkie instrukcje już wykonywane są rozliczane. Następnie należy wykonać w tym momencie uruchamiania.

1. Jeśli odwijanie od w prologu, należy użyć indeksu 0 jako punktu początkowego. Obliczenia długości z sekwencji kodu prologu i należy obliczyć liczbę bajtów w danym Komputerem jest od końca prologu. Następnie przejdź do przodu, za pomocą kodów odwijania, pomijanie unwind kodów, dopóki wszystkie instrukcje nie zostały jeszcze wykonywane są rozliczane. Następnie należy wykonać w tym momencie uruchamiania.

W wyniku tych zasad unwind kodów prologu zawsze musi być pierwszym w tablicy, a także są kody używane na odpoczynek, ogólnie rzecz biorąc, wielkość liter odwijanie od treści. Istnienie sekwencji kodu specyficznego dla epilogu należy stosować bezpośrednio po.

### <a name="function-fragments"></a>Funkcja fragmentów

Do celów optymalizacji kodu i innych powodów może być korzystniejsze podziału funkcji na fragmenty rozdzielonych (nazywane również regiony). Po zakończeniu tej operacji każdego wynikowego fragmentu funkcja wymaga własnej oddzielnych .pdata (i prawdopodobnie .xdata) rekordu.

Dla rozdzielonych dodatkowej fragmentu, który ma swój własny prologu oczekuje się, że żadne dostosowanie stosu odbywa się w prologu jej. Wszystkie stosu miejsca wymaganego przez pomocniczy regionów, które muszą być wstępnie przydzielone przez jego obszar nadrzędny (lub regionu hosta o nazwie). Pozwala to wskaźnik stosem wyłącznie w oryginalnym prologu funkcji.

Typowa funkcja fragmentów jest "Kod separacji" przez kompilator może przenieść region kodu poza jej hosta funkcji. Istnieją trzy nietypowych sytuacjach, na które może uzyskano przez oddzielenie kodu.

#### <a name="example"></a>Przykład:

- (w regionie 1: rozpoczęcie)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (w regionie 1: koniec)
- (region 3: rozpoczęcie)

    ```asm
        ...
    ```

- (region 3: koniec)
- (region 2: begin)

    ```asm
    ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (regionie 2: koniec)

1. Tylko prologu (region 1: wszystkie epilogs znajdują się w oddzielnych regionach):

   Tylko prologu musi być opisany. To nie może być reprezentowany przez format compact .pdata. W przypadku pełnej .xdata, to może być reprezentowany przez ustawienie liczby epilogu = 0. Zobacz w regionie 1 w powyższym przykładzie.

   Kodów odwinięcia: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Tylko Epilogs (regionie 2: prologu znajduje się w regionie hosta)

   Zakłada się, że za pomocą kontroli czasu, przejdziemy do tego obszaru, wszystkie kody prologu zostały wykonane. Częściowe unwind może nastąpić w epilogs samo jak w przypadku normalnej funkcji. Ten typ regionu nie może być reprezentowany przez compact .pdata. W rekordzie pełną xdata mogą być zakodowane przy użyciu "fantomu" prologu otoczone `end_c` i `end` unwind pary kodu.  Wiodące `end_c` wskazuje rozmiar prologu jest równy zero. Indeks epilogu pojedynczej punktami początkowy epilogu `set_fp`.

   Kodzie operacji unwind dla regionu 2: `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Brak prologs lub epilogs (region 3: prologs i wszystkie epilogs znajdują się w innych fragmentów):

   Format Compact .pdata mogą być stosowane przez ustawienie flagi = 10. Urządzenia z rekordem .xdata pełną, liczba epilogu = 1. Operacja unwind kod jest taki sam, jak te w regionie 2 powyżej, ale również wskazuje indeks Start epilogu `end_c`. Rozwinięcie częściowych nie można zastosować w tym regionie kodu.

Innego przypadku bardziej skomplikowanych funkcji fragmentów jest "Zmniejszanie mocy operacji zależnie zawijania" przez kompilator może wybrać opóźnienia, zapisywanie niektóre zapisane wywoływanego rejestrów, dopóki poza prologu wejścia funkcji.

- (w regionie 1: rozpoczęcie)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (regionie 2: rozpoczęcie)

    ```asm
        stp     r21,r22,[sp,224]        // save_regp 2, 224
        ...
        ldp     r21,r22,[sp,224]        // save_regp 2, 224
    ```

- (regionie 2: koniec)

    ```asm
        ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (w regionie 1: koniec)

W prologu regionu 1 jest wstępnie przydzielić miejsca stosu. Należy pamiętać, że ten region 2 będzie miał ten sam kod odwijania, który nawet zostanie przeniesiona poza jej hosta funkcji.

Region 1: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end` z indeksem Start epilogu wskazuje `set_fp` w zwykły sposób.

Region 2: `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`. Indeks Start epilogu wskazuje na pierwszy kodzie operacji unwind `save_regp 2, 224`.

### <a name="large-functions"></a>Duże funkcje

Fragmenty nadającego się do opisu funkcji przekracza limit 1 mln nałożonych przez pola bitowe w nagłówku .xdata. Do opisania bardzo dużych funkcji tak, po prostu musi ona być dzielony na fragmenty mniejszy niż 1 mln. Każdy fragment należy dostosować tak, aby nie podzielona epilogu do wielu fragmentów.

Tylko pierwszy fragment funkcję będzie zawierać prologu; wszystkie inne fragmenty są oznaczone jako mające nie prologu. W zależności od liczby epilogs obecne poszczególne fragmenty może zawierać zero lub więcej epilogs. Należy pamiętać, że zakres epilogu każdego fragmentu określa ich początkowe przesunięcie względem początku fragmentu, a nie na początku funkcji.

Jeśli fragment nie prologu i epilogu nie, nadal wymaga własnej .pdata (i ewentualnie .xdata) rekord opisano, jak rozwijają się od w treści funkcji.

## <a name="examples"></a>Przykłady

### <a name="example-1-frame-chained-compact-form"></a>Przykład 1: Formularz compact łańcuchowa ramki

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

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Przykład 2: Tworzenie łańcucha ramki pełnej postaci za pomocą duplikatu prologu i epilogu

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

Należy pamiętać, że indeks EpilogStart [0] wskazuje tę samą sekwencję prologu unwind kodu.

### <a name="example-3-variadic-unchained-function"></a>Przykład 3: Ze zmienną liczbą argumentów unchained — funkcja

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

Uwaga: Indeks EpilogStart [4] wskazuje środka prologu unwind kodu (częściowo ponownego użycia rozwinięcie array).

## <a name="see-also"></a>Zobacz także

[Przegląd Konwencji ARM64 ABI](arm64-windows-abi-conventions.md)<br/>
[Obsługa wyjątków ARM](arm-exception-handling.md)
