---
title: Wskaźniki inteligentne (Modern C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: 0e93ce033649f5654595ae23a5f10da347879718
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365548"
---
# <a name="smart-pointers-modern-c"></a>Wskaźniki inteligentne (Modern C++)

W nowoczesnym programowaniu języka C++ biblioteka standardowa zawiera *inteligentne wskaźniki,* które służą do zapewnienia, że programy są wolne od przecieków pamięci i zasobów i są bezpieczne dla wyjątków.

## <a name="uses-for-smart-pointers"></a>Zastosowania inteligentnych wskaźników

Inteligentne wskaźniki są definiowane w obszarze `std` nazw w [ \<pamięci>](../standard-library/memory.md) pliku nagłówka. Są one kluczowe dla [RAII](objects-own-resources-raii.md) lub *pozyskiwania zasobów jest inicjowanie* programowania idiom. Głównym celem tego idiomu jest zapewnienie, że pozyskiwanie zasobów występuje w tym samym czasie, co inicjacja obiektu, tak aby wszystkie zasoby dla tego obiektu były tworzone i gotowe w jednym wierszu kodu. W praktyce główną zasadą RAII jest dawanie na własność dowolnego zasobu z przyznaną stertą — na przykład dynamicznie przydzielonej pamięci lub uchwytów obiektu systemowego — obiektowi z przyznanym stosem, którego destruktor zawiera kod w celu usunięcia lub zwolnienia zasobów, a także związany z nim kod porządkujący.

W większości przypadków, podczas inicjowania surowego wskaźnika lub uchwytu zasobu w celu wskazania rzeczywistego zasobu, należy natychmiast przekazać wskaźnik do inteligentnego wskaźnika. W nowoczesnym C++, surowe wskaźniki są używane tylko w małych blokach kodu o ograniczonym zakresie, pętlach lub funkcjach pomocniczych, gdzie wydajność ma kluczowe znaczenie i nie ma możliwości popełnienia błędu w zakresie własności.

Poniższy przykład porównuje deklarację surowego wskaźnika z deklaracją inteligentnego wskaźnika.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak pokazano w przykładzie, inteligentny wskaźnik jest szablonem klasy, którą deklarujesz na stosie i inicjujesz przy użyciu surowego wskaźnika, który wskazuje na obiekt z przydzieloną stertą. Po zainicjowaniu inteligentnego wskaźnika, inteligentny wskaźnik jest właścicielem wskaźnika surowego. Oznacza to, że inteligentny wskaźnik jest odpowiedzialny za usunięcie pamięci określonej przez surowy wskaźnik. Destruktor inteligentnego wskaźnika zawiera wywołanie usunięcia, a ponieważ inteligentny wskaźnik jest zadeklarowany na stosie, jego destruktor jest wywołany, kiedy inteligentny wskaźnik wychodzi poza zakres, nawet jeśli później na stosie jest zgłoszony wyjątek.

Dostęp do zhermetyzowanego wskaźnika `->` przy `*`użyciu znanych operatorów wskaźnika i , które przeciążenia klasy inteligentnego wskaźnika zwraca zhermetyzowany wskaźnik nieprzetworzony.

Idiom inteligentnego wskaźnika języka C++ przypomina tworzenie obiektów w językach takich, jak C#: utwórz obiekt, a następnie pozwól systemowi zadbać o usunięcie go w odpowiednim czasie. Różnica polega na tym, że w tle nie działa żaden odrębny moduł odśmiecania; pamięć jest zarządzana przez standardowe zasady zakresu C++, tak że środowisko wykonawcze jest szybsze i wydajniejsze.

> [!IMPORTANT]
> Zawsze twórz inteligentne wskaźniki w osobnym wierszu kodu, nigdy na liście parametrów, tak aby nie wystąpił niewielki wyciek zasobów z powodu pewnych reguł alokacji listy parametrów.

W poniższym przykładzie pokazano, jak typ inteligentnego `unique_ptr` wskaźnika z biblioteki standardowej języka C++ może służyć do hermetyzacji wskaźnika do dużego obiektu.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

W przykładzie pokazano niezbędne kroki używania inteligentnych wskaźników.

1. Zadeklaruj inteligentny wskaźnik jako zmienną automatyczną (lokalną). (Nie należy **new** używać `malloc` nowego lub wyrażenia na samym inteligentnym wskaźniku).

1. W parametrze typu określ typ wskazywanego zhermetyzowanego wskaźnika.

1. Przekaż nieprzetworzony wskaźnik do **nowego**obiektu -ed w konstruktorze inteligentnego wskaźnika. (Niektóre funkcje narzędziowe lub konstruktory inteligentnego wskaźnika robią to automatycznie.)

1. Użyj przeciążonych `->` `*` operatorów, aby uzyskać dostęp do obiektu.

1. Niech inteligentny wskaźnik usunie obiekt.

Inteligentne wskaźniki są zaprojektowane tak, aby były maksymalnie efektywne, zarówno w zakresie pamięci, jak i wydajności. Na przykład jedynym elementem `unique_ptr` członkowskim danych jest zhermetyzowany wskaźnik. Oznacza to, że `unique_ptr` jest dokładnie taki sam rozmiar jak ten wskaźnik, cztery bajty lub osiem bajtów. Uzyskiwanie dostępu do zhermetyzowanego wskaźnika przy użyciu przeciążenia inteligentnego wskaźnika * i operatorów -> nie jest znacznie wolniejsze niż bezpośredni dostęp do nieprzetworzonych wskaźników.

Inteligentne wskaźniki mają własne funkcje członkowskie, które są dostępne za pomocą notacji "kropka". Na przykład niektóre wskaźniki inteligentne biblioteki standardowej języka C++ mają funkcję resetowania elementu członkowskiego, która zwalnia własność wskaźnika. Jest to przydatne, kiedy chcesz zwolnić pamięć zajmowaną przez inteligentny wskaźnik, zanim inteligentny wskaźnik wyjdzie poza zakres, jak pokazano w poniższym przykładzie.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentne wskaźniki umożliwiają zwykle bezpośredni dostęp do własnego surowego wskaźnika. Wskaźniki inteligentne biblioteki standardowej `get` języka C++ mają `CComPtr` w `p` tym celu funkcję elementu członkowskiego i mają element członkowski klasy publicznej. Zapewniając bezpośredni dostęp do podstawowych wskaźników, możesz skorzystać z inteligentnego wskaźnika do zarządzania pamięcią we własnym kodzie i nadal przekazywać surowy wskaźnik do kodu, który nie obsługuje inteligentnych wskaźników.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Rodzaje inteligentnych wskaźników

Poniższa sekcja podsumowuje różne rodzaje inteligentnych wskaźników, które są dostępne w środowisku programowania Windows, i opisuje, kiedy ich używać.

### <a name="c-standard-library-smart-pointers"></a>Inteligentne wskaźniki biblioteki standardowej języka C++

Używaj tych inteligentnych wskaźników jako pierwszych, w celu hermetyzacji wskaźników jako zwykłych starych obiektów C++ (Plain Old C++ Objects — POCO).

- `unique_ptr`<br/>
   Pozwala na dokładnie jednego właściciela podstawowego wskaźnika. Użyj jako domyślnego wyboru dla POCO, chyba `shared_ptr`że wiesz na pewno, że potrzebujesz pliku . Może być przeniesiony do nowego właściciela, ale nie kopiowany lub udostępniony. Zastępuje `auto_ptr`, który jest przestarzały. Porównaj `boost::scoped_ptr`z . `unique_ptr`jest mały i wydajny; rozmiar jest jeden wskaźnik i obsługuje rvalue odwołania do szybkiego wstawiania i pobierania z kolekcji biblioteki standardowej języka C++. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i używanie unique_ptr wystąpień](how-to-create-and-use-unique-ptr-instances.md) i [unique_ptr klasa](../standard-library/unique-ptr-class.md).

