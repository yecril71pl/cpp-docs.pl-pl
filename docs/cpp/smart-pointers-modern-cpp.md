---
title: Inteligentne wskaźniki (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9142ba85a78259c0a6e5ae06f3745d414e62e908
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425631"
---
# <a name="smart-pointers-modern-c"></a>Wskaźniki inteligentne (Modern C++)

W nowoczesnym programowaniu C++, standardowa biblioteka zawiera *inteligentne wskaźniki*, które są używane, aby mieć pewność, że programy są wolne od pamięci i wycieki zasobów są bezpieczne pod względem wyjątków.

## <a name="uses-for-smart-pointers"></a>Zastosowania inteligentnych wskaźników

Inteligentne wskaźniki są zdefiniowane w `std` przestrzeni nazw w [ \<pamięci >](../standard-library/memory.md) pliku nagłówka. Są niezwykle istotne w procesie [RAII](../cpp/objects-own-resources-raii.md) lub *inicjowania jest pozyskiwanie zasobów* idiomu programowania. Głównym celem tego idiomu jest zapewnienie, że pozyskiwanie zasobów występuje w tym samym czasie, co inicjacja obiektu, tak aby wszystkie zasoby dla tego obiektu były tworzone i gotowe w jednym wierszu kodu. W praktyce główną zasadą RAII jest dawanie na własność dowolnego zasobu z przyznaną stertą — na przykład dynamicznie przydzielonej pamięci lub uchwytów obiektu systemowego — obiektowi z przyznanym stosem, którego destruktor zawiera kod w celu usunięcia lub zwolnienia zasobów, a także związany z nim kod porządkujący.

W większości przypadków, podczas inicjowania surowego wskaźnika lub uchwytu zasobu w celu wskazania rzeczywistego zasobu, należy natychmiast przekazać wskaźnik do inteligentnego wskaźnika. W nowoczesnym C++, surowe wskaźniki są używane tylko w małych blokach kodu o ograniczonym zakresie, pętlach lub funkcjach pomocniczych, gdzie wydajność ma kluczowe znaczenie i nie ma możliwości popełnienia błędu w zakresie własności.

Poniższy przykład porównuje deklarację surowego wskaźnika z deklaracją inteligentnego wskaźnika.

[!code-cpp[smart_pointers_intro#1](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

Jak pokazano w przykładzie, inteligentny wskaźnik jest szablonem klasy, którą deklarujesz na stosie i inicjujesz przy użyciu surowego wskaźnika, który wskazuje na obiekt z przydzieloną stertą. Po zainicjowaniu inteligentnego wskaźnika, inteligentny wskaźnik jest właścicielem wskaźnika surowego. Oznacza to, że inteligentny wskaźnik jest odpowiedzialny za usunięcie pamięci określonej przez surowy wskaźnik. Destruktor inteligentnego wskaźnika zawiera wywołanie usunięcia, a ponieważ inteligentny wskaźnik jest zadeklarowany na stosie, jego destruktor jest wywołany, kiedy inteligentny wskaźnik wychodzi poza zakres, nawet jeśli później na stosie jest zgłoszony wyjątek.

Dostęp zhermetyzowanego wskaźnika za pomocą znanych operatorów wskaźnika, `->` i `*`, która klasa inteligentnego wskaźnika przeciążenia zwraca wskaźnik surowego zhermetyzowania.

Idiom inteligentnego wskaźnika języka C++ przypomina tworzenie obiektów w językach takich, jak C#: utwórz obiekt, a następnie pozwól systemowi zadbać o usunięcie go w odpowiednim czasie. Różnica polega na tym, że w tle nie działa żaden odrębny moduł odśmiecania; pamięć jest zarządzana przez standardowe zasady zakresu C++, tak że środowisko wykonawcze jest szybsze i wydajniejsze.

> [!IMPORTANT]
>  Zawsze twórz inteligentne wskaźniki w osobnym wierszu kodu, nigdy na liście parametrów, tak aby nie wystąpił niewielki wyciek zasobów z powodu pewnych reguł alokacji listy parametrów.

W poniższym przykładzie przedstawiono sposób `unique_ptr` typ inteligentnego wskaźnika standardowej biblioteki C++ może być użyty do hermetyzacji wskaźnika do dużego obiektu.

[!code-cpp[smart_pointers_intro#2](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

W przykładzie pokazano niezbędne kroki używania inteligentnych wskaźników.

1. Zadeklaruj inteligentny wskaźnik jako zmienną automatyczną (lokalną). (Nie używaj **nowe** lub `malloc` wyrażenia samego inteligentnego wskaźnika.)

1. W parametrze typu określ typ wskazywanego zhermetyzowanego wskaźnika.

1. Przekaż surowy wskaźnik do **nowe**-obiektu w Konstruktorze sprytnego wskaźnika. (Niektóre funkcje narzędziowe lub konstruktory inteligentnego wskaźnika robią to automatycznie.)

1. Użyj przeciążonego `->` i `*` operatory dostępu do obiektu.

1. Niech inteligentny wskaźnik usunie obiekt.

Inteligentne wskaźniki są zaprojektowane tak, aby były maksymalnie efektywne, zarówno w zakresie pamięci, jak i wydajności. Na przykład, jedyny element członkowski w `unique_ptr` to zhermetyzowany wskaźnik. Oznacza to, że `unique_ptr` jest dokładnie taki sam rozmiar jak ten wskaźnik, cztery bity lub osiem bitów. Dostęp do zhermetyzowanego wskaźnika za pomocą inteligentnego wskaźnika przeciążenia * i -> operatorzy nie są znacznie wolniejsze niż dostęp do surowych wskaźników bezpośrednio.

Inteligentne wskaźniki mają swoje własne funkcje członkowskie, które są dostępne przy użyciu notacji „kropkowej”. Na przykład niektóre inteligentne wskaźniki standardowej biblioteki języka C++ mają funkcję resetowania elementu członkowskiego, która uwalnia własność wskaźnika. Jest to przydatne, kiedy chcesz zwolnić pamięć zajmowaną przez inteligentny wskaźnik, zanim inteligentny wskaźnik wyjdzie poza zakres, jak pokazano w poniższym przykładzie.

[!code-cpp[smart_pointers_intro#3](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

Inteligentne wskaźniki umożliwiają zwykle bezpośredni dostęp do własnego surowego wskaźnika. Inteligentne wskaźniki standardowej biblioteki języka C++ mają `get` funkcja elementu członkowskiego, w tym celu i `CComPtr` ma publiczną `p` składowej klasy. Zapewniając bezpośredni dostęp do podstawowych wskaźników, możesz skorzystać z inteligentnego wskaźnika do zarządzania pamięcią we własnym kodzie i nadal przekazywać surowy wskaźnik do kodu, który nie obsługuje inteligentnych wskaźników.

[!code-cpp[smart_pointers_intro#4](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>Rodzaje inteligentnych wskaźników

Poniższa sekcja podsumowuje różne rodzaje inteligentnych wskaźników, które są dostępne w środowisku programowania Windows, i opisuje, kiedy ich używać.

### <a name="c-standard-library-smart-pointers"></a>C++ Standard Library inteligentnych wskaźników

Używaj tych inteligentnych wskaźników jako pierwszych, w celu hermetyzacji wskaźników jako zwykłych starych obiektów C++ (Plain Old C++ Objects — POCO).

- `unique_ptr` Zezwala na dokładnie jednego właściciela podstawowego wskaźnika. Użyj jako domyślnego wyboru dla POCO, chyba że wiesz, w przypadku niektórych wymaganych `shared_ptr`. Może być przeniesiony do nowego właściciela, ale nie kopiowany lub udostępniony. Zastępuje `auto_ptr`, które jest przestarzałe. Porównaj `boost::scoped_ptr`. `unique_ptr` jest mały i wydajny; rozmiar to jeden wskaźnik i obsługuje odwołania rvalue dla ostatniego wstawienia i wydobycia z kolekcji standardowej biblioteki języka C++. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wystąpień unique_ptr i korzystanie](../cpp/how-to-create-and-use-unique-ptr-instances.md) i [unique_ptr — klasa](../standard-library/unique-ptr-class.md).

- `shared_ptr` Dokumentacja inteligentny wskaźnik zliczonych. Użyj, jeżeli chcesz przypisać jeden surowy wskaźnik wielu właścicielom, na przykład, kiedy zwracasz kopię wskaźnika z kontenera, ale chcesz zatrzymać oryginał. Surowy wskaźnik nie jest usuwana, dopóki wszystkie `shared_ptr` właściciele zniknie z zakresu lub w inny sposób zrezygnują własności. Rozmiar to dwa wskaźniki; jeden dla obiektu i jeden dla współdzielonego bloku kontroli, który zawiera licznik odwołań. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wystąpień shared_ptr i korzystanie](../cpp/how-to-create-and-use-shared-ptr-instances.md) i [shared_ptr — klasa](../standard-library/shared-ptr-class.md).

- `weak_ptr` Szczególny inteligentny wskaźnik używany w połączeniu z `shared_ptr`. A `weak_ptr` zapewnia dostęp do obiektu, który jest własnością jednego lub więcej `shared_ptr` wystąpienia, ale nie uczestniczy w zliczaniu odwołań. Używaj, jeżeli chcesz obserwować obiekt, ale nie wymagasz, aby pozostał aktywny. Wymagane w niektórych przypadkach, aby złamać odwołania cykliczne między `shared_ptr` wystąpień. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wystąpień weak_ptr i korzystanie](../cpp/how-to-create-and-use-weak-ptr-instances.md) i [weak_ptr, klasa](../standard-library/weak-ptr-class.md).

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>{1&gt;Inteligentne wskaźniki dla obiektów COM (klasyczne programowanie Windows)&lt;1}

Kiedy pracujesz z obiektami COM, zawiń wskaźniki interfejsu w odpowiedni typ inteligentnego wskaźnika. Active Template Library (ATL) definiuje kilka inteligentnych wskaźników do różnych celów. Można również użyć `_com_ptr_t` typ inteligentnego wskaźnika, której kompilator używa podczas tworzenia klas otoki z plików .tlb. To najlepszy wybór, jeśli nie chcesz dołączyć plików nagłówkowych ATL.

[Klasa CComPtr](../atl/reference/ccomptr-class.md)<br/>
Użyj tego, jeżeli nie możesz użyć ATL. Wykonuje liczenia odwołań przy użyciu `AddRef` i `Release` metody. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i wykorzystania wystąpień CComPtr i CComQIPtr](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComQIPtr](../atl/reference/ccomqiptr-class.md)<br/>
Przypomina `CComPtr` , ale także zapewnia uproszczoną składnię do wywoływania `QueryInterface` obiektów COM. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i wykorzystania wystąpień CComPtr i CComQIPtr](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).

[Klasa CComHeapPtr](../atl/reference/ccomheapptr-class.md)<br/>
Inteligentny wskaźnik do obiektów, które używają `CoTaskMemFree` aby zwolnić pamięć.

[Klasa CComGITPtr](../atl/reference/ccomgitptr-class.md)<br/>
Inteligentny wskaźnik dla interfejsów, które są uzyskiwane z tabeli interfejsu globalnego (GIT).

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)<br/>
Przypomina `CComQIPtr` funkcji, ale nie zależy od nagłówków ATL.

### <a name="atl-smart-pointers-for-poco-objects"></a>{1&gt;Inteligentne wskaźniki ATL dla obiektów POCO&lt;1}

Oprócz inteligentnych wskaźników dla obiektów COM, ATL także definiuje inteligentne wskaźniki i kolekcje inteligentnych wskaźników dla zwykłych starych obiektów C++. W klasycznym programowaniu Windows, te typy są użyteczną do kolekcji standardowej biblioteki języka C++, szczególnie w przypadku, gdy przenoszenie kodu nie jest wymagane lub gdy użytkownik nie chce mieszać modeli programowania standardowej biblioteki języka C++ i ATL.

[Klasa CAutoPtr](../atl/reference/cautoptr-class.md)<br/>
Inteligentny wskaźnik, który wymusza unikatowe własności poprzez przeniesienie własności na kopię. Porównywalne do zaniechanej `std::auto_ptr` klasy.

[Klasa CHeapPtr](../atl/reference/cheapptr-class.md)<br/>
Inteligentny wskaźnik dla obiektów, które są przydzielane przy użyciu języka C [— funkcja malloc](../c-runtime-library/reference/malloc.md) funkcji.

[Klasa CAutoVectorPtr](../atl/reference/cautovectorptr-class.md)<br/>
Inteligentny wskaźnik dla tablic, które są przydzielane przy użyciu `new[]`.

[Klasa CAutoPtrArray](../atl/reference/cautoptrarray-class.md)<br/>
Klasa, która hermetyzuje tablicę `CAutoPtr` elementów.

[Klasa CAutoPtrList](../atl/reference/cautoptrlist-class.md)<br/>
Klasa, która hermetyzuje metody do manipulowania listą `CAutoPtr` węzłów.

## <a name="see-also"></a>Zobacz także

[Witamy z powrotem w C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)