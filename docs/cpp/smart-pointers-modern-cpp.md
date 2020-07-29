---
title: Wskaźniki inteligentne (Modern C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: 698843ced3235d9622af3610a5209669407e9e05
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186142"
---
# <a name="smart-pointers-modern-c"></a>Wskaźniki inteligentne (Modern C++)

W nowoczesnej programowaniu C++, standardowa biblioteka zawiera *inteligentne wskaźniki*, które są używane w celu zapewnienia, że programy nie uwalniają pamięci i przecieków zasobów i są bezpieczne pod względem wyjątków.

## <a name="uses-for-smart-pointers"></a>Zastosowania inteligentnych wskaźników

Inteligentne wskaźniki są zdefiniowane w `std` przestrzeni nazw w [\<memory>](../standard-library/memory.md) pliku nagłówkowym. Są one niezwykle ważne dla [RAII](objects-own-resources-raii.md) lub *pozyskiwania zasobów jest inicjowanie* programowania idiom. Głównym celem tego idiomu jest zapewnienie, że pozyskiwanie zasobów występuje w tym samym czasie, co inicjacja obiektu, tak aby wszystkie zasoby dla tego obiektu były tworzone i gotowe w jednym wierszu kodu. W praktyce główną zasadą RAII jest dawanie na własność dowolnego zasobu z przyznaną stertą — na przykład dynamicznie przydzielonej pamięci lub uchwytów obiektu systemowego — obiektowi z przyznanym stosem, którego destruktor zawiera kod w celu usunięcia lub zwolnienia zasobów, a także związany z nim kod porządkujący.

W większości przypadków, podczas inicjowania surowego wskaźnika lub uchwytu zasobu w celu wskazania rzeczywistego zasobu, należy natychmiast przekazać wskaźnik do inteligentnego wskaźnika. W nowoczesnym C++, surowe wskaźniki są używane tylko w małych blokach kodu o ograniczonym zakresie, pętlach lub funkcjach pomocniczych, gdzie wydajność ma kluczowe znaczenie i nie ma możliwości popełnienia błędu w zakresie własności.

Poniższy przykład porównuje deklarację surowego wskaźnika z deklaracją inteligentnego wskaźnika.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak pokazano w przykładzie, inteligentny wskaźnik jest szablonem klasy, którą deklarujesz na stosie i inicjujesz przy użyciu surowego wskaźnika, który wskazuje na obiekt z przydzieloną stertą. Po zainicjowaniu inteligentnego wskaźnika, inteligentny wskaźnik jest właścicielem wskaźnika surowego. Oznacza to, że inteligentny wskaźnik jest odpowiedzialny za usunięcie pamięci określonej przez surowy wskaźnik. Destruktor inteligentnego wskaźnika zawiera wywołanie usunięcia, a ponieważ inteligentny wskaźnik jest zadeklarowany na stosie, jego destruktor jest wywołany, kiedy inteligentny wskaźnik wychodzi poza zakres, nawet jeśli później na stosie jest zgłoszony wyjątek.

Uzyskuj dostęp do zhermetyzowanego wskaźnika za pomocą znanych operatorów wskaźnika `->` i `*` , które klasy inteligentnego wskaźnika przeciążać, aby zwracać surowy wskaźnik nieprzetworzony.

Idiom inteligentnego wskaźnika języka C++ przypomina tworzenie obiektów w językach takich, jak C#: utwórz obiekt, a następnie pozwól systemowi zadbać o usunięcie go w odpowiednim czasie. Różnica polega na tym, że w tle nie działa żaden odrębny moduł odśmiecania; pamięć jest zarządzana przez standardowe zasady zakresu C++, tak że środowisko wykonawcze jest szybsze i wydajniejsze.

> [!IMPORTANT]
> Zawsze twórz inteligentne wskaźniki w osobnym wierszu kodu, nigdy na liście parametrów, tak aby nie wystąpił niewielki wyciek zasobów z powodu pewnych reguł alokacji listy parametrów.

Poniższy przykład pokazuje, jak `unique_ptr` typ inteligentnego wskaźnika z standardowej biblioteki języka C++ może służyć do hermetyzacji wskaźnika do dużego obiektu.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

W przykładzie pokazano niezbędne kroki używania inteligentnych wskaźników.

1. Zadeklaruj inteligentny wskaźnik jako zmienną automatyczną (lokalną). (Nie używaj **`new`** `malloc` wyrażenia OR dla samego wskaźnika inteligentnego).

1. W parametrze typu określ typ wskazywanego zhermetyzowanego wskaźnika.

1. Przekaż surowy wskaźnik do **`new`** obiektu-ED w konstruktorze inteligentnego wskaźnika. (Niektóre funkcje narzędziowe lub konstruktory inteligentnego wskaźnika robią to automatycznie.)

1. Użyj przeciążonych `->` operatorów i, `*` Aby uzyskać dostęp do obiektu.

1. Niech inteligentny wskaźnik usunie obiekt.

Inteligentne wskaźniki są zaprojektowane tak, aby były maksymalnie efektywne, zarówno w zakresie pamięci, jak i wydajności. Na przykład jedyny element członkowski danych w programie `unique_ptr` jest wskaźnikiem hermetyzowanym. Oznacza to, że `unique_ptr` jest to dokładnie taki sam rozmiar jak ten wskaźnik, cztery bajty lub osiem bajtów. Uzyskiwanie dostępu do zhermetyzowanego wskaźnika przy użyciu funkcji inteligentnych operatorów przeciążonych * i-> nie jest znacząco wolniejsze niż bezpośredni dostęp do pierwotnych wskaźników.

Inteligentne wskaźniki mają własne funkcje członkowskie, do których uzyskuje się dostęp przy użyciu notacji "kropka". Na przykład niektóre inteligentne wskaźniki standardowej biblioteki C++ mają funkcję resetowania elementu członkowskiego, która zwalnia własność wskaźnika. Jest to przydatne, kiedy chcesz zwolnić pamięć zajmowaną przez inteligentny wskaźnik, zanim inteligentny wskaźnik wyjdzie poza zakres, jak pokazano w poniższym przykładzie.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentne wskaźniki umożliwiają zwykle bezpośredni dostęp do własnego surowego wskaźnika. Inteligentne wskaźniki standardowej biblioteki języka C++ mają w `get` tym celu funkcję członkowską i `CComPtr` mają publiczną `p` składową klasy. Zapewniając bezpośredni dostęp do podstawowych wskaźników, możesz skorzystać z inteligentnego wskaźnika do zarządzania pamięcią we własnym kodzie i nadal przekazywać surowy wskaźnik do kodu, który nie obsługuje inteligentnych wskaźników.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Rodzaje inteligentnych wskaźników

Poniższa sekcja podsumowuje różne rodzaje inteligentnych wskaźników, które są dostępne w środowisku programowania Windows, i opisuje, kiedy ich używać.

### <a name="c-standard-library-smart-pointers"></a>Inteligentne wskaźniki standardowej biblioteki C++

Używaj tych inteligentnych wskaźników jako pierwszych, w celu hermetyzacji wskaźników jako zwykłych starych obiektów C++ (Plain Old C++ Objects — POCO).

- `unique_ptr`<br/>
   Pozwala na dokładnie jednego właściciela podstawowego wskaźnika. Użyj jako domyślnego wyboru dla POCO, chyba że wiadomo, że jest to wymagane `shared_ptr` . Może być przeniesiony do nowego właściciela, ale nie kopiowany lub udostępniony. Zastępuje `auto_ptr` , który jest przestarzały. Porównaj z `boost::scoped_ptr` . `unique_ptr`jest mały i wydajny; rozmiar jest jednym wskaźnikiem i obsługuje odwołania rvalue do szybkiego wstawiania i pobierania z kolekcji standardowej biblioteki języka C++. Plik nagłówka: `<memory>` . Aby uzyskać więcej informacji, zobacz [How to: Create and Use Unique_ptr Instances](how-to-create-and-use-unique-ptr-instances.md) and [unique_ptr Class](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Inteligentny wskaźnik zliczonych odwołań. Użyj, jeżeli chcesz przypisać jeden surowy wskaźnik wielu właścicielom, na przykład, kiedy zwracasz kopię wskaźnika z kontenera, ale chcesz zatrzymać oryginał. Nieprzetworzony wskaźnik nie zostanie usunięty, dopóki wszyscy `shared_ptr` właściciele nie znikną z zakresu lub w inny sposób nie podano własności. Rozmiar to dwa wskaźniki; jeden dla obiektu i jeden dla współdzielonego bloku kontroli, który zawiera licznik odwołań. Plik nagłówka: `<memory>` . Aby uzyskać więcej informacji, zobacz [How to: Create and Use Shared_ptr Instances](how-to-create-and-use-shared-ptr-instances.md) and [shared_ptr Class](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Specjalny wskaźnik inteligentny dla przypadków użycia w połączeniu z `shared_ptr` . `weak_ptr`Zapewnia dostęp do obiektu, który należy do jednego lub większej liczby `shared_ptr` wystąpień, ale nie uczestniczy w zliczaniu odwołań. Używaj, jeżeli chcesz obserwować obiekt, ale nie wymagasz, aby pozostał aktywny. Wymagane w niektórych przypadkach, aby przerwać odwołania cykliczne między `shared_ptr` wystąpieniami. Plik nagłówka: `<memory>` . Aby uzyskać więcej informacji, zobacz [How to: Create and Use Weak_ptr Instances](how-to-create-and-use-weak-ptr-instances.md) and [weak_ptr Class](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Inteligentne wskaźniki dla obiektów COM (klasyczne programowanie systemu Windows)

Kiedy pracujesz z obiektami COM, zawiń wskaźniki interfejsu w odpowiedni typ inteligentnego wskaźnika. Active Template Library (ATL) definiuje kilka inteligentnych wskaźników do różnych celów. Można również użyć `_com_ptr_t` typu inteligentnego wskaźnika, który jest używany przez kompilator, gdy tworzy klasy otoki z plików. tlb. To najlepszy wybór, jeśli nie chcesz dołączyć plików nagłówkowych ATL.

[Klasa CComPtr](../atl/reference/ccomptr-class.md)<br/>
Użyj tego, jeżeli nie możesz użyć ATL. Wykonuje zliczanie odwołań przy użyciu `AddRef` `Release` metod i. Aby uzyskać więcej informacji, zobacz [How to: Create and use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComQIPtr](../atl/reference/ccomqiptr-class.md)<br/>
Przypomina, `CComPtr` ale również zapewnia uproszczoną składnię do wywoływania `QueryInterface` obiektów com. Aby uzyskać więcej informacji, zobacz [How to: Create and use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComHeapPtr](../atl/reference/ccomheapptr-class.md)<br/>
Inteligentny wskaźnik do obiektów, które używają `CoTaskMemFree` do zwolnienia pamięci.

[Klasa CComGITPtr](../atl/reference/ccomgitptr-class.md)<br/>
Inteligentny wskaźnik dla interfejsów, które są uzyskiwane z tabeli interfejsu globalnego (GIT).

[Klasa _com_ptr_t](com-ptr-t-class.md)<br/>
Przypomina `CComQIPtr` funkcje, ale nie są zależne od nagłówków ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>Inteligentne wskaźniki ATL dla obiektów POCO

Oprócz inteligentnych wskaźników dla obiektów COM, ATL definiuje również inteligentne wskaźniki i kolekcje inteligentnych wskaźników dla zwykłych starych obiektów C++ (POCO). W klasycznym programowaniu systemu Windows te typy są przydatnymi alternatywami dla standardowych kolekcji bibliotek języka C++, zwłaszcza gdy Przenoszenie kodu nie jest wymagane lub gdy nie chcesz mieszać modeli programowania biblioteki standardowej C++ i ATL.

[Klasa CAutoPtr](../atl/reference/cautoptr-class.md)<br/>
Inteligentny wskaźnik, który wymusza unikatowe własności poprzez przeniesienie własności na kopię. Porównywalne do przestarzałej `std::auto_ptr` klasy.

[Klasa CHeapPtr](../atl/reference/cheapptr-class.md)<br/>
Inteligentny wskaźnik dla obiektów, które są przydzielone przy użyciu funkcji C [malloc](../c-runtime-library/reference/malloc.md) .

[Klasa CAutoVectorPtr](../atl/reference/cautovectorptr-class.md)<br/>
Inteligentny wskaźnik dla tablic, które są przydzielone za pomocą `new[]` .

[Klasa CAutoPtrArray](../atl/reference/cautoptrarray-class.md)<br/>
Klasa, która hermetyzuje tablicę `CAutoPtr` elementów.

[Klasa CAutoPtrList](../atl/reference/cautoptrlist-class.md)<br/>
Klasa, która hermetyzuje metody manipulowania listą `CAutoPtr` węzłów.

## <a name="see-also"></a>Zobacz także

[Wskaźniki](pointers-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)
