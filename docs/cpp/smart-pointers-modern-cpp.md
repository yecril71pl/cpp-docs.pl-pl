---
title: Wskaźniki inteligentne (Modern C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: 293dca7cce4cffce83e474ff4f2e7753d18882c2
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303359"
---
# <a name="smart-pointers-modern-c"></a>Wskaźniki inteligentne (Modern C++)

W nowoczesnych C++ programowaniu Biblioteka standardowa obejmuje *inteligentne wskaźniki*, które są używane w celu zapewnienia, że programy nie uwalniają pamięci i przecieków zasobów i są bezpieczne pod względem wyjątków.

## <a name="uses-for-smart-pointers"></a>Zastosowania inteligentnych wskaźników

Inteligentne wskaźniki są zdefiniowane w przestrzeni nazw `std` w pliku nagłówkowym [>\<pamięci](../standard-library/memory.md) . Są one niezwykle ważne dla [RAII](objects-own-resources-raii.md) lub *pozyskiwania zasobów jest inicjowanie* programowania idiom. Głównym celem tego idiomu jest zapewnienie, że pozyskiwanie zasobów występuje w tym samym czasie, co inicjacja obiektu, tak aby wszystkie zasoby dla tego obiektu były tworzone i gotowe w jednym wierszu kodu. W praktyce główną zasadą RAII jest dawanie na własność dowolnego zasobu z przyznaną stertą — na przykład dynamicznie przydzielonej pamięci lub uchwytów obiektu systemowego — obiektowi z przyznanym stosem, którego destruktor zawiera kod w celu usunięcia lub zwolnienia zasobów, a także związany z nim kod porządkujący.

W większości przypadków, podczas inicjowania surowego wskaźnika lub uchwytu zasobu w celu wskazania rzeczywistego zasobu, należy natychmiast przekazać wskaźnik do inteligentnego wskaźnika. W nowoczesnym C++, surowe wskaźniki są używane tylko w małych blokach kodu o ograniczonym zakresie, pętlach lub funkcjach pomocniczych, gdzie wydajność ma kluczowe znaczenie i nie ma możliwości popełnienia błędu w zakresie własności.

Poniższy przykład porównuje deklarację surowego wskaźnika z deklaracją inteligentnego wskaźnika.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak pokazano w przykładzie, inteligentny wskaźnik jest szablonem klasy, którą deklarujesz na stosie i inicjujesz przy użyciu surowego wskaźnika, który wskazuje na obiekt z przydzieloną stertą. Po zainicjowaniu inteligentnego wskaźnika, inteligentny wskaźnik jest właścicielem wskaźnika surowego. Oznacza to, że inteligentny wskaźnik jest odpowiedzialny za usunięcie pamięci określonej przez surowy wskaźnik. Destruktor inteligentnego wskaźnika zawiera wywołanie usunięcia, a ponieważ inteligentny wskaźnik jest zadeklarowany na stosie, jego destruktor jest wywołany, kiedy inteligentny wskaźnik wychodzi poza zakres, nawet jeśli później na stosie jest zgłoszony wyjątek.

Dostęp do zhermetyzowanego wskaźnika za pomocą znanych operatorów wskaźnika, `->` i `*`, które Klasa inteligentnego wskaźnika przeciąża, aby zwrócić surowy wskaźnik nieprzetworzony.

Idiom inteligentnego wskaźnika języka C++ przypomina tworzenie obiektów w językach takich, jak C#: utwórz obiekt, a następnie pozwól systemowi zadbać o usunięcie go w odpowiednim czasie. Różnica polega na tym, że w tle nie działa żaden odrębny moduł odśmiecania; pamięć jest zarządzana przez standardowe zasady zakresu C++, tak że środowisko wykonawcze jest szybsze i wydajniejsze.

> [!IMPORTANT]
>  Zawsze twórz inteligentne wskaźniki w osobnym wierszu kodu, nigdy na liście parametrów, tak aby nie wystąpił niewielki wyciek zasobów z powodu pewnych reguł alokacji listy parametrów.

Poniższy przykład pokazuje, jak typ inteligentnego wskaźnika `unique_ptr` z biblioteki C++ standardowej może służyć do hermetyzacji wskaźnika do dużego obiektu.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

W przykładzie pokazano niezbędne kroki używania inteligentnych wskaźników.

1. Zadeklaruj inteligentny wskaźnik jako zmienną automatyczną (lokalną). (Nie używaj wyrażenia **New** lub `malloc` na samym wskaźniku inteligentnym).

1. W parametrze typu określ typ wskazywanego zhermetyzowanego wskaźnika.

1. Przekaż surowy wskaźnik do **nowego**obiektu w konstruktorze inteligentnego wskaźnika. (Niektóre funkcje narzędziowe lub konstruktory inteligentnego wskaźnika robią to automatycznie.)

1. Użyj przeciążonych `->` i operatory `*`, aby uzyskać dostęp do obiektu.

1. Niech inteligentny wskaźnik usunie obiekt.

Inteligentne wskaźniki są zaprojektowane tak, aby były maksymalnie efektywne, zarówno w zakresie pamięci, jak i wydajności. Na przykład jedynym elementem członkowskim danych w `unique_ptr` jest wskaźnik hermetyzowany. Oznacza to, że `unique_ptr` ma dokładnie taki sam rozmiar jak ten wskaźnik, cztery bajty lub osiem bajtów. Uzyskiwanie dostępu do zhermetyzowanego wskaźnika przy użyciu funkcji inteligentnych operatorów przeciążonych * i-> nie jest znacząco wolniejsze niż bezpośredni dostęp do pierwotnych wskaźników.

Inteligentne wskaźniki mają własne funkcje członkowskie, do których uzyskuje się dostęp przy użyciu notacji "kropka". Na przykład niektóre C++ inteligentne wskaźniki biblioteki standardowej mają funkcję resetowania elementu członkowskiego, która zwalnia własność wskaźnika. Jest to przydatne, kiedy chcesz zwolnić pamięć zajmowaną przez inteligentny wskaźnik, zanim inteligentny wskaźnik wyjdzie poza zakres, jak pokazano w poniższym przykładzie.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentne wskaźniki umożliwiają zwykle bezpośredni dostęp do własnego surowego wskaźnika. C++Inteligentne wskaźniki biblioteki standardowej mają do tego celu `get` funkcję członkowską, a `CComPtr` ma publiczny element członkowski klasy `p`. Zapewniając bezpośredni dostęp do podstawowych wskaźników, możesz skorzystać z inteligentnego wskaźnika do zarządzania pamięcią we własnym kodzie i nadal przekazywać surowy wskaźnik do kodu, który nie obsługuje inteligentnych wskaźników.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Rodzaje inteligentnych wskaźników

Poniższa sekcja podsumowuje różne rodzaje inteligentnych wskaźników, które są dostępne w środowisku programowania Windows, i opisuje, kiedy ich używać.

### <a name="c-standard-library-smart-pointers"></a>C++Inteligentne wskaźniki biblioteki standardowej

Używaj tych inteligentnych wskaźników jako pierwszych, w celu hermetyzacji wskaźników jako zwykłych starych obiektów C++ (Plain Old C++ Objects — POCO).

- `unique_ptr`<br/>
   Pozwala na dokładnie jednego właściciela podstawowego wskaźnika. Użyj jako domyślnego wyboru dla POCO, chyba że wiadomo, że jest wymagane `shared_ptr`. Może być przeniesiony do nowego właściciela, ale nie kopiowany lub udostępniony. Zastępuje `auto_ptr`, który jest przestarzały. Porównaj z `boost::scoped_ptr`. `unique_ptr` jest mały i wydajny; rozmiar jest jednym wskaźnikiem i obsługuje odwołania rvalue do szybkiego wstawiania i pobierania z C++ standardowych kolekcji bibliotek. Plik nagłówkowy: `<memory>`. Aby uzyskać więcej informacji, zobacz [How to: Create and Use Unique_ptr Instances](how-to-create-and-use-unique-ptr-instances.md) and [unique_ptr Class](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Inteligentny wskaźnik zliczonych odwołań. Użyj, jeżeli chcesz przypisać jeden surowy wskaźnik wielu właścicielom, na przykład, kiedy zwracasz kopię wskaźnika z kontenera, ale chcesz zatrzymać oryginał. Nieprzetworzony wskaźnik nie zostanie usunięty, dopóki wszyscy właściciele `shared_ptr` nie znikną z zakresu lub w inny sposób nie podano własności. Rozmiar to dwa wskaźniki; jeden dla obiektu i jeden dla współdzielonego bloku kontroli, który zawiera licznik odwołań. Plik nagłówkowy: `<memory>`. Aby uzyskać więcej informacji, zobacz [How to: Create and Use Shared_ptr Instances](how-to-create-and-use-shared-ptr-instances.md) and [shared_ptr Class](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Specjalny wskaźnik inteligentny dla przypadków użycia w połączeniu z `shared_ptr`. `weak_ptr` zapewnia dostęp do obiektu, który należy do co najmniej jednego wystąpienia `shared_ptr`, ale nie uczestniczy w zliczaniu odwołań. Używaj, jeżeli chcesz obserwować obiekt, ale nie wymagasz, aby pozostał aktywny. Wymagane w niektórych przypadkach, aby przerwać odwołania cykliczne między wystąpieniami `shared_ptr`. Plik nagłówkowy: `<memory>`. Aby uzyskać więcej informacji, zobacz [How to: Create and Use Weak_ptr Instances](how-to-create-and-use-weak-ptr-instances.md) and [weak_ptr Class](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Inteligentne wskaźniki dla obiektów COM (klasyczne programowanie systemu Windows)

Kiedy pracujesz z obiektami COM, zawiń wskaźniki interfejsu w odpowiedni typ inteligentnego wskaźnika. Active Template Library (ATL) definiuje kilka inteligentnych wskaźników do różnych celów. Można również użyć typu inteligentnego wskaźnika `_com_ptr_t`, którego kompilator używa, gdy tworzy klasy otoki z plików. tlb. To najlepszy wybór, jeśli nie chcesz dołączyć plików nagłówkowych ATL.

[Klasa CComPtr](../atl/reference/ccomptr-class.md)<br/>
Użyj tego, jeżeli nie możesz użyć ATL. Wykonuje zliczanie odwołań przy użyciu metod `AddRef` i `Release`. Aby uzyskać więcej informacji, zobacz [How to: Create and use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComQIPtr](../atl/reference/ccomqiptr-class.md)<br/>
Przypomina `CComPtr`, ale również zapewnia uproszczoną składnię do wywoływania `QueryInterface` na obiektach COM. Aby uzyskać więcej informacji, zobacz [How to: Create and use CComPtr and CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComHeapPtr](../atl/reference/ccomheapptr-class.md)<br/>
Inteligentny wskaźnik do obiektów, które używają `CoTaskMemFree` do zwalniania pamięci.

[Klasa CComGITPtr](../atl/reference/ccomgitptr-class.md)<br/>
Inteligentny wskaźnik dla interfejsów, które są uzyskiwane z tabeli interfejsu globalnego (GIT).

[_com_ptr_t, klasa](com-ptr-t-class.md)<br/>
Przypomina `CComQIPtr` w funkcji, ale nie zależy od nagłówków ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>Inteligentne wskaźniki ATL dla obiektów POCO

Oprócz inteligentnych wskaźników dla obiektów COM, ATL definiuje również inteligentne wskaźniki i kolekcje inteligentnych wskaźników dla zwykłych starych C++ obiektów (POCO). W klasycznym programowaniu systemu Windows te typy są przydatnymi alternatywami dla C++ standardowych kolekcji bibliotek, szczególnie gdy Przenoszenie kodu nie jest wymagane lub gdy nie chcesz mieszać modeli programowania biblioteki C++ standardowej i ATL.

[Klasa CAutoPtr](../atl/reference/cautoptr-class.md)<br/>
Inteligentny wskaźnik, który wymusza unikatowe własności poprzez przeniesienie własności na kopię. Porównywalne do przestarzałej klasy `std::auto_ptr`.

[Klasa CHeapPtr](../atl/reference/cheapptr-class.md)<br/>
Inteligentny wskaźnik dla obiektów, które są przydzielone przy użyciu funkcji C [malloc](../c-runtime-library/reference/malloc.md) .

[Klasa CAutoVectorPtr](../atl/reference/cautovectorptr-class.md)<br/>
Inteligentny wskaźnik dla tablic, które są przydzielone za pomocą `new[]`.

[Klasa CAutoPtrArray](../atl/reference/cautoptrarray-class.md)<br/>
Klasa, która hermetyzuje tablicę elementów `CAutoPtr`.

[Klasa CAutoPtrList](../atl/reference/cautoptrlist-class.md)<br/>
Klasa, która hermetyzuje metody manipulowania listą węzłów `CAutoPtr`.

## <a name="see-also"></a>Zobacz także

[Wskaźniki](pointers-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
