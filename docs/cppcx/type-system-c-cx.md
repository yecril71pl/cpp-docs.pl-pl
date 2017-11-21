---
title: "System typów (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
caps.latest.revision: "28"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: c1839fad0c929f6e24b74f74c2cc91e29e07005b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="type-system-ccx"></a>System typów (C + +/ CX)
Za pomocą architektury środowiska wykonawczego systemu Windows, można użyć C + +/ CX, Visual Basic, Visual C# i JavaScript do pisania aplikacji i składników, które bezpośrednio uzyskać dostępu do interfejsu API systemu Windows i współpraca z innymi środowiska wykonawczego systemu Windows, aplikacje i składniki. Uniwersalnych aplikacji platformy systemu Windows, które zostały napisane w języku C++ skompiluj do kodu natywnego, która wykonuje bezpośrednio w Procesor. Uniwersalnych aplikacji platformy systemu Windows, które zostały napisane w języku C# lub Visual Basic kompilacji na język pośredni firmy Microsoft (MSIL), a następnie wykonaj w środowisku uruchomieniowym języka (wspólnego CLR). Wykonanie uniwersalnych aplikacji platformy systemu Windows, które zostały napisane w języku JavaScript w środowisku czasu wykonywania. Samych elementów systemu operacyjnego środowiska wykonawczego systemu Windows są napisane w języku C++ i Uruchom jako kodu natywnego. Wszystkie te składniki i aplikacje platformy uniwersalnej systemu Windows komunikują się bezpośrednio za pośrednictwem interfejsu binarne (ABI) środowiska wykonawczego systemu Windows.  
  
 Aby włączyć obsługę środowiska uruchomieniowego systemu Windows w nowoczesnych idiom C++, firma Microsoft opracowała C + +/ CX. C + +/ CX zawiera wbudowane typy podstawowe i implementacji podstawowych typów środowiska wykonawczego systemu Windows, które Włącz C++ aplikacje i składniki do komunikowania się za pośrednictwem interfejsu ABI przy użyciu aplikacji napisanych w innych językach. Możesz używać dowolnego typu środowiska wykonawczego systemu Windows lub Tworzenie klasy, struktury, interfejsy i inne typy danych zdefiniowane przez użytkownika, które mogą być używane przez inne aplikacje platformy uniwersalnej systemu Windows i składników. aplikacji platformy uniwersalnej systemu Windows, który jest napisany w języku C + +/ CX umożliwia także regularne C++ klas i struktur tak długo, jak nie posiadają powszechnej dostępności.  
  
 Szczegółowe omówienie C + +/ CX projekcji języka i jak działa w tle, zobacz wpisy na blogu:  
  
1.  [C + +/ CX część 0 \[ n \]: wprowadzenie](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)  
  
2.  [C + +/ CX część 1 z \[ n \]: prostą klasę](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)  
  
3.  [C + +/ CX część 2 \[ n \]: typy, które nosić Kapelusze](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)  
  
4.  [C + +/ CX część 3 \[ n \]: konstruowanego](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)  
  
5.  [C + +/ CX część 4 \[ n \]: statyczne funkcje Członkowskie](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)  
  
## <a name="windows-metadata-winmd-files"></a>Pliki metadanych (.winmd) dla systemu Windows  
 Podczas kompilowania aplikacji platformy uniwersalnej systemu Windows, który jest napisany w języku C++ kompilator generuje plik wykonywalny w kodzie natywnym maszyny, a także generuje oddzielny plik metadanych (.winmd) systemu Windows, który zawiera opisy typy publiczne środowiska wykonawczego systemu Windows, które obejmują klasy, struktury, wyliczenia, interfejsów, sparametryzowane interfejsów i delegatów. Format, który jest używany w zestawach .NET Framework jest podobny do formatu metadanych.  W składniku C++ plik winmd zawiera tylko metadane; kod wykonywalny znajduje się w oddzielnym pliku. Jest to w przypadku składników środowiska wykonawczego systemu Windows, które są dołączone do systemu Windows. Nazwa pliku WinMD muszą być zgodne i być prefiksem głównej przestrzeni nazw w kodzie źródłowym. (Dla języków .NET Framework, plik winmd zawiera zarówno kod i metadanych, podobnie jak zestaw .NET Framework).  
  
 Metadane w pliku winmd reprezentuje publikowanej powierzchni kodu. Typy opublikowanych są widoczne dla innych platformy uniwersalnej systemu Windows niezależnie od tego, w jakim języku te inne aplikacje są napisane w. W związku z tym metadanych lub kodzie opublikowanych może zawierać wyłącznie typy określone przez system typów środowiska wykonawczego systemu Windows. Nie można opublikować konstrukcji języka, które są specyficzne dla języka C++, takie jak zwykłych klas, tablic, szablonów i kontenery STL w metadanych, ponieważ aplikacji klienckiej Javascript lub C# nie wiedział, co należy zrobić z nimi.  
  
 Określa, czy jest widoczna w metadanych typu lub metody zależy od tego, jakie modyfikatory dostępności są stosowane do niego. Aby były widoczne, typ musi być zadeklarowana w przestrzeni nazw i musi być zadeklarowany jako publiczny. Klasa ref niepublicznych jest dozwolona jako typu wewnętrznego pomocnika w kodzie; Podobnie nie jest widoczny w metadanych. Nawet w klasie ref publiczny nie wszystkie elementy członkowskie są zawsze widoczne. W poniższej tabeli przedstawiono relację między specyfikatory dostępu C++ w klasie ref publicznego i widoczność metadanych środowiska wykonawczego systemu Windows:  
  
