---
title: "Błąd narzędzi konsolidatora LNK2005 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2005
dev_langs: C++
helpviewer_keywords: LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72fc5157bb1863fe3aebe99b2a9d59ee965cf563
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2005"></a>Błąd narzędzi konsolidatora LNK2005
*symbol* już zdefiniowany w obiekcie  
  
Symbol *symbol* został zdefiniowany więcej niż raz.   
  
Ten błąd występuje błąd krytyczny [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).  
  
### <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania  
  
Ogólnie rzecz biorąc, ten błąd oznacza, że zostało przerwane *reguły jednej definicji*, dzięki czemu tylko jedną definicję szablon używany, funkcji, typu lub obiekt w pliku danego obiektu i tylko jedną definicję przez cały plik wykonywalny dla widoczne na zewnątrz obiekty lub funkcje.  
  
Poniżej przedstawiono niektóre typowe przyczyny tego błędu.  
  
-   Ten błąd może wystąpić, gdy plik nagłówka definiuje zmienną. Na przykład jeśli ten plik nagłówka w więcej niż jeden plik źródłowy w projekcie, powoduje błąd:  
  
    ```h  
    // LNK2005_global.h  
    int global_int;  // LNK2005
    ```  
  
    Możliwe rozwiązania obejmują:  
  
    -   Deklarowanie zmiennej `extern` w pliku nagłówka: `extern int global_int;`, następnie zdefiniuj go i opcjonalnie zainicjować jeden i tylko jeden plik źródłowy: `int global_int = 17;`. Ta zmienna jest teraz globalnym czy można użyć w żadnym pliku źródłowego ona `extern`, na przykład przez dołączenie pliku nagłówka. Zalecamy to rozwiązanie dla zmiennych, które muszą być globalnych, ale dobrym engineering oprogramowania rozwiązanie zmniejsza do minimum zmienne globalne.  
    
    -   Deklarowanie zmiennej [statycznych](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`. Ogranicza dostęp do bieżącego obiektu pliku definicji i wiele plików obiekt ma swoje własne kopie zmiennej. Nie zaleca się, że definiowania zmienne statyczne pliki nagłówkowe z powodu był bardziej czytelny z zmienne globalne. Preferowane jest statyczny definicje zmiennych, Przenieś do plików źródłowych, które z nich korzystają.  
  
    -   Deklarowanie zmiennej [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`. To informuje konsolidator, wybierz jedną definicję do użytku przez wszystkie odwołania zewnętrznego i odrzucają pozostałe. To rozwiązanie jest czasami przydatna podczas łączenia biblioteki importu. W przeciwnym razie nie zaleca się on w sposób, aby uniknąć błędów konsolidatora.  
  
-   Ten błąd może wystąpić, gdy plik nagłówka definiuje funkcję, która nie jest `inline`. Jeśli ten plik nagłówka można dołączyć więcej niż jeden plik źródłowy, możesz uzyskać wiele definicji funkcji w pliku wykonywalnym.  
    
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
  
    -   Usuń treść funkcji z pliku nagłówka i pozostawić tylko deklaracji, a następnie wdrożenie funkcji w jeden i tylko jeden plik źródłowy:  
  
        ```h  
        // LNK2005_func_decl.h  
        int sample_function(int);  
        ```  
  
        ```cpp  
        // LNK2005_func_impl.cpp  
        int sample_function(int k) { return 42 * (k % 167); }  
        ```  
-   Ten błąd może również wystąpić w przypadku definiowania funkcji elementów członkowskich poza deklaracją klasy w pliku nagłówka:  
  
    ```h  
    // LNK2005_member_outside.h  
    class Sample {
    public:
        int sample_function(int);  
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    Aby rozwiązać ten problem, należy przenieść definicje funkcji Członkowskich w klasie. Funkcje elementów członkowskich, zdefiniowane wewnątrz deklaracji klasy są wbudowane niejawnie.  
  
    ```h  
    // LNK2005_member_inline.h  
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }  
    };
    ```  
  
-   Ten błąd może wystąpić, gdy łącze więcej niż jedną wersję biblioteki standardowej lub CRT. Na przykład jeśli próbujesz połączyć zarówno detalicznej i biblioteki debugowania CRT lub statycznych i dynamicznych wersje biblioteki lub dwie różne wersje biblioteki standardowej z pliku wykonywalnego, ten błąd może być zgłaszany wiele razy. Aby rozwiązać ten problem, Usuń wszystkie oprócz jednego kopię wszystkich bibliotek polecenia łącza. Nie zaleca się mieszać handlowych i debugować biblioteki lub różnych wersji biblioteki, w tym samym pliku wykonywalnego.  
  
    Mówić konsolidator, aby użyć bibliotek innych niż domyślne, w wierszu polecenia, określić bibliotekami używać, oraz [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) opcję, aby wyłączyć domyślne biblioteki. W środowisku IDE, dodaj odwołania do projektu, aby określić w bibliotekach, a następnie otwórz **strony właściwości** okna dialogowego projektu, a w **konsolidatora**, **dane wejściowe** właściwości Ustaw opcję **Ignoruj wszystkie domyślne biblioteki**, lub **Ignoruj określone biblioteki domyślne** właściwości, aby wyłączyć domyślne biblioteki.   
  
-   Ten błąd może wystąpić, jeśli mieszać korzystanie z bibliotek statycznych i dynamicznych, korzystając z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcji. Na przykład ten błąd może wystąpić w przypadku tworzenia biblioteki DLL do użycia w pliku wykonywalnego prowadzący w CRT statycznych. Aby rozwiązać ten problem, użyj tylko biblioteki statyczne lub tylko dynamicznej biblioteki dla całego pliku wykonywalnego i żadnych bibliotek, które kompilacji do użycia w pliku wykonywalnego.  
  
-   Ten błąd może wystąpić, jeśli symbol jest spakowanych funkcji (utworzony przez kompilowania przy użyciu [/Gy](../../build/reference/gy-enable-function-level-linking.md)) i została uwzględniona w więcej niż jeden plik, ale został zmieniony między kompilacji. Aby rozwiązać ten problem, skompiluj ponownie wszystkie pliki, które obejmują spakowanych funkcji.  
  
-   Ten błąd może wystąpić, jeśli symbol jest określony inaczej w dwóch obiektów w różne biblioteki, a oba obiekty Członkowskie są używane. Jednym ze sposobów rozwiązania tego problemu, gdy statycznie połączone biblioteki jest użycie obiektu elementu członkowskiego z tylko jedną bibliotekę, a obejmują tej biblioteki, najpierw w wierszu polecenia konsolidatora. Aby korzystać z obu symbole, należy utworzyć sposób, aby odróżnić je. Na przykład można utworzyć biblioteki ze źródła, można zawijać każdej biblioteki w unikatową przestrzeń nazw. Alternatywnie można utworzyć nowej biblioteki otoka, używający unikatowych nazw zawijać odwołania do jednej z bibliotek oryginalnego, połączyć nowej biblioteki oryginalna biblioteka, a następnie połącz plik wykonywalny do nowej biblioteki zamiast oryginalna Biblioteka.  
  
-   Ten błąd może wystąpić, jeśli `extern const` zmienna została zdefiniowana dwukrotnie i ma inną wartość w każdej definicji. Aby rozwiązać ten problem, zdefiniuj stałej tylko jeden raz, lub użyj przestrzeni nazw lub `enum class` definicje, aby odróżnić stałe.  
  
-   Ten błąd może wystąpić, jeśli używasz uuid.lib w połączeniu z innymi plikami .lib, które definiują identyfikatorów GUID (na przykład oledb.lib i adsiid.lib). Na przykład:  
  
    ```Output  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     Aby rozwiązać ten problem, Dodaj [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) opcje wiersza polecenia konsolidatora i upewnij się, że tego uuid.lib jest biblioteka pierwszym odwołuje się do.
  
## <a name="additional-information"></a>Dodatkowe informacje  
  
Jeśli używasz starszej wersji zestawu narzędzi, zobacz te artykuły bazy wiedzy Knowledge Base, aby uzyskać więcej informacji na temat określonych przyczyny tego błędu:  
  
-   [Błąd LNK2005 występuje, gdy biblioteka CRT i biblioteki MFC są połączone w niewłaściwej kolejności w programie Visual C++](https://support.microsoft.com/kb/148652)  
  
-   [Poprawka: Globalne przeciążone Delete operatora przyczyny LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [Błędy LNK2005 podczas kompilowania projekt wykonywalny (.exe) w programie Visual C++ ATL](https://support.microsoft.com/kb/184235).  
  
