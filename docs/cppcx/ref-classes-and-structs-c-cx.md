---
title: Klasy i struktury odwołania (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
ms.openlocfilehash: a817529f24f1df3a3258b4596cd4d14533356a02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456228"
---
# <a name="ref-classes-and-structs-ccx"></a>Klasy i struktury odwołania (C + +/ CX)

C + +/ CX obsługuje zdefiniowanych przez użytkownika *klasy ref* i *struktury ref*i zdefiniowane przez użytkownika *wartość klasy* i *wartość struktury*. Te struktury danych są podstawowym kontenerów, przez które C + +/ CX obsługuje system typów środowiska wykonawczego Windows. Ich zawartość są emitowane do metadanych zgodnie z niektórych określone zasady, a dzięki temu przekazywane między składników środowiska wykonawczego Windows i aplikacji Universal Windows Platform, które zostały napisane w języku C++ lub innych języków.

Klasa ref lub ref struct ma te podstawowe funkcje:

- Musi być zadeklarowany w przestrzeni nazw, w zakresie przestrzeni nazw i w tej przestrzeni nazw może być publicznym lub prywatnym ułatwień dostępu. Tylko typy publiczne są emitowane do metadanych. Definicje klas publicznych zagnieżdżone nie są dozwolone, w tym publiczny zagnieżdżony [wyliczenia](../cppcx/enums-c-cx.md) klasy. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw i widoczność typów](../cppcx/namespaces-and-type-visibility-c-cx.md).

- Może on zawierać jako elementy członkowskie C + +/ CX, łącznie z klasy ref, wartość klasy, struktury ref, strukturach wartości lub struktury wartości null. Może również zawierać typy skalarne, takie jak float64, wartość logiczna i tak dalej. Może również zawierać standardowych typów C++ takich jak `std::vector` lub niestandardowej klasy tak długo, jak nie są publicznie udostępniane. C + +/ CX konstrukcje mogą mieć `public`, `protected`, `internal`, `private`, lub `protected private` ułatwień dostępu. Wszystkie `public` lub `protected` elementy członkowskie są emitowane do metadanych. Standard C++ typy muszą mieć `private`, `internal`, lub `protected private` ułatwień dostępu, co zapobiega emitowane do metadanych.

- To może wprowadzić co najmniej jeden *interfejsu klasy* lub *interfejsu struktury*.

- Mogą dziedziczyć z jednej klasy bazowej i klas bazowych, samodzielnie mają dodatkowe ograniczenia. Dziedziczenie w hierarchii klas publicznych ref ma więcej ograniczeń niż dziedziczenia klasy ref prywatnych.

- Go nie mogą być deklarowane jako ogólnego. Jeśli ma ona prywatną dostępność, może być szablonem.

- Jego okres istnienia jest zarządzana przez automatyczne liczenie odwołań.

## <a name="declaration"></a>Deklaracja

Poniższy fragment kodu deklaruje `Person` klasy referencyjnej. Należy zauważyć, że standard C++ `std::map` typ jest używany w prywatnych elementów członkowskich i środowiska uruchomieniowego Windows`IMapView` interfejs jest używany w interfejsie publicznym. Ponadto należy zauważyć, że "^" jest dołączany do deklaracji typów odwołań.

[!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]

## <a name="implementation"></a>Implementacja

Ten przykładowy kod przedstawia implementację `Person` klasy referencyjnej:

[!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]

## <a name="usage"></a>Użycie

W kolejnym przykładzie kodu pokazano, jak kod klienta używa `Person` klasy referencyjnej.

[!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]

Semantyka stosu umożliwia również zadeklarować zmienną klasy lokalnego odwołania. Taki obiekt zachowuje się jak zmiennej opartej na stosie, nawet jeśli pamięć nadal jest przydzielany dynamicznie. Jedną istotną różnicą jest, czy odwołania śledzenia (%) nie można przypisać do zmiennej, która jest zadeklarowana za pomocą semantyka stosu; gwarantuje to, że licznik odwołań zostanie zmniejszona do zera, jeśli funkcja kończy działanie. W tym przykładzie przedstawiono klasy referencyjnej podstawowe `Uri`i funkcję, która używa go z semantyką stosu:

[!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]

## <a name="memory-management"></a>Zarządzanie pamięcią

Przydziel w pamięci dynamicznej klasy referencyjnej za pomocą `ref new` — słowo kluczowe.

[!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]

Operator uchwytu do obiektu ^ jest znana jako "hat" i jest całkowicie inteligentnego wskaźnika języka C++. Wskazuje ilość pamięci automatycznie jest niszczony, kiedy ostatnia hat wykracza poza zakres lub jawnie ustawione na `nullptr`.

