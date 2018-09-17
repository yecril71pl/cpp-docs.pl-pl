---
title: Błąd narzędzi konsolidatora LNK2005 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b20d3037649e99419250f1b3ec4255f2e87e31e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718825"
---
# <a name="linker-tools-error-lnk2005"></a>Błąd narzędzi konsolidatora LNK2005

> *symbol* już zdefiniowany w obiekcie  
  
Symbol *symbol* został zdefiniowany więcej niż raz.
  
Ten błąd występuje błąd krytyczny [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).  
  
### <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i potencjalne rozwiązania  
  
Ogólnie rzecz biorąc, ten błąd oznacza, że zostało przerwane *reguły jednej definicji*, tylko jedną definicję używanego szablonu, funkcji, typ lub obiekt w pliku danego obiektu i tylko jedną definicję, co pozwala na cały plik wykonywalny dla widoczne na zewnątrz obiektów lub funkcji.  
  
Poniżej przedstawiono niektóre typowe przyczyny tego błędu.  
  
-   Ten błąd może wystąpić, gdy plik nagłówkowy definiuje zmienną. Na przykład jeśli dodasz tego pliku nagłówkowego w więcej niż jeden plik źródłowy w projekcie powoduje błąd:  
  
    ```h  
    // LNK2005_global.h  
    int global_int;  // LNK2005
    ```  
  
    Możliwe rozwiązania obejmują:  
  
    -   Zadeklaruj zmienną `extern` w pliku nagłówkowym: `extern int global_int;`, następnie zdefiniuj go i opcjonalnie zainicjować go w jeden i tylko jeden plik źródłowy: `int global_int = 17;`. Ta zmienna jest teraz globalną, można użyć w dowolnym plikiem źródłowym, deklarując ją `extern`, na przykład przez dołączenie pliku nagłówka. Firma Microsoft zaleca tego rozwiązania dla zmiennych, które muszą być globalne, ale dobrym inżynierii oprogramowania rozwiązanie zmniejsza do minimum zmiennych globalnych.  
    
    -   Zadeklaruj zmienną [statyczne](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`. Ogranicza zakres definicji do bieżącego pliku obiektu i zezwala na wiele plików obiektu do ich własnych kopię zmiennej. Nie zaleca się że definiowania zmiennych statycznych w plikach nagłówkowych, ze względu na potencjalnych pomyłek ze zmiennymi globalnymi. Chcesz przenieść definicje zmiennych statycznych do plików źródłowych, które z nich korzystają.  
  
    -   Zadeklaruj zmienną [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`. To informuje konsolidator, wybierz jedną definicję do użytku przez wszystkie odwołania zewnętrzne i odrzucają pozostałe. To rozwiązanie przydaje się czasami podczas łączenia z bibliotekami importowanymi. W przeciwnym razie nie zalecamy jej jako sposobu uniknięcia błędy konsolidatora.  
  
-   Ten błąd może wystąpić, gdy plik nagłówkowy definiuje funkcję, która nie jest `inline`. Jeśli dodasz tego pliku nagłówkowego w więcej niż jeden plik źródłowy, uzyskasz wiele definicji funkcji w pliku wykonywalnym.  
    
    ```h  
    // LNK2005_func.h  
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    Możliwe rozwiązania obejmują:  
  
    -   Dodaj `inline` słów kluczowych funkcji: 

        ```h  
        // LNK2005_func_inline.h  
        inline int sample_function(int k) { return 42 * (k % 167); }  
        ```  
  
    -   Usuń treść funkcji z pliku nagłówka i pozostaw tylko deklaracji, a następnie wdrożenie funkcji w jeden i tylko jeden plik źródłowy:  
  
        ```h  
        // LNK2005_func_decl.h  
        int sample_function(int);  
        ```  
  
        ```cpp  
        // LNK2005_func_impl.cpp  
        int sample_function(int k) { return 42 * (k % 167); }  
        ```  
-   Ten błąd może również wystąpić, jeśli zdefiniujesz elementów członkowskich poza deklaracją klasy w pliku nagłówkowym:  
  
    ```h  
    // LNK2005_member_outside.h  
    class Sample {
    public:
        int sample_function(int);  
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    Aby rozwiązać ten problem, Przenieś definicje funkcji elementów członkowskich wewnątrz klasy. Funkcje Członkowskie zdefiniowane wewnątrz deklaracji klasy są niejawnie śródwierszowych.  
  
    ```h  
    // LNK2005_member_inline.h  
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }  
    };
    ```  
  
-   Ten błąd może wystąpić w przypadku połączenia więcej niż jedna wersja biblioteki standardowej lub CRT. Na przykład Jeśli spróbujesz połączyć zarówno sprzedaży detalicznej i biblioteki CRT debugowania lub statycznych i dynamicznych wersje biblioteki lub dwie różne wersje biblioteki standardowej plik wykonywalny, ten błąd może być zgłaszany wiele razy. Aby rozwiązać ten problem, Usuń wszystkie oprócz jednego kopię wszystkich bibliotek z polecenia łącze. Firma Microsoft nie zaleca się mieszać handlu detalicznego i debugowania bibliotek lub różne wersje biblioteki, w tym samym pliku wykonywalnym.  
  
    Powiedzieć konsolidator, aby korzystać z bibliotek innych niż domyślne, w wierszu polecenia, należy określić biblioteki, a następnie użyć [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) opcję, aby wyłączyć domyślne biblioteki. W środowisku IDE, należy dodać odwołania do projektu, aby określić biblioteki, a następnie otwórz **stron właściwości** okno dialogowe dla projektu, a w **konsolidatora**, **dane wejściowe** właściwości Ustaw opcję **Ignoruj wszystkie domyślne biblioteki**, lub **Ignoruj określone biblioteki domyślne** właściwości, aby wyłączyć domyślne biblioteki.   
  
-   Ten błąd może wystąpić, jeśli mieszanie korzystanie z bibliotek statycznych i dynamicznych, gdy używasz [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcji. Na przykład ten błąd może wystąpić, jeśli tworzysz bibliotekę DLL do użytku w plik wykonywalny prowadzący w statycznych CRT. Aby rozwiązać ten problem, użyj tylko bibliotek statycznych lub tylko bibliotekami dynamicznymi dla całego pliku wykonywalnego i wszystkie biblioteki, które tworzysz do użycia w pliku wykonywalnym.  
  
-   Ten błąd może wystąpić, jeśli symbol jest spakowanych funkcji (utworzone przez kompilowanie za pomocą [/Gy](../../build/reference/gy-enable-function-level-linking.md)) i został dołączony w więcej niż jeden plik, ale został zmieniony między kompilacje. Aby rozwiązać ten problem, ponownie skompilować wszystkie pliki, które zawierają spakowanych funkcji.  
  
-   Ten błąd może wystąpić, jeśli symbol jest zdefiniowany w różny sposób w dwóch obiektów w innych bibliotekach, a oba obiekty Członkowskie są używane. Jednym ze sposobów, aby rozwiązać ten problem, gdy są łączone statycznie biblioteki jest użycie obiektu elementu członkowskiego z tylko jedną bibliotekę i zawierają biblioteki, najpierw w wierszu polecenia konsolidatora. Aby korzystać z obu symbole, należy utworzyć sposób, aby odróżnić je. Na przykład można utworzyć biblioteki ze źródła, można opakować każdej biblioteki w unikatową przestrzeń nazw. Alternatywnie można utworzyć nową bibliotekę otoki, który używa unikatowych nazw opakować odwołania do jednego z oryginalnej biblioteki, połączyć nową bibliotekę oryginalnej biblioteki, a następnie połącz plik wykonywalny do nowej biblioteki zamiast oryginalnej biblioteki.  
  
-   Ten błąd może wystąpić, jeśli `extern const` zmienna jest zdefiniowana w dwa razy i ma inną wartość w każdej definicji. Aby rozwiązać ten problem, zdefiniuj stałą tylko raz, lub użyj przestrzeni nazw lub `enum class` definicji w celu odróżnienia stałych.  
  
-   Ten błąd może wystąpić, jeśli używasz uuid.lib w połączeniu z innymi plikami .lib, definiujące identyfikatorów GUID (na przykład oledb.lib i adsiid.lib). Na przykład:  
  
    ```Output  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     Aby rozwiązać ten problem, należy dodać [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) opcje wiersza polecenia konsolidatora i upewnij się, że ten uuid.lib jest pierwszy biblioteki, do których odwołuje się.
  
## <a name="additional-information"></a>Dodatkowe informacje  
  
Jeśli używasz starszej wersji zestawu narzędzi, zobacz następujące artykuły bazy wiedzy Knowledge Base, aby uzyskać więcej informacji na temat określonej przyczyny tego błędu:  
  
-   [Błąd LNK2005 występuje, gdy biblioteka CRT i bibliotek MFC, które są połączone w niewłaściwej kolejności w programie Visual C++](https://support.microsoft.com/kb/148652)  
  
-   [Poprawka: Globalnego przeciążona Delete operatora powoduje, że LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [Występują błędy LNK2005 podczas kompilowania projektu plik wykonywalny (.exe) w programie Visual C++ ATL](https://support.microsoft.com/kb/184235).  
  