|||  
|-|-|  
|**Publikowany w metadanych**|**Nie jest publikowany w metadanych**|  
|public|private|  
|protected|internal|  
|publiczny, chroniony|prywatne chronione|  
  
 Można użyć **przeglądarki obiektów** do wyświetlania zawartości plików winmd. Składniki środowiska uruchomieniowego systemu Windows, które są dołączone do systemu Windows znajdują się w pliku plik Windows.winmd. Plik default.winmd zawiera typy podstawowe, które są używane w języku C + +/ CX i platform.winmd zawiera dodatkowe typy pochodzące z obszaru nazw platformy. Domyślnie tych trzech plików winmd znajdują się w każdym projekcie C++ dla aplikacji platformy uniwersalnej systemu Windows.  
  
> [!TIP]
>  Typy w [Namespace Platform::Collections](../cppcx/platform-collections-namespace.md) nie pojawiają się w pliku winmd, ponieważ nie są publicznie udostępniane. Są one prywatnej specyficzne dla języka C++ implementacji interfejsów, które są zdefiniowane w `Windows::Foundation::Collections`. Aplikacji środowiska wykonawczego systemu Windows, który jest zapisany w JavaScript lub C# nie wiadomo co [klasy Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) , ale może zużyć `Windows::Foundation::Collections::IVector`. `Platform::Collections` Typy są definiowane w collection.h.  
  
## <a name="windows-runtime-type-system-in-ccx"></a>System typów środowiska wykonawczego systemu Windows w języku C + +/ CX  
 W poniższych sekcjach opisano najważniejszych funkcji system typów środowiska wykonawczego systemu Windows i jak są obsługiwane w języku C + +/ CX.  
  
### <a name="namespaces"></a>Namespaces  
 Wszystkie typy środowiska wykonawczego systemu Windows musi być zadeklarowana w przestrzeni nazw; Interfejs API systemu Windows, sam jest zorganizowana według przestrzeni nazw. Plik winmd musi mieć takiej samej nazwie, który ma głównej przestrzeni nazw. Na przykład klasy o nazwie A.B.C.MyClass można wdrożyć tylko wtedy, gdy jest on zdefiniowany w pliku metadanych o nazwie A.winmd lub A.B.winmd lub A.B.C.winmd. Nazwę biblioteki DLL nie musi być zgodna z nazwą pliku winmd.  
  
 Interfejs API systemu Windows, sam ma zostały reinvented jako biblioteki dobrze factored klasy, która jest zorganizowana według przestrzeni nazw.  Wszystkie składniki środowiska uruchomieniowego systemu Windows są zadeklarowane w przestrzeniach nazw Windows.*.  
  
 Aby uzyskać więcej informacji, zobacz [obszary nazw i typ widoczności](../cppcx/namespaces-and-type-visibility-c-cx.md).  
  
### <a name="fundamental-types"></a>Typy podstawowe  
 Środowisko wykonawcze systemu Windows definiuje następujących typów podstawowych, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, jednego, Double, Char16, Boolean i ciąg. C + +/ CX obsługuje podstawowe typy liczbowe w jego domyślny obszar nazw jako uint16, uint32, uint64, int16, int32, int64, float32, float64 i char16. Przestrzeń nazw platformy można zdefiniować Boolean i String.  
  
 C + +/ CX definiuje również uint8 odpowiednikiem `unsigned char`, która nie jest obsługiwana w środowisku wykonawczym systemu Windows i nie można używać w publicznych interfejsach API.  
  
 Podstawowe typu może być zerowalne, opakowując go w [interfejsu Platform::IBox](../cppcx/platform-ibox-interface.md) interfejsu. Aby uzyskać więcej informacji, zobacz [wartość klas i struktur](../cppcx/value-classes-and-structs-c-cx.md).  
  
 Aby uzyskać więcej informacji na temat typów podstawowych, zobacz [typy podstawowe](../cppcx/fundamental-types-c-cx.md)  
  
### <a name="strings"></a>Ciągi  
 Ciąg środowiska wykonawczego systemu Windows jest niezmienialny sekwencji znaków UNICODE, 16-bitowych. Ciąg środowiska wykonawczego systemu Windows jest przekazywany jako `Platform::String^`. Ta klasa dostarcza metody konstrukcji ciągu, manipulowanie i konwersji do i z `wchar_t`.  
  
 Aby uzyskać więcej informacji, zobacz [ciągów](../cppcx/strings-c-cx.md).  
  
### <a name="arrays"></a>Tablice  
 Środowisko wykonawcze systemu Windows obsługuje tablic wielowymiarowych 1 dowolnego typu. Tablic zawierających tablice nie są obsługiwane.  W języku C + +/ CX, tablic środowiska wykonawczego systemu Windows jest przekazywany jako [Platform::Array klasy](../cppcx/platform-array-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [tablicy i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)  
  
### <a name="ref-classes-and-structs"></a>REF klasy i struktury  
 Klasa środowiska uruchomieniowego systemu Windows jest zaprojektowana w języku C + +/ CX jako klasy referencyjnej lub ref struct, ponieważ są one kopiowane przez odwołanie. Zarządzanie pamięcią ref klas i struktur ref jest obsługiwane niewidocznie za pomocą liczenie odwołań. Gdy ostatnie odwołanie do obiektu odbędzie się poza zakresem, obiekt zostanie zniszczony. Ref struct klasy lub ref wykonywać następujące czynności:  
  
-   Zawiera jako elementy członkowskie konstruktorów, metod, właściwości i zdarzeń. Te elementy Członkowskie mogą mieć dostępności publiczne, prywatne, chronionych lub wewnętrzny.  
  
-   Może zawierać prywatnej zagnieżdżonych wyliczenia, struktury lub definicji klas.  
  
-   Dziedziczenie bezpośrednio z jedną klasę podstawową i można zaimplementować dowolną liczbę interfejsów. Wszystkie klasy ref są umożliwiają niejawnej konwersji na [klasy Platform::Object](../cppcx/platform-object-class.md) , można zmienić jego metody wirtualne — na przykład [Object::ToString](../cppcx/platform-object-class.md#tostring).  
  
 Klasa ref, który ma publicznego konstruktora musi być zadeklarowany jako sealed, aby uniknąć dalszych pochodnym.  
  
 Aby uzyskać więcej informacji, zobacz [Ref klasy i struktury](../cppcx/ref-classes-and-structs-c-cx.md)  
  
### <a name="value-classes-and-structs"></a>Wartość klasy i struktury  
 Wartość klasie lub strukturze wartość reprezentuje struktury danych podstawowych i zawiera tylko pola, które mogą być wartość klasy, struktury wartość lub typu `Platform::String^`.  Wartość struktur i klas wartości są kopiowane wartości.  
  
 Struktura wartości mogą dopuszczać wartości null przez zawijania w interfejsie IBox.  
  
 Aby uzyskać więcej informacji, zobacz [wartość klas i struktur](../cppcx/value-classes-and-structs-c-cx.md).  
  
### <a name="partial-classes"></a>Klasy częściowe  
 Funkcja klasy częściowej umożliwia jedną klasę do zdefiniowania przez wiele plików. Jest on używany głównie w celu włączenia narzędzi generowania kodu, takich jak zmodyfikować jeden plik, nie ingerując w pliku, który można edytować w edytorze XAML.  
  
 Aby uzyskać więcej informacji, zobacz [klasy częściowe](../cppcx/partial-classes-c-cx.md)  
  
### <a name="properties"></a>Właściwości  
 Właściwość jest elementem członkowskim danych publicznych dowolnego typu środowiska wykonawczego systemu Windows i jest zaimplementowany jako pary metod get/set. Kod klienta uzyskuje dostęp do właściwości, tak jakby był on pole publiczne. Właściwości, która wymaga bez niestandardowych pobrać lub kod zestawu nosi nazwę *właściwość prosta* deklarowanych bez jawnych get lub ustaw metody i.  
  
 Aby uzyskać więcej informacji, zobacz [właściwości](../cppcx/properties-c-cx.md).  
  
### <a name="windows-runtime-collections-in-ccx"></a>Kolekcje środowiska wykonawczego systemu Windows w języku C + +/ CX  
 Środowisko wykonawcze systemu Windows definiuje zbiór interfejsów dla typów kolekcji, które implementuje każdego języka w jego własnej sposób. C + +/ CX zawiera implementacje w [klasy Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md), [Platform::Collections::Map klasy](../cppcx/platform-collections-map-class.md), a innymi typami pokrewnej kolekcji konkretnych, które są zgodne z ich Standardowa biblioteka szablonów (STL) odpowiedniki.  
  
 Aby uzyskać więcej informacji, zobacz [kolekcji](../cppcx/collections-c-cx.md).  
  
### <a name="template-ref-classes"></a>Szablon klasy ref  
 Klasy ref prywatne i wewnętrzne może być szablonem i specjalnych.  
  
 Aby uzyskać więcej informacji, zobacz [klasy ref szablonów](../cppcx/template-ref-classes-c-cx.md).  
  
### <a name="interfaces"></a>Interfejsy  
 Interfejs środowiska uruchomieniowego systemu Windows definiuje zestaw właściwości publiczne, metod i zdarzeń, które klasy referencyjnej lub ref struct musi implementować Jeśli dziedziczy z interfejsu.  
  
 Aby uzyskać więcej informacji, zobacz [interfejsów](../cppcx/interfaces-c-cx.md).  
  
### <a name="enums"></a>Wyliczenia  
 Klasa wyliczenia w środowiska wykonawczego systemu Windows jest podobny do zakresami wyliczenia w języku C++. Typ podstawowy jest int32, chyba że zastosowano atrybut [Flags] — w takim przypadku typ podstawowy jest uint32.  
  
 Aby uzyskać więcej informacji, zobacz [wyliczenia](../cppcx/enums-c-cx.md).  
  
### <a name="delegates"></a>Delegaty  
 Delegat w środowisku wykonawczym systemu Windows jest odpowiednikiem obiektu std::function w języku C++. Jest specjalnym rodzajem klasy ref, która służy do wywoływania funkcje dostarczonych przez klienta, które mają niezgodne podpisów.  Obiekty delegowane są najczęściej używane w środowisku wykonawczym systemu Windows jako typ zdarzenia.  
  
 Aby uzyskać więcej informacji, zobacz [delegatów](../cppcx/delegates-c-cx.md).  
  
### <a name="exceptions"></a>Wyjątki  
 W języku C + +/ CX, można przechwycić typów wyjątków niestandardowych, [std::exception](../standard-library/exception-class.md) typów, a [Platform::Exception](../cppcx/platform-exception-class.md) typów.  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki](../cppcx/exceptions-c-cx.md).  
  
### <a name="events"></a>Zdarzenia  
 Zdarzenie jest publicznym elementem członkowskim klasy referencyjnej lub ref struct, którego typ jest typem delegowanym. Zdarzenie może być wywoływany tylko — to znaczy uruchamiany — przez klasę będący właścicielem. Jednak kod klienta zapewniają własnej funkcji, które są określane jako procedury obsługi zdarzeń i są wywoływane, gdy klasa będąca właścicielem generowane zdarzenie.  
  
 Aby uzyskać więcej informacji, zobacz [zdarzenia](../cppcx/events-c-cx.md).  
  
### <a name="casting"></a>Rzutowanie  
 C + +/ CX obsługuje standardowe operatory C++ rzutowania [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md), i [reinterpret_cast](../cpp/reinterpret-cast-operator.md), a także **safe_cast**operator, który jest przeznaczony dla C + +/ CX.  
  
 Aby uzyskać więcej informacji, zobacz [rzutowanie](../cppcx/casting-c-cx.md).  
  
### <a name="boxing"></a>Boxing  
 Opakowany zmienna jest typem wartości, który jest opakowany w typu odwołania w sytuacjach, w których wymagane są semantykę odwołania.  
  
 Aby uzyskać więcej informacji, zobacz [Boxing](../cppcx/boxing-c-cx.md).  
  
### <a name="attributes"></a>Atrybuty  
 Atrybut jest wartość metadanych, który można zastosować do dowolnego typu środowiska wykonawczego systemu Windows lub elementu członkowskiego typu i mogą być kontrolowane w czasie wykonywania. Środowisko wykonawcze systemu Windows definiuje zestaw typowych atrybutów w `Windows::Foundation::Metadata` przestrzeni nazw. Zdefiniowane przez użytkownika atrybuty w publicznych interfejsach nie są obsługiwane przez środowisko wykonawcze systemu Windows w tej wersji.  
  
## <a name="api-deprecation"></a>Amortyzacja interfejsu API  
 Opisuje sposób publiczne interfejsy API zostać oznaczone jako przestarzałe przy użyciu tego samego atrybutu, która jest używana przez typy systemu środowiska wykonawczego systemu Windows.  
  
 Aby uzyskać więcej informacji, zobacz [wycofano typy i składniki](../cppcx/deprecating-types-and-members-c-cx.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
