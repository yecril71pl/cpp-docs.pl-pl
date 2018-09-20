---
title: Notacja rzutowania i z polecenia safe_cast&lt; &gt; | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88e8165bde08b65b4f078c4b48863c2088132fca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427867"
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Notacja rzutowania i z polecenia safe_cast&lt;&gt;

Notacja rzutowania zmienił się z zarządzanych rozszerzeń języka C++ do Visual C++.

Modyfikowanie istniejącej struktury to interfejs inne i trudniejsze niż umożliwiają utworzenie dobrze dopasowanego początkową strukturę. Ma mniejszą liczbę stopni swobody, a rozwiązanie dąży do kompromis między idealne restrukturyzacji i co to jest to możliwe, biorąc pod uwagę istniejące zależności strukturalnych.

Rozszerzenie języka jest inny przykład. Na początku lat 1990 jak zmiana orientacji obiektu programowania stało się ważne paradygmat potrzebę bezpiecznegop typu o takiej funkcji w języku C++ stało się naciśnięcie. Rzutowanie jest użytkownika niewirtualną, niejawną Konwersja klasy bazowej wskaźnik lub odwołanie do wskaźnika lub odwołania do klasy pochodnej. Rzutowanie wymaga jawnego rzutowania. Przyczyną jest to rzeczywisty typ wskaźnika klasy podstawowej aspektów środowiska uruchomieniowego; Kompilator w związku z tym nie może sprawdzić go. Lub zmienić, który, takiej funkcji, podobnie jak wywołanie funkcji wirtualnej wymaga pewnego rodzaju rozwiązania dynamiczne. Wywołuje to dwa pytania:

- Dlaczego rzutowania się niezbędne w paradygmaty zorientowanego na obiekt? Mechanizm funkcji wirtualnej jest niewystarczająca? Oznacza to, dlaczego nie jeden oświadczeń to potrzebę rzutowania (lub Rzutowanie dowolny) Błąd projektu?