Zgodnie z definicją klasa ref ma semantykę odwołania. Po przypisaniu klasy referencyjnej zmiennej jest uchwyt, który został skopiowany nie samego obiektu. W następnym przykładzie po przypisaniu zarówno `myClass` i `myClass2` wskazują na tym samym miejscu pamięci.

[!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]

Gdy w języku C + +/ CX klasy referencyjnej zostanie uruchomiony, jego pamięci jest inicjowany z wartością zerową przed jego konstruktor jest wywoływana w związku z tym nie jest konieczne inicjalizacji zero poszczególnych elementów członkowskich, w tym właściwości. Jeśli C + +/ CX klasa pochodzi od klasy Windows środowiska uruchomieniowego C++ Library (WRL), tylko C + +/ CX, część klasy pochodnej jest inicjowany z wartością zerową.

### <a name="members"></a>Elementy członkowskie

Klasa ref mogą zawierać `public`, `protected`, i `private` funkcji elementów członkowskich; tylko `public` i `protected` elementy członkowskie są emitowane do metadanych. Klasy referencyjnej i klasy zagnieżdżone są dozwolone, ale nie może być `public`. Pola publiczne nie są dozwolone publiczne elementy członkowskie danych musi być zadeklarowany jako właściwości. Prywatnych lub chronionych wewnętrznych składowych danych mogą być pól. Domyślnie w klasie ref dostępność wszystkich elementów członkowskich jest `private`.

Struktury ref jest taka sama jak klasa ref, z tą różnicą, że domyślnie jego członkowie mają `public` ułatwień dostępu.

Element `public` klasy referencyjnej lub ref struct jest emitowane w metadanych, ale może być używany z innych aplikacji uniwersalnych platformy Windows i składników środowiska wykonawczego Windows musi mieć co najmniej jeden konstruktor publiczny lub chroniony. Klasa ref publicznej, która ma on publicznego konstruktora musi być także zadeklarowana jako `sealed` Aby uniknąć dalszych tworzenie wartości pochodnych przez interfejsem binarnym aplikacji (ABI).

Publiczne elementy członkowskie nie mogą być deklarowane jako const ponieważ system typów środowiska wykonawczego Windows nie obsługuje const. Właściwość statyczna służy do deklarowania element członkowski danych publicznych z wartością stałą.

Podczas definiowania ref publiczne klasy lub struktury, kompilator stosuje wymaganych atrybutów do klasy i zapisuje je w pliku winmd w aplikacji. Jednak podczas definiowania publicznych niezapieczętowana klasa ref ręcznie zastosować `Windows::Foundation::Metadata::WebHostHidden` atrybutu, aby upewnić się, że klasa nie jest widoczna dla aplikacji Universal Windows Platform, które zostały napisane w języku JavaScript.

Klasa referencyjna może mieć standardowych typów języka C++, w tym `const` typów, w dowolnym `private`, `internal`, lub `protected private` elementów członkowskich.

Klasy ref publicznych, które ma parametry typu nie są dozwolone. Klasy ref ogólny zdefiniowany przez użytkownika nie są dozwolone. Prywatne, wewnętrzne lub zabezpieczone prywatnej klasy ref może być szablonem.

## <a name="destructors"></a>Destruktory

W języku C + +/ CX, wywołanie `delete` na destruktorem publicznym wywołuje destruktora, niezależnie od tego, licznik odwołań obiektu. To zachowanie umożliwia zdefiniowanie destruktora, który wykonuje niestandardowe oczyszczania nie RAII zasobów w sposób deterministyczny. Jednak nawet w takim przypadku sam obiekt nie zostanie usunięta z pamięci. Pamięć dla obiektu jest zwalniana tylko wtedy, gdy licznik odwołań osiągnie zero.

Jeśli destruktor klasy nie jest publiczny, następnie jest tylko wywoływana, gdy licznik odwołań osiągnie zero. Jeśli wywołasz `delete` na obiekt, który ma destruktor prywatnych, kompilator generuje ostrzeżenie C4493, który jest wyświetlany komunikat "Usuń wyrażenie nie przynosi efektu jako destruktor \<Nazwa typu > nie ma dostępności"public"."

Destruktory klasy REF mogą być deklarowane tylko w następujący sposób:

- publiczne i wirtualnych (dozwolone w typach zapieczętowanych i niezapieczętowanych)

- chronione, prywatne i niewirtualną (dozwolone tylko dla typów niezapieczętowanych)

- prywatne i niewirtualną (dozwolone tylko w typach zapieczętowanych)