- `shared_ptr`<br/>
   Inteligentny wskaźnik zliczonych odwołań. Użyj, jeżeli chcesz przypisać jeden surowy wskaźnik wielu właścicielom, na przykład, kiedy zwracasz kopię wskaźnika z kontenera, ale chcesz zatrzymać oryginał. Surowy wskaźnik nie jest `shared_ptr` usuwany, dopóki wszyscy właściciele nie znikną z zakresu lub w inny sposób nie zdącą własności. Rozmiar to dwa wskaźniki; jeden dla obiektu i jeden dla współdzielonego bloku kontroli, który zawiera licznik odwołań. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i używanie shared_ptr wystąpień](how-to-create-and-use-shared-ptr-instances.md) i [shared_ptr klasa](../standard-library/shared-ptr-class.md).

- `weak_ptr`<br/>
    Specjalny wskaźnik inteligentny do użytku `shared_ptr`w połączeniu z . A `weak_ptr` zapewnia dostęp do obiektu, który `shared_ptr` jest własnością jednego lub więcej wystąpień, ale nie uczestniczy w zliczaniu odwołań. Używaj, jeżeli chcesz obserwować obiekt, ale nie wymagasz, aby pozostał aktywny. Wymagane w niektórych przypadkach do `shared_ptr` przerwania odwołań cyklicznych między wystąpieniami. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i używanie weak_ptr wystąpień](how-to-create-and-use-weak-ptr-instances.md) i [weak_ptr klasa](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>Inteligentne wskaźniki dla obiektów COM (klasyczne programowanie systemu Windows)

Kiedy pracujesz z obiektami COM, zawiń wskaźniki interfejsu w odpowiedni typ inteligentnego wskaźnika. Active Template Library (ATL) definiuje kilka inteligentnych wskaźników do różnych celów. Można również użyć `_com_ptr_t` typu wskaźnika inteligentnego, który kompilator używa podczas tworzenia klas otoki z plików .tlb. To najlepszy wybór, jeśli nie chcesz dołączyć plików nagłówkowych ATL.

[Klasa CComPtr](../atl/reference/ccomptr-class.md)<br/>
Użyj tego, jeżeli nie możesz użyć ATL. Wykonuje zliczanie odwołań przy użyciu `AddRef` i `Release` metody. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i używanie wystąpień CComPtr i CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComQIPtr](../atl/reference/ccomqiptr-class.md)<br/>
Przypomina, `CComPtr` ale również zapewnia uproszczoną `QueryInterface` składnię wywoływania obiektów COM. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i używanie wystąpień CComPtr i CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComHeapPtr](../atl/reference/ccomheapptr-class.md)<br/>
Inteligentny wskaźnik do `CoTaskMemFree` obiektów, które używają do zwolnienia pamięci.