- Dlaczego Obsługa rzutowania się problemem w języku C++? Przecież nie jest to problem występujący w językach obiektowych, takich jak Smalltalk (lub później, Java i C#)? Co to jest dotyczących języka C++, która sprawia, że obsługa funkcji downcast trudne?

Funkcja wirtualna reprezentuje określony algorytm zależne od typu wspólnego do rodziny typów. (Firma Microsoft nie rozważają interfejsów, które nie są obsługiwane w języku C++ ISO, ale są dostępne w CLR — programowanie i zawierające interesujące zamiast projektu). Projekt tej rodziny, który zazwyczaj jest reprezentowany przez hierarchię klas, w którym jest abstrakcyjna klasa bazowa deklarowanie wspólny interfejs (funkcji wirtualnych) i zestaw konkretnych klas pochodnych, które reprezentują rzeczywiste typy rodziny w aplikacji w domenie.

A `Light` hierarchii w domenie aplikacji komputera wygenerowane aplikacje CGI, na przykład mają wspólne atrybuty takie jak `color`, `intensity`, `position`, `on`, `off`i tak dalej. Jeden można kontrolować kilka światła, za pomocą wspólnego interfejsu, nie martwiąc się, czy określonego światła jest funkcja w centrum uwagi, światło kierunkowe, niekierunkowa (myśl słońce) lub może być drzwi wolierowego światła. W tym przypadku rzutowanie do określonego typu światła wykonywać jego interfejsu wirtualnego nie jest konieczne. W środowisku produkcyjnym jednak szybkość jest niezbędne. Jedna może być downcast i jawnie wywołać każdą metodę za dotarłam wykonywania śródwierszowego wywołań, mogą być wykonywane zamiast przy użyciu mechanizmu wirtualnego.

Jednym z powodów przypisania elementu podrzędnego w języku C++ jest tak, Pomiń wirtualnego mechanizm poinformowanie znaczące korzyści w wydajności środowiska uruchomieniowego. (Zwróć uwagę, że automatyzację ręcznego Optymalizacja aktywny obszar badań. Jednak jest trudne do rozwiązania niż zastępowanie jawne użycie `register` lub `inline` — słowo kluczowe.)

Drugi przyczynę downcast znajduje się poza podwójną charakter polimorfizmu. Jednym ze sposobów myślenia polimorfizmu jest są podzielone na pasywnym i dynamiczne pary formularzy.

Wywołanie wirtualnej (i takiej funkcji) reprezentuje dynamiczne używa polimorfizmu: jeden wykonuje akcję na podstawie rzeczywistego typu wskaźnika klasy podstawowej, w tym konkretnym przypadku wykonywanie programu.

Przypisywanie obiektu klasy pochodnej na wskaźnik jej klasy bazowej, jest jednak pasywnym formularza polimorfizmu; Polimorfizm używa jako mechanizm transportu. To jest głównym zastosowaniem `Object`, na przykład w wstępnie ogólnego CLR — programowanie. W przypadku pasywnie wskaźnika klasy podstawowej, wybrany dla transportu i przechowywania, zwykle udostępnia interfejs, który jest zbyt abstrakcyjna. `Object`, na przykład zapewnia około pięć metod za pośrednictwem jego interfejsu; Każde zachowanie dokładniejszą wymaga jawnego przypisania elementu podrzędnego. Na przykład jeśli chcemy dopasować kąt polecanych lub jego stawki dla jesienna wyłączone, firma Microsoft musiałaby downcast jawnie. Interfejs wirtualny w obrębie rodziny podtypy praktycznie nie może być nadzbiorem wszystkie możliwe metody wielu podrzędnych, a więc takiej funkcji zawsze będą potrzebne w ramach obiektowy język.

Jeśli downcast bezpiecznego funkcji jest wymagana w języku zorientowane obiektowo, a następnie Dlaczego trwało C++ tak długo, aby dodać jeden? Problem jest w sposób udostępnić informacje dotyczące typu run-time wskaźnika. W przypadku funkcji wirtualnej informacje czasu wykonywania ustawiono w dwóch częściach przez kompilator:

- Obiekt klasy zawiera wskaźnika elementu członkowskiego dodatkowe tabeli wirtualnej (zarówno na początku lub na końcu obiektu klasy; to ma historię interesujące sam w sobie) który zapewnia odpowiedni tabeli wirtualnej. Na przykład obiekt funkcji spotlight adresów wirtualnych tabelę funkcji spotlight, światło kierunkowe, kierunkowe światła tabeli wirtualnej i tak dalej

- Każda funkcja wirtualna ma skojarzoną stałej miejsca w tabeli, a rzeczywiste wystąpienie do wywołania, jest reprezentowane przez adres są przechowywane w tabeli. Na przykład wirtualnych `Light` destruktora może być skojarzona z gniazda 0, `Color` z gniazda 1 i tak dalej. Jest to wydajne, jeśli jest to mało strategii, ponieważ skonfigurowano w czasie kompilacji i reprezentuje minimalne obciążenie.

Ten problem, następnie jest jak udostępniać informacje o typie wskaźnika bez zmieniania rozmiaru wskaźników C++, przez dodanie drugiego adresu lub przez bezpośrednie dodanie jakiegoś typu kodowania. Nie jest dopuszczalne tych programistów (i programów) który zrezygnować z paradygmaty zorientowanego na obiekt - nadal spowodowało dominujący użytkowników. Inną możliwością było wprowadzenie specjalne wskaźnik do typu polimorficznej klasy, ale to może być mylące i utrudniają transfer zmieszać dwa, zwłaszcza w przypadku problemów arytmetyka wskaźnika. Nie byłoby możliwe do zaakceptowania Obsługa tabeli środowiska wykonawczego, które kojarzy każdego wskaźnika z jego obecnie skojarzony typ i dynamicznie aktualizowania.

Problem jest następnie parę społeczności użytkowników, które mają różne, ale uzasadnione aspiracje programowania. Rozwiązanie musi być kompromis między dwoma środowiskami, umożliwiając nie tylko ich wdychania, ale zdolność do współpracy. Oznacza to, że rozwiązań oferowanych przez po obu stronach mogą było i rozwiązanie na koniec implementowane za mniej niż idealne. Rzeczywista rozdzielczość opiera się funkcjonowanie wokół definicję klasy polimorficzne: polimorficznej klasy jest taki, który zawiera funkcję wirtualną. Klasy polimorficzne obsługuje dynamiczne bezpieczne przypisania elementu podrzędnego. Rozwiązuje problem Obsługa wskaźnik jako address, ponieważ wszystkie klasy polimorficzne zawiera tego dodatkowe wskaźnika elementu członkowskiego do ich skojarzonej tabeli wirtualnej. Skojarzony typ informacji, w związku z tym, mogą znajdować się w tabeli wirtualnej rozszerzonej struktury. Koszt bezpieczny przypisania elementu podrzędnego (prawie) jest zlokalizowana użytkownikom placówki.

Następny problem z bezpieczny przypisania elementu podrzędnego jest jego składni. Ponieważ jest rzutowanie, oryginalnym propozycji Komitetu ISO C++ używane składni unadorned rzutowania, jak w poniższym przykładzie:

```
spot = ( SpotLight* ) plight;
```

ale została odrzucona przez Komitet, ponieważ on nie zezwala na użytkownikowi na kontrolowanie kosztów rzutowania. Jeśli dynamiczne bezpieczny downcast ma tej samej składni jako niebezpieczny wcześniej, ale statyczne notacji rzutowania, a następnie ją staje się podstawienia, a użytkownik nie ma możliwości Pomiń koszty środowiska uruchomieniowego, gdy jest prawdopodobnie zbyt kosztowne i niepotrzebne.

Ogólnie rzecz biorąc w języku C++ jest zawsze mechanizm, za pomocą którego można pominąć funkcje obsługiwane przez kompilator. Na przykład, możemy wyłączyć wirtualnego mechanizm, za pomocą operatora zakresu klasy (`Box::rotate(angle)`) lub wywołując metodę wirtualną za pośrednictwem obiektu klasy (a nie wskaźnik lub odwołanie do tej klasy). Ten ostatni pomijanie nie jest wymagane przez język, ale jest jakości wydania implementacji, podobnie jak pomijanie tworzenia tymczasowych w deklaracji w postaci:

```
// compilers are free to optimize away the temporary
X x = X::X( 10 );
```

Wniosek został przeniesiony z powrotem do dalszego rozpatrzenia i kilka notacji alternatywne zostały uznane za i ten, który został sprowadzony z powrotem do Komitet został formularza (`?type`), który wskazano jego nieokreślonej — czyli dynamiczny charakter. To nadać użytkownikowi możliwość przełączać się między dwoma formami — statyczne lub dynamiczne —, ale nikt była zbyt przyjemność z nim. Aby był powrót do tablicy rysowania. Trzecia i pomyślne jest obecnie standard `dynamic_cast<type>`, który został uogólniony, aby zestaw cztery notacji rzutowania w stylu nowe.

W języku C++ ISO `dynamic_cast` zwraca `0` podczas zastosowane na typ wskaźnika nieodpowiednią i zgłasza `std::bad_cast` wyjątku, gdy jest stosowany do typu odwołania. W zarządzanych rozszerzeń języka C++ stosując `dynamic_cast` do typu zarządzane odniesienia (ze względu na jego reprezentację wskaźnika) zawsze zwracana `0`. `__try_cast<type>` wprowadzono analogowy wyjątek zostanie zgłoszony wariant `dynamic_cast`, chyba że wyniku weryfikacji zgłasza wyjątek `System::InvalidCastException` Jeśli Rzutowanie nie powiedzie się.

```
public __gc class ItemVerb;
public __gc class ItemVerbCollection {
public:
   ItemVerb *EnsureVerbArray() [] {
      return __try_cast<ItemVerb *[]>
         (verbList->ToArray(__typeof(ItemVerb *)));
   }
};
```

W nowej składni `__try_cast` zostały zmienione w jako `safe_cast`. W tym miejscu jest tego samego fragmentu kodu w nowej składni:

```
public ref class ItemVerb;
public ref class ItemVerbCollection {
public:
   array<ItemVerb^>^ EnsureVerbArray() {
      return safe_cast<array<ItemVerb^>^>
         ( verbList->ToArray( ItemVerb::typeid ));
   }
};
```

W kodzie zarządzanym jest ważne, aby umożliwić weryfikowalny kod, ograniczając możliwość rzutowania między typami w sposób, aby pozostawić kod niemożliwy programistów. To jest krytycznym aspektem paradygmat programowania dynamicznego, reprezentowane przez nową składnię. Z tego powodu wystąpień rzutowań w starym stylu są zmienione wewnętrznie jako rzutowań w czasie wykonywania, więc, na przykład:

```
// internally recast into the
// equivalent safe_cast expression above
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );
```

Z drugiej strony ponieważ polimorfizm zapewnia aktywne i tryb pasywny, czasami jest konieczne przeprowadzenie downcast tylko w celu uzyskania dostępu do interfejsu API niewirtualną podtypu. Taka sytuacja może wystąpić, na przykład za pomocą elementy członkowskie klasy, chcesz adres wszelkie typ w hierarchii (pasywnym polimorfizm jako mechanizm transportu), ale dla których jest znany rzeczywistego wystąpienia w kontekście określonego programu. W tym przypadku sprawdzanie w czasie wykonania rzutowania może być nie do przyjęcia obciążenie. W przypadku nowej składni ma pełnić rolę zarządzanych systemach, język programowania, podaj metod umożliwienia w czasie kompilacji (oznacza to, statyczne) przypisania elementu podrzędnego. Dlatego zastosowanie `static_cast` notacji mogły pozostawać w czasie kompilacji, przypisania elementu podrzędnego:

```
// ok: cast performed at compile-time.
// No run-time check for type correctness
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));
```

Problem jest, że nie istnieje sposób, aby zagwarantować, że programista, wykonując `static_cast` jest poprawna i intencjami; oznacza to, że nie istnieje żaden sposób wymusić kodu zarządzanego jako możliwe do zweryfikowania. To jest bardziej pilne problemem w ramach modelu dynamicznych programu niż w trybie macierzystym, ale nie są wystarczające w systemie programowania języka, aby uniemożliwić użytkownikowi możliwość przełączać się między statyczne i środowisko wykonawcze rzutowania.

Istnieje pułapki wydajności i niedogodności w nowej składni, jednak. W programowaniu natywnego jest nie różnicy w wydajności notacji rzutowania w stylu stary i nowy styl `static_cast` notacji. Ale w nowej składni notacji rzutowania w starym stylu jest znacznie bardziej kosztowne niż w przypadku nowego stylu `static_cast` notacji. Przyczyną jest to, że kompilator wewnętrznie przekształca użytkowania notacji stary styl do sprawdzanie w czasie wykonania, która zgłosiła wyjątek. Ponadto zmienia także profil wykonania kodu, ponieważ sprawia, że dzięki temu aplikacja — być może należy uważnie nieprzechwycony wyjątek, ale ten sam błąd nie spowodują ten wyjątek, jeśli `static_cast` notacji były używane. Może być jedną dokumentu uważają, że pomoże to prod użytkowników do przy użyciu notacji nowym stylem. Ale tylko wtedy, gdy kończy się niepowodzeniem; w przeciwnym razie spowodować programów, które używają notacji stary styl znacznie wolniejsze działanie bez widocznej zrozumieć Dlaczego, podobne do następujących pułapek programisty C:

```
// pitfall # 1:
// initialization can remove a temporary class object,
// assignment cannot
Matrix m;
m = another_matrix;

// pitfall # 2: declaration of class objects far from their use
Matrix m( 2000, 2000 ), n( 2000, 2000 );
if ( ! mumble ) return;
```

## <a name="see-also"></a>Zobacz też

[Ogólne zmiany w języku (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[Rzutowania w stylu języka C z/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)<br/>
[przedstawienie operacji safe_cast](../windows/safe-cast-cpp-component-extensions.md)