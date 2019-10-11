---
title: Obsługa wyjątków ARM64
ms.date: 11/19/2018
ms.openlocfilehash: b4f9a5d6f86f8b88ef42525e6a9bb1b4071585ce
ms.sourcegitcommit: a9f1a1ba078c2b8c66c3d285accad8e57dc4539a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2019
ms.locfileid: "72037743"
---
# <a name="arm64-exception-handling"></a>Obsługa wyjątków ARM64

System Windows on ARM64 używa tego samego mechanizmu obsługi wyjątków strukturalnych dla asynchronicznie generowanych przez sprzęt wyjątków i synchronicznych wyjątków generowanych przez oprogramowanie. Obsługa wyjątków specyficznych dla języka jest tworzona w oparciu o obsługę wyjątków strukturalnych systemu Windows przy użyciu funkcji pomocnika języka. W tym dokumencie opisano obsługę wyjątków w systemie Windows na ARM64 oraz pomocników języka używanych przez kod generowany przez asembler Microsoft ARM i kompilator MSVC.

## <a name="goals-and-motivation"></a>Cele i motywacja

Wyjątkiem są konwencje danych dotyczące odwinięcia wyjątku, a ten opis ma na celu:

1. Podaj wystarczającą ilość opisu, aby zezwolić na odwracanie bez kodu w każdym przypadku.

   - Analizowanie kodu wymaga, aby kod był stronicowany. Zapobiega to występowaniu w niektórych sytuacjach, gdy jest to przydatne (śledzenie, próbkowanie, debugowanie).

   - Analizowanie kodu jest złożone; kompilator należy zachować ostrożność, aby generować tylko instrukcje, które w programie unwiatrer może dekodować.

   - Jeśli nie można w pełni opisać odwinięcia przy użyciu kodów operacji unwind, wówczas w niektórych przypadkach musi on wrócić do dekodowania instrukcji. Zwiększa to ogólną złożoność i najlepiej jest unikać.

1. Obsługa rozwinięcia w funkcjach MID i epilogu.

   - Funkcja odwinięcia jest używana w systemie Windows w przypadku więcej niż obsługi wyjątków, więc ma kluczowe znaczenie, aby można było wykonać dokładne odwinięcie nawet wtedy, gdy w środku sekwencji kodu prolog lub epilogu.

1. Zapoznaj się z minimalną ilością miejsca.

   - Kody operacji unwind nie mogą być zagregowane w celu znacznego zwiększenia rozmiaru binarnego.

   - Ze względu na to, że kody operacji unwind mogą być blokowane w pamięci, niewielki wpływ zapewnia minimalne obciążenie dla każdego załadowanego pliku binarnego.

## <a name="assumptions"></a>Założenia

Są to założenia wprowadzone w opisie obsługi wyjątków:

1. Zarejestrowanie i epilogs w celu przesłania duplikatów. Korzystając z zalet tej typowej cechy, rozmiar metadanych koniecznych do opisania odwinięcia może być znacznie zmniejszony. W treści funkcji nie ma znaczenia, czy operacje prologu są cofnięte lub operacje epilogu są wykonywane w sposób do przodu. Oba powinny generować identyczne wyniki.

1. Funkcje w całości są stosunkowo małe. W celu osiągnięcia najbardziej wydajnego pakowania danych na tym komputerze jest używana kilka optymalizacji.

1. Brak kodu warunkowego w epilogs.

1. Rejestr dedykowanych wskaźników ramki: Jeśli Sp zostanie zapisany w innym rejestrze (x29) w prologu, ten rejestr pozostanie nienaruszony w całej funkcji, dzięki czemu oryginalne Sp można odzyskać w dowolnym momencie.

1. Jeśli SP nie zostanie zapisany w innym rejestrze, wszystkie manipulowanie wskaźnikiem stosu odbywa się wyłącznie w prologu i epilogu.

1. Układ ramki stosu jest zorganizowany zgodnie z opisem w następnej sekcji.

## <a name="arm64-stack-frame-layout"></a>Układ ramki stosu ARM64

(media/arm64-exception-handling-stack-frame.png "Układ ramki stosu") ![układu ramki stosu]