Nie inne kombinacje ułatwień dostępu, virtualness i sealedness jest dozwolone.  Jeśli jawnie nie zadeklarowała destruktora, kompilator generuje publicznego destruktora wirtualnego, jeśli typ klasy bazowej lub dowolnego elementu członkowskiego ma destruktorem publicznym. W przeciwnym razie kompilator generuje prywatny chroniony Niewirtualny destruktor w przypadku typów niezapieczętowanych lub prywatnej Niewirtualny destruktor dla typach zapieczętowanych.

Zachowanie jest niezdefiniowane, jeśli zostanie podjęta próba dostęp do elementów członkowskich klasy, która ma już jego destruktor uruchomione. najprawdopodobniej spowoduje awarię programu. Wywoływanie `delete t` na typ, który ma nie publicznego destruktora nie ma wpływu. Wywoływanie `delete this` dla typu lub podstawowej klasy, która ma poprawną `private` lub `protected private` destruktor z w jego hierarchii typów nie ma również wpływu.

Kiedy Deklarujesz destruktorem publicznym, kompilator generuje kod, tak aby klasy referencyjnej implementuje `Platform::IDisposable` i implementuje destruktor `Dispose` metody. `Platform::IDisposable` jest C + +/ CX rzut `Windows::Foundation::IClosable`. Nigdy w sposób jawny implementują te interfejsy.

## <a name="inheritance"></a>Dziedziczenie

Platform::Object jest uniwersalnym klasę bazową dla wszystkich klas ref. Wszystkie klasy referencyjnej są niejawnie konwertowane na Platform::Object, można zmienić [Object::ToString](../cppcx/platform-object-class.md#tostring). Jednak model dziedziczenia Windows Runtime nieprzeznaczonych jako ogólnego modelu dziedziczenia; w języku C + +/ CX, oznacza to, że klasy referencyjnej publiczne zdefiniowane przez użytkownika nie może służyć jako klasę bazową.

Jeśli utworzysz formant użytkownika XAML i obiekt uczestniczy w systemie właściwości zależności, a następnie można użyć `Windows::UI::Xaml::DependencyObject` jako klasę bazową.

Po zdefiniowaniu niezapieczętowane klasy `MyBase` tej, która dziedziczy `DependencyObject`, publicznych lub prywatnych odwołania klas w składniku lub aplikacja może dziedziczyć z `MyBase`. Dziedziczenie klas publicznych ref powinno mieć miejsce tylko do obsługi przesłonięć metod wirtualnych, polimorficznych tożsamości i hermetyzacji.

Prywatnej podstawowej klasy ref nie jest wymagane do uzyskania z istniejącej klasy niezapieczętowany. Jeśli potrzebujesz hierarchii obiektów modelu struktury programu lub włączyć ponownego użycia kodu, użyj klasy ref prywatne lub wewnętrzne lub jeszcze lepiej standardowych klas języka C++. Może narazić funkcje hierarchii obiektu prywatnego przy użyciu otoki klasy publicznej ref zapieczętowany.

Klasa ref, która ma Konstruktor publiczny lub chroniony w języku C + +/ CX musi być zadeklarowana jako zapieczętowany. Ograniczenie to oznacza, że nie ma możliwości dla klas, które są zapisywane w innych językach, takich jak C# lub Visual Basic dziedziczy z typów, które deklarują w składniku Windows Runtime, która jest napisana w języku C + +/ CX.

Poniżej przedstawiono podstawowe zasady dziedziczenia w języku C + +/ CX:

- REF klasy mogą dziedziczyć bezpośrednio z co najwyżej jednej klasy bazowej ref, ale może implementować dowolną liczbę interfejsów.

- Jeśli klasa ma Konstruktor publiczny, musi być zadeklarowana jako sealed, aby uniknąć dalszych pochodnym.

- Można utworzyć publiczny niezapieczętowanych klas bazowych, które mają wewnętrzne lub zabezpieczone konstruktory prywatne, pod warunkiem, że klasa bazowa pochodzi bezpośrednio lub pośrednio z istniejący, niezapieczętowany klasy bazowej takich jak `Windows::UI::Xaml::DependencyObject`. Dziedziczenie klasy ref zdefiniowanych przez użytkownika na pliki .winmd nie jest obsługiwana; jednak klasy referencyjnej można dziedziczyć interfejsu, który jest zdefiniowany w innym pliku winmd. Można utworzyć klasy pochodne od klasy zdefiniowane przez użytkownika bazowej ref tylko w obrębie tego samego składnika środowiska wykonawczego Windows lub aplikacji Universal Windows Platform.

- Klasy ref obsługiwane są tylko publiczne dziedziczenie.

   [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]

Poniższy przykład pokazuje, jak do udostępnienia klasy publicznej ref pochodzący z innych klas ref w hierarchii dziedziczenia.

[!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Wartość klas i struktur](../cppcx/value-classes-and-structs-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)