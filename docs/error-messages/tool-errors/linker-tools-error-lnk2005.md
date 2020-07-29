---
title: Błąd narzędzi konsolidatora LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 278f05b8338ac4238d6862fd7b9bd7744f6c8ee5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225218"
---
# <a name="linker-tools-error-lnk2005"></a>Błąd narzędzi konsolidatora LNK2005

> *symbol* jest już zdefiniowany w obiekcie

*Symbol* symbolu został zdefiniowany więcej niż raz.

Następuje błąd krytyczny [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania

Ogólnie rzecz biorąc, ten błąd oznacza, że została uszkodzona *jedna reguła definicji*, która umożliwia tylko jedną definicję dowolnego użytego szablonu, funkcji, typu lub obiektu w danym pliku obiektu, i tylko jedną definicję w całym pliku wykonywalnym dla obiektów lub funkcji widocznych zewnętrznie.

Poniżej przedstawiono kilka typowych przyczyn tego błędu.

- Ten błąd może wystąpić, gdy plik nagłówkowy definiuje zmienną. Na przykład jeśli ten plik nagłówkowy zostanie uwzględniony w więcej niż jednym pliku źródłowym w projekcie, zostanie zwrócony komunikat o błędzie:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Dostępne są następujące rozwiązania:

  - Zadeklaruj zmienną **`extern`** w pliku nagłówkowym: `extern int global_int;` , a następnie zdefiniuj ją i opcjonalnie zainicjuj w jednym i tylko jednym pliku źródłowym: `int global_int = 17;` . Ta zmienna jest teraz globalnym, którego można użyć w dowolnym pliku źródłowym przez zadeklarowanie go **`extern`** , na przykład przez dołączenie pliku nagłówkowego. Zalecamy używanie tego rozwiązania w przypadku zmiennych, które muszą być globalne, ale dobrą metodą inżynieria oprogramowania minimalizuje zmienne globalne.

  - Zadeklaruj zmienną [statyczną](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;` . Ogranicza zakres definicji do bieżącego pliku obiektu i umożliwia wielu plikom obiektów posiadanie własnej kopii zmiennej. Nie zalecamy definiowania zmiennych statycznych w plikach nagłówkowych ze względu na potencjalną pomyłkę ze zmiennymi globalnymi. Wolisz przenosić definicje zmiennych statycznych do plików źródłowych, które z nich korzystają.

  - Zadeklaruj zmienną [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;` . Nakazuje konsolidatorowi wybranie jednej definicji do użycia przez wszystkie odwołania zewnętrzne i odrzucenie reszty. To rozwiązanie jest czasami przydatne podczas łączenia bibliotek importu. W przeciwnym razie nie zalecamy jej jako sposobu uniknięcia błędów konsolidatora.

- Ten błąd może wystąpić, gdy plik nagłówkowy definiuje funkcję, która nie jest **`inline`** . Jeśli ten plik nagłówkowy zostanie uwzględniony w więcej niż jednym pliku źródłowym, można uzyskać wiele definicji funkcji w pliku wykonywalnym.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Dostępne są następujące rozwiązania:

  - Dodaj **`inline`** słowo kluczowe do funkcji:

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - Usuń treść funkcji z pliku nagłówkowego i pozostaw tylko deklarację, a następnie Zaimplementuj funkcję w jednym i tylko w jednym pliku źródłowym:

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- Ten błąd może również wystąpić, jeśli zdefiniujesz funkcje Członkowskie poza deklaracją klasy w pliku nagłówka:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Aby rozwiązać ten problem, Przenieś definicje funkcji składowej wewnątrz klasy. Funkcje składowe zdefiniowane wewnątrz deklaracji klasy są niejawnie podkreślane.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Ten błąd może wystąpić w przypadku połączenia więcej niż jednej wersji biblioteki standardowej lub CRT. Na przykład, jeśli spróbujesz połączyć zarówno bibliotekę sieci sprzedaży detalicznej, jak i debugowania, lub zarówno statyczną, jak i dynamiczną wersję biblioteki lub dwie różne wersje biblioteki standardowej do pliku wykonywalnego, ten błąd może być raportowany wiele razy. Aby rozwiązać ten problem, Usuń wszystkie kopie oprócz jednej biblioteki z polecenia link. Nie zalecamy używania bibliotek detalicznych i debugowania ani różnych wersji biblioteki w tym samym pliku wykonywalnym.

   Aby określić, że konsolidator ma używać bibliotek innych niż domyślne, w wierszu polecenia określ biblioteki, które mają być używane, i użyj opcji [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) , aby wyłączyć domyślne biblioteki. W środowisku IDE Dodaj odwołania do projektu, aby określić biblioteki, które mają być używane, a następnie otwórz okno dialogowe **strony właściwości** dla projektu, a następnie na stronie właściwości **konsolidatora**, **wprowadź** wartość **Zignoruj wszystkie biblioteki domyślne**lub **Ignoruj określone właściwości bibliotek** domyślnych, aby wyłączyć domyślne biblioteki.

- Ten błąd może wystąpić, jeśli podczas korzystania z bibliotek statycznych i dynamicznych używasz opcji [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) . Na przykład ten błąd może wystąpić, jeśli utworzysz bibliotekę DLL do użycia w pliku wykonywalnym, który łączy się ze statyczną CRT. Aby rozwiązać ten problem, należy użyć tylko bibliotek statycznych lub tylko bibliotek dynamicznych dla całego pliku wykonywalnego i dla wszystkich bibliotek, które są kompilowane do użycia w pliku wykonywalnym.

- Ten błąd może wystąpić, jeśli symbol jest funkcją spakowaną (utworzoną przez kompilację z [/Gy](../../build/reference/gy-enable-function-level-linking.md)) i został uwzględniony w więcej niż jednym pliku, ale został zmieniony między kompilacjami. Aby rozwiązać ten problem, Skompiluj ponownie wszystkie pliki, które zawierają spakowaną funkcję.

- Ten błąd może wystąpić, jeśli symbol jest zdefiniowany inaczej w dwóch obiektach Członkowskich w różnych bibliotekach, a oba obiekty składowe są używane. Jednym ze sposobów rozwiązania tego problemu, gdy biblioteki są połączone statycznie, jest użycie obiektu elementu członkowskiego tylko z jednej biblioteki i dołączenie tej biblioteki najpierw w wierszu polecenia konsolidatora. Aby używać obu symboli, należy utworzyć sposób ich rozróżniania. Na przykład, jeśli możesz skompilować biblioteki ze źródła, możesz otoczyć każdą bibliotekę w unikatowym obszarze nazw. Alternatywnie można utworzyć nową bibliotekę otoki, która używa unikatowych nazw do zawijania odwołań do jednej z oryginalnych bibliotek, połączyć nową bibliotekę z oryginalną biblioteką, a następnie połączyć plik wykonywalny z nową biblioteką, a nie z oryginalną biblioteką.

- Ten błąd może wystąpić, jeśli `extern const` zmienna jest zdefiniowana dwa razy i ma inną wartość w każdej definicji. Aby rozwiązać ten problem, Zdefiniuj stałą tylko raz lub użyj przestrzeni nazw lub **`enum class`** definicji w celu odróżnienia stałych.

- Ten błąd może wystąpić, jeśli używasz identyfikatora UUID. lib w połączeniu z innymi plikami lib, które definiują identyfikatory GUID (na przykład OLEDB. lib i adsiid. lib). Na przykład:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Aby rozwiązać ten problem, należy dodać [/Force: Multiple](../../build/reference/force-force-file-output.md) do opcji wiersza polecenia konsolidatora i upewnić się, że identyfikator UUID. lib to pierwsza biblioteka, do której się odwołuje.
