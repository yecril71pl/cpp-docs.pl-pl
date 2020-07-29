---
title: Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows
ms.date: 10/12/2018
ms.topic: overview
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: aa6e5d1ea7d1bc2d7ebfaf07c7c9f808b37e9804
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219771"
---
# <a name="component-extensions-for-net-and-uwp"></a>Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows

Standard C++ umożliwia dostawcom kompilatora udostępnianie niestandardowych rozszerzeń w języku. Firma Microsoft udostępnia rozszerzenia ułatwiające łączenie natywnego kodu C++ z kodem, który jest uruchamiany na .NET Framework lub platforma uniwersalna systemu Windows (platformy UWP). Rozszerzenia platformy .NET są nazywane C++/CLI i tworzą kod, który jest wykonywany w środowisku wykonawczym środowiska uruchomieniowego platformy .NET, który jest nazywany CLR. Rozszerzenia platformy UWP są nazywane C++/CX i tworzą natywny kod maszynowy.

> [!NOTE]
> W przypadku nowych aplikacji zalecamy użycie języka C++/WinRT zamiast języka C++/CX. C++/WinRT to nowy, standardowy język C++ 17 przeznaczony do środowisko wykonawcze systemu Windows interfejsów API. Będziemy nadal obsługiwać C++/CX i WRL, ale zdecydowanie zaleca się, aby nowe aplikacje korzystały z języka C++/WinRT. Aby uzyskać więcej informacji, zobacz [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Dwa środowiska uruchomieniowe, jeden zestaw rozszerzeń

C++/CLI rozszerza standard ISO/ANSI C++ i jest zdefiniowany w standardzie ECMA C++/CLI. Aby uzyskać więcej informacji, zobacz [programowanie .NET przy użyciu języka C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Rozszerzenia C++/CX są podzbiorem języka C++/CLI. Chociaż składnia rozszerzenia jest identyczna w większości przypadków, generowany kod zależy od tego, czy określono `/ZW` opcję kompilatora docelową platformy UWP, czy też `/clr` opcję docelową platformy .NET. Te przełączniki są ustawiane automatycznie w przypadku tworzenia projektu przy użyciu programu Visual Studio.

## <a name="data-type-keywords"></a>Słowa kluczowe typu danych

Rozszerzenia języka obejmują *zagregowane słowa kluczowe*, które składają się z dwóch tokenów oddzielonych znakami odstępu. Tokeny mogą mieć jedno znaczenie, gdy są używane oddzielnie, i inne znaczenie, gdy są używane razem. Na przykład słowo "ref" jest zwykłym identyfikatorem, a słowo "Class" jest słowem kluczowym, które deklaruje klasę natywną. Ale jeśli te wyrazy są połączone z **klasą ref**, to uzyskane słowo kluczowe Aggregate deklaruje jednostkę, która jest znana jako *Klasa środowiska uruchomieniowego*.

Rozszerzenia zawierają również *kontekstowe* słowa kluczowe. Słowo kluczowe jest traktowane jako kontekstowe, w zależności od rodzaju instrukcji zawierającej ją, i jej umieszczenia w tej instrukcji. Na przykład token "Property" może być identyfikatorem lub może deklarować specjalny rodzaj składowej klasy publicznej.

Poniższa tabela zawiera listę słów kluczowych w rozszerzeniu języka C++.

|Słowo kluczowe|Kontekstowe|Przeznaczenie|Dokumentacja|
|-------------|-----------------------|-------------|---------------|
|**ref — Klasa**<br /><br /> **ref — struktura**|Nie|Deklaruje klasę.|[Klasy i struktury](classes-and-structs-cpp-component-extensions.md)|
|**Klasa wartości**<br /><br /> **Struktura wartości**|Nie|Deklaruje klasę wartości.|[Klasy i struktury](classes-and-structs-cpp-component-extensions.md)|
|**interface, klasa**<br /><br /> **Struktura interfejsu**|Nie|Deklaruje interfejs.|[interface, klasa](interface-class-cpp-component-extensions.md)|
|**enum, klasa**<br /><br /> **Wyliczenie — struktura**|Nie|Deklaruje Wyliczenie.|[enum, klasa](enum-class-cpp-component-extensions.md)|
|**`property`**|Tak|Deklaruje właściwość.|[wartość](property-cpp-component-extensions.md)|
|**Wierz**|Tak|Deklaruje delegata.|[delegat  (C++/CLI i C++/CX)](delegate-cpp-component-extensions.md)|
|**wydarzen**|Tak|Deklaruje zdarzenie.|[wydarzen](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Specyfikatory zastąpienia

Możesz użyć następujących słów kluczowych, aby zakwalifikować zachowanie przesłaniania dla celów pochodnych. Chociaż **`new`** słowo kluczowe nie jest rozszerzeniem języka C++, jest wyświetlane w tym miejscu, ponieważ może być używane w dodatkowym kontekście. Niektóre specyfikatory są również prawidłowe dla programowania natywnego. Aby uzyskać więcej informacji, zobacz [jak: deklarowanie specyfikatorów przesłonięć w kompilacjach natywnych (C++/CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Słowo kluczowe|Kontekstowe|Przeznaczenie|Dokumentacja|
|-------------|-----------------------|-------------|---------------|
|**streszczeń**|Tak|Wskazuje, że funkcje lub klasy są abstrakcyjne.|[streszczeń](abstract-cpp-component-extensions.md)|
|**`new`**|Nie|Wskazuje, że funkcja nie jest przesłonięciem wersji klasy bazowej.|[new (nowe gniazdo w vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Tak|Wskazuje, że metoda musi być przesłonięciem wersji klasy bazowej.|[override](override-cpp-component-extensions.md)|
|**sealed**|Tak|Zapobiega używaniu klas jako klas bazowych.|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Słowa kluczowe dla typów ogólnych

Dodano następujące słowa kluczowe do obsługi typów ogólnych. Aby uzyskać więcej informacji, zobacz [Ogólne](generics-cpp-component-extensions.md).

|Słowo kluczowe|Kontekstowe|Przeznaczenie|
|-------------|-----------------------|-------------|
|**ogólnego**|Nie|Deklaruje typ ogólny.|
|**miejscu**|Tak|Określa ograniczenia, które są stosowane do parametru typu ogólnego.|

## <a name="miscellaneous-keywords"></a>Różne słowa kluczowe

Do rozszerzeń języka C++ dodano następujące słowa kluczowe.

|Słowo kluczowe|Kontekstowe|Przeznaczenie|Dokumentacja|
|-------------|-----------------------|-------------|---------------|
|**finally**|Tak|Wskazuje domyślne zachowanie obsługi wyjątków.|[Obsługa wyjątków](exception-handling-cpp-component-extensions.md)|
|**for each, in**|Nie|Wylicza elementy kolekcji.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|Nie|Przydziela typy na stosie zebranych elementów bezużytecznych. Użyj zamiast **`new`** i **`delete`** .|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**nowe odwołania**|Tak|Przypisuje typ środowisko wykonawcze systemu Windows. Użyj zamiast **`new`** i **`delete`** .|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Tak|Wskazuje, że element członkowski może być zainicjowany tylko w deklaracji lub w konstruktorze statycznym.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**wpisać**|Tak|Tworzy zmienną literału.|[wpisać](literal-cpp-component-extensions.md)|
|**`nullptr`**|Nie|Oznacza, że uchwyt lub wskaźnik nie wskazuje na obiekt.|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Konstrukcje szablonu

Poniższe konstrukcje języka są implementowane jako szablony, a nie słowa kluczowe. Jeśli określisz `/ZW` opcję kompilatora, są one zdefiniowane w `lang` przestrzeni nazw. Jeśli określisz `/clr` opcję kompilatora, są one zdefiniowane w `cli` przestrzeni nazw.

|Słowo kluczowe|Przeznaczenie|Dokumentacja|
|-------------|-------------|---------------|
|**array**|Deklaruje tablicę.|[Macierze](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(Tylko CLR) Wskazuje dane w typie referencyjnym.|[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(Tylko CLR) Wskazuje typy odwołań CLR do tymczasowego pomijania systemu odzyskiwania pamięci.|[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|Określa i wykonuje metodę optymalnego rzutowania dla typu środowiska uruchomieniowego.|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**`typeid`**|(Tylko CLR) Pobiera <xref:System.Type?displayProperty=fullName> obiekt, który opisuje dany typ lub obiekt.|[typeid](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Deklaratory

Następujący typ Deklaratory powoduje, że środowisko uruchomieniowe automatycznie zarządza okresem istnienia i usuwaniem przyznanych obiektów.

|Operator|Przeznaczenie|Dokumentacja|
|--------------|-------------|---------------|
|`^`|Deklaruje dojście do obiektu; oznacza to, że wskaźnik do środowisko wykonawcze systemu Windows lub obiektu CLR, który jest automatycznie usuwany, gdy nie będzie już można go używać.|[Operator uchwytu do obiektu (^)](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Deklaruje odwołanie śledzenia; oznacza to odwołanie do środowisko wykonawcze systemu Windows lub obiektu CLR, który jest automatycznie usuwany, gdy nie będzie już można go używać.|[Operator odwołania śledzenia](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Dodatkowe konstrukcje i Tematy pokrewne

Ta sekcja zawiera listę dodatkowych konstrukcji programistycznych i tematów odnoszących się do środowiska CLR.

|Temat|Opis|
|-----------|-----------------|
|[__identifier (C++/CLI)](identifier-cpp-cli.md)|(Środowisko wykonawcze systemu Windows i CLR) Umożliwia używanie słów kluczowych jako identyfikatorów.|
|[Listy zmiennych argumentów (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Środowisko wykonawcze systemu Windows i CLR) Włącza funkcję, aby przyjmować zmienną liczbę argumentów.|
|[Odpowiedniki typów natywnych języka C++ w programie .NET Framework (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Wyświetla listę typów CLR, które są używane zamiast typów całkowitych języka C++.|
|[domena aplikacji](../cpp/appdomain.md) **`__declspec`** modyfikator|**`__declspec`** modyfikator, który jest upoważniony do istnienia zmiennych statycznych i globalnych na domenę aplikacji.|
|[Rzutowania w stylu C i kompilator /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)|Opisuje, jak są interpretowane rzutowania w stylu języka C.|
|[__clrcall](../cpp/clrcall.md) konwencji wywoływania|Wskazuje konwencję wywoływania zgodną ze środowiskiem CLR.|
|`__cplusplus_cli`|[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)|
|[Atrybuty niestandardowe](user-defined-attributes-cpp-component-extensions.md)|Opisuje sposób definiowania własnych atrybutów CLR.|
|[Obsługa wyjątków](exception-handling-cpp-component-extensions.md)|Zawiera omówienie obsługi wyjątków.|
|[Jawne zastąpienia](explicit-overrides-cpp-component-extensions.md)|Pokazuje, jak funkcje Członkowskie mogą przesłaniać dowolnych członków.|
|[Zaprzyjaźnione zestawy (C++)](../dotnet/friend-assemblies-cpp.md)|W tym artykule omówiono sposób, w jaki zestaw klienta może uzyskać dostęp do wszystkich typów w składniku zestawu.|
|[Boxing](boxing-cpp-component-extensions.md)|Pokazuje warunki, w których typy wartości są opakowane.|
|[Obsługa kompilatora dla cech typu](compiler-support-for-type-traits-cpp-component-extensions.md)|Omawia sposób wykrywania właściwości typów w czasie kompilacji.|
|[zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) dyrektywy pragma|Pokazuje, jak funkcje zarządzane i niezarządzane mogą współistnieć w tym samym module.|
|[proces](../cpp/process.md) **`__declspec`** modyfikator|**`__declspec`** modyfikator, który zezwala na istnienie zmiennych statycznych i globalnych na proces.|
|[Odbicie (C++/CLI)](../dotnet/reflection-cpp-cli.md)|Pokazuje wersję środowiska CLR informacji o typie czasu wykonywania.|
|[Ciąg](string-cpp-component-extensions.md)|Omawia konwersję kompilatora literałów ciągów do <xref:System.String> .|
|[Przekazywanie dalej typu (C++/CLI)](type-forwarding-cpp-cli.md)|Umożliwia przenoszenie typu w zestawie wysyłkowym do innego zestawu, dzięki czemu kod klienta nie musi być ponownie kompilowany.|
|[Atrybuty zdefiniowane przez użytkownika](user-defined-attributes-cpp-component-extensions.md)|Pokazuje zdefiniowane przez użytkownika atrybuty.|
|[#using — dyrektywa](../preprocessor/hash-using-directive-cpp.md)|Importuje zestawy zewnętrzne.|
|[Dokumentacja XML](../build/reference/xml-documentation-visual-cpp.md)|Objaśnia dokumentację kodu opartą na języku XML za pomocą [/doc (Przetwarzaj komentarze dokumentacji) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
