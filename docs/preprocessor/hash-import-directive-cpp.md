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
ms.openlocfilehash: afd05e7380ec3838fe9763be23ccfae338adb4fb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220265"
---
# <a name="import-directive-c"></a>#import — dyrektywaC++()

**C++Specjalne**

Służy do uwzględniania informacji z biblioteki typów. Zawartość biblioteki typów jest konwertowana na C++ klasy, głównie OPISUJĄC interfejsy com.

## <a name="syntax"></a>Składnia

> **#import** *atrybuty*"*filename*" \[] \
> **#import** *atrybuty nazwy pliku*> ]\[ \<

### <a name="parameters"></a>Parametry

*Nazwa pliku*\
Określa bibliotekę typów do zaimportowania. *Nazwa pliku* może być jednym z następujących rodzajów:

- Nazwa pliku, który zawiera bibliotekę typów, na przykład plik. olb,. tlb lub. dll. Słowo kluczowe, `file:`, może poprzedzać każdą nazwę pliku.

- Identyfikator ProgID kontrolki w bibliotece typów. Słowo kluczowe, `progid:`, może poprzedzać każdy ProgID. Na przykład:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Aby uzyskać więcej informacji na temat identyfikatorów ProgID, zobacz [Określanie identyfikatora lokalizacji i numeru wersji](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   W przypadku korzystania z 32-bitowego kompilatora krzyżowego w 64-bitowym systemie operacyjnym kompilator może odczytać tylko gałąź rejestru 32-bitowego. Możesz chcieć użyć natywnego kompilatora 64-bitowego do kompilowania i rejestrowania biblioteki typów 64-bitowych.

- Identyfikator biblioteki dla biblioteki typów. Słowo kluczowe, `libid:`, może poprzedzać każdy identyfikator biblioteki. Na przykład:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Jeśli nie określisz `version` lub `lcid`, [reguły](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) zastosowane do `progid:` są również stosowane do. `libid:`

- Plik wykonywalny (. exe).

- Plik biblioteki (dll) zawierający zasób biblioteki typów (na przykład. ocx).

- Dokument złożony zawierający bibliotekę typów.

- Każdy inny format pliku, który może być zrozumiały dla interfejsu API **LoadTypeLib** .

*Attributes*\
Jeden lub więcej [atrybutów #import](#_predir_the_23import_directive_import_attributes). Oddziel atrybuty spacją lub przecinkiem. Przykład:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-oraz

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Uwagi

### <a name="_predir_the_23import_directive_searchorderforfilename"></a>Kolejność wyszukiwania dla nazwy pliku

*Nazwa pliku* jest opcjonalnie poprzedzona specyfikacją katalogu. Nazwa pliku musi mieć nazwę istniejącego pliku. Różnica między dwoma formularzami składni polega na kolejności, w której preprocesor wyszukuje pliki biblioteki typów, gdy ścieżka jest nieukończona.

|Formularz składni|Akcja|
|-----------------|------------|
|Formularz w cudzysłowie|Nakazuje preprocesorowi wyszukanie plików biblioteki typów najpierw w katalogu pliku, który zawiera instrukcję **#import** , a następnie w katalogach dowolnego pliku (`#include`). Preprocesor przeszukuje następnie pokazane poniżej ścieżki.|
|Formularz z nawiasami ostrymi|Nakazuje preprocesorowi wyszukanie plików biblioteki typów w następujących ścieżkach:<br /><br /> 1.  Lista ścieżek zmiennych środowiskowych `PATH`<br />2.  Lista ścieżek zmiennych środowiskowych `LIB`<br />3.  Ścieżka określona przez opcję kompilatora [/i](../build/reference/i-additional-include-directories.md) , z wyjątkiem tego, że kompilator wyszukuje bibliotekę typów, do której odwołuje się inna biblioteka typów z atrybutem [no_registry](../preprocessor/no-registry.md) .|

### <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Określ identyfikator lokalizacji i numer wersji

Podczas określania identyfikatora ProgID można także określić identyfikator lokalizacji i numer wersji ProgID. Na przykład:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Jeśli nie określisz identyfikatora lokalizacji, zostanie wybrany identyfikator ProgID zgodnie z następującymi regułami:

- Jeśli istnieje tylko jeden identyfikator lokalizacji, jest on używany.

- Jeśli istnieje więcej niż jeden identyfikator lokalizacji, zostanie użyta pierwsza z nich z numerem wersji 0, 9 lub 409.

- Jeśli istnieje więcej niż jeden identyfikator lokalizacji i żadna z nich nie jest równa 0, 9 lub 409, zostanie użyta Ostatnia z nich.

- Jeśli nie określisz numeru wersji, używana jest Najnowsza wersja.

###  <a name="_predir_the_23import_directive_header_files_created_by_import"></a>Pliki nagłówkowe utworzone przez import

**#import** tworzy dwa pliki nagłówkowe, które odtworzą zawartość biblioteki typów w C++ kodzie źródłowym. Podstawowy plik nagłówkowy jest podobny do tego utworzonego przez kompilator Microsoft Interface Definition Language (MIDL), ale z dodatkowym, generowanym przez kompilator kodem i danymi. [Podstawowy plik nagłówkowy](#_predir_the_primary_type_library_header_file) ma taką samą nazwę bazową jak biblioteka typów i. Rozszerzenie TLH. Pomocniczy plik nagłówkowy ma taką samą nazwę bazową jak biblioteka typów, z. Rozszerzenie TLI. Zawiera implementacje dla funkcji składowych generowanych przez kompilator i jest dołączony (`#include`) w podstawowym pliku nagłówkowym.

W przypadku importowania właściwości dispinterface, która `byref` używa parametrów, **#import** nie generuje instrukcji [__declspec (Property)](../cpp/property-cpp.md) dla funkcji.

Oba pliki nagłówkowe są umieszczane w katalogu wyjściowym określonym przez opcję [/FO (Name Object File)](../build/reference/fo-object-file-name.md) . Są one następnie odczytywane i kompilowane przez kompilator, tak jakby podstawowy plik nagłówkowy miał nazwę `#include` dyrektywy.

Następujące optymalizacje kompilatora pochodzą z **#import** dyrektywie:

- Plik nagłówkowy, po utworzeniu, ma taką samą sygnaturę czasową jak biblioteka typów.

- Podczas przetwarzania **#import** , kompilator najpierw sprawdza, czy nagłówek istnieje i jest aktualny. Jeśli tak, nie trzeba go ponownie tworzyć.

Dyrektywa **#import** również uczestniczy w minimalnej kompilacji i można ją umieścić w prekompilowanym pliku nagłówkowym.  Aby uzyskać więcej informacji, zobacz [Tworzenie prekompilowanych plików nagłówkowych](../build/creating-precompiled-header-files.md).

### <a name="_predir_the_primary_type_library_header_file"></a>Podstawowy plik nagłówka biblioteki typów

Podstawowy plik nagłówka biblioteki typów składa się z siedmiu sekcji:

- Styl standardowy: Składa się z `#include` komentarzy, instrukcji dla comdef. H (która definiuje niektóre standardowe makra używane w nagłówku) i inne informacje o różnych konfiguracjach.

- Przekazanie do przodu i definicje typów: Składa się z deklaracji struktury `struct IMyInterface` , takich jak i Typedefs.

- Deklaracje inteligentnego wskaźnika: Klasa `_com_ptr_t` szablonu jest inteligentnym wskaźnikiem. Hermetyzuje on wskaźniki interfejsu i eliminuje konieczność wywołania `AddRef`, `Release`, i `QueryInterface` funkcji. Powoduje także ukrycie `CoCreateInstance` wywołania podczas tworzenia nowego obiektu com. Ta sekcja używa instrukcji `_COM_SMARTPTR_TYPEDEF` makra do ustalenia elementów typedef interfejsów COM jako specjalizacji szablonu klasy szablonu [_com_ptr_t](../cpp/com-ptr-t-class.md) . Na przykład dla interfejsu `IMyInterface`,. Plik TLH będzie zawierać:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   do którego kompilatora zostanie rozwinięty:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Typ `IMyInterfacePtr` może być następnie użyty zamiast wskaźnika `IMyInterface*`interfejsu RAW. W związku z tym nie ma potrzeby wywoływania różnych `IUnknown` funkcji składowych

- Deklaracje "element": Przede wszystkim składają się z definicji klas i innych elementów, które uwidaczniają `ITypeLib:GetTypeInfo`poszczególne elementy elementu WebItems zwrócone przez. W tej sekcji wszystkie elementy informacyjne z biblioteki typów są odzwierciedlone w nagłówku formularza zależnie `TYPEKIND` od informacji.

- Opcjonalna Definicja identyfikatora GUID starego stylu: Zawiera inicjalizacje nazwanych stałych identyfikatora GUID. Te nazwy mają postać `CLSID_CoClass` i `IID_Interface`, podobnie jak te wygenerowane przez kompilator MIDL.

- `#include`Instrukcja dla nagłówka biblioteki typów pomocniczych.

- Standardowa stopka: Obecnie zawiera `#pragma pack(pop)`.

Wszystkie sekcje, z wyjątkiem standardowa sekcja i Standardowa stopka, są ujęte w przestrzeni nazw z nazwą określoną przez `library` instrukcję w oryginalnym pliku IDL. Można użyć nazw z nagłówka biblioteki typów według jawnej kwalifikacji przy użyciu nazwy przestrzeni nazw. Lub można uwzględnić następujące instrukcje:

```cpp
using namespace MyLib;
```

bezpośrednio po instrukcji **#import** w kodzie źródłowym.

Przestrzeń nazw można pominąć przy użyciu atrybutu [no_namespace](no-namespace.md)) dyrektywy **#import** . Pomijanie przestrzeni nazw może jednak prowadzić do kolizji nazw. Nazwa przestrzeni nazw może również być zmieniona przez atrybut [rename_namespace](rename-namespace.md) .

Kompilator zapewnia pełną ścieżkę do dowolnej zależności biblioteki typów, która jest wymagana przez bibliotekę typów, która jest aktualnie przetwarzana. Ścieżka jest zapisywana w formie komentarzy do nagłówka biblioteki typów (. TLH), które kompilator generuje dla każdej przetworzonej biblioteki typów.

Jeśli biblioteka typów zawiera odwołania do typów zdefiniowanych w innych bibliotekach typów, a następnie. Plik TLH będzie zawierać komentarze do następującego sortowania:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Rzeczywista nazwa pliku w komentarzu **#import** jest pełną ścieżką biblioteki typów, do której istnieje odwołanie, jako przechowywane w rejestrze. Jeśli wystąpią błędy, które są spowodowane brakującymi definicjami typów, sprawdź komentarze w nagłówku. TLH, aby zobaczyć, które zależne biblioteki typów mogą wymagać zaimportowania jako pierwsze. Przyczyną błędów są błędy składniowe (na przykład C2143, C2146, C2321), C2501 (brakujące specyfikatory decl) lub C2433 ("inline" jest niedozwolone w deklaracji danych) podczas kompilowania. Plik TLI.

Aby rozwiązać problemy z zależnościami, ustal, które z komentarzy dotyczących zależności nie są udostępniane przez nagłówki systemowe, a następnie podaj **#import** dyrektywę w pewnym momencie przed dyrektywą **#import** biblioteki typów zależnych.

### <a name="_predir_the_23import_directive_import_attributes"></a>Atrybuty #import

**#import** opcjonalnie może zawierać co najmniej jeden atrybut. Te atrybuty informują kompilator, aby zmodyfikował zawartość nagłówków biblioteki typów. Symbol ukośnika odwrotnego ( **\\** ) może służyć do dołączania dodatkowych wierszy w pojedynczej instrukcji **#import** . Na przykład:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Aby uzyskać więcej informacji, zobacz [#import atrybuty](../preprocessor/hash-import-attributes-cpp.md).

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)\
[Obsługa kompilatora COM](../cpp/compiler-com-support.md)
