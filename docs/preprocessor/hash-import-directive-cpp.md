---
title: '#Importuj dyrektywy (C++)'
ms.date: 10/18/2018
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
ms.openlocfilehash: a7dc30d3e5869e9b0f534a4769d4517a0514c144
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822629"
---
# <a name="import-directive-c"></a>#import — dyrektywa (C++)

**Określonego język C++**

Używane do przyłączania informacji z biblioteki typów. Zawartość biblioteki typów jest przekształcana na klasy C++, głównie opisujące interfejsy COM.

## <a name="syntax"></a>Składnia

```
#import "filename" [attributes]
#import <filename> [attributes]
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Określa typ biblioteki do zaimportowania. *Nazwa pliku* może być jedną z następujących czynności:

- Nazwa pliku, który zawiera biblioteki typów, na przykład pliku olb, TLB lub dll. Słowo kluczowe **pliku:**, może poprzedzać nazwę każdego pliku.

- Progid kontrolki w bibliotece typów. Słowo kluczowe **progid:**, może poprzedzać każde progid. Na przykład:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Aby uzyskać więcej informacji na temat identyfikatorów programu, zobacz [określenie Identyfikatora lokalizacji i numeru wersji](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Należy pamiętać, że podczas kompilowania z kompilatorem krzyżowym na 64-bitowym systemie operacyjnym, kompilator będzie można odczytać tylko w gałęzi rejestru 32-bitowych. Możesz chcieć użycie natywnego 64-bitowego kompilatora do skompilowania i zarejestrować bibliotekę typów 64-bitowych.

- Identyfikator biblioteki dla biblioteki typów. Słowo kluczowe **libid:**, może poprzedzać każdy identyfikator biblioteki. Na przykład:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Jeśli nie określisz wersji lub identyfikatora lcid, [reguły](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) które są stosowane do **progid:** są również stosowane do **libid:**.

- Plik wykonywalny (.exe).

- Plik biblioteki (.dll), zawierające zasób biblioteki typów (na przykład .ocx).

- Dokument złożony posiagający bibliotekę typów.

- Innym formacie pliku, który może być rozumiany przez **LoadTypeLib** interfejsu API.

*Atrybuty*<br/>
Co najmniej jeden [#import atrybutów](#_predir_the_23import_directive_import_attributes). Oddziel atrybuty spacją lub przecinkiem. Na przykład:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-lub —

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Uwagi

## <a name="_predir_the_23import_directive_searchorderforfilename"></a> Kolejność wyszukiwania nazwy pliku

*Nazwa pliku* jest opcjonalnie poprzedzona przez specyfikację katalogu. Nazwa pliku musi odnosić istniejącego pliku. Różnica między dwoma formami składni polega na kolejności, w którym preprocesor szuka plików typu biblioteki Jeśli ścieżka nie jest całkowicie określona.

|Forma składni|Akcja|
|-----------------|------------|
|Cytowany formularz|Nakazuje preprocesorowi szukać typów plików biblioteki wpierw w katalogu pliku który zawiera **#import** instrukcji, a następnie w katalogach dowolnych plików, które obejmują (`#include`) tego pliku. Preprocesor wyszukuje następnie wzdłuż ścieżek przedstawionych poniżej.|
|Formularz nawias kątowy|Nakazuje preprocesorowi wyszukiwać typy plików biblioteki wzdłuż następującej ścieżki:<br /><br /> 1.  `PATH` Lista ścieżek zmiennej środowiskowej<br />2.  `LIB` Lista ścieżek zmiennej środowiskowej<br />3.  Ścieżka określona przez /I (dodatkowe katalogi dołączenia) opcję kompilatora, z wyjątkiem sytuacji kiedy kompilator szuka biblioteki typów, przywoływany z innej biblioteki typów z [no_registry](../preprocessor/no-registry.md) atrybutu.|

##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> Określanie Identyfikatora lokalizacji i numeru wersji