W przypadku funkcji łańcucha ramek FP i LR można zapisać w dowolnym miejscu w obszarze zmiennej lokalnej w zależności od kwestii optymalizacji. Celem jest maksymalizacja liczby miejsc, do których można uzyskać dostęp za pomocą jednej pojedynczej instrukcji na podstawie wskaźnika ramki (x29) lub wskaźnika stosu (SP). Jednak w przypadku funkcji `alloca` musi on być łańcuchem, a x29 musi wskazywać na dół stosu. Aby umożliwić lepsze pokrycie w trybie par rejestracji, nielotne obszary zapisywania są umieszczane w górnej części stosu lokalnego. Poniżej przedstawiono przykłady ilustrujące kilka najbardziej wydajnych sekwencji prologu. W celu zapewnienia przejrzystości i lepszej lokalizacji pamięci podręcznej kolejność przechowywania zapisywanych rejestrów we wszystkich kanonicznych dziennikach jest w kolejności "rosnąco". `#framesz` poniżej reprezentuje rozmiar całego stosu (z wyłączeniem obszaru alloca). `#localsz` i `#outsz` oznacza, że rozmiar lokalnego obszaru (łącznie z obszarem zapisu dla pary \<x29, LR >) i wyjściowy rozmiar parametru jest odpowiednio.

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

   Wszystkie elementy lokalne są dostępne w oparciu o SP. \<x29, LR > punkty do poprzedniej ramki. Dla rozmiaru ramki \< = 512, "Sub SP,..." można je zoptymalizować w przypadku przeniesienia zapisanego obszaru REGS na dół stosu. Minusem, że nie jest spójna z innymi układami powyżej, i zapisano REGS Weź część zakresu dla trybu pary-regs i przednich i po indeksie.

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

   \* alokacja obszaru zapisu reg nie jest przedstawiona w STP, ponieważ wstępnie indeksowane wartości STP reg-LR nie mogą być reprezentowane za pomocą kodów unwind.

   Wszystkie elementy lokalne są dostępne w oparciu o SP. \<x29 > wskazuje na poprzednią ramkę.

1. Łańcuchy, #framesz \< = 512, #outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   Dzięki porównaniu do #1 prologu powyżej, korzyść polega na tym, że wszystkie instrukcje dotyczące zapisywania w rejestrze są gotowe do wykonania bezpośrednio po przydzieleniu tylko jednego stosu instrukcji. W związku z tym nie istnieje żadne przeciwdziałanie w odniesieniu do programu SP, które uniemożliwia użycie równoległości poziomu instrukcji.

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

Rekordy. pdata to uporządkowana Tablica elementów o stałej długości, która opisuje każdą funkcję manipulowania stosem w pliku binarnym środowiska PE. Zwróć uwagę na wyrażenie "manipulowanie stosem": funkcje liścia, które nie wymagają żadnego magazynu lokalnego, a które nie muszą zapisywać/przywracać rejestrów nietrwałych, nie wymagają rekordu. pdata; należy je jawnie pominąć, aby zaoszczędzić miejsce. Odwinięcie od jednej z tych funkcji może po prostu uzyskać adres zwrotny z LR, aby przenieść się do obiektu wywołującego.

Każdy rekord. pData dla ARM64 ma długość 8 bajtów. Ogólny format każdego rekordu umieszcza 32-bitowy adres RVA funkcji uruchamianej w pierwszym wyrazie, a następnie drugi z, który zawiera wskaźnik do elementu o zmiennej długości. xdata lub spakowany wyraz opisujący funkcję w postaci kanonicznej.

![pData rekordu układu](media/arm64-exception-handling-pdata-record.png ". pdata — układ") rekordu

Pola są następujące:

- **Początkowy adres RVA funkcji** to 32-bitowy adres RVA początku funkcji.

- **Flaga** to pole 2-bitowe, które wskazuje, jak interpretować pozostałe 30 bitów drugiego. pdata. Jeśli **Flaga** ma wartość 0, pozostałe bity tworzą **adres RVA informacji o wyjątku** (z niską liczbą bitów niejawnie 0). Jeśli **Flaga** jest różna od zera, pozostałe bity tworzą **spakowaną strukturę danych unwind** .

- **Informacje o wyjątku adres RVA** jest adresem struktury informacji o wyjątku o zmiennej długości przechowywanej w sekcji. xdata. Te dane muszą być wyrównane 4-bajtowo.

- **Spakowane dane unwind** to skompresowany opis operacji wymaganych do odwinięcia z funkcji, przy założeniu, że forma kanoniczna. W takim przypadku nie jest wymagany żaden rekord. xdata.

### <a name="xdata-records"></a>rekordy. xdata

Gdy spakowany format unwindy jest niewystarczający do opisania odwinięcia funkcji, należy utworzyć rekord o zmiennej długości. xdata. Adres tego rekordu jest przechowywany w drugim słowie rekordu. pdata. Format XData jest spakowanym zestawem wyrazów o zmiennej długości:

![xdata rekordu układu](media/arm64-exception-handling-xdata-record.png ". xdata — układ") rekordu

Te dane są podzielone na cztery sekcje:

1. Nagłówek 1 lub 2-Word opisujący ogólny rozmiar struktury i udostępniający dane funkcji klucza. Drugi wyraz jest obecny tylko wtedy, gdy zarówno **Liczba epilogu** , jak i **słowa kodu** są ustawione na 0. To są pola bitowe w nagłówku:

   a. **Długość funkcji** to pole 18-bitowe wskazujące łączną długość funkcji w bajtach podzieloną przez 4. Jeśli funkcja jest większa niż 1M, do opisania funkcji należy użyć wielu pData i XData. Aby uzyskać więcej informacji, zobacz sekcję [duże funkcje](#large-functions) .

   b. **Verse** to pole 2-bitowe opisujące wersję pozostałej XData. W przypadku tego zapisu zostanie zdefiniowana tylko wersja 0 i w ten sposób wartości 1-3 są niedozwolone.

   s. **X** to pole 1-bitowe wskazujące obecność (1) lub nieobecność (0) danych wyjątków.

   Wykres. Wartość **E** to jedno pole bitowe wskazuje, że informacje opisujące pojedynczy epilogu są pakowane do nagłówka (1), a nie wymagają dodatkowych słów Scope w dalszej części (0).

   Adres. **Epilogu Count** to pole 5-bitowe, które ma dwa średnie, w zależności od stanu **E** bitowej:

      1. Jeśli wartość **E** jest ustawiona na 0: określa liczbę całkowitej liczby zakresów epilogu opisanych w sekcji 2. Jeśli w funkcji istnieje więcej niż 31 zakresów, pole **słowa Code** musi mieć wartość 0, aby wskazać, że wymagane jest słowo rozszerzenia.

      2. Jeśli wartość **E** jest ustawiona na 1, to pole określa indeks pierwszego kodu operacji unwind, który opisuje ten i tylko epilogu.

   n. **Słowa kodu** to pole 5-bitowe, które określa liczbę 32-bitowych wyrazów, które muszą zawierać wszystkie kody operacji unwind w sekcji 3. Jeśli wymagane są więcej niż 31 wyrazów (tj. więcej niż 124 bajtów kodu wywinięcia), to pole musi mieć wartość 0, aby wskazać, że wymagane jest słowo rozszerzenia.

   g. **Rozszerzona liczba epilogu** i **rozszerzone słowa kodu** są odpowiednio 16-bitowymi i 8-bitowymi polami, które zapewniają więcej miejsca do kodowania nietypowo dużej liczby epilogs lub nietypowo dużej liczby słów kodu unwind. Słowo Extension zawierające te pola jest obecne tylko wtedy, gdy zarówno pole **Count epilogu** , jak i **słowa kodu** w pierwszym słowie nagłówka są ustawione na 0.

1. Po powyższym nagłówku i opcjonalnym rozszerzonym nagłówku, jeśli **Liczba epilogu** nie jest równa zero, to lista informacji na temat zakresów epilogu, spakowanych jeden do wyrazu i przechowywanych w kolejności rosnącego przesunięcia początkowego. Każdy zakres zawiera następujące bity:

   a. **Epilogu rozpoczęcia przesunięcia** to pole 18-bitowe opisujące przesunięcie w bajtach podzielone przez 4, epilogu względem początku funkcji

   b. **Res** to pole 4-bitowe zarezerwowane do użytku w przyszłości. Wartość musi być równa 0.

   s. **Indeks początkowy epilogu** to 10-bitowe (2 więcej bitów niż **rozszerzone słowa kodu**) wskazujące indeks bajtów pierwszego kodu operacji unwind, który opisuje ten epilogu.

1. Po liście zakresów epilogu jest tablicą bajtów, które zawierają kody wyłączania, opisane szczegółowo w dalszej części. Ta tablica jest dopełniana na końcu do najbliższej pełnej granicy słowa. Kody operacji unwind są zapisywane w tej tablicy, zaczynając od najbliższej treści funkcji, poruszając się w kierunku krawędzi funkcji. Bajty dla każdego kodu unwindy są przechowywane w kolejności big-endian, aby można je było pobrać bezpośrednio, rozpoczynając od najbardziej znaczącego bajtu, który identyfikuje operację i długość reszty kodu.

1. Na koniec po bajtach kodu unwind, jeśli bit **X** w nagłówku został ustawiony na 1, nastąpi informacje dotyczące obsługi wyjątków. Składa się z jednego adresu **RVA procedury obsługi wyjątku** dostarczającego adres samej procedury obsługi wyjątków, a następnie od razu przez zmienną długość danych wymaganą przez program obsługi wyjątków.

Powyższy rekord. xdata został zaprojektowany w taki sposób, że możliwe jest pobranie pierwszych 8 bajtów i z tego, że program obliczy pełny rozmiar rekordu (minus długość danych wyjątków o zmiennym rozmiarze). Poniższy fragment kodu oblicza rozmiar rekordu:

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

Należy zauważyć, że chociaż Prolog i każdy epilogu ma swój własny indeks w kodach operacji unwind, tabela jest współdzielona i jest w pełni możliwe (i nierzadko niespotykane), że mogą współużytkować te same kody (Zobacz przykład 2 w sekcji Przykłady etykiety Co więcej). Autorzy kompilatora powinni zoptymalizować w tym przypadku, w szczególności, ponieważ największy indeks, który może być określony, to 255, w związku z tym ograniczając łączną liczbę kodów operacji unwind dla określonej funkcji.

### <a name="unwind-codes"></a>Kody operacji unwind

Tablica kodów operacji unwind jest pulą sekwencji, które opisują dokładnie sposób cofania efektów prologu w kolejności, w której operacje muszą być cofnięte. Kody operacji unwind można traktować jako zestaw instrukcji mini zakodowany jako ciąg bajtów. Po zakończeniu wykonywania, adres zwrotny do wywołania funkcji znajduje się w rejestrze LR i wszystkie nietrwałe rejestry są przywracane do ich wartości w momencie wywołania funkcji.

Jeśli wyjątki były gwarantowane tylko w obrębie treści funkcji (i nigdy z prologem lub jakimkolwiek epilogu), wówczas konieczne będzie tylko pojedyncze sekwencje. Jednak model unwindy dla systemu Windows wymaga, aby można było odciągać od częściowo wykonanego prologu lub epilogu. Aby można było spełnić to wymaganie, kody odwinięcia zostały starannie zaprojektowane w taki sposób, że jednoznacznie mapują 1:1 na każdy odpowiedni opcode w prologu i epilogu. Ma to kilka implikacji:

1. Zliczając liczbę kodów operacji unwind, można obliczyć długość prologu i epilogu.

1. Zliczając liczbę instrukcji poza początkiem zakresu epilogu, można pominąć równoważną liczbę kodów unwind i wykonać pozostałe sekwencje w celu ukończenia częściowo wykonanego elementu unwindy, który był wykonywany przez epilogu.

1. Zliczając liczbę instrukcji przed końcem prologu, można pominąć równoważną liczbę kodów unwind i wykonać resztę sekwencji, aby cofnąć tylko te części prologu, które zakończyły wykonywanie.

Kody operacji unwind są kodowane zgodnie z poniższą tabelą. Wszystkie kody operacji unwind są pojedynczym/podwójnym bajtem, z wyjątkiem tego, który alokuje duży stos. Całkowicie ma 21 kod operacji unwind. Każdy kod operacji unwind mapuje dokładnie jedną instrukcję w prologu/epilogu, aby umożliwić odwinięcie częściowo wykonanych dzienników i epilogs.

|Kod unwind|Bity i interpretacja|
|-|-|
|`alloc_s`|000XXXXX: Przydziel mały stos z rozmiarem \< 512 (2 ^ 5 * 16).|
|`save_r19r20_x`|    001zzzzz: Zapisz parę \<x19, x20 > w [Sp-#Z * 8]!, wstępnie indeksowanym przesunięciu > =-248 |
|`save_fplr`|        01zzzzzz: Zapisz parę \<x29, LR > w [Sp + #Z * 8], offset \< = 504. |
|`save_fplr_x`|        10zzzzzz: Zapisz parę \<x29, LR > w [SP-(#Z + 1) * 8]!, wstępnie indeksowane przesunięcie > =-512 |
|`alloc_m`|        11000xxx'xxxxxxxx: Przydziel duży stos z rozmiarem \< KB/16% 11. |
|`save_regp`|        110010xx'xxzzzzzz: Zapisz parę x (19 + #X) w [Sp + #Z * 8], offset \< = 504 |
|`save_regp_x`|        110011xx'xxzzzzzz: Zapisz parę x (19 + #X) w [SP-(#Z + 1) * 8]!, wstępnie indeksowane przesunięcie > =-512 |
|`save_reg`|        110100xx'xxzzzzzz: Zapisz reg x (19 + #X) w [Sp + #Z * 8], offset \< = 504 |
|`save_reg_x`|        1101010x'xxxzzzzz: Zapisz reg x (19 + #X) w [SP-(#Z + 1) * 8]!, wstępnie indeksowane przesunięcie > =-256 |
|`save_lrpair`|         1101011x'xxzzzzzz: Zapisz parę \<x (19 + 2 *#X), lr > w [Sp + #Z*8], offset \< = 504 |
|`save_fregp`|        1101100x'xxzzzzzz: Zapisz parę d (8 + #X) w [Sp + #Z * 8], offset \< = 504 |
|`save_fregp_x`|        1101101x'xxzzzzzz: Zapisz parę d (8 + #X), w [SP-(#Z + 1) * 8]!, wstępnie indeksowane przesunięcie > =-512 |
|`save_freg`|        1101110x'xxzzzzzz: Zapisz reg d (8 + #X) w [Sp + #Z * 8], offset \< = 504 |
|`save_freg_x`|        11011110 ' xxxzzzzz: Zapisz reg d (8 + #X) w [SP-(#Z + 1) * 8]!, wstępnie indeksowane przesunięcie > =-256 |
|`alloc_l`|         11100000 ' xxxxxxxx'xxxxxxxx'xxxxxxxx: Przydziel duży stos o rozmiarze \< 256M (2 ^ 24 * 16) |
|`set_fp`|        11100001: Skonfiguruj x29: z: MOV x29, Sp |
|`add_fp`|        11100010 ' XXXXXXXX: Skonfiguruj x29 with: Add x29, SP, #x * 8 |
|`nop`|            11100011: nie jest wymagana żadna operacja operacji unwind. |
|`end`|            11100100: koniec kodu unwind. Oznacza RET w epilogu. |
|`end_c`|        11100101: koniec kodu unwind w bieżącym zakresie łańcucha. |
|`save_next`|        11100110: Zapisz następną parę rejestrów int lub FP. |
|`arithmetic(add)`|    11100111 ' 000zxxxx: Dodaj plik cookie reg (z) do LR (0 = x28, 1 = SP); Dodaj LR, LR, reg (z) |
|`arithmetic(sub)`|    11100111 ' 001zxxxx: subcookie reg (z) z LR (0 = x28, 1 = SP); Sub LR, LR, reg (z) |
|`arithmetic(eor)`|    11100111 ' 010zxxxx: EOR LR with cookie reg (z) (0 = x28, 1 = SP); EOR LR, LR, reg (z) |
|`arithmetic(rol)`|    11100111 ' 0110xxxx: symulowane roli of LR z plikiem cookie reg (x28); xip0 = minus x28; ROR LR, xip0 |
|`arithmetic(ror)`|    11100111 ' 100zxxxx: ROR LR with cookie reg (z) (0 = x28, 1 = SP); ROR LR, LR, reg (z) |
| |            11100111: xxxz----:----zarezerwowane |
| |              11101xxx: zarezerwowane dla niestandardowych przypadków sterty poniżej wygenerowane tylko dla procedur ASM |
| |              11101000: niestandardowy stos dla MSFT_OP_TRAP_FRAME |
| |              11101001: niestandardowy stos dla MSFT_OP_MACHINE_FRAME |
| |              11101010: niestandardowy stos dla MSFT_OP_CONTEXT |
| |              11101100: niestandardowy stos dla MSFT_OP_CLEAR_UNWOUND_TO_CALL |
| |              1111xxxx: zarezerwowane |

W instrukcji z dużymi wartościami obejmującymi wiele bajtów, najbardziej znaczące bity są przechowywane jako pierwsze. Powyższe kody operacji unwind są zaprojektowane tak, aby po prostu wyszukać pierwszy bajt kodu, można sprawdzić łączny rozmiar w bajtach kodu unwind. Mając na względzie, że każdy kod operacji unwindy jest dokładnie mapowany do instrukcji w prologu/epilogu, aby obliczyć rozmiar prologu lub epilogu, wszystko to, co należy zrobić, jest przechodzenie od początku sekwencji do końca przy użyciu tabeli odnośników lub podobnego urządzenia w celu określenia, jak długo cor kod operacji odpowiada.

Należy zauważyć, że adresowanie przesunięcia po indeksowaniu nie jest dozwolone w prologu. Wszystkie zakresy przesunięcia (#Z) pasują do kodowania wartości STP/STR Addressing, z wyjątkiem `save_r19r20_x`, w których 248 jest wystarczająca dla wszystkich obszarów zapisu (10 int rejestrów + 8 FP rejestry wejściowe + 8 rejestrów wejściowych).

`save_next` musi następować po zapisaniu pary rejestrów nietrwałych int lub FP: `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x` lub innego `save_next`. Zapisuje następną parę rejestru w następnym 16-bajtowym gnieździe w kolejności "rosnąco". `save-next` po `save_next` oznacza, że Ostatnia para rejestrów int odwołuje się do pierwszej pary rejestrów FP.

Ponieważ rozmiar i instrukcje regularnego powrotu i przeskoku są takie same, nie ma potrzeby wykonywania oddzielonego kodu `end` w przypadku scenariuszy wywołania tail.

`end_c` jest przeznaczony do obsługi nieciągłych fragmentów funkcji na potrzeby optymalizacji. @No__t-0 wskazujący koniec kodów operacji unwind w bieżącym zakresie musi następować inna seria kodu unwind, zakończona rzeczywistą `end`. Kody operacji unwind między `end_c` i `end` reprezentują operacje prologu w regionie nadrzędnym ("Fantom" prologu).  Więcej szczegółów i przykładów opisano w sekcji poniżej.

### <a name="packed-unwind-data"></a>Spakowane dane operacji unwind

W przypadku funkcji, których dzienniki i epilogs są zgodne z formularzem kanonicznym opisanym poniżej, można użyć spakowanych danych operacji unwind, co eliminuje konieczność całkowitego i znacznego obniżenia kosztów związanych z udostępnianiem danych unwind. Kanoniczne dzienniki i epilogs są przeznaczone do spełniania typowych wymagań prostej funkcji, która nie wymaga obsługi wyjątków, i która wykonuje jego konfigurację i operacje usuwania w kolejności standardowej.

Format rekordu. pdata z zapakowanymi danymi unwind wygląda następująco:

![rekord. pdata z zapakowanymi danymi unwind](media/arm64-exception-handling-packed-unwind-data.png ". pdata rekord z zapakowanymi danymi unwind")

Pola są następujące:

- **Początkowy adres RVA funkcji** to 32-bitowy adres RVA początku funkcji.
- **Flaga** jest polem 2-bitowym, jak opisano powyżej, z następującymi znaczeniami:
  - 00 = spakowane dane operacji unwind nie są używane; pozostałe bity wskazują na rekord. xdata
  - 01 = spakowane dane unwind używane w sposób opisany poniżej z pojedynczym prologem i epilogu na początku i na końcu zakresu
  - 10 = spakowane dane z operacji unwind używane w sposób opisany poniżej dla kodu bez żadnych Prolog i epilogu; jest to przydatne w przypadku opisywania segmentów funkcji oddzielonych.
  - 11 = zarezerwowane;
- **Długość funkcji** jest polem 11-bitowym dostarczającym długość całej funkcji w bajtach podzieloną przez 4. Jeśli funkcja jest większa niż 8k, zamiast tego należy użyć pełnego rekordu. xdata.
- **Rozmiar ramki** to pole 9-bitowe wskazujące liczbę bajtów stosu przydzielonego dla tej funkcji, podzieloną przez 16. Funkcje, które przydzielą większe niż (8k-16) bajty stosu, muszą używać pełnego rekordu. xdata. Obejmuje to obszar zmiennych lokalnych, obszar parametru wychodzącego, zapisywany typ int i FP oraz obszar parametrów macierzystych, ale z wyłączeniem dynamicznego obszaru alokacji.
- **CR** jest flagą 2-bitową wskazującą, czy funkcja zawiera dodatkowe instrukcje dotyczące konfigurowania łańcucha ramek i łącza zwrotnego:
  - 00 = Funkcja bez łańcucha, \<x29, LR > para nie jest zapisywana w stosie.
  - 01 = funkcja niełańcuchowa, \<lr > jest zapisywana na stosie
  - 10 = zarezerwowane;
  - 11 = funkcja łańcuchowa, instrukcja magazynu/pary ładowania jest używana w prologu/epilogu \<x29, LR >
- **H** jest flagą 1-bitową wskazującą, czy funkcja jest domachowa do rejestrów parametrów liczb całkowitych (x0-120) przez przechowywanie ich na bardzo rozpoczęciu funkcji. (0 = nie zawiera rejestrów domowych, 1 = Rejestr domy).
- **RegI** to pole 4-bitowe wskazujące liczbę rejestrów nietrwałych int (x19-x28) zapisanych w lokalizacji stosu kanonicznego.
- **RegF** to pole 3-bitowe wskazujące liczbę rejestrów nietrwałych FP (D8-D15) zapisanych w lokalizacji stosu kanonicznego. (RegF = 0: nie zapisano żadnego rejestru FP; RegF > 0: rejestry RegF + 1 FP są zapisywane). Spakowane dane unwind nie mogą być używane dla funkcji, która zapisuje tylko jeden rejestr FP.

Dzienniki kanoniczne, które znajdują się w kategoriach 1, 2 (bez wychodzącego obszaru parametrów), 3 i 4 w powyższej sekcji mogą być reprezentowane przez spakowany format unwind.  Epilogs dla funkcji kanonicznych podążają za bardzo podobnym formularzem, z wyjątkiem **H** nie ma wpływu, instrukcje `set_fp` są pomijane, a kolejność czynności oraz instrukcje w każdym kroku są odwrócone w epilogu. Algorytm spakowanej xdata wykonuje następujące kroki opisane w poniższej tabeli:

Krok 0: przeprowadzenie wstępnego obliczania rozmiaru każdego obszaru.

Krok 1. zapisywanie rejestrów zapisanych w liczbie int.

Krok 2. ten krok jest specyficzny dla typu 4 w wczesnych sekcjach. LR jest zapisywana na końcu obszaru int.

Krok 3. zapisywanie zapisywanych rejestrów FP.

Krok 4. zapisywanie argumentów wejściowych w obszarze parametru macierzystego.

Krok 5. przydzielenie pozostałych stosów, w tym obszarów lokalnych, \<x29, LR > i wychodzącego obszaru parametrów. 5a odnosi się do typu kanonicznego 1. 5B i 5c są dla typu kanonicznego 2. 5D i 5e są dla obu typów 3 i 4.

Czynności #|Oflaguj wartości|Liczba instrukcji|Kod operacji|Kod unwind
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **RegI** < = 10|RegI/2 + **RegI** % 2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**= = 01 *|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** < = 7|(RegF + 1)/2 +<br/>(RegF + 1)% 2)|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** = = 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** = = 11 & & #locsz<br/> < = 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5B|**CR** = = 11 & &<br/>512 < #locsz < = 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** = = 11 & & #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5D|(**CR** = = 00 \| @ no__t-2 **CR**= = 01) & &<br/>#locsz < = 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** = = 00 \| @ no__t-2 **CR**= = 01) & &<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* Jeśli **CR** = = 01 i **RegI** jest liczbą nieparzystą, krok 2 i ostatni save_rep w kroku 1 są scalone w jednej save_regp.

\* @ no__t-1 Jeśli **RegI** == **CR** = = 0, a **RegF** ! = 0, pierwsza wartość STP dla zmiennoprzecinkowego wykonuje wstępne zmniejszenie.

\* @ no__t-1 @ no__t-2 żadne instrukcje odpowiadające `mov x29,sp` nie są obecne w epilogu. Nie można użyć spakowanych danych operacji unwind, jeśli funkcja wymaga przywrócenia elementu Sp z x29.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Likwidacja częściowych dzienników i epilogs

Najbardziej powszechną sytuacją odwinięcia jest taka, w której wystąpił wyjątek lub wywołanie w treści funkcji, z dala od prologu i wszystkich epilogs. W takiej sytuacji odmowa jest prosta: po prostu rozpoczyna wykonywanie kodów w tablicy unwinds Zaczynając od indeksu 0 i kontynuuje do momentu wykrycia końcowego kodu operacji.

Jest trudniejsze do poprawnego odwinięcia w przypadku, gdy wystąpi wyjątek lub przerwanie podczas wykonywania prologu lub epilogu. W takich sytuacjach Ramka stosu jest tylko częściowo zbudowana, a lewę jest dokładne określenie, co zostało wykonane w celu poprawnego cofnięcia.

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

Obok każdego kodu operacji jest odpowiednim kodem unwind opisującym tę operację. Pierwszą rzeczą, którą należy zwrócić, jest to, że seria kodów operacji unwind dla prologu jest dokładnym odbiciem lustrzanym kodów unwind dla epilogu (nie zliczanie końcowej instrukcji epilogu). Jest to typowa sytuacja, dlatego w związku z tym kody unwind dla prologu są zawsze zakładane jako przechowywane w kolejności odwrotnej od kolejności wykonywania prologu.

W tym przypadku dla prologu i epiloguu pozostawiamy wspólny zestaw kodów operacji unwind:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

Rozpoczynając od epilogu przypadku (bardziej prostego, jakby jest w normalnej kolejności), przy przesunięciu 0 w epilogu (które zaczyna się od przesunięcia 0x100 w funkcji), oczekujemy na wykonanie pełnej sekwencji operacji unwind, ponieważ nie zostało jeszcze wykonane żadne czyszczenie. Jeśli znajdziesz wypróbujemy jedną instrukcję (w przesunięciu 2 w epilogu), możemy pomyślnie wyłączać je, pomijając pierwszy kod operacji unwind. Uogólnianie tej sytuacji, przy założeniu, że 1:1 mapowanie między opcodemi a kodami rozwinięcia, możemy stwierdzać, że w przypadku odstąpienia od instrukcji n w epilogu należy pominąć pierwsze n kodów i rozpocząć od tego miejsca.

Powoduje to, że podobna logika działa dla prologu, z wyjątkiem odwrotnej. W przypadku odwracania od przesunięcia 0 w prologu chcemy wykonać nic. Jeśli przesunięto od 2, który jest jedną instrukcją w, wówczas chcemy rozpocząć wykonywanie sekwencji unwindy po jednym kodzie unwindy od końca (należy pamiętać, że kody są przechowywane w kolejności odwrotnej). W tym miejscu można również uogólnić, że w przypadku odwinięcia od instrukcji n w prologu, należy rozpocząć wykonywanie n kodów operacji unwind na końcu listy kodów.

Teraz nie zawsze jest tak, że kody Prolog i epilogu pasują do siebie. Z tego powodu tablica unwind może potrzebować kilku sekwencji kodów. Aby określić przesunięcie lokalizacji, w której mają zostać rozpoczęte przetwarzanie kodów, użyj następującej logiki:

1. W przypadku odwinięcia od treści funkcji, po prostu Rozpocznij wykonywanie kodów unwind na indeksie 0 i Kontynuuj do momentu, aż zostanie umieszczony "końcowy" kod operacji.

1. W przypadku odwinięcia z epilogu należy użyć początkowego indeksu epilogu dostarczonego z zakresem epilogu jako punktu początkowego. Oblicz, ile bajtów danego komputera pochodzi z początku epilogu. Następnie przejdź dalej do kolejnych kodów unwind, pomijając kody operacji unwind, dopóki nie zostaną uwzględnione wszystkie już wykonywane instrukcje. Następnie wykonaj od tego momentu.

1. Jeśli jest to rozwinięcia z poziomu prologu, Użyj indeksu 0 jako punktu początkowego. Oblicz długość kodu prologu z sekwencji, a następnie Oblicz, ile bajtów danego komputera jest od końca prologu. Następnie przejdź dalej do kolejnych kodów unwind, pomijając kody operacji unwind, dopóki nie zostaną uwzględnione wszystkie instrukcje, które nie zostały jeszcze wykonane. Następnie wykonaj od tego momentu.

W wyniku tych reguł kody unwind dla prologu muszą zawsze być pierwszym w tablicy i są również kodami używanymi do Nieprzerwania w ogólnym przypadku odwinięcia z treści. Wszelkie sekwencje kodu specyficzne dla epilogu powinny być od razu po.

### <a name="function-fragments"></a>Fragmenty funkcji

W celu optymalizacji kodu i innych powodów warto podzielić funkcję na fragmenty rozdzielone (nazywane również regionami). Po wykonaniu tej czynności każdy pofragmentowany funkcja wymaga własnego rekordu pData (i prawdopodobnie xdata).

W przypadku rozdzielonego pomocniczego fragmentu z własnym prologem oczekuje się, że żadne dopasowanie stosu nie zostanie wykonane w prologu. Wszystkie miejsca na stosie wymagane przez regiony pomocnicze muszą być wstępnie przydzielone przez jego region nadrzędny (lub nazywany regionem hosta). Pozwala to na zachowanie wskaźnika stosu wyłącznie w pierwotnym prologu funkcji.

Typowym przypadkiem fragmentów funkcji jest "separacja kodu" z tym kompilatorem może przenosić region kodu z funkcji hosta. Istnieją trzy nietypowe przypadki, które mogą być spowodowane rozdzieleniem kodu.

#### <a name="example"></a>Przykład:

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

   Należy opisać tylko Prolog. Nie może to być reprezentowane przez format Compact. pdata. W pełnej xdata przypadku może to być reprezentowane przez ustawienie epilogu Count = 0. Zobacz region 1 w powyższym przykładzie.

   Kody operacji unwind: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Tylko epilogs (region 2: Prolog znajduje się w regionie hosta)

   Przyjmuje się, że przez kontrolkę czas przeskoczy do tego regionu, wszystkie kody prologu zostały wykonane. Częściowe odwinięcie może wystąpić w epilogs w taki sam sposób jak w przypadku normalnej funkcji. Tego typu regionu nie można reprezentować przez Compact. pdata. W pełnym rekordzie xdata można je zakodować przy użyciu prologu "fantomu", który jest poddany `end_c` i `end`.  Interlinia `end_c` wskazuje, że rozmiar prologu wynosi zero. Epilogu początkowy indeks pojedynczych punktów epilogu do `set_fp`.

   Kod unwind dla regionu 2: `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Brak dzienników lub epilogs (region 3: zarejestrowanie i wszystkie epilogs znajdują się w innych fragmentach):

   Format Compact. pdata można zastosować za pośrednictwem flagi ustawień = 10. W przypadku pełnego rekordu. xdata liczba epilogu = 1. Kod unwind jest taki sam jak w przypadku regionu 2, ale indeks początkowy epilogu wskazuje również na `end_c`. Częściowe odwinięcie nie będzie nigdy wykonywane w tym regionie kodu.

Innym bardziej skomplikowanym przypadkiem fragmentów funkcji jest "zmniejszenie zawijania", dzięki czemu kompilator może wybrać opóźnienie zapisywania niedozwolonych, zapisywanych rejestrów.

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

W prologu regionu 1 przestrzeń stosu jest wstępnie przypisana. Należy pamiętać, że region 2 będzie miał ten sam kod operacji unwindy nawet wtedy, gdy jego funkcja hosta została przeniesiona.

Region 1: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end` z epilogu początkowy Indeks wskazuje na `set_fp` w zwykły sposób.

Region 2: `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`. Epilogu początkowy Indeks wskazuje na pierwszy kod operacji unwind `save_regp 2, 224`.

### <a name="large-functions"></a>Duże funkcje

Fragmenty mogą być używane do opisywania funkcji większych niż limit 1M narzucony przez pola bitowe w nagłówku. xdata. Aby opisać bardzo dużą funkcję podobną do tej, należy po prostu podzielić ją na fragmenty mniejsze niż 1M. Każdy fragment powinien zostać dostosowany, aby nie dzielił epilogu na wiele elementów.

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

Należy zauważyć, że indeks EpilogStart [0] wskazuje tę samą sekwencję kodu unwindy prologu.

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

Uwaga: indeks EpilogStart [4] wskazuje na środek kodu unwindy prologu (częściowo ponownie używany tablicę operacji unwind).

## <a name="see-also"></a>Zobacz także

[Omówienie Konwencji ABI ARM64](arm64-windows-abi-conventions.md)<br/>
[Obsługa wyjątków ARM](arm-exception-handling.md)
