---
title: System typów (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: f4a6ea32681ad033b5db9451682c764f0a6d8959
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404629"
---
# <a name="type-system-ccx"></a>System typów (C++/CX)

Korzystając z architektury środowisko wykonawcze systemu Windows, można używać C++/CX, Visual Basic, Visual C# i JavaScript do pisania aplikacji i składników, które bezpośrednio uzyskują dostęp do interfejsu API systemu Windows i współdziałają z innymi środowisko wykonawcze systemu Windows aplikacjami i składnikami. Platforma uniwersalna systemu Windows aplikacje, które są zapisywane w języku C++ Kompiluj do kodu natywnego, który jest wykonywany bezpośrednio w procesorze CPU. Platforma uniwersalna systemu Windows aplikacje, które są zapisywane w języku C# lub Visual Basic kompilują do języka pośredniego firmy Microsoft (MSIL) i wykonują w środowisku uruchomieniowym języka wspólnego (CLR). Platforma uniwersalna systemu Windows aplikacje, które są zapisywane w języku JavaScript, są wykonywane w środowisku wykonawczym. Środowisko wykonawcze systemu Windows składniki systemu operacyjnego są zapisywane w języku C++ i uruchamiane jako kod natywny. Wszystkie te składniki i platforma uniwersalna systemu Windows aplikacje komunikują się bezpośrednio za pomocą interfejsu środowisko wykonawcze systemu Windows aplikacji binarnej (ABI).

Aby włączyć obsługę środowisko wykonawcze systemu Windows w nowoczesnej C++ idiom, firma Microsoft utworzyła C++/CX. C++/CX udostępnia wbudowane typy podstawowe i implementacje podstawowych typów środowisko wykonawcze systemu Windows, które umożliwiają aplikacjom i składnikom C++ komunikowanie się w ABI z aplikacjami, które są zapisywane w innych językach. Można użyć dowolnego typu środowisko wykonawcze systemu Windows lub tworzyć klasy, struktury, interfejsy i inne typy zdefiniowane przez użytkownika, które mogą być używane przez inne platforma uniwersalna systemu Windows aplikacje i składniki. Aplikacja platforma uniwersalna systemu Windows, która jest zapisywana w języku C++/CX, może również używać zwykłych klas i struktur języka C++, o ile nie mają publicznego ułatwienia dostępu.

Szczegółowe omówienie projekcji języka C++/CX i sposobu jej działania w ramach okładek można znaleźć w następujących wpisach w blogu:

- [C++/CX — część 0 z \[ n \] : wprowadzenie](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)

- [C++/CX część 1 z \[ n \] : prosta Klasa](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)

- [C++/CX — część 2 of \[ n \] : typy, które zużywają systemy](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)

- [C++/CX, część 3 z \[ n \] : w konstrukcji](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)

- [C++/CX część 4 of \[ n \] : statyczne funkcje członkowskie](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)

## <a name="windows-metadata-winmd-files"></a>Pliki metadanych systemu Windows (WinMD)

Podczas kompilowania aplikacji platforma uniwersalna systemu Windows, która jest zapisywana w języku C++, kompilator generuje plik wykonywalny w kodzie macierzystym maszynowym, a także generuje oddzielny pliku metadanych (WinMD) systemu Windows, który zawiera opisy typów publicznych środowisko wykonawcze systemu Windows, które obejmują klasy, struktury, wyliczenia, interfejsy, interfejsy sparametryzowane i delegatów. Format metadanych jest podobny do formatu, który jest używany w zestawach .NET Framework.  W składniku C++ plik. winmd zawiera tylko metadane; kod wykonywalny znajduje się w oddzielnym pliku. W tym przypadku składniki środowisko wykonawcze systemu Windows, które są dołączone do systemu Windows. Nazwa pliku WinMD musi być zgodna lub być prefiksem głównej przestrzeni nazw w kodzie źródłowym. (W przypadku języków .NET Framework plik WinMD zawiera zarówno kod, jak i metadane, tak jak w przypadku zestawu .NET Framework.)

Metadane w pliku winmd przedstawiają opublikowaną powierzchnię kodu. Opublikowane typy są widoczne dla innych platform uniwersalnych systemu Windows niezależnie od języka, w którym są zapisywane inne aplikacje. W związku z tym metadane lub Twój opublikowany kod może zawierać tylko typy określone przez system typu środowisko wykonawcze systemu Windows. Konstrukcje języka, które są specyficzne dla języka C++, takie jak regularne klasy, tablice, szablony lub kontenery STL, nie mogą być publikowane w metadanych, ponieważ aplikacja kliencka JavaScript lub C# nie wie, co należy zrobić z nimi.

Określa, czy typ lub metoda jest widoczna w metadanych, zależy od tego, jakie Modyfikatory dostępności są do niego stosowane. Aby były widoczne, typ musi być zadeklarowany w przestrzeni nazw i musi być zadeklarowany jako publiczny. Niepubliczna Klasa ref jest dozwolona jako wewnętrzny typ pomocnika w kodzie; nie jest on widoczny w metadanych. Nawet w publicznej klasie ref nie wszystkie składowe są zawsze widoczne. W poniższej tabeli wymieniono relacje między specyfikatorami dostępu C++ w publicznej klasie referencyjnej i środowisko wykonawcze systemu Windows widoczność metadanych:

|||
|-|-|
|**Opublikowano w metadanych**|**Nie opublikowano w metadanych**|
|public|private|
|protected|internal|
|chroniona publiczna|private protected|

Możesz użyć **Przeglądarka obiektów** , aby wyświetlić zawartość plików WinMD. Składniki środowisko wykonawcze systemu Windows dołączone do systemu Windows znajdują się w pliku winmd systemu Windows. Domyślny plik. winmd zawiera podstawowe typy, które są używane w języku C++/CX, a platforma. winmd zawiera dodatkowe typy z przestrzeni nazw platformy. Domyślnie te trzy pliki winmd są zawarte w każdym projekcie C++ dla aplikacji platforma uniwersalna systemu Windows.

> [!TIP]
> Typy w [przestrzeni nazw platform:: Collections](../cppcx/platform-collections-namespace.md) nie są wyświetlane w pliku winmd, ponieważ nie są one publiczne. Są to prywatne implementacje specyficzne dla języka C++ dotyczące interfejsów, które są zdefiniowane w systemie `Windows::Foundation::Collections` . Aplikacja środowisko wykonawcze systemu Windows, która jest zapisywana w języku JavaScript lub C#, nie wie, co jest [Klasa platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) , ale może zużywać `Windows::Foundation::Collections::IVector` . `Platform::Collections`Typy są zdefiniowane w kolekcji. h.

## <a name="windows-runtime-type-system-in-ccx"></a>System typów środowisko wykonawcze systemu Windows w języku C++/CX

W poniższych sekcjach opisano główne funkcje systemu typu środowisko wykonawcze systemu Windows i sposób ich obsługi w języku C++/CX.

### <a name="namespaces"></a>Namespaces

Wszystkie typy środowisko wykonawcze systemu Windows muszą być zadeklarowane w przestrzeni nazw; sam interfejs API systemu Windows jest zorganizowany według przestrzeni nazw. Plik. winmd musi mieć taką samą nazwę, która ma główną przestrzeń nazw. Na przykład Klasa o nazwie A. B. C. MyClass można utworzyć wystąpienie tylko wtedy, gdy jest zdefiniowana w pliku metadanych o nazwie A. winmd lub A. B. winmd lub A. B. winmd. Nazwa biblioteki DLL nie jest wymagana, aby odpowiadała nazwie pliku winmd.

Sam interfejs API systemu Windows został przestawiony jako wydajna Biblioteka klas uporządkowana według przestrzeni nazw.  Wszystkie składniki środowisko wykonawcze systemu Windows są zadeklarowane w przestrzeniach nazw Windows. *.

Aby uzyskać więcej informacji, zobacz [przestrzenie nazw i widoczność typów](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="fundamental-types"></a>Typy podstawowe

Środowisko wykonawcze systemu Windows definiuje następujące podstawowe typy: UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, Double, Char16, Boolean i String. C++/CX obsługuje podstawowe typy liczbowe w swojej domyślnej przestrzeni nazw jako UInt16, UInt32, UInt64, Int16, Int32, Int64, float32, Float64 i char16. Wartość logiczna i ciąg są również zdefiniowane w przestrzeni nazw platformy.

C++/CX definiuje również Uint8, równoważne z `unsigned char` , co nie jest obsługiwane w środowisko wykonawcze systemu Windows i nie może być używane w publicznych interfejsach API.

Typ podstawowy może dopuszczać wartość null przez zapakowanie go w interfejsie interfejsu [:: IBox](../cppcx/platform-ibox-interface.md) . Aby uzyskać więcej informacji, zobacz [klasy wartości i struktury](../cppcx/value-classes-and-structs-c-cx.md).

Aby uzyskać więcej informacji na temat typów podstawowych, zobacz [podstawowe typy](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>Ciągi

Ciąg środowisko wykonawcze systemu Windows jest niezmiennym sekwencją 16-bitowych znaków UNICODE. Ciąg środowisko wykonawcze systemu Windows jest rzutowany jako `Platform::String^` . Ta klasa udostępnia metody tworzenia ciągów, manipulowania i konwersji do i z `wchar_t` .

Aby uzyskać więcej informacji, zobacz [ciągi](../cppcx/strings-c-cx.md).

### <a name="arrays"></a>Tablice

Środowisko wykonawcze systemu Windows obsługuje tablice jednowymiarowe dowolnego typu. Tablice tablic nie są obsługiwane.  W języku C++/CX tablice środowisko wykonawcze systemu Windows są rzutowane jako [Klasa platform:: Array](../cppcx/platform-array-class.md).

Aby uzyskać więcej informacji, zobacz [Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Klasy i struktury odwołania

Klasa środowisko wykonawcze systemu Windows jest rzutowana w języku C++/CX jako Klasa referencyjna lub struktura ref, ponieważ są one kopiowane przez odwołanie. Zarządzanie pamięcią dla klas referencyjnych i struktur ref jest obsługiwane w sposób niewidoczny przy użyciu zliczania odwołań. Gdy ostatnie odwołanie do obiektu wykracza poza zakres, obiekt zostanie zniszczony. Klasa ref lub ref struct mogą:

- Zawierają jako konstruktory elementów członkowskich, metody, właściwości i zdarzenia. Ci członkowie mogą mieć dostęp publiczny, prywatny, chroniony lub wewnętrzny.

- Może zawierać prywatne zagnieżdżone definicje wyliczeniowe, struktury lub klas.

- Może dziedziczyć bezpośrednio z jednej klasy bazowej i może implementować dowolną liczbę interfejsów. Wszystkie klasy referencyjne są niejawnie konwertowane na [klasę platform:: Object](../cppcx/platform-object-class.md) i mogą przesłonić swoje metody wirtualne — na przykład [Object:: ToString](../cppcx/platform-object-class.md#tostring).

Klasa referencyjna, która ma Konstruktor publiczny, musi być zadeklarowana jako Sealed, aby zapobiec dalszemu wywodzeniu.

Aby uzyskać więcej informacji, zobacz [klasy referencyjne i struktury](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>Klasy i struktury wartości

Klasa wartości lub struktura wartości reprezentuje podstawową strukturę danych i zawiera tylko pola, które mogą być klasami wartości, strukturami wartości lub typem `Platform::String^` .  Struktury wartości i klasy wartości są kopiowane przez wartość.

Strukturę wartości można wprowadzać do wartości null poprzez Zawijanie w interfejsie IBox.

Aby uzyskać więcej informacji, zobacz [klasy wartości i struktury](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="partial-classes"></a>Klasy częściowe

Funkcja klasy częściowej umożliwia zdefiniowanie jednej klasy na wielu plikach. Służy on głównie do włączania narzędzi do generowania kodu, takich jak Edytor XAML, aby zmodyfikować jeden plik bez dotykania edytowanego pliku.

Aby uzyskać więcej informacji, zobacz [klasy częściowe](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>Właściwości

Właściwość jest publiczną składową danych dowolnego typu środowisko wykonawcze systemu Windows i jest zaimplementowana jako para metod get/set. Kod klienta uzyskuje dostęp do właściwości tak, jakby była polem publicznym. Właściwość, która nie wymaga niestandardowego kodu get lub Set, jest znana jako *Właściwość prosta* i może być zadeklarowana bez jawnych metod get lub Set.

Aby uzyskać więcej informacji, zobacz [Właściwości](../cppcx/properties-c-cx.md).

### <a name="windows-runtime-collections-in-ccx"></a>Kolekcje środowisko wykonawcze systemu Windows w języku C++/CX

Środowisko wykonawcze systemu Windows definiuje zestaw interfejsów dla typów kolekcji, które każdy język implementuje we własnym zakresie. C++/CX udostępnia implementacje w klasie [platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md), [platform:: Collections:: map](../cppcx/platform-collections-map-class.md)i innych powiązanych typach kolekcji, które są zgodne ze swoimi odpowiednikami biblioteki standardowych szablonów (STL).

Aby uzyskać więcej informacji, zobacz [kolekcje](../cppcx/collections-c-cx.md).

### <a name="template-ref-classes"></a>Klasy odwołania szablonu

Prywatne i wewnętrzne klasy referencyjne mogą być szablonowe i wyspecjalizowane.

Aby uzyskać więcej informacji, zobacz [Template ref Classes](../cppcx/template-ref-classes-c-cx.md).

### <a name="interfaces"></a>Interfejsy

Interfejs środowisko wykonawcze systemu Windows definiuje zestaw właściwości publicznych, metod i zdarzeń, które Klasa referencyjna lub struktura ref muszą implementować, jeśli dziedziczy z interfejsu.

Aby uzyskać więcej informacji, zobacz [interfejsy](../cppcx/interfaces-c-cx.md).

### <a name="enums"></a>Wyliczenia

Klasa enum w środowisko wykonawcze systemu Windows przypomina Wyliczenie w zakresie z zakresem w języku C++. Typ podstawowy to Int32, chyba że jest stosowany atrybut [flags] — w takim przypadku typem podstawowym jest UInt32.

Aby uzyskać więcej informacji, zobacz [wyliczenia](../cppcx/enums-c-cx.md).

### <a name="delegates"></a>Delegaty

Delegat w środowisko wykonawcze systemu Windows jest analogiczny do obiektu std:: Function w języku C++. Jest to specjalny rodzaj klasy referencyjnej, który służy do wywoływania funkcji udostępnianych przez klienta, które mają zgodne podpisy.  Delegaty są najczęściej używane w środowisko wykonawcze systemu Windows jako typ zdarzenia.

Aby uzyskać więcej informacji, zobacz [delegats](../cppcx/delegates-c-cx.md).

### <a name="exceptions"></a>Wyjątki

W języku C++/CX można przechwytywać niestandardowe typy wyjątków, [std:: typy wyjątków](../standard-library/exception-class.md) i [platform::](../cppcx/platform-exception-class.md) Types.

Aby uzyskać więcej informacji, zobacz [wyjątki](../cppcx/exceptions-c-cx.md).

### <a name="events"></a>Zdarzenia

Zdarzenie to publiczny element członkowski w klasie ref lub ref struct, którego typem jest typ delegata. Zdarzenie może zostać wywołane — to znaczy, zostało wyzwolone przez klasę będącą właścicielem. Jednak kod klienta może udostępniać własne funkcje, które są znane jako programy obsługi zdarzeń i są wywoływane, gdy klasa będąca właścicielem wyzwala zdarzenie.

Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).

### <a name="casting"></a>Rzutowanie

C++/CX obsługuje Operatory rzutowania standardowego języka C++ [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md)i [reinterpret_cast](../cpp/reinterpret-cast-operator.md), a także operator **Safe_cast** , który jest specyficzny dla języka C++/CX.

Aby uzyskać więcej informacji, zobacz [rzutowanie](../cppcx/casting-c-cx.md).

### <a name="boxing"></a>Boxing

Zmienna opakowana jest typem wartości, który jest opakowany w typ referencyjny w sytuacjach, gdy wymagana jest semantyka odwołania.

Aby uzyskać więcej informacji, zobacz [opakowanie](../cppcx/boxing-c-cx.md).

### <a name="attributes"></a>Atrybuty

Atrybut jest wartością metadanych, którą można zastosować do dowolnego typu środowisko wykonawcze systemu Windows lub elementu członkowskiego typu i można ją sprawdzić w czasie wykonywania. Środowisko wykonawcze systemu Windows definiuje zestaw wspólnych atrybutów w `Windows::Foundation::Metadata` przestrzeni nazw. Zdefiniowane przez użytkownika atrybuty interfejsów publicznych nie są obsługiwane przez środowisko wykonawcze systemu Windows w tej wersji.

## <a name="api-deprecation"></a>Przestarzałe interfejsy API

Opisuje sposób oznaczania publicznych interfejsów API jako przestarzałych przy użyciu tego samego atrybutu, który jest używany przez typy systemu środowisko wykonawcze systemu Windows.

Aby uzyskać więcej informacji, zobacz [przestarzałe typy i składowe](../cppcx/deprecating-types-and-members-c-cx.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
