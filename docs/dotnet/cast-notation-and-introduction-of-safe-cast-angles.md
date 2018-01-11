---
title: Notacja rzutowania i przedstawienie safe_cast&lt; &gt; | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80d1a6e8b1a1691b4e76bfdc1232c95c22d01408
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Notacja rzutowania i przedstawienie safe_cast&lt;&gt;
Notacja rzutowania został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Modyfikowanie istniejącej struktury jest inne i trudniejsze środowisko niż obsługuje tworzenie początkowej struktury. Brak mniejsza liczba stopni swobody, a rozwiązanie zwykle kierunku kompromis między idealne restrukturyzacji i co jest możliwe ze względu istniejących strukturalnych zależności.  
  
 Rozszerzenia języka jest inny przykład. Na początku lat 1990 jak zmiana orientacji obiektu programowania stał się ważne modelu potrzebę bezpieczne budynek przypisanie elementu podrzędnego w języku C++ stał się naciśnięcie klawisza. Rzutowanie w dół jest użytkownika jawnej konwersji klasy podstawowej wskaźnik lub odwołanie do wskaźnika lub odwołania do klasy pochodnej. Rzutowanie w dół, wymaga jawnego rzutowania. Przyczyną jest to rzeczywisty typ wskaźnika do klasy podstawowej aspekt środowiska uruchomieniowego; Kompilator w związku z tym nie można sprawdzić go. Lub zmienić, który, obiekt przypisanie elementu podrzędnego, podobnie jak w wywołaniu funkcji wirtualnych wymaga pewnej formy rozpoznawania dynamicznych. Uruchamia to dwa pytania:  
  
-   Dlaczego przypisanie elementu podrzędnego się niezbędne w zorientowany obiektowo model? Mechanizm funkcji wirtualnej nie wystarcza? Oznacza to, dlaczego nie jedną oświadczeń to potrzebę przypisanie elementu podrzędnego (lub Rzutowanie jakiegokolwiek) awarii projektu?  
  
-   Dlaczego obsługę przypisanie elementu podrzędnego powinna być problem w języku C++ Po wszystkich nie jest problemem w zorientowane obiektowo języków, takich jak Smalltalk (lub później, Java i C#)? Co to jest o C++, która ułatwia obsługę obiekt przypisanie elementu podrzędnego trudne?  
  
 Funkcję wirtualną reprezentuje typowe algorytmu zależne od typu do rodziny typów. (Firma Microsoft nie rozważa interfejsy, które nie są obsługiwane w języku C++ ISO, ale są dostępne w programowaniu CLR i reprezentujących interesujące zamiast projektu). Projekt tej rodziny jest zazwyczaj reprezentowany przez hierarchii klas, w którym jest abstrakcyjna klasa podstawowa deklarowanie wspólnego interfejsu (funkcje wirtualne) oraz zestaw konkretnych klas pochodnych, które zawierają rzeczywiste typy rodziny w aplikacji domeny.  
  
 A `Light` hierarchii w domenie aplikacji komputera wygenerowany obrazów (CGI), na przykład, takich jak mają takie same atrybuty wspólne `color`, `intensity`, `position`, `on`, `off`i tak dalej. Kilka świateł jedną kontrolować za pomocą wspólnego interfejsu bez obaw czy światło określonego spotlight, światło kierunkowe, niekierunkowa (Pomyśl o sun) lub być może drzwi wolierowego światła. W takim przypadku rzutowanie w dół z określonym typem jasny wykonywać jego interfejsu wirtualnego nie jest konieczne. W środowisku produkcyjnym jednak szybkość jest ważne. Jedna może być przypisanie elementu podrzędnego i jawnego wywołania każdej metody, jeśli przez grozi to wykonywanie śródwierszowe wywołania można wykonać zamiast przy użyciu mechanizmu wirtualnego.  
  
 Powodem przypisanie elementu podrzędnego w języku C++ jest tak, Pomiń wirtualnego mechanizmu zamian za istotny przyrost wydajności środowiska wykonawczego. (Należy pamiętać, że automatyzację ręczne Optymalizacja aktywny obszar badań. Jednak jest trudne do rozwiązania niż zastąpienie jawne `register` lub `inline` — słowo kluczowe.)  
  
 Drugi przyczynę przypisanie elementu podrzędnego wypada poza podwójną rodzaj polimorfizm. Jednym ze sposobów traktować polimorfizm jest jest podzielona na pasywnym dynamiczne parę formularzy.  
  
 Wirtualne wywołania (oraz możliwości przypisanie elementu podrzędnego) reprezentuje dynamiczne zastosowań polimorfizm: jeden wykonuje akcję na podstawie rzeczywistego typu wskaźnika klasy podstawowej na określone wystąpienie wykonywania programu.  
  
 Przypisywanie obiektu klasy pochodnej na wskaźnik jej klasy podstawowej, jednak jest pasywny formą polimorfizm; Polimorfizm używa jako mechanizm transportu. To jest główny stosowania `Object`, na przykład w programowaniu CLR wstępnie ogólnego. W przypadku pasywnie wskaźnika klasy podstawowej, zwykle wybrany dla transportu i przechowywania udostępnia interfejs, który jest zbyt abstrakcyjny. `Object`, na przykład udostępnia około pięciu metody za pomocą jego interfejsu; wszelkie więcej określone zachowanie wymaga jawnego przypisanie elementu podrzędnego. Na przykład jeśli chcemy dopasować kąt naszych spotlight lub swoją szybkość znajduje się poza, firma Microsoft będzie musiał przypisanie elementu podrzędnego jawnie. Interfejs wirtualny w obrębie rodziny podtypów praktycznie nie może być nadzbiorem wszystkie możliwe metody wiele podrzędnych, a więc obiekt przypisanie elementu podrzędnego, zawsze będą wymagane w ciągu zorientowany obiektowo język.  
  
 Przypisanie elementu podrzędnego sejfie zakładzie jest potrzebna, jeśli w zorientowany obiektowo język, a następnie Dlaczego trwało C++ tak długo dodać? Problem dotyczy jak udostępnić informacje dotyczące typu run-time wskaźnika. W przypadku funkcji wirtualnej informacji środowiska wykonawczego został skonfigurowany w dwóch częściach przez kompilator:  
  
-   Obiekt klasy zawiera wskaźnik elementu członkowskiego dodatkowe tabeli wirtualnej (na początku lub na końcu obiektu klasy; to jest ma interesujące historii w sobie) która rozwiązuje odpowiednie tabeli wirtualnej. Na przykład obiekt spotlight adresów tabeli wirtualnej spotlight, światło kierunkowe, kierunkową światła tabeli wirtualnej i tak dalej  
  
-   Każdej funkcji wirtualnej ma skojarzoną stałej miejsca w tabeli, a rzeczywiste wystąpienie do wywołania jest reprezentowana przez adres przechowywane w tabeli. Na przykład wirtualnych `Light` destruktora mogą być skojarzone z miejscem 0, `Color` z gniazda 1 i tak dalej. Jest to efektywne, jeżeli sztywne strategii, ponieważ skonfigurowano w czasie kompilacji i reprezentuje minimalnego obciążenia.  
  
 Ten problem, jest następnie, jak udostępniać informacje typu wskaźnika bez zmieniania rozmiaru wskaźników C++, dodając drugi adres lub dodając bezpośrednio jakiegoś typu kodowania. Nie jest możliwe do zaakceptowania tych programistów (i programy) który zrezygnować z zorientowany obiektowo model - nadal będącą dominujący użytkowników. Inną możliwością został wprowadzenie specjalnych wskaźnik do typu klasy polimorficznej, ale to może być mylące i utrudnia mieszać między dwoma, zwłaszcza w przypadku problemów arytmetyka wskaźnika. Nie byłoby możliwe do zaakceptowania Obsługa tabeli czasu wykonywania, który kojarzy wskaźnika każdego z jego obecnie skojarzony typ i dynamicznie zaktualizowaniem go.  
  
 Problem jest następnie parę środowiska użytkownika, które mają różne, ale uzasadnionych aspiracje programowania. Rozwiązanie musi być kompromis między dwa społeczności, umożliwiając nie ich wdychania tylko zdolność do współpracy. Oznacza to, czy rozwiązania oferowane przez obu stronach mogą było i rozwiązanie wdrożone na koniec mniej niż doskonałe. Rzeczywiste rozwiązania problemem definicję klasy polimorficzne: klasy polimorficznej to taki, który zawiera funkcję wirtualną. Klasy polimorficzne obsługuje dynamiczne bezpieczne przypisanie elementu podrzędnego. Rozwiązuje problem Obsługa — wskaźnik jako — adres, ponieważ wszystkie klasy polimorficzne zawiera ten element członkowski dodatkowe wskaźnika do ich skojarzonej tabeli wirtualnej. W związku z tym informacji skojarzonego typu mogą być przechowywane w strukturze tabeli wirtualnej rozszerzonej. Koszt bezpieczne przypisanie elementu podrzędnego (prawie) jest zlokalizowane dla użytkowników funkcji.  
  
 Następny problem z bezpiecznej przypisanie elementu podrzędnego jest jego składni. Rzutowanie, dlatego oryginalnego wniosku Komitetowi ISO C++ używana składnia rzutowania unadorned, jak w poniższym przykładzie:  
  
```  
spot = ( SpotLight* ) plight;  
```  
  
 ale została odrzucona przez Komitet, ponieważ nie zezwala użytkownikowi na kontrolowanie kosztów rzutowania. Jeśli dynamiczny bezpieczne przypisanie elementu podrzędnego ma takiej samej składni jak wcześniej unsafe, ale statyczne notacji rzutowania, a następnie go staje się podstawienia, a użytkownik nie ma możliwości Pomiń narzut czasu wykonywania, gdy jest niepotrzebne i prawdopodobnie zbyt kosztowne.  
  
 Ogólnie rzecz biorąc w języku C++ jest zawsze mechanizm, przez którą chcesz pominąć funkcje obsługiwane przez kompilator. Na przykład możemy wyłączyć wirtualnego mechanizm, za pomocą operatora zakresem klasy (`Box::rotate(angle)`) lub przez wywołanie metody wirtualnej za pośrednictwem obiektu klasy (a nie wskaźnik lub odwołanie do tej klasy). Ten ostatni pomijania nie jest wymagane przez język, ale jest jakość problem implementacji, podobnie jak pomijanie konstrukcji tymczasowych w deklaracji w postaci:  
  
```  
// compilers are free to optimize away the temporary  
X x = X::X( 10 );  
```  
  
 Wniosku zostało odebrane dla dalszego brany pod uwagę i uwzględniono kilka notacji alternatywnych i jeden przywrócone Komitetowi został formularza (`?type`), który wskazano jego nieokreślonej — to znaczy dynamiczny charakter. To udzielił użytkownikowi możliwość przełączania między dwoma formularzami — statyczne lub dynamiczne —, ale nikt nie był zbyt przyjemnością z nim. Aby był powrót do tablicy rysunku. Trzeci i pomyślne jest obecnie standardowe `dynamic_cast<type>`, który został uogólnione w celu zestaw cztery notacji rzutowania w stylu nowe.  
  
 W języku C++ ISO `dynamic_cast` zwraca `0` po zastosowaniu do typu wskaźnika nieodpowiednie i zgłasza `std::bad_cast` wyjątku, gdy jest stosowany do typu referencyjnego. W przypadku rozszerzeń zarządzanych dla języka C++ stosowanie `dynamic_cast` do typu zarządzane odniesienia (ze względu na jego reprezentacja wskaźnika) zawsze zwracana `0`. `__try_cast<type>`wprowadzono analogowy wyjątek zgłaszanie wariant `dynamic_cast`, z wyjątkiem tego, że zgłasza `System::InvalidCastException` Jeśli Rzutowanie nie powiedzie się.  
  
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
  
 W nowej składni `__try_cast` zostały zmienione jako `safe_cast`. Oto tego samego fragmentu kodu w nowej składni:  
  
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
  
 W kodzie zarządzanym jest ważne umożliwić weryfikowalny kod ograniczając możliwości programistów można rzutować między typami w sposób, aby pozostawić kod niemożliwy. Jest to krytyczne aspekt dynamiczne modelu programowania reprezentowany przez nowej składni. Z tego powodu wystąpień rzutowania w stylu są zmienione wewnętrznie jako rzutowania w czasie wykonywania, tak że, na przykład:  
  
```  
// internally recast into the   
// equivalent safe_cast expression above  
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );   
```  
  
 Z drugiej strony ponieważ polimorfizm zapewnia aktywnych i pasywnych tryb, czasami jest konieczne przeprowadzenie przypisanie elementu podrzędnego tylko w celu uzyskania dostępu do interfejsu API niewirtualną podtypu. Taka sytuacja może wystąpić, na przykład z członków klasy chcą adres dowolny typ w hierarchii (pasywnego polimorfizm jako mechanizm transportu), ale znane rzeczywistego wystąpienia w kontekście określonego programu. W takim przypadku kontrolę środowiska wykonawczego rzutowanie może być nadmiernego obciążenia. W przypadku nowej składni jako zarządzanych systemach język programowania, podaj niektórych oznacza umożliwienia w czasie kompilacji (to znaczy statycznych) przypisanie elementu podrzędnego. Dlatego zastosowanie `static_cast` notacji może pozostawać w czasie kompilacji przypisanie elementu podrzędnego:  
  
```  
// ok: cast performed at compile-time.   
// No run-time check for type correctness  
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));  
```  
  
 Problem jest, że nie istnieje sposób zagwarantować, że programisty czynności `static_cast` jest poprawna i dobrze tych; oznacza to, że nie istnieje sposób wymusić kodu zarządzanego jako możliwe do zweryfikowania. To jest bardziej pilne w modelu dynamicznych programu niż w trybie macierzystym, ale nie są wystarczające w systemie programowania języka aby uniemożliwić użytkownikowi możliwość przełączania między statyczna i środowiska wykonawczego rzutowania.  
  
 Pułapki wydajności i niedogodności w nowej składni, jednak występuje. W programowaniu macierzystego, nie ma różnic w wydajności między notacji rzutowania w stylu stary i nowy styl `static_cast` notacji. Jednak w nowej składni jest znacznie droższe niż użycie nowych stylów Notacja rzutowania w stylu `static_cast` notacji. Przyczyną jest to, że kompilator wewnętrznie przekształca użycie notacji stary styl do wyboru czasu wykonywania, która zgłasza wyjątek. Ponadto zmieniają się także profil wykonania kodu, ponieważ powoduje on nieprzechwycony wyjątek Przywracanie aplikacji – prawdopodobnie rozsądny sposób, ale ten sam błąd nie może powodować ten wyjątek, jeśli `static_cast` notacji były używane. Takim przypadku można przyjąć się, że zapewni produkcyjnego użytkowników w notacji nowego stylu. Ale tylko wtedy, gdy działanie nie powiodło się; w przeciwnym razie spowoduje ona, że programy, które umożliwia notacji stary styl znacznie spowolnić bez widocznych zrozumieć Dlaczego, podobne do następujących problemów programisty C:  
  
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
 [Ogólne zmiany w języku (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [Rzutowania w stylu języka C z/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)