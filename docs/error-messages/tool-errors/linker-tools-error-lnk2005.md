---
title: Błąd narzędzi konsolidatora LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 6090478c3761c477250b6706a350e261b51f2a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353238"
---
# <a name="linker-tools-error-lnk2005"></a>Błąd narzędzi konsolidatora LNK2005

> *symbol* już zdefiniowany w obiekcie

*Symbol* symbolu został zdefiniowany więcej niż jeden raz.

Po tym błędzie występuje błąd krytyczny [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania

Ogólnie rzecz biorąc, ten błąd oznacza, że złamałeś *regułę jednej definicji,* która pozwala na tylko jedną definicję dla dowolnego używanego szablonu, funkcji, typu lub obiektu w danym pliku obiektu i tylko jedną definicję całego pliku wykonywalnego dla zewnętrznych obiektów lub funkcji.

Oto kilka typowych przyczyn tego błędu.

- Ten błąd może wystąpić, gdy plik nagłówka definiuje zmienną. Na przykład jeśli ten plik nagłówka zostanie uwzględniny w więcej niż jednym pliku źródłowym w projekcie, spowoduje to błąd:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Możliwe rozwiązania obejmują:

  - Zadeklaruj `extern` zmienną `extern int global_int;`w pliku nagłówka: , a następnie zdefiniuj ją i opcjonalnie zainicjalizuj w jednym i tylko jednym pliku źródłowym: `int global_int = 17;`. Ta zmienna jest teraz globalną, której można użyć `extern`w dowolnym pliku źródłowym, deklarując ją , na przykład przez dołączenie pliku nagłówka. Zaleca się to rozwiązanie dla zmiennych, które muszą być globalne, ale dobra praktyka inżynierii oprogramowania minimalizuje zmienne globalne.

  - Zadeklarować zmienną `static int static_int = 17;` [statyczną](../../cpp/storage-classes-cpp.md#static): . Ogranicza to zakres definicji do bieżącego pliku obiektu i umożliwia wiele plików obiektów, aby mieć własną kopię zmiennej. Nie zaleca się definiowania zmiennych statycznych w plikach nagłówkowych ze względu na możliwość pomylenia ze zmiennymi globalnymi. Wolisz przenosić definicje zmiennych statycznych do plików źródłowych, które ich używają.

  - Zadeklaruj `__declspec(selectany) int global_int = 17;` [zmienną selectany](../../cpp/selectany.md): . To informuje konsolidatora, aby wybrać jedną definicję do użycia przez wszystkie odwołania zewnętrzne i odrzucić resztę. To rozwiązanie jest czasami przydatne podczas łączenia bibliotek importu. W przeciwnym razie nie zaleca się go jako sposób na uniknięcie błędów konsolidatora.

- Ten błąd może wystąpić, gdy plik nagłówka `inline`definiuje funkcję, która nie jest . Jeśli ten plik nagłówka zostanie uwzględniny w więcej niż jednym pliku źródłowym, w pliku wykonywalnym zostanie dostępnych wiele definicji funkcji.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Możliwe rozwiązania obejmują:

  - Dodaj `inline` słowo kluczowe do funkcji:

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - Usuń treść funkcji z pliku nagłówka i pozostaw tylko deklarację, a następnie zaimplementuj funkcję w jednym i tylko jednym pliku źródłowym:

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- Ten błąd może również wystąpić, jeśli zdefiniowane funkcje elementów członkowskich poza deklaracją klasy w pliku nagłówka:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Aby rozwiązać ten problem, przenieś definicje funkcji elementu członkowskiego wewnątrz klasy. Funkcje elementów członkowskich zdefiniowane wewnątrz deklaracji klasy są niejawnie inlined.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Ten błąd może wystąpić, jeśli łączysz więcej niż jedną wersję biblioteki standardowej lub CRT. Na przykład jeśli spróbujesz połączyć biblioteki CRT zarówno sieci sprzedaży, jak i debugowania lub zarówno statycznych, jak i dynamicznych wersji biblioteki lub dwóch różnych wersji standardowej biblioteki z plikiem wykonywalnym, ten błąd może być zgłaszany wiele razy. Aby rozwiązać ten problem, usuń z polecenia łącza wszystkie z jednej kopii każdej biblioteki z jednej biblioteki. Nie zaleca się mieszania bibliotek sieci sprzedaży i debugowania lub różnych wersji biblioteki w tym samym pliku wykonywalnym.

   Aby poinformować konsolidatora o użyciu bibliotek innych niż domyślne, w wierszu polecenia określ biblioteki do użycia i użyj opcji [/NODEFAULTLIB,](../../build/reference/nodefaultlib-ignore-libraries.md) aby wyłączyć biblioteki domyślne. W ide, dodaj odwołania do projektu, aby określić biblioteki do użycia, a następnie otwórz okno dialogowe **Strony właściwości** dla projektu, a na stronie **Właściwości Konsolidator** **, Input,** ustaw **opcję Ignoruj wszystkie biblioteki domyślne**lub **Ignoruj określone właściwości bibliotek domyślnych,** aby wyłączyć biblioteki domyślne.

- Ten błąd może wystąpić, jeśli podczas korzystania z opcji [/clr](../../build/reference/clr-common-language-runtime-compilation.md) jest mieszanie bibliotek statycznych i dynamicznych. Na przykład ten błąd może wystąpić, jeśli tworzysz bibliotekę DLL do użycia w pliku wykonywalnym, który łączy w statycznym CRT. Aby rozwiązać ten problem, należy używać tylko bibliotek statycznych lub tylko bibliotek dynamicznych dla całego pliku wykonywalnego i dla wszystkich bibliotek, które można utworzyć do użycia w pliku wykonywalnym.

- Ten błąd może wystąpić, jeśli symbol jest funkcją spakowaną (utworzoną przez kompilację z [/Gy](../../build/reference/gy-enable-function-level-linking.md)) i został uwzględniony w więcej niż jednym pliku, ale został zmieniony między kompilacjami. Aby rozwiązać ten problem, ponownie skompiluj wszystkie pliki, które zawierają funkcję spakowaną.

- Ten błąd może wystąpić, jeśli symbol jest zdefiniowany inaczej w dwóch obiektach członkowskich w różnych bibliotekach i oba obiekty członkowskie są używane. Jednym ze sposobów rozwiązania tego problemu, gdy biblioteki są statycznie połączone jest użycie obiektu członkowskiego tylko z jednej biblioteki i dołączenie tej biblioteki najpierw w wierszu polecenia konsolidatora. Aby użyć obu symboli, należy utworzyć sposób ich rozróżniania. Na przykład jeśli można tworzyć biblioteki ze źródła, można zawinąć każdej biblioteki w unikatowym obszarze nazw. Alternatywnie można utworzyć nową bibliotekę otoki, która używa unikatowych nazw do zawijania odwołań do jednej z oryginalnych bibliotek, łączenia nowej biblioteki z oryginalną biblioteką, a następnie łączenia pliku wykonywalnego z nową biblioteką zamiast oryginalnej biblioteki.

- Ten błąd może `extern const` wystąpić, jeśli zmienna jest zdefiniowana dwukrotnie i ma inną wartość w każdej definicji. Aby rozwiązać ten problem, należy zdefiniować stałą `enum class` tylko raz lub użyć obszarów nazw lub definicji do odróżnienia stałych.

- Ten błąd może wystąpić, jeśli używasz uuid.lib w połączeniu z innymi plikami lib definiuuujymidy (na przykład oledb.lib i adsiid.lib). Przykład:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Aby rozwiązać ten problem, dodaj [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) do opcji wiersza polecenia konsolidatora i upewnij się, że uuid.lib jest pierwszą biblioteką, do których się odwołuje.
