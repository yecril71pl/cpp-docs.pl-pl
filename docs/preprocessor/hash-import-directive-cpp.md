---
title: '#import, dyrektywa (C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: 9cdfef091b659151f427c381e386f0e83396e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332065"
---
# <a name="import-directive-c"></a>#import dyrektywy (C++)

**C++ Specyficzne**

Służy do dołączania informacji z biblioteki typów. Zawartość biblioteki typów jest konwertowana na klasy C++, głównie opisujące interfejsy COM.

## <a name="syntax"></a>Składnia

> **#import** "*nazwa*pliku \[" *atrybuty*]\
> \< **#import** *atrybuty* *nazwy*> \[pliku ]

### <a name="parameters"></a>Parametry

*Pod nazwą*\
Określa bibliotekę typów do zaimportowania. Nazwa *pliku* może być jednym z następujących rodzajów:

- Nazwa pliku zawierającego bibliotekę typów, taką jak plik .olb, .tlb lub .dll. Słowo kluczowe `file:`, może poprzedzać każdą nazwę pliku.

- Progid formantu w bibliotece typów. Słowo kluczowe `progid:`, może poprzedzać każdy progid. Przykład:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Aby uzyskać więcej informacji na temat progidów, zobacz [Określanie identyfikatora lokalizacji i numeru wersji](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   W przypadku korzystania z kompilatora 32-bitowego w 64-bitowym systemie operacyjnym kompilator może odczytać tylko gałąź rejestru 32-bitowego. Możesz użyć natywnego kompilatora 64-bitowego do tworzenia i rejestrowania biblioteki typów 64-bitowych.

- Identyfikator biblioteki typów. Słowo kluczowe `libid:`, może poprzedzać każdy identyfikator biblioteki. Przykład:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Jeśli nie określisz `version` `lcid`lub , [reguły](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) stosowane do `progid:` `libid:`są również stosowane do .

- Plik wykonywalny (.exe).

- Plik biblioteki (dll) zawierający zasób biblioteki typów (na przykład ocx).

- Dokument złożony zawierający bibliotekę typów.

- Każdy inny format pliku, który może być zrozumiany przez interfejs API **LoadTypeLib.**

*Atrybuty*\
Co najmniej jeden [#import atrybutów](#_predir_the_23import_directive_import_attributes). Oddziel atrybuty spacją lub przecinkiem. Przykład:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-lub-

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Uwagi

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a>Wyszukaj nazwę pliku

*nazwa pliku* jest opcjonalnie poprzedzona specyfikacją katalogu. Nazwa pliku musi nadać nazwę istniejącemu plikowi. Różnica między dwoma formularzami składni jest kolejność, w jakiej preprocesor wyszukuje pliki biblioteki typów, gdy ścieżka jest niecałkowicie określona.

|Formularz składni|Akcja|
|-----------------|------------|
|Cytowany formularz|Nakazuje preprocesorowi wyszukanie plików biblioteki typów najpierw w katalogu pliku zawierającego **instrukcję #import,** a następnie`#include`w katalogach dowolnego pliku zawierającego ( ) ten plik. Następnie preprocesor przeszukuje ścieżki pokazane poniżej.|
|Formularz wspornika kątowego|Nakazuje preprocesorowi wyszukiwanie plików biblioteki typów w następujących ścieżkach:<br /><br /> 1. `PATH` Lista ścieżek zmiennych środowiskowych<br />2. `LIB` Lista ścieżek zmiennych środowiskowych<br />3. Ścieżka określona przez opcję kompilatora [/I,](../build/reference/i-additional-include-directories.md) z tą różnicą, że kompilator wyszukuje bibliotekę typów, do których odwołuje się inna biblioteka typów z atrybutem [no_registry.](../preprocessor/no-registry.md)|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Określ identyfikator lokalizacji i numer wersji

Po określeniu progidu można również określić identyfikator lokalizacji i numer wersji progidu. Przykład:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Jeśli nie określisz identyfikatora lokalizacji, progid jest wybierany zgodnie z następującymi regułami:

- Jeśli istnieje tylko jeden identyfikator lokalizacji, ten jest używany.

- Jeśli istnieje więcej niż jeden identyfikator lokalizacji, używany jest pierwszy z wersją o numerze 0, 9 lub 409.

- Jeśli istnieje więcej niż jeden identyfikator lokalizacji i żaden z nich nie jest 0, 9 lub 409, używany jest ostatni.

- Jeśli nie określisz numeru wersji, używana jest najnowsza wersja.

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a>Pliki nagłówkowe utworzone przez import

**#import** tworzy dwa pliki nagłówka, które rekonstruować zawartość biblioteki typów w kodzie źródłowym języka C++. Podstawowy plik nagłówka jest podobny do pliku produkowanego przez kompilator języka MIDL (Microsoft Interface Definition Language), ale z dodatkowym kodem i danymi generowanymi przez kompilator. [Podstawowy plik nagłówka](#_predir_the_primary_type_library_header_file) ma taką samą nazwę podstawową jak biblioteka typów oraz plik . rozszerzenie TLH. Pomocniczy plik nagłówka ma taką samą nazwę podstawową jak biblioteka typów, z plikiem . rozszerzenie TLI. Zawiera implementacje dla funkcji elementów członkowskich generowanych`#include`przez kompilator i jest uwzględniony ( ) w podstawowym pliku nagłówka.

Jeśli importowanie dispinterface właściwość, która używa parametrów, `byref` **#import** nie generuje [__declspec(właściwość)](../cpp/property-cpp.md) instrukcji dla funkcji.

Oba pliki nagłówkowe są umieszczane w katalogu wyjściowym określonym przez opcję [/Fo (plik obiektu nazwy).](../build/reference/fo-object-file-name.md) Są one następnie odczytywane i kompilowane przez kompilator, `#include` tak jakby podstawowy plik nagłówka został nazwany przez dyrektywę.

Następujące optymalizacje kompilatora są dostarczane z **dyrektywą #import:**

- Po utworzeniu pliku nagłówka jest ono podane w tym samym czasie co biblioteka typów.

- Podczas **przetwarzania #import** kompilator najpierw sprawdza, czy nagłówek istnieje i jest aktualny. Jeśli tak, to nie trzeba go odtworzyć.

**Dyrektywa #import** uczestniczy również w minimalnej przebudowy i może być umieszczona w wstępnie skompilowanym pliku nagłówka.  Aby uzyskać więcej informacji, zobacz [Tworzenie wstępnie skompilowanych plików nagłówkowych](../build/creating-precompiled-header-files.md).

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a>Plik nagłówka biblioteki typów podstawowych

Podstawowy plik nagłówka biblioteki typów składa się z siedmiu sekcji:

- Nagłówek boilerplate: Składa `#include` się z komentarzy, oświadczenie dla COMDEF. H (który definiuje niektóre standardowe makra używane w nagłówku) i inne różne informacje o konfiguracji.

- Forward odwołania i typedefs: Składa się `struct IMyInterface` z deklaracji struktury, takich jak i typedefs.

- Deklaracje inteligentnego wskaźnika: klasa `_com_ptr_t` szablonu jest inteligentnym wskaźnikiem. Hermetyzuje wskaźniki interfejsu i eliminuje konieczność `AddRef`wywoływania `Release`programu `QueryInterface` i funkcji. Ukrywa również wywołanie `CoCreateInstance` podczas tworzenia nowego obiektu COM. W tej sekcji użyto instrukcji `_COM_SMARTPTR_TYPEDEF` makra do ustanowienia typedefs interfejsów COM jako specjalizacje szablonu [_com_ptr_t](../cpp/com-ptr-t-class.md) klasy szablonu. Na przykład dla `IMyInterface`interfejsu , . Plik TLH będzie zawierał:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   kompilator zostanie rozszerzony do:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Typ `IMyInterfacePtr` może być następnie używany zamiast `IMyInterface*`nieprzetworzonego wskaźnika interfejsu . W związku z tym nie ma `IUnknown` potrzeby wywoływania różnych funkcji członkowskich

- Deklaracje typeinfo: Przede wszystkim składa się z definicji klas i innych `ITypeLib:GetTypeInfo`elementów eksponujących poszczególne elementy typeinfo zwrócone przez . W tej sekcji każdy typeinfo z biblioteki typów jest odzwierciedlany `TYPEKIND` w nagłówku w formularzu zależnym od informacji.

- Opcjonalna definicja identyfikatora GUID w starym stylu: zawiera inicjalizowania nazwanych stałych GUID. Nazwy te mają `CLSID_CoClass` `IID_Interface`formularz i , podobne do tych generowanych przez kompilator MIDL.

- `#include`instrukcji dla nagłówka biblioteki typów pomocniczych.

- Stopka kotła: Obecnie `#pragma pack(pop)`zawiera .

Wszystkie sekcje, z wyjątkiem pozycji kotła i sekcji standardowej stopki, są ujęte `library` w obszarze nazw z jego nazwą określoną przez instrukcję w oryginalnym pliku IDL. Nazwy z nagłówka biblioteki typów można używać według jawnej kwalifikacji przy użyciu nazwy obszaru nazw. Można też dołączyć następującą instrukcję:

```cpp
using namespace MyLib;
```

niezwłocznie po **#import** instrukcji w kodzie źródłowym.

Obszar nazw można pominąć za pomocą atrybutu [no_namespace](no-namespace.md)) **dyrektywy #import.** Jednak wygaszenie obszaru nazw może prowadzić do kolizji nazw. Nazwa obszaru nazw może również zostać zmieniona przez atrybut [rename_namespace.](rename-namespace.md)

Kompilator zapewnia pełną ścieżkę do dowolnej zależności biblioteki typów wymaganej przez aktualnie przetwarzaną bibliotekę typów. Ścieżka jest zapisywana w formie komentarzy do nagłówka biblioteki typów (. TLH), który kompilator generuje dla każdej przetworzonej biblioteki typów.

Jeśli biblioteka typów zawiera odwołania do typów zdefiniowanych w innych bibliotekach typów, wówczas plik . Plik TLH będzie zawierał komentarze następującego rodzaju:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Rzeczywista nazwa pliku w **komentarzu #import** jest pełną ścieżką biblioteki typów odsyłanych, przechowywaną w rejestrze. Jeśli wystąpią błędy spowodowane brakującymi definicjami typów, sprawdź komentarze na czele pliku . TLH, aby zobaczyć, które biblioteki typów zależnych mogą wymagać zaimportowania jako pierwsze. Prawdopodobne błędy to błędy składni (na przykład C2143, C2146, C2321), C2501 (brak specyfikatorów decl) lub C2433 ('inline' nie jest dozwolone w deklaracji danych) podczas kompilowania . TLI.

Aby rozwiązać błędy zależności, należy określić, które komentarze zależności nie są w inny sposób przewidziane przez nagłówki systemowe, a następnie podać **#import** dyrektywy w pewnym momencie przed **#import** dyrektywy biblioteki typów zależnych.

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a>#import atrybuty

**#import** opcjonalnie może zawierać jeden lub więcej atrybutów. Te atrybuty powiedzieć kompilator zmodyfikować zawartość nagłówków biblioteki typów. Symbol ukośnika odwrotnego (**\\**) może służyć do uwzględnienia dodatkowych linii w jednej instrukcji **#import.** Przykład:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Aby uzyskać więcej informacji, zobacz [#import atrybuty](../preprocessor/hash-import-attributes-cpp.md).

**KONIEC C++ Specyficzne**

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)\
[Obsługa com kompilatora](../cpp/compiler-com-support.md)
