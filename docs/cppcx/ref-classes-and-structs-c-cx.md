---
title: Klasy i struktury ref (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
ms.openlocfilehash: b58c5b64d8f4a60b418fdd2b11318055a8fb618e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740886"
---
# <a name="ref-classes-and-structs-ccx"></a>Klasy i struktury ref (C++/CX)

C++/CX obsługuje zdefiniowane przez użytkownika *klasy referencyjne* i *struktury ref*oraz *klasy wartości* zdefiniowane przez użytkownika i *struktury wartości*. Te struktury danych są kontenerami podstawowymi, C++za pomocą których/CX obsługuje system typów środowisko wykonawcze systemu Windows. Ich zawartość jest emitowana do metadanych zgodnie z określonymi regułami i umożliwia ich przekazywanie między składnikami środowisko wykonawcze systemu Windows i platforma uniwersalna systemu Windows aplikacjami, które są zapisane w lub w C++ innych językach.

Klasa referencyjna lub struktura ref ma następujące podstawowe funkcje:

- Musi być zadeklarowany w przestrzeni nazw, w zakresie przestrzeni nazw, a w tej przestrzeni nazw może być dostępna publiczna lub prywatna dostępność. Tylko typy publiczne są emitowane do metadanych. Zagnieżdżone definicje klas publicznych są niedozwolone, łącznie z zagnieżdżonymi publicznymi klasami [enum](../cppcx/enums-c-cx.md) . Aby uzyskać więcej informacji, zobacz [przestrzenie nazw i widoczność typów](../cppcx/namespaces-and-type-visibility-c-cx.md).

- Może zawierać jako składowe C++/CX, w tym klasy referencyjne, klasy wartości, struktury ref, struktury wartości lub struktury wartości null. Może również zawierać typy skalarne, takie jak Float64, bool i tak dalej. Może również zawierać typy standardowe C++ , takie jak `std::vector` lub Klasa niestandardowa, o ile nie są publiczne. C++Konstrukcje/CX mogą mieć `public`, `protected`, `internal` `private`, lub`protected private` dostępność. Wszystkie `public` lub`protected` elementy członkowskie są emitowane do metadanych. Standardowe C++ typy muszą mieć `private`, `internal`, lub `protected private` dostępność, które uniemożliwiają emitowanie ich do metadanych.

- Może zaimplementować jedną lub więcej *klas interfejsów* lub *struktur interfejsów*.

- Może dziedziczyć z jednej klasy bazowej, a same klasy bazowe mają dodatkowe ograniczenia. Dziedziczenie w publicznych hierarchiach klas referencyjnych ma większe ograniczenia niż dziedziczenie w prywatnych klasach referencyjnych.

- Nie może być zadeklarowany jako generyczny. Jeśli ma prywatny dostęp, może to być szablon.

- Jego okres istnienia jest zarządzany przez automatyczne zliczanie odwołań.

## <a name="declaration"></a>Oświadczeń

Poniższy fragment kodu deklaruje `Person` klasę ref. Należy zauważyć, że C++ `std::map` typ standardowy jest używany w prywatnych składowych, a interfejs`IMapView` środowisko wykonawcze systemu Windows jest używany w interfejsie publicznym. Zauważ również, że znak "^" jest dołączany do deklaracji typów referencyjnych.

[!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]

## <a name="implementation"></a>Implementacja

Ten przykład kodu pokazuje implementację `Person` klasy ref:

[!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]

## <a name="usage"></a>Użycie

Następny przykład kodu pokazuje, `Person` jak kod klienta używa klasy ref.

[!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]

Można również użyć semantyki stosu, aby zadeklarować zmienną lokalnej klasy referencyjnej. Taki obiekt zachowuje się jak zmienna oparta na stosie, mimo że pamięć jest nadal przydzielana dynamicznie. Istotną różnicą jest to, że nie można przypisać odwołania śledzenia (%) do zmiennej, która jest zadeklarowana przy użyciu semantyki stosu; gwarantuje to, że liczba odwołań jest zmniejszana do zera, gdy funkcja kończy działanie. Ten przykład pokazuje podstawową klasę `Uri`ref i funkcję, która używa jej z semantyką stosu:

[!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]

## <a name="memory-management"></a>Zarządzanie pamięcią

Należy przydzielić klasę ref w pamięci dynamicznej przy użyciu `ref new` słowa kluczowego.

[!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]

Operator dojścia do obiektu ^ jest znany jako "Hat" i jest zasadniczo C++ inteligentnym wskaźnikiem. Pamięć, do której wskazuje, jest automatycznie niszczona, gdy Ostatnia Hat wykracza poza zakres lub jest jawnie ustawiona `nullptr`na.

Według definicji Klasa ref ma semantykę odwołania. Po przypisaniu zmiennej klasy ref jest to dojście, które jest kopiowane, a nie sam obiekt. W następnym przykładzie po przypisaniu `myClass` i `myClass2` wskazaniu w tej samej lokalizacji pamięci.

[!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]

Po utworzeniu C++wystąpienia klasy ref/CX jej pamięć jest inicjowana zero przed wywołaniem konstruktora; w związku z tym nie jest konieczne, aby od zera zainicjować pojedynczych członków, w tym właściwości. Jeśli Klasa C++/CX dziedziczy z klasy środowisko wykonawcze systemu Windows C++ Library (WRL), tylko część klasy pochodnej C++/CX jest inicjowana zero.

### <a name="members"></a>Elementy członkowskie

Klasa referencyjna może zawierać `public`, `protected`i `private` składowe funkcji; tylko `public` `protected` elementy członkowskie są emitowane do metadanych. Klasy zagnieżdżone i klasy ref są dozwolone, ale nie `public`mogą być. Pola publiczne są niedozwolone; publiczne składowe danych muszą być zadeklarowane jako właściwości. Prywatnymi lub chronionymi wewnętrznymi elementami członkowskimi danych mogą być pola. Domyślnie w klasie ref dostępność wszystkich elementów członkowskich to `private`.

Struktura ref jest taka sama jak Klasa ref, z tą różnicą, że domyślnie jej członkowie `public` mają dostęp.

Klasa `public` ref lub ref struct są emitowane w metadanych, ale aby można było korzystać z innych platforma uniwersalna systemu Windows aplikacji i składników Środowisko wykonawcze systemu Windows, musi on mieć co najmniej jednego publicznego lub chronionego konstruktora. Publiczna Klasa referencyjna, która ma Konstruktor publiczny, musi być zadeklarowana jako, `sealed` aby zapobiec dalszemu wyprowadzaniu za pomocą interfejsu binarnego aplikacji (ABI).

Publiczne składowe nie mogą być zadeklarowane jako const, ponieważ system typu środowisko wykonawcze systemu Windows nie obsługuje const. Możesz użyć właściwości statycznej, aby zadeklarować publiczną składową danych z wartością stałą.

Podczas definiowania publicznej klasy lub struktury referencyjnej kompilator stosuje wymagane atrybuty do klasy i zapisuje te informacje w pliku winmd aplikacji. Jednak podczas definiowania publicznej niezapieczętowanej klasy ref należy ręcznie zastosować `Windows::Foundation::Metadata::WebHostHidden` atrybut, aby upewnić się, że Klasa nie będzie widoczna dla platforma uniwersalna systemu Windows aplikacji, które są zapisywane w języku JavaScript.

Klasa referencyjna może mieć typy C++ standardowe, w `const` tym typy `internal`, w `private`dowolnych `protected private` lub składowych.

Publiczne klasy referencyjne, które mają parametry typu, są niedozwolone. Klasy referencyjne ogólne zdefiniowane przez użytkownika są niedozwolone. Prywatna, wewnętrzna lub chroniona prywatna Klasa referencyjna może być szablonem.

## <a name="destructors"></a>Destruktory

W C++/CX wywoływanie `delete` przez destruktor publiczny wywołuje destruktor, niezależnie od liczby odwołań obiektu. To zachowanie umożliwia zdefiniowanie destruktora, który wykonuje niestandardowe Oczyszczanie zasobów innych niż RAII w sposób deterministyczny. Jednak nawet w tym przypadku sam obiekt nie jest usuwany z pamięci. Pamięć dla obiektu jest zwalniana tylko wtedy, gdy licznik odwołań osiągnie wartość zero.

Jeśli destruktor klasy nie jest publiczny, jest wywoływany tylko wtedy, gdy licznik odwołań osiągnie wartość zero. Jeśli wywołasz `delete` obiekt, który ma destruktor prywatny, kompilator zgłasza C4493 ostrzegawczy, co oznacza, że "wyrażenie usuwania nie ma żadnego efektu, ponieważ destruktor \<typu > nie ma dostępu" Public "."

Destruktory klasy referencyjnej mogą być deklarowane tylko w następujący sposób:

- publiczne i wirtualne (dozwolone dla typów zapieczętowanych lub niezapieczętowanych)

- chroniona prywatna i niewirtualna (dozwolone tylko w przypadku niezapieczętowanych typów)

- prywatne i niewirtualne (dozwolone tylko w przypadku zapieczętowanych typów)

Nie jest dozwolona żadna inna kombinacja dostępności, wirtualizacji i zamknięcia.  Jeśli nie deklarujesz jawnie destruktora, kompilator generuje publiczny destruktor wirtualny, jeśli klasa bazowa typu lub dowolny element członkowski ma destruktor publiczny. W przeciwnym razie kompilator generuje chroniony prywatny destruktor niewirtualny dla niezapieczętowanych typów lub prywatny destruktor niewirtualny dla typów zapieczętowanych.

Zachowanie jest niezdefiniowane, jeśli próbujesz uzyskać dostęp do elementów członkowskich klasy, która ma już uruchomiony destruktor; najprawdopodobniej spowoduje to awarię programu. Wywołanie `delete t` na typie, który nie ma destruktora publicznego nie ma żadnego wpływu. Wywoływanie `delete this` typu lub klasy bazowej, która ma znany `private` lub `protected private` destruktor z w hierarchii typów, również nie ma żadnego wpływu.

Podczas deklarowania destruktora publicznego kompilator generuje kod, tak aby Klasa ref implementuje `Platform::IDisposable` i destruktor `Dispose` implementuje metodę. `Platform::IDisposable`jest projekcją C++ `Windows::Foundation::IClosable`/CX. Nigdy nie implementuje jawnie tych interfejsów.

## <a name="inheritance"></a>Dziedziczenie

Platform:: Object jest uniwersalną klasą bazową dla wszystkich klas referencyjnych. Wszystkie klasy referencyjne są niejawnie konwertowane na platformę:: Object i mogą przesłonić [obiekt:: ToString](../cppcx/platform-object-class.md#tostring). Jednak model dziedziczenia środowisko wykonawcze systemu Windows nie jest przeznaczony jako model dziedziczenia ogólnego; w C++/CX oznacza to, że publiczna Klasa referencyjna zdefiniowana przez użytkownika nie może stanowić klasy bazowej.

Jeśli tworzysz kontrolkę użytkownika XAML, a obiekt uczestniczy w systemie właściwości zależności, można użyć `Windows::UI::Xaml::DependencyObject` jako klasy bazowej.

Po zdefiniowaniu niezapieczętowanej klasy `MyBase` , która dziedziczy z `DependencyObject`, inne publiczne lub prywatne klasy referencyjne w składniku lub aplikacji mogą dziedziczyć `MyBase`po. Dziedziczenie w publicznych klasach referencyjnych powinno być wykonywane tylko w celu obsługi zastąpień metod wirtualnych, tożsamości polimorficznej i hermetyzacji.

Prywatna Klasa referencyjna nie jest wymagana do wyprowadzania z istniejącej niezapieczętowanej klasy. Jeśli potrzebujesz hierarchii obiektów do modelowania własnej struktury programu lub włączania ponownego użycia kodu, użyj prywatnych lub wewnętrznych klas referencyjnych lub lepszych, a także w przypadku C++ klas standardowych. Funkcję hierarchii obiektów prywatnych można uwidocznić za pomocą publicznej, zapieczętowanej otoki klasy referencyjnej.

Klasa ref, która ma Konstruktor publiczny lub Protected w C++/CX, musi być zadeklarowana jako Sealed. To ograniczenie oznacza, że nie ma żadnego sposobu dla klas, które są zapisywane w innych językach C# , takich jak lub Visual Basic dziedziczenie z typów zadeklarowanych w składniku środowisko wykonawcze systemu Windows, które C++są zapisywane w/CX.

Poniżej przedstawiono podstawowe reguły dziedziczenia w programie C++/CX:

- Klasy referencyjne mogą dziedziczyć bezpośrednio z co najwyżej jednej podstawowej klasy referencyjnej, ale mogą implementować dowolną liczbę interfejsów.

- Jeśli klasa ma Konstruktor publiczny, musi być zadeklarowana jako zapieczętowana, aby zapobiec dalszemu wywodzeniu.

- Można utworzyć publiczne niezapieczętowane klasy bazowe, które mają wewnętrzne lub chronione konstruktory prywatne, pod warunkiem, że klasa bazowa dziedziczy bezpośrednio lub pośrednio z istniejącej niezapieczętowanej klasy podstawowej, `Windows::UI::Xaml::DependencyObject`takiej jak. Dziedziczenie klas ref zdefiniowanych przez użytkownika w plikach winmd nie jest obsługiwane. jednak Klasa ref może dziedziczyć z interfejsu, który jest zdefiniowany w innym pliku winmd. Klasy pochodne można utworzyć na podstawie zdefiniowanej przez użytkownika klasy referencyjnej, tylko w tym samym składniku środowisko wykonawcze systemu Windows lub platforma uniwersalna systemu Windows aplikacji.

- Dla klas ref obsługiwane jest tylko publiczne dziedziczenie.

   [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]

Poniższy przykład pokazuje, jak uwidocznić publiczną klasę referencyjną, która pochodzi od innych klas referencyjnych w hierarchii dziedziczenia.

[!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Klasy i struktury wartości](../cppcx/value-classes-and-structs-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
