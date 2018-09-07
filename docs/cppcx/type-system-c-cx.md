---
title: System typów (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7b9f17007c1614761f1b7872d8d421f0f5e18df
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105175"
---
# <a name="type-system-ccx"></a>System typów (C + +/ CX)

Za pomocą architektury środowiska wykonawczego Windows, można użyć C + +/ CX, Visual Basic, Visual C# i JavaScript do pisania aplikacji i składników, które bezpośrednio dostęp do interfejsu API Windows współpracować z innymi aplikacji środowiska wykonawczego Windows i składników. Aplikacje uniwersalne platformy Windows, które zostały napisane w języku C++ kompilacji do kodu macierzystego, który jest wykonywany bezpośrednio w procesorze CPU. Aplikacje uniwersalne platformy Windows, które zostały napisane w języku C# lub Visual Basic skompiluj go do języka Microsoft intermediate language (MSIL), a następnie wykonaj w środowisku uruchomieniowym języka (wspólnego CLR). Wykonywanie aplikacji uniwersalnych platformy Windows, które zostały napisane w języku JavaScript w środowisku uruchomieniowym. Składniki systemu operacyjnego Windows w czasie wykonywania, samodzielnie są napisane w języku C++ i uruchomić jako kodu natywnego. Wszystkie te składniki i aplikacje platformy uniwersalnej Windows komunikują się bezpośrednio za pomocą interfejsem binarnym aplikacji (ABI) środowiska wykonawczego Windows.

Aby włączyć obsługę środowiska wykonawczego Windows w nowoczesnych idiom języka C++, firma Microsoft utworzyła C + +/ CX. C + +/ CX udostępnia wbudowane typy podstawowe i implementacji podstawowych typów środowiska wykonawczego Windows, które umożliwiają aplikacji C++ i składników do komunikowania się za pośrednictwem interfejsu ABI z aplikacjami, które są zapisywane w innych językach. Możesz używać dowolnego typu środowiska uruchomieniowego Windows lub tworzenie klas, struktur, interfejsów i inne typy danych zdefiniowane przez użytkownika, które mogą być wykorzystane przez inne aplikacje platformy uniwersalnej Windows i składników. aplikacji Universal Windows Platform, która jest napisana w języku C + +/ CX umożliwia również regularne C++ klasy i struktury tak długo, jak nie posiadają powszechnej dostępności.

Szczegółowe omówienie C + +/ CX języka Prognoza i jak to działa w sposób niewidoczny, zobacz te Posty na blogu:

1. [C + +/ CX część 0 \[n\]: wprowadzenie](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)

1. [C + +/ CX, część 1 z \[n\]: prostą klasę](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)

1. [C + +/ CX część 2 \[n\]: typy, które systemy Wear](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)

1. [C + +/ CX część 3 \[n\]: W trakcie tworzenia](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)

1. [C + +/ CX część 4 \[n\]: statyczne funkcje Członkowskie](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)

## <a name="windows-metadata-winmd-files"></a>Pliki metadanych (.winmd) Windows

Podczas kompilowania aplikacji platformy uniwersalnej Windows, która jest napisana w języku C++, kompilator generuje plik wykonywalny w macierzystym kodzie maszynowym i również generuje oddzielny plik metadanych (.winmd) Windows, który zawiera opisy typów publicznych Windows Runtime które obejmują klasy, struktury, wyliczenia, interfejsy, sparametryzowane interfejsów i delegatów. Format metadanych jest podobny do formatu, który jest używany w zestawów .NET Framework.  W składniku C++ plik .winmd zawiera tylko metadane; kod wykonywalny znajduje się w oddzielnym pliku. Jest to wymagane dla składników środowiska wykonawczego Windows, które są dołączone do Windows. Nazwa pliku WinMD musi odpowiadać lub być prefiksem głównej przestrzeni nazw w kodzie źródłowym. (W językach .NET Framework plik .winmd zawiera kod i metadanych, podobnie jak zestaw .NET Framework).

Metadane w pliku winmd reprezentuje publikowanej powierzchni swój kod. Typy opublikowanych są widoczne dla innych uniwersalnych platform Windows niezależnie od tego, jakiego języka innych aplikacji, które są zapisywane. W związku z tym metadanych lub kodzie opublikowanych może zawierać wyłącznie typy określone przez system typów środowiska wykonawczego Windows. Nie można opublikować konstrukcji języka, które są specyficzne dla języka C++, takich jak zwykłych klas, tablic, szablony lub kontenery STL w metadanych, ponieważ aplikację kliencką Javascript i C# nie wiadomo, co należy zrobić z nimi.

Czy typ lub metoda jest widoczny w metadanych zależy od tego, jakie modyfikatory dostępności są do niego zastosowane. Były widoczne, typ musi być zadeklarowany w przestrzeni nazw i musi być zadeklarowany jako publiczny. Klasa ref niepublicznych jest dozwolona jako typu wewnętrznego pomocnika w kodzie; po prostu nie jest widoczne w metadanych. Nawet w klasie ref publiczne nie wszystkie elementy członkowskie są zawsze widoczne. W poniższej tabeli przedstawiono relację między specyfikatorów dostępu C++ w klasie ref publicznych i widoczność metadanych Windows Runtime:

|||
|-|-|
|**Publikowany w metadanych**|**Nie jest publikowany w metadanych**|
|public|private|
|protected|internal|
|public, protected|prywatny chroniony|

Możesz użyć **przeglądarki obiektów** do wyświetlania zawartości plików winmd. Składników środowiska wykonawczego Windows, które są dołączone do Windows znajdują się w pliku Windows.winmd. Plik default.winmd zawiera podstawowe typy, które są używane w języku C + +/ CX i platform.winmd zawiera dodatkowych typów z przestrzeni nazw Platform. Domyślnie te trzy pliki .winmd znajdują się w każdym projekcie C++ dla aplikacji Universal Windows Platform.

> [!TIP]
> Typy w [Namespace Platform::Collections](../cppcx/platform-collections-namespace.md) nie pojawiają się w pliku winmd, ponieważ nie są publicznie udostępniane. Są one implementacji prywatnej specyficznych dla języka C++ interfejsów, które są zdefiniowane w `Windows::Foundation::Collections`. Aplikację Windows Runtime, która jest napisana w języku JavaScript, czy języka C# nie wie, co [platform::Collections:: Vector, klasa](../cppcx/platform-collections-vector-class.md) , ale można korzystać `Windows::Foundation::Collections::IVector`. `Platform::Collections` Typy są definiowane w collection.h.

## <a name="windows-runtime-type-system-in-ccx"></a>System typów środowiska wykonawczego Windows w języku C + +/ CX

W poniższych sekcjach opisano najważniejszych funkcji systemu typów środowiska wykonawczego Windows i jak są one obsługiwane w języku C + +/ CX.

### <a name="namespaces"></a>Namespaces

Wszystkich typów środowiska wykonawczego Windows musi być zadeklarowany w przestrzeni nazw; sam interfejs API Windows jest zorganizowana według przestrzeni nazw. Pliku winmd musi mieć taką samą nazwę, który ma głównej przestrzeni nazw. Na przykład klasa, która nosi nazwę A.B.C.MyClass wystąpienia można tworzyć tylko wtedy, gdy jest on zdefiniowany w pliku metadanych, który nosi nazwę A.winmd i A.B.winmd lub A.B.C.winmd. Nazwa pliku DLL, nie musi być zgodna z nazwą pliku .winmd.

Sam interfejs API Windows został zbudowany od nowa jako bibliotekę dobrze uwarunkowaną klasy, która jest zorganizowana według przestrzeni nazw.  Wszystkie składniki środowiska wykonawczego Windows są deklarowane w przestrzeni nazw Windows.*.

Aby uzyskać więcej informacji, zobacz [przestrzenie nazw i widoczność typów](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="fundamental-types"></a>Typy podstawowe

Środowisko wykonawcze Windows definiuje następujących typów podstawowych, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, jednego, Double, Char16, atrybut typu wartość logiczna i ciąg. C + +/ CX obsługuje podstawowe typy liczbowe w jej domyślny obszar nazw jako uint16, uint32, uint64, int16, int32, int64, float32, float64 i char16. Atrybut typu wartość logiczna i ciąg również są zdefiniowane w przestrzeni nazw platformy.

C + +/ CX definiuje również uint8 odpowiednikiem `unsigned char`, która nie jest obsługiwana w środowisku uruchomieniowym Windows i nie można używać w publicznych interfejsów API.

Typ podstawowy może być typem dopuszczającym opakowując go w [Platform::IBox, interfejs](../cppcx/platform-ibox-interface.md) interfejsu. Aby uzyskać więcej informacji, zobacz [klasy i struktury wartości](../cppcx/value-classes-and-structs-c-cx.md).

Aby uzyskać więcej informacji na temat typów podstawowych, zobacz [typy podstawowe](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>Ciągi

Ciąg Windows Runtime to niezmienne sekwencja znaków UNICODE, 16-bitowych. Ciąg środowiska uruchomieniowego Windows jest przekazywany jako `Platform::String^`. Ta klasa zawiera metody służące do konstruowania ciągu, manipulowanie i konwersji do i z `wchar_t`.

Aby uzyskać więcej informacji, zobacz [ciągi](../cppcx/strings-c-cx.md).

### <a name="arrays"></a>Tablice

Środowisko uruchomieniowe Windows obsługuje 1-wymiarowe tablic dowolnego typu. Tablice tablic nie są obsługiwane.  W języku C + +/ CX, tablice środowiska uruchomieniowego Windows jest przekazywany jako [Platform::Array, klasa](../cppcx/platform-array-class.md).

Aby uzyskać więcej informacji, zobacz [tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Klasy i struktury odwołania

Klasy środowiska wykonawczego Windows jest przekazywany w języku C + +/ CX jako klasy referencyjnej lub ref struct, ponieważ są one kopiowane przez odwołanie. Zarządzanie pamięcią dla klasy i struktury ref odwołania jest obsługiwane w sposób niewidoczny dla użytkownika za pomocą zliczanie odwołań. Gdy ostatnie odwołanie do obiektu wykracza poza zakres, obiekt zostanie zniszczony. Struktury ref klasy lub ref wykonywać następujące czynności:

- Zawierać jako elementy członkowskie konstruktorów, metod, właściwości i zdarzeń. Członkowie ci mogą mieć publiczny, prywatny, chroniony lub wewnętrzny ułatwień dostępu.

- Może zawierać prywatne wyliczenia zagnieżdżonych, struktury lub definicji klas.

- Bezpośrednio może dziedziczyć z jednej klasy bazowej i może implementować dowolną liczbę interfejsów. Wszystkie klasy referencyjnej są niejawnie konwertowane na [Platform::Object, klasa](../cppcx/platform-object-class.md) , można zmienić jego metod wirtualnych — na przykład [Object::ToString](../cppcx/platform-object-class.md#tostring).

Klasa ref, który ma on publicznego konstruktora musi być zadeklarowana jako sealed, aby uniknąć dalszych pochodnym.

Aby uzyskać więcej informacji, zobacz [klasy i struktury odwołania](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>Wartość klas i struktur

Wartość klasy lub struktury wartość reprezentuje strukturę danych podstawowych i zawiera tylko pola, które mogą być wartości klasy, struktury wartości lub typu `Platform::String^`.  Wartość struktur i klas wartości są kopiowane przez wartość.

Struktura wartości można dopuszczać przez opakowywanie w interfejsie IBox.

Aby uzyskać więcej informacji, zobacz [klasy i struktury wartości](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="partial-classes"></a>Klasy częściowe

Funkcja klasy częściowej umożliwia jedną klasę do zdefiniowania za pośrednictwem wielu plików. Służy przede wszystkim, aby włączyć narzędzia generowania kodu, takie jak edytor XAML, aby zmodyfikować jeden plik bez modyfikowania pliku, który można edytować.

Aby uzyskać więcej informacji, zobacz [klasy częściowe](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>Właściwości

Właściwość jest elementem członkowskim publicznych danych dowolnego typu środowiska uruchomieniowego Windows i jest implementowany jako pary metod get/set. Kod klienta uzyskuje dostęp do właściwości, tak jakby pole publiczne. Pobierz właściwości, która wymaga bez niestandardowych lub ustawianie kodu jest znany jako *właściwość prosta* deklarowanych bez jawnych get lub zestawu metod i.

Aby uzyskać więcej informacji, zobacz [właściwości](../cppcx/properties-c-cx.md).

### <a name="windows-runtime-collections-in-ccx"></a>Kolekcje środowiska wykonawczego Windows w języku C + +/ CX

Środowisko wykonawcze Windows definiuje zestaw interfejsów dla typów kolekcji, które każdy język implementuje w inny sposób. C + +/ CX zawiera implementacje w [platform::Collections:: Vector, klasa](../cppcx/platform-collections-vector-class.md), [platform::Collections:: map, klasa](../cppcx/platform-collections-map-class.md), a innymi typami kolekcji konkretnych powiązanych, które są zgodne z ich Standardowy szablon biblioteki (STL) ich odpowiedniki.

Aby uzyskać więcej informacji, zobacz [kolekcje](../cppcx/collections-c-cx.md).

### <a name="template-ref-classes"></a>Klasy odwołania szablonu

Klasy ref prywatne i wewnętrzne może być oparte na szablonach, wyspecjalizowana.

Aby uzyskać więcej informacji, zobacz [klasy odwołania szablonu](../cppcx/template-ref-classes-c-cx.md).

### <a name="interfaces"></a>Interfejsy

Interfejs Windows Runtime definiuje zestaw właściwości publicznych, metod i zdarzeń, które klasy referencyjnej lub ref struct musi implementować, jeśli dziedziczy interfejs.

Więcej informacji znajdziesz w artykule [Interfejsy](../cppcx/interfaces-c-cx.md).

### <a name="enums"></a>Wyliczenia

Wylicz klasy środowiska wykonawczego Windows przypomina wyliczeniowym w języku C++. Typ podstawowy jest typu int32, o ile nie zastosowano atrybut [Flags] — w takim przypadku typ podstawowy jest uint32.

Aby uzyskać więcej informacji, zobacz [wyliczenia](../cppcx/enums-c-cx.md).

### <a name="delegates"></a>Delegaty

Delegat środowiska wykonawczego Windows jest analogiczne do obiektu std::function w języku C++. To specjalny rodzaj klasy referencyjnej, która jest używana do wywołania funkcji dostarczonych przez klienta, które mają zgodnych sygnatur.  Delegaty są najczęściej używane w środowisku uruchomieniowym Windows jako typ zdarzenia.

Aby uzyskać więcej informacji, zobacz [delegatów](../cppcx/delegates-c-cx.md).

### <a name="exceptions"></a>Wyjątki

W języku C + +/ CX może przechwycić wyjątku niestandardowych typów [std::exception](../standard-library/exception-class.md) typów i [Platform::Exception](../cppcx/platform-exception-class.md) typów.

Aby uzyskać więcej informacji, zobacz [wyjątki](../cppcx/exceptions-c-cx.md).

### <a name="events"></a>Zdarzenia

Zdarzenie jest publicznej składowej w klasie ref lub struktury ref, którego typ jest typem delegowanym. Zdarzenie może być wywoływany tylko — oznacza to, że wywoływane — przez klasę będącej właścicielem. Kod klienta może jednak zapewniać własnych funkcji, które są znane jako programów obsługi zdarzeń i są wywoływane, gdy klasa będąca właścicielem generowane zdarzenie.

Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).

### <a name="casting"></a>Rzutowanie

C + +/ CX obsługuje standardowe operatorów rzutowania języka C++ [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md), i [reinterpret_cast](../cpp/reinterpret-cast-operator.md), a także **safe_cast**operator, który jest specyficzny dla języka C + +/ CX.

Aby uzyskać więcej informacji, zobacz [rzutowanie](../cppcx/casting-c-cx.md).

### <a name="boxing"></a>Boxing

Spakowany zmienna jest typ wartości, która jest opakowana w typu odwołania w sytuacjach, w których wymagane są semantyką odwołań.

Aby uzyskać więcej informacji, zobacz [pakowania](../cppcx/boxing-c-cx.md).

### <a name="attributes"></a>Atrybuty

Atrybut jest wartość metadanych, które można zastosować do dowolnego środowiska uruchomieniowego Windows typu lub składowej typu i mogą być kontrolowane w czasie wykonywania. Środowisko wykonawcze Windows definiuje zestaw wspólne atrybuty w `Windows::Foundation::Metadata` przestrzeni nazw. Atrybuty zdefiniowane przez użytkownika w publicznych interfejsach nie są obsługiwane przez środowisko wykonawcze Windows w tej wersji.

## <a name="api-deprecation"></a>Zakończenie obsługi interfejsu API

Opisuje sposób oznaczania publicznych interfejsów API jako przestarzałe przy użyciu tego samego atrybutu, która jest używana przez typy systemu Windows w czasie wykonywania.

Aby uzyskać więcej informacji, zobacz [wycofane typy i składowe](../cppcx/deprecating-types-and-members-c-cx.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
