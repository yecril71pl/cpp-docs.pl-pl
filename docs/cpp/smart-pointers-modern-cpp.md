---
title: Wskaźniki inteligentne (Modern C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: a18a5daa45f4f913b6b6dd714956f8592ca0a8d0
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246341"
---
# <a name="smart-pointers-modern-c"></a>Wskaźniki inteligentne (Modern C++)

In modern C++ programming, the Standard Library includes *smart pointers*, which are used to help ensure that programs are free of memory and resource leaks and are exception-safe.

## <a name="uses-for-smart-pointers"></a>Zastosowania inteligentnych wskaźników

Smart pointers are defined in the `std` namespace in the [\<memory>](../standard-library/memory.md) header file. They are crucial to the [RAII](objects-own-resources-raii.md) or *Resource Acquisition Is Initialization* programming idiom. Głównym celem tego idiomu jest zapewnienie, że pozyskiwanie zasobów występuje w tym samym czasie, co inicjacja obiektu, tak aby wszystkie zasoby dla tego obiektu były tworzone i gotowe w jednym wierszu kodu. W praktyce główną zasadą RAII jest dawanie na własność dowolnego zasobu z przyznaną stertą — na przykład dynamicznie przydzielonej pamięci lub uchwytów obiektu systemowego — obiektowi z przyznanym stosem, którego destruktor zawiera kod w celu usunięcia lub zwolnienia zasobów, a także związany z nim kod porządkujący.

W większości przypadków, podczas inicjowania surowego wskaźnika lub uchwytu zasobu w celu wskazania rzeczywistego zasobu, należy natychmiast przekazać wskaźnik do inteligentnego wskaźnika. W nowoczesnym C++, surowe wskaźniki są używane tylko w małych blokach kodu o ograniczonym zakresie, pętlach lub funkcjach pomocniczych, gdzie wydajność ma kluczowe znaczenie i nie ma możliwości popełnienia błędu w zakresie własności.

Poniższy przykład porównuje deklarację surowego wskaźnika z deklaracją inteligentnego wskaźnika.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak pokazano w przykładzie, inteligentny wskaźnik jest szablonem klasy, którą deklarujesz na stosie i inicjujesz przy użyciu surowego wskaźnika, który wskazuje na obiekt z przydzieloną stertą. Po zainicjowaniu inteligentnego wskaźnika, inteligentny wskaźnik jest właścicielem wskaźnika surowego. Oznacza to, że inteligentny wskaźnik jest odpowiedzialny za usunięcie pamięci określonej przez surowy wskaźnik. Destruktor inteligentnego wskaźnika zawiera wywołanie usunięcia, a ponieważ inteligentny wskaźnik jest zadeklarowany na stosie, jego destruktor jest wywołany, kiedy inteligentny wskaźnik wychodzi poza zakres, nawet jeśli później na stosie jest zgłoszony wyjątek.

Access the encapsulated pointer by using the familiar pointer operators, `->` and `*`, which the smart pointer class overloads to return the encapsulated raw pointer.

Idiom inteligentnego wskaźnika języka C++ przypomina tworzenie obiektów w językach takich, jak C#: utwórz obiekt, a następnie pozwól systemowi zadbać o usunięcie go w odpowiednim czasie. Różnica polega na tym, że w tle nie działa żaden odrębny moduł odśmiecania; pamięć jest zarządzana przez standardowe zasady zakresu C++, tak że środowisko wykonawcze jest szybsze i wydajniejsze.

> [!IMPORTANT]
>  Zawsze twórz inteligentne wskaźniki w osobnym wierszu kodu, nigdy na liście parametrów, tak aby nie wystąpił niewielki wyciek zasobów z powodu pewnych reguł alokacji listy parametrów.

The following example shows how a `unique_ptr` smart pointer type from the C++ Standard Library could be used to encapsulate a pointer to a large object.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

W przykładzie pokazano niezbędne kroki używania inteligentnych wskaźników.

1. Zadeklaruj inteligentny wskaźnik jako zmienną automatyczną (lokalną). (Do not use the **new** or `malloc` expression on the smart pointer itself.)

1. W parametrze typu określ typ wskazywanego zhermetyzowanego wskaźnika.

1. Pass a raw pointer to a **new**-ed object in the smart pointer constructor. (Niektóre funkcje narzędziowe lub konstruktory inteligentnego wskaźnika robią to automatycznie.)

1. Use the overloaded `->` and `*` operators to access the object.

1. Niech inteligentny wskaźnik usunie obiekt.

Inteligentne wskaźniki są zaprojektowane tak, aby były maksymalnie efektywne, zarówno w zakresie pamięci, jak i wydajności. For example, the only data member in `unique_ptr` is the encapsulated pointer. This means that `unique_ptr` is exactly the same size as that pointer, either four bytes or eight bytes. Accessing the encapsulated pointer by using the smart pointer overloaded * and -> operators is not significantly slower than accessing the raw pointers directly.

Inteligentne wskaźniki mają swoje własne funkcje członkowskie, które są dostępne przy użyciu notacji „kropkowej”. For example, some C++ Standard Library smart pointers have a reset member function that releases ownership of the pointer. Jest to przydatne, kiedy chcesz zwolnić pamięć zajmowaną przez inteligentny wskaźnik, zanim inteligentny wskaźnik wyjdzie poza zakres, jak pokazano w poniższym przykładzie.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentne wskaźniki umożliwiają zwykle bezpośredni dostęp do własnego surowego wskaźnika. C++ Standard Library smart pointers have a `get` member function for this purpose, and `CComPtr` has a public `p` class member. Zapewniając bezpośredni dostęp do podstawowych wskaźników, możesz skorzystać z inteligentnego wskaźnika do zarządzania pamięcią we własnym kodzie i nadal przekazywać surowy wskaźnik do kodu, który nie obsługuje inteligentnych wskaźników.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Kinds of smart pointers

Poniższa sekcja podsumowuje różne rodzaje inteligentnych wskaźników, które są dostępne w środowisku programowania Windows, i opisuje, kiedy ich używać.

### <a name="c-standard-library-smart-pointers"></a>C++ Standard Library smart pointers

Używaj tych inteligentnych wskaźników jako pierwszych, w celu hermetyzacji wskaźników jako zwykłych starych obiektów C++ (Plain Old C++ Objects — POCO).

- `unique_ptr`<br/>
   Pozwala na dokładnie jednego właściciela podstawowego wskaźnika. Use as the default choice for POCO unless you know for certain that you require a `shared_ptr`. Może być przeniesiony do nowego właściciela, ale nie kopiowany lub udostępniony. Replaces `auto_ptr`, which is deprecated. Compare to `boost::scoped_ptr`. `unique_ptr` is small and efficient; the size is one pointer and it supports rvalue references for fast insertion and retrieval from C++ Standard Library collections. Header file: `<memory>`. For more information, see [How to: Create and Use unique_ptr Instances](how-to-create-and-use-unique-ptr-instances.md) and [unique_ptr Class](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Inteligentny wskaźnik zliczonych odwołań. Użyj, jeżeli chcesz przypisać jeden surowy wskaźnik wielu właścicielom, na przykład, kiedy zwracasz kopię wskaźnika z kontenera, ale chcesz zatrzymać oryginał. The raw pointer is not deleted until all `shared_ptr` owners have gone out of scope or have otherwise given up ownership. Rozmiar to dwa wskaźniki; jeden dla obiektu i jeden dla współdzielonego bloku kontroli, który zawiera licznik odwołań. Header file: `<memory>`. For more information, see [How to: Create and Use shared_ptr Instances](how-to-create-and-use-shared-ptr-instances.md) and [shared_ptr Class](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Special-case smart pointer for use in conjunction with `shared_ptr`. A `weak_ptr` provides access to an object that is owned by one or more `shared_ptr` instances, but does not participate in reference counting. Używaj, jeżeli chcesz obserwować obiekt, ale nie wymagasz, aby pozostał aktywny. Required in some cases to break circular references between `shared_ptr` instances. Header file: `<memory>`. For more information, see [How to: Create and Use weak_ptr Instances](how-to-create-and-use-weak-ptr-instances.md) and [weak_ptr Class](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Smart pointers for COM objects (classic Windows programming)

Kiedy pracujesz z obiektami COM, zawiń wskaźniki interfejsu w odpowiedni typ inteligentnego wskaźnika. Active Template Library (ATL) definiuje kilka inteligentnych wskaźników do różnych celów. You can also use the `_com_ptr_t` smart pointer type, which the compiler uses when it creates wrapper classes from .tlb files. To najlepszy wybór, jeśli nie chcesz dołączyć plików nagłówkowych ATL.

[Klasa CComPtr](../atl/reference/ccomptr-class.md)<br/>
Użyj tego, jeżeli nie możesz użyć ATL. Performs reference counting by using the `AddRef` and `Release` methods. For more information, see [How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComQIPtr](../atl/reference/ccomqiptr-class.md)<br/>
Resembles `CComPtr` but also provides simplified syntax for calling `QueryInterface` on COM objects. For more information, see [How to: Create and Use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComHeapPtr](../atl/reference/ccomheapptr-class.md)<br/>
Smart pointer to objects that use `CoTaskMemFree` to free memory.

[Klasa CComGITPtr](../atl/reference/ccomgitptr-class.md)<br/>
Inteligentny wskaźnik dla interfejsów, które są uzyskiwane z tabeli interfejsu globalnego (GIT).

[_com_ptr_t, klasa](com-ptr-t-class.md)<br/>
Resembles `CComQIPtr` in functionality but does not depend on ATL headers.

### <a name="atl-smart-pointers-for-poco-objects"></a>ATL smart pointers for POCO objects

In addition to smart pointers for COM objects, ATL also defines smart pointers, and collections of smart pointers, for plain old C++ objects (POCO). In classic Windows programming, these types are useful alternatives to the C++ Standard Library collections, especially when code portability is not required or when you do not want to mix the programming models of the C++ Standard Library and ATL.

[Klasa CAutoPtr](../atl/reference/cautoptr-class.md)<br/>
Inteligentny wskaźnik, który wymusza unikatowe własności poprzez przeniesienie własności na kopię. Comparable to the deprecated `std::auto_ptr` Class.

[Klasa CHeapPtr](../atl/reference/cheapptr-class.md)<br/>
Smart pointer for objects that are allocated by using the C [malloc](../c-runtime-library/reference/malloc.md) function.

[Klasa CAutoVectorPtr](../atl/reference/cautovectorptr-class.md)<br/>
Smart pointer for arrays that are allocated by using `new[]`.

[Klasa CAutoPtrArray](../atl/reference/cautoptrarray-class.md)<br/>
Class that encapsulates an array of `CAutoPtr` elements.

[Klasa CAutoPtrList](../atl/reference/cautoptrlist-class.md)<br/>
Class that encapsulates methods for manipulating a list of `CAutoPtr` nodes.

## <a name="see-also"></a>Zobacz także

[Wskaźniki](pointers-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