Kiedy określasz progid, możesz również określić lokalizację ID i numeru wersji ProgID. Na przykład:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Jeśli nie zostanie określony identyfikator lokalizacji, identyfikator progid jest wybierany zgodnie z następującymi zasadami:

- Jeśli istnieje tylko jeden identyfikator lokalizacji, ten właśnie jest używany.

- Jeśli istnieje więcej niż jeden identyfikator lokalizacji, pierwszy z nich z numerem wersji 0, 9 lub 409 jest używany.

- Jeśli istnieje więcej niż jeden identyfikator lokalizacji, a żaden z nich nie jest 0, 9 lub 409, ostatni z nich jest używany.

- Jeśli nie określisz numeru wersji, jest używana najnowsza wersja.

##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> Pliki nagłówkowe utworzone przez Import

**#import** tworzy dwa pliki nagłówkowe, które odtwarzają zawartość biblioteki typów w kodzie źródłowym C++. Plik nagłówka podstawowego jest podobny do wytworzonego przez kompilator Microsoft Interface Definition Language (MIDL), ale z dodatkowy kod generowany przez kompilator i danych. [Główny plik nagłówka](#_predir_the_primary_type_library_header_file) ma taką samą nazwę bazy jak biblioteka typów, plus. Tlh — rozszerzenie. Plik nagłówka ma taką samą nazwę bazy jak biblioteka typów za pomocą. Rozszerzenie TLI. Zawiera implementacje dla funkcji elementów członkowskich generowanych przez kompilator i jest zawarty w (`#include`) w podstawowym pliku nagłówkowym.

W przypadku importowania właściwości dispinterface, która używa parametrów byref, #import nie wygeneruje __declspec ([właściwość](../cpp/property-cpp.md)) poufności informacji dla funkcji.

Oba pliki nagłówkowe są umieszczane w katalogu wyjściowym określonym przez opcję /Fo (nazwa pliku obiektu). Są następnie odczytywane i kompilowane przez kompilator, tak jakby główny plik nagłówka został nazwany według `#include` dyrektywy.

Następujące optymalizacje kompilatora pochodzą z **#import** dyrektywy:

- Plik nagłówkowy, podczas tworzenia otrzymuje taki sam znacznik czasu jak biblioteka typów.

- Gdy **#import** jest przetwarzany, kompilator najpierw sprawdza, czy nagłówek istnieje i jest aktualny. Jeśli tak, następnie nie musi zostać utworzony ponownie.

**#Import** dyrektywy również uczestniczy w minimalnej odbudowie i może zostać umieszczony w pliku wstępnie skompilowanego nagłówka. Zobacz [tworzenie prekompilowanych plików nagłówka](../build/creating-precompiled-header-files.md) Aby uzyskać więcej informacji.

###  <a name="_predir_the_primary_type_library_header_file"></a> Plik nagłówkowy biblioteki typu podstawowego
Plik nagłówkowy biblioteki typu podstawowego składa się z siedmiu sekcji:

- Standardowy nagłówek: Składa się z komentarzy, `#include` poufności informacji dotyczące COMDEF. Godz. (która określa niektóre standardowe makra używane w nagłówku) oraz inne informacje różne ustawienia.

- Prześlij dalej odniesienia i definicje typów: Składa się z deklaracji struktury, takich jak `struct IMyInterface` i definicje typów.

- Deklaracje sprytnego wskaźnika: Klasa szablonu `_com_ptr_t` jest implementacją sprytnego wskaźnika, który hermetyzuje wskaźniki interfejsu i eliminuje konieczność wywoływania `AddRef`, `Release`, `QueryInterface` funkcji. Ponadto, ukrywa `CoCreateInstance` wywołania podczas tworzenia nowego obiektu COM. Ten rozdział wykorzystuje makro instrukcję `_COM_SMARTPTR_TYPEDEF` Aby ustalić definicje typów interfejsów COM, które mają być specjalizacjami z [_com_ptr_t](../cpp/com-ptr-t-class.md) klasy szablonu. Na przykład w przypadku interfejsu `IMyInterface`,. Tlh — plik będzie zawierać:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   które kompilator rozszerzy do:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Typ `IMyInterfacePtr` mogą być później wykorzystany surowego wskaźnika interfejsu `IMyInterface*`. W związku z tym, istnieje nie trzeba wywoływac różnych `IUnknown` elementów członkowskich

