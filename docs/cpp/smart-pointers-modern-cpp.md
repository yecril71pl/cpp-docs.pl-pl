---
title: "Inteligentne wskaźników (Modern C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e5883cc7f028c2d64c038a2cdbd9b8365b7e61d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="smart-pointers-modern-c"></a>Wskaźniki inteligentne (Modern C++)
W nowoczesnych programowania w języku C++, biblioteki standardowej zawiera *wskaźniki inteligentne*, które są używane do zapewnienia, że programy są wolnej pamięci i przecieków zasobów i są bezpieczne dla wyjątku.  
  
## <a name="uses-for-smart-pointers"></a>Zastosowania inteligentnych wskaźników  
 Wskaźniki inteligentne są zdefiniowane w `std` przestrzeni nazw w [ \<pamięci >](../standard-library/memory.md) pliku nagłówka. Są niezwykle istotne w procesie [RAII](../cpp/objects-own-resources-raii.md) lub *Initialialization jest nabywania zasobów* idiom programowania. Głównym celem tego idiomu jest zapewnienie, że pozyskiwanie zasobów występuje w tym samym czasie, co inicjacja obiektu, tak aby wszystkie zasoby dla tego obiektu były tworzone i gotowe w jednym wierszu kodu. W praktyce główną zasadą RAII jest dawanie na własność dowolnego zasobu z przyznaną stertą — na przykład dynamicznie przydzielonej pamięci lub uchwytów obiektu systemowego — obiektowi z przyznanym stosem, którego destruktor zawiera kod w celu usunięcia lub zwolnienia zasobów, a także związany z nim kod porządkujący.  
  
 W większości przypadków, podczas inicjowania surowego wskaźnika lub uchwytu zasobu w celu wskazania rzeczywistego zasobu, należy natychmiast przekazać wskaźnik do inteligentnego wskaźnika. W nowoczesnym C++, surowe wskaźniki są używane tylko w małych blokach kodu o ograniczonym zakresie, pętlach lub funkcjach pomocniczych, gdzie wydajność ma kluczowe znaczenie i nie ma możliwości popełnienia błędu w zakresie własności.  
  
 Poniższy przykład porównuje deklarację surowego wskaźnika z deklaracją inteligentnego wskaźnika.  
  
 [!code-cpp[smart_pointers_intro#1](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]  
  
 Jak pokazano w przykładzie, inteligentny wskaźnik jest szablonem klasy, którą deklarujesz na stosie i inicjujesz przy użyciu surowego wskaźnika, który wskazuje na obiekt z przydzieloną stertą. Po zainicjowaniu inteligentnego wskaźnika, inteligentny wskaźnik jest właścicielem wskaźnika surowego. Oznacza to, że inteligentny wskaźnik jest odpowiedzialny za usunięcie pamięci określonej przez surowy wskaźnik. Destruktor inteligentnego wskaźnika zawiera wywołanie usunięcia, a ponieważ inteligentny wskaźnik jest zadeklarowany na stosie, jego destruktor jest wywołany, kiedy inteligentny wskaźnik wychodzi poza zakres, nawet jeśli później na stosie jest zgłoszony wyjątek.  
  
 Dostęp przy użyciu operatorów znanych wskaźnika hermetyzowany wskaźnika `->` i `*`, która klasa wskaźnika inteligentnego overloads do zwrócenia hermetyzowany wskaźnika raw.  
  
 Idiom inteligentnego wskaźnika języka C++ przypomina tworzenie obiektów w językach takich, jak C#: utwórz obiekt, a następnie pozwól systemowi zadbać o usunięcie go w odpowiednim czasie. Różnica polega na tym, że w tle nie działa żaden odrębny moduł odśmiecania; pamięć jest zarządzana przez standardowe zasady zakresu C++, tak że środowisko wykonawcze jest szybsze i wydajniejsze.  
  
> [!IMPORTANT]
>  Zawsze twórz inteligentne wskaźniki w osobnym wierszu kodu, nigdy na liście parametrów, tak aby nie wystąpił niewielki wyciek zasobów z powodu pewnych reguł alokacji listy parametrów.  
  
 W poniższym przykładzie przedstawiono sposób `unique_ptr` typu wskaźnika inteligentnego z standardowa biblioteka C++ może służyć do Hermetyzowanie wskaźnik do dużego obiektu.  
  
 [!code-cpp[smart_pointers_intro#2](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]  
  
 W przykładzie pokazano niezbędne kroki używania inteligentnych wskaźników.  
  
1.  Zadeklaruj inteligentny wskaźnik jako zmienną automatyczną (lokalną). (Nie należy używać `new` lub `malloc` wyrażenia wskaźnika inteligentnego samej siebie.)  
  
2.  W parametrze typu określ typ wskazywanego zhermetyzowanego wskaźnika.  
  
3.  Nieprzetworzona wskaźnikiem do `new`-ed obiektu w Konstruktorze wskaźnika inteligentnego. (Niektóre funkcje narzędziowe lub konstruktory inteligentnego wskaźnika robią to automatycznie.)  
  
4.  Użyj przeciążone `->` i `*` operatory dostępu do tego obiektu.  
  
5.  Niech inteligentny wskaźnik usunie obiekt.  
  
 Inteligentne wskaźniki są zaprojektowane tak, aby były maksymalnie efektywne, zarówno w zakresie pamięci, jak i wydajności. Na przykład element członkowski danych tylko w `unique_ptr` jest hermetyzowany wskaźnika. Oznacza to, że `unique_ptr` jest taki sam rozmiar, jako wskaźnik, cztery bajty lub 8 bajtów. Dostęp do wskaźnika hermetyzowany przy użyciu wskaźnika inteligentnego przeciążony * i -> operatorów nie jest znacznie niższej niż bezpośrednio dostęp do nieprzetworzonej wskaźników.  
  
 Inteligentne wskaźniki mają swoje własne funkcje członkowskie, które są dostępne przy użyciu notacji „kropkowej”. Na przykład niektóre wskaźniki inteligentne standardowa biblioteka C++ ma resetowania funkcji członkowskiej, który zwalnia własność wskaźnika. Jest to przydatne, kiedy chcesz zwolnić pamięć zajmowaną przez inteligentny wskaźnik, zanim inteligentny wskaźnik wyjdzie poza zakres, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[smart_pointers_intro#3](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]  
  
 Inteligentne wskaźniki umożliwiają zwykle bezpośredni dostęp do własnego surowego wskaźnika. Ma wskaźniki inteligentne standardowa biblioteka C++ `get` funkcji członkowskiej, w tym celu i `CComPtr` ma publiczny `p` elementu członkowskiego klasy. Zapewniając bezpośredni dostęp do podstawowych wskaźników, możesz skorzystać z inteligentnego wskaźnika do zarządzania pamięcią we własnym kodzie i nadal przekazywać surowy wskaźnik do kodu, który nie obsługuje inteligentnych wskaźników.  
  
 [!code-cpp[smart_pointers_intro#4](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]  
  
## <a name="kinds-of-smart-pointers"></a>Rodzaje inteligentnych wskaźników  
 Poniższa sekcja podsumowuje różne rodzaje inteligentnych wskaźników, które są dostępne w środowisku programowania Windows, i opisuje, kiedy ich używać.  
  
 **Wskaźniki inteligentne biblioteki C++ Standard**  
 Używaj tych inteligentnych wskaźników jako pierwszych, w celu hermetyzacji wskaźników jako zwykłych starych obiektów C++ (Plain Old C++ Objects — POCO).  
  
-   `unique_ptr`   
     Pozwala na dokładnie jednego właściciela podstawowego wskaźnika. Używanie jako domyślny wybór POCO znając dla niektórych wymaganych `shared_ptr`. Może być przeniesiony do nowego właściciela, ale nie kopiowany lub udostępniony. Zastępuje `auto_ptr`, które jest przestarzałe. Porównaj z `boost::scoped_ptr`. `unique_ptr`jest mała i wydajne; rozmiar jest jeden wskaźnik i obsługuje odwołań do r-wartości do wstawienia szybkiego i pobierania z kolekcji standardowa biblioteka C++. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wystąpień unique_ptr i korzystanie](../cpp/how-to-create-and-use-unique-ptr-instances.md) i [unique_ptr — klasa](../standard-library/unique-ptr-class.md).  
  
-   `shared_ptr`   
     Inteligentny wskaźnik zliczonych odwołań. Użyj, jeżeli chcesz przypisać jeden surowy wskaźnik wielu właścicielom, na przykład, kiedy zwracasz kopię wskaźnika z kontenera, ale chcesz zatrzymać oryginał. Nieprzetworzone wskaźnika nie są usuwane aż wszystkie `shared_ptr` właścicieli przeszły poza zakresem wartości lub mieć w przeciwnym razie własności. Rozmiar to dwa wskaźniki; jeden dla obiektu i jeden dla współdzielonego bloku kontroli, który zawiera licznik odwołań. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wystąpień shared_ptr i korzystanie](../cpp/how-to-create-and-use-shared-ptr-instances.md) i [shared_ptr — klasa](../standard-library/shared-ptr-class.md).  
  
-   `weak_ptr`   
    Specjalny przypadek wskaźnika inteligentnego do użycia w połączeniu z `shared_ptr`. A `weak_ptr` zapewnia dostęp do obiektu, który jest właścicielem co najmniej jeden `shared_ptr` wystąpienia, ale nie uczestniczy w liczenie odwołań. Używaj, jeżeli chcesz obserwować obiekt, ale nie wymagasz, aby pozostał aktywny. Wymagane w niektórych przypadkach można przerwać cykliczne odwołanie pomiędzy `shared_ptr` wystąpień. Plik nagłówka: `<memory>`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie wystąpień weak_ptr i korzystanie](../cpp/how-to-create-and-use-weak-ptr-instances.md) i [weak_ptr — klasa](../standard-library/weak-ptr-class.md).  
  
 **Wskaźniki inteligentne dla obiektów COM (Programowanie systemu Windows)**  
 Kiedy pracujesz z obiektami COM, zawiń wskaźniki interfejsu w odpowiedni typ inteligentnego wskaźnika. Active Template Library (ATL) definiuje kilka inteligentnych wskaźników do różnych celów. Można również użyć `_com_ptr_t` typ wskaźnika inteligentnego, który używa kompilatora podczas tworzenia klasy otoki z plików .tlb. To najlepszy wybór, jeśli nie chcesz dołączyć plików nagłówkowych ATL.  
  
 [Klasa CComPtr](../atl/reference/ccomptr-class.md)  
 Użyj tego, jeżeli nie możesz użyć ATL. Wykonuje Zliczanie przy użyciu `AddRef` i `Release` metody. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i użyj CComPtr i CComQIPtr wystąpień](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).  
  
 [Klasa CComQIPtr](../atl/reference/ccomqiptr-class.md)  
 Podobny `CComPtr` , ale również zapewnia uproszczoną składnię wywołania `QueryInterface` obiektów COM. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i użyj CComPtr i CComQIPtr wystąpień](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).  
  
 [Klasa CComHeapPtr](../atl/reference/ccomheapptr-class.md)  
 Wskaźnik inteligentny do obiektów, które `CoTaskMemFree` zwolnienia pamięci.  
  
 [Klasa CComGITPtr](../atl/reference/ccomgitptr-class.md)  
 Inteligentny wskaźnik dla interfejsów, które są uzyskiwane z tabeli interfejsu globalnego (GIT).  
  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)  
 Podobny `CComQIPtr` funkcji, ale nie zależy od nagłówki ATL.  
  
 **Wskaźniki inteligentne ATL dla obiektów POCO**  
 Oprócz inteligentnych wskaźników dla obiektów COM, ATL także definiuje inteligentne wskaźniki i kolekcje inteligentnych wskaźników dla zwykłych starych obiektów C++. W klasycznym programowania w języku systemu Windows, te typy są przydatne alternatywy dla kolekcji standardowa biblioteka C++, szczególnie w przypadku, gdy przenośność kodu nie jest wymagana lub gdy nie chcesz mieszać modele programowania standardowa biblioteka C++ i ATL.  
  
 [Klasa CAutoPtr](../atl/reference/cautoptr-class.md)  
 Inteligentny wskaźnik, który wymusza unikatowe własności poprzez przeniesienie własności na kopię. Porównywalna przestarzałe `std::auto_ptr` klasy.  
  
 [Klasa CHeapPtr](../atl/reference/cheapptr-class.md)  
 Wskaźnika inteligentnego dla obiektów przydzielonych za pomocą C [— funkcja malloc](../c-runtime-library/reference/malloc.md) funkcji.  
  
 [Klasa CAutoVectorPtr](../atl/reference/cautovectorptr-class.md)  
 Wskaźnika inteligentnego dla tablic, które są przydzielane za pomocą `new[]`.  
  
 [Klasa CAutoPtrArray](../atl/reference/cautoptrarray-class.md)  
 Klasa, która hermetyzuje tablicę `CAutoPtr` elementów.  
  
 [Klasa CAutoPtrList](../atl/reference/cautoptrlist-class.md)  
 Klasa, która hermetyzuje metody listę `CAutoPtr` węzłów.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)   