[Klasa CComGITPtr](../atl/reference/ccomgitptr-class.md)<br/>
Inteligentny wskaźnik dla interfejsów, które są uzyskiwane z tabeli interfejsu globalnego (GIT).

[_com_ptr_t — Klasa](com-ptr-t-class.md)<br/>
Przypomina `CComQIPtr` funkcjonalność, ale nie zależy od nagłówków ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>Inteligentne wskaźniki ATL dla obiektów POCO

Oprócz inteligentnych wskaźników dla obiektów COM, ATL definiuje również inteligentne wskaźniki i kolekcje inteligentnych wskaźników dla zwykłych starych obiektów C++ (POCO). W klasycznym programowaniu systemu Windows te typy są przydatne alternatywy dla kolekcji biblioteki standardowej języka C++, zwłaszcza gdy przenośność kodu nie jest wymagana lub gdy nie chcesz mieszać modeli programowania biblioteki standardowej języka C++ i ATL.

[Klasa CAutoPtr](../atl/reference/cautoptr-class.md)<br/>
Inteligentny wskaźnik, który wymusza unikatowe własności poprzez przeniesienie własności na kopię. Porównywalne do przestarzałej `std::auto_ptr` klasy.

[Klasa CHeapPtr](../atl/reference/cheapptr-class.md)<br/>
Inteligentny wskaźnik dla obiektów, które są przydzielane przy użyciu funkcji [Malloc](../c-runtime-library/reference/malloc.md) C.

[Klasa CAutoVectorPtr](../atl/reference/cautovectorptr-class.md)<br/>
Inteligentny wskaźnik dla tablic, które `new[]`są przydzielane przy użyciu programu .

[Klasa CAutoPtrArray](../atl/reference/cautoptrarray-class.md)<br/>
Klasa, która hermetyzuje `CAutoPtr` tablicę elementów.

[Klasa CAutoPtrList](../atl/reference/cautoptrlist-class.md)<br/>
Klasa, która hermetyzuje metody manipulowania listą węzłów. `CAutoPtr`

## <a name="see-also"></a>Zobacz też

[Wskaźniki](pointers-cpp.md)<br/>
[Odwołanie do języka języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)