- Deklaracje TypeInfo: Składa się głównie z definicji klas i innych elementów ukazujących indywidualne elementy typeinfo zwrócone przez `ITypeLib:GetTypeInfo`. W tej sekcji, każdy element typeinfo z biblioteki typów znajduje odzwierciedlenie w nagłówku formularza w zależności od `TYPEKIND` informacji.

- Opcjonalne definicja w starym stylu identyfikatora GUID: Zawiera inicjalizacje nazwanych stałych identyfikatora GUID. Są to nazwy w postaci `CLSID_CoClass` i `IID_Interface`, podobne do tych wygenerowanych przez kompilator MIDL.

- `#include` Instrukcja dla nagłówka biblioteki typu pomocniczego.

- Standardowe stopki: Obecnie dotyczy to `#pragma pack(pop)`.

Wszystkie sekcje, z wyjątkiem nagłówek standardowy i szablonowe sekcji stopki, są ujęte w przestrzeni nazw z jego nazwą określoną przez `library` instrukcji w oryginalnym pliku IDL. Można użyć nazw z nagłówka biblioteki typów, poprzez jawną kwalifikację z nazwą przestrzeni nazw lub umieszczając następującą instrukcję:

```cpp
using namespace MyLib;
```

natychmiast po **#import** instrukcji w kodzie źródłowym.

Przestrzeń nazw może być pominięty przy użyciu [no_namespace](#_predir_no_namespace) atrybutu **#import** dyrektywy. Jednakże pomijanie przestrzeni nazw może prowadzić do konfliktów nazw. Przestrzeń nazw również może mieć zmienionej nazwy przez [rename_namespace](#_predir_rename_namespace) atrybutu.

Kompilator zapewnia pełną ścieżkę do dowolnego typu zależności biblioteki wymaganego przez bibliotekę typu, którą aktualnie przetwarza. Ścieżka jest zapisana w formie komentarzy w nagłówku biblioteki typów (. Tlh —), kompilator generuje dla każdej przetworzonej biblioteki typów.

Jeśli biblioteka typów zawiera odwołania do typów zdefiniowanych w innych bibliotekach typu, a następnie. Tlh — plik będzie zawierać komentarze w rodzaju:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Nazwa pliku w **#import** komentarza jest pełną ścieżką biblioteki typów odsyłaczy, przechowywane w rejestrze. Jeśli wystąpią błędy, które z powodu braku definicji typu, należy sprawdzić komentarze na czele. Tlh — aby zobaczyć zależne typy bibliotek, należy najpierw zaimportować. Prawdopodobne błędy są błędami składni (na przykład, C2143, C2146, C2321), C2501 (Brak specyfikatorów decl), lub C2433 ("inline" nie jest dozwolone w deklaracji danych) podczas kompilacji. Plik TLI.

Należy określić, które zależności komentarze nie zostały inaczej dostarczone dla przez nagłówki systemu, a następnie podaj **#import** dyrektywy w pewnym momencie przed **#import** dyrektywy zależnego Wpisz biblioteki, aby naprawić błędy.

## <a name="_predir_the_23import_directive_import_attributes"></a> atrybuty #import

**#import** może opcjonalnie obejmować jeden lub więcej atrybutów. Te atrybuty każą kompilatorowi modyfikować zawartość nagłówków biblioteki typów. Ukośnik odwrotny (**\\**) symbolu można uwzględnić dodatkowe wiersze w jednym **#import** instrukcji. Na przykład:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Aby uzyskać więcej informacji, zobacz [#import atrybutów](../preprocessor/hash-import-attributes-cpp.md).

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)<br/>
[Obsługa kompilatora COM](../cpp/compiler-com-support.md)