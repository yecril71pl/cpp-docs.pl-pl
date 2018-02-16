---
title: REF klas i struktur (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d8b7717c98ebd4bab8c0d3d8c20a594a3f4d58e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ref-classes-and-structs-ccx"></a>REF klas i struktur (C + +/ CX)
C + +/ CX obsługuje użytkownika *klasy ref* i *struktury ref*i zdefiniowanych przez użytkownika *wartość klasy* i *wartość struktury*. Te struktury danych są głównej kontenerów, przez które C + +/ CX obsługuje system typów środowiska wykonawczego systemu Windows. Ich zawartość są emitowane metadanych zgodnie z niektórych określone zasady, a dzięki temu przekazywane między składników środowiska wykonawczego systemu Windows i aplikacji platformy uniwersalnej systemu Windows, które są napisane w języku C++ lub innych języków.  
  
 Klasa ref lub ref struct ma tych podstawowych funkcji:  
  
-   Musi być zadeklarowana w przestrzeni nazw, w zakresie przestrzeni nazw i w tej przestrzeni nazw może mieć dostępności publicznych lub prywatnych. Tylko typy publiczne są emitowane metadanych. Definicje klas publicznych zagnieżdżone nie są dozwolone, tym zagnieżdżonych publicznego [wyliczenia](../cppcx/enums-c-cx.md) klasy. Aby uzyskać więcej informacji, zobacz [obszary nazw i typ widoczności](../cppcx/namespaces-and-type-visibility-c-cx.md).  
  
-   Może on zawierać jako elementy członkowskie C + +/ CX tym klasy ref, wartość klasy, struktury ref, wartość struktury lub struktury wartość null. Może również zawierać typy skalarne, takie jak float64, bool i tak dalej. Standardowe typy C++ również może zawierać takie jak `std::vector` lub niestandardowej klasy, dopóki nie są publicznie udostępniane. C + +/ CX konstrukcji może mieć `public`, `protected`, `internal`, `private`, lub `protected private` ułatwień dostępu. Wszystkie `public` lub `protected` elementy członkowskie są emitowane metadanych. Standardowe typy C++ musi mieć `private`, `internal`, lub `protected private` ułatwień dostępu, co uniemożliwia ich błędnemu emitowaniu metadanych.  
  
-   Może on implementować co najmniej jeden *interfejsu klasy* lub *interfejsu struktury*.  
  
-   Może on dziedziczyć z jedną klasę podstawową i klasy podstawowej, same mają dodatkowe ograniczenia. Dziedziczenie w hierarchii klasy ref publicznego ma więcej ograniczeń, niż dziedziczenia w klasy ref prywatnych.  
  
-   Nie może być zadeklarowana do jako ogólnego. Jeśli ma ona prywatną dostępność, może to być szablon.  
  
-   Jego okres istnienia jest zarządzana przez automatyczne liczenie odwołań.  
  
## <a name="declaration"></a>Deklaracja  
 Deklaruje następującego fragmentu kodu `Person` klasy referencyjnej. Zwróć uwagę, że standardu C++ `std::map` typ jest używany w prywatne elementy członkowskie i środowiska wykonawczego systemu Windows`IMapView` interfejs jest używany interfejs publiczny. Ponadto należy zauważyć, że "^" jest dołączany do deklaracje typów referencyjnych.  
  
 [!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]  
  
## <a name="implementation"></a>Implementacja  
 Ten przykładowy kod przedstawia implementację `Person` klasy referencyjnej:  
  
 [!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]  
  
## <a name="usage"></a>Użycie  
 W kolejnym przykładzie kodu pokazano, jak kod klienta używa `Person` klasy referencyjnej.  
  
 [!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]  
  
 Semantyka stosu służy również do deklarowania zmiennych lokalnych ref. Taki obiekt zachowuje się jak zmienną opartego na stosie, mimo że pamięć wciąż jest przydzielony dynamicznie. Jedną istotną różnicą jest, że nie można przypisać odwołania śledzenia (%) do zmiennej, która jest zadeklarowana przy użyciu semantyka stosu; gwarantuje to, że liczba odwołań zostanie zmniejszona do zera, gdy funkcja jest kończona. W tym przykładzie przedstawiono klasy podstawowej ref `Uri`i funkcję, która korzysta z niego z semantyka stosu:  
  
 [!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]  
  
## <a name="memory-management"></a>Zarządzanie pamięcią  
 Przydziel klasy ref w pamięci dynamicznej za pomocą `ref new` — słowo kluczowe.  
  
 [!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]  
  
 Operator uchwytu do obiektu ^ jest znana jako "hat" i jest całkowicie C++ wskaźnika inteligentnego. Pamięć wskazuje automatycznie zostanie zniszczony podczas ostatniego hat wykracza poza zakres lub jest jawnie ustawiona na `nullptr`.  
  
 Zgodnie z definicją klasy ref ma semantykę odwołania. Po przypisaniu klasy ref zmiennej, jest dojście, który został skopiowany nie samego obiektu. W następnym przykładzie po przypisania zarówno `myClass` i `myClass2` punktu w tej samej lokalizacji pamięci.  
  
 [!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]  
  
 Gdy C + +/ CX klasy referencyjnej zostanie uruchomiony, pamięci jest zero zainicjowany przed wywołaniem konstruktora jego; w związku z tym nie jest konieczne poszczególnych elementów, w tym właściwości inicjalizacji zero. Jeśli C + +/ CX klasa pochodzi od klasy biblioteki języka C++ środowiska wykonawczego systemu Windows (WRL), tylko C + +/ CX klasy pochodnej części jest inicjowany przez zero.  
  
### <a name="members"></a>Elementy członkowskie  
 Klasa ref może zawierać `public`, `protected`, i `private` funkcji elementów członkowskich, a jedynie `public` i `protected` elementy członkowskie są wydane do metadanych. Klasy referencyjnej i klasy zagnieżdżone są dozwolone, ale nie może być `public`. Pola publiczne są niedozwolone; publiczne elementy członkowskie danych musi być zadeklarowany jako właściwości. Elementy członkowskie prywatnych lub chronionych wewnętrznych danych może być pól. Domyślnie w klasie ref dostępność wszystkich elementów członkowskich jest `private`.  
  
 Struktura ref jest taka sama jak klasa ref, z tą różnicą, że domyślnie jej członkowie mają `public` ułatwień dostępu.  
  
 A `public` klasy referencyjnej lub ref struct jest emitowany w metadanych, ale może być używany z innych aplikacji platformy uniwersalnej systemu Windows i składników środowiska wykonawczego systemu Windows musi mieć co najmniej jeden konstruktor publiczne lub chronione. Klasy ref publicznego, który ma publicznego konstruktora również musi być zadeklarowany jako `sealed` Aby uniknąć dalszych pochodnym za pośrednictwem interfejsu binarne aplikacji (ABI).  
  
 Publiczne elementy członkowskie nie można zadeklarować jako const ponieważ system typów środowiska wykonawczego systemu Windows nie obsługuje const. Właściwość statyczna służy do deklarowania publicznego elementu członkowskiego danych z wartością stałą.  
  
 Podczas definiowania struktury lub klasy referencyjnej publiczne, kompilator stosuje wymaganych atrybutów do klasy i zapisuje je w pliku winmd aplikacji. Jednak podczas definiowania publicznego niezapieczętowana klasa ref ręcznie zastosować `Windows::Foundation::Metadata::WebHostHidden` atrybutu, aby upewnić się, że klasa nie jest widoczny dla aplikacji platformy uniwersalnej systemu Windows, które zostały napisane w języku JavaScript.  
  
 Klasa referencyjna może mieć standardowych typów języka C++, w tym `const` typów w żadnym `private`, `internal`, lub `protected private` elementów członkowskich.  
  
 Klasa ref publicznej, która ma parametry typu nie są dozwolone. Klasy ref ogólnego zdefiniowane przez użytkownika nie są dozwolone. Prywatnych, wewnętrznych ani chronionych prywatnej klasy ref może być szablonem.  
  
## <a name="destructors"></a>Destruktory  
 W języku C + +/ CX, wywoływania `delete` na destruktorem publicznym wywołuje destruktor niezależnie od liczby odwołanie do obiektu. To zachowanie umożliwia zdefiniowanie destruktora wykonujący niestandardowe Oczyszczanie zasobów z systemem innym niż RAII w sposób deterministyczna. Jednak nawet w tym przypadku sam obiekt jest nie usunięte z pamięci. Pamięci dla obiekt zostanie zwolniona tylko, gdy liczba odwołań osiągnie wartość zero.  
  
 Jeśli klasa destruktor nie jest publiczny, następnie jest tylko wywoływana, gdy liczba odwołań osiągnie wartość zero. Jeśli wywołujesz `delete` na obiekcie, który ma destruktor prywatne, kompilator zgłasza ostrzeżenie C4493, jago "wyrażenie usunięcia nie obowiązuje jako destruktor \<Nazwa typu > nie mieć dostępność"public"."  
  
 Destruktory klasy REF mogą być deklarowane tylko w następujący sposób:  
  
-   publiczny i wirtualnych (dozwolone w typach zapieczętowanych i niezapieczętowanych)  
  
-   chronione prywatne i niewirtualną (dozwolone tylko dla typów niezapieczętowanych)  
  
-   prywatne i niewirtualną (dozwolone tylko w typach zapieczętowanych)  
  
 Nie inne kombinacje ułatwień dostępu, virtualness i sealedness jest dozwolone.  Jeśli destruktor nie jawnie deklarować kompilator generuje publicznego destruktor wirtualny Jeśli klasy podstawowej typu lub dowolnego elementu członkowskiego ma destruktorem publicznym. W przeciwnym razie kompilator generuje prywatne chronione Niewirtualny destruktor w przypadku typów niezapieczętowanych lub prywatnej Niewirtualny destruktor dla typów zapieczętowanych.  
  
 Zachowanie jest niezdefiniowana, jeżeli zostanie podjęta próba dostęp do elementów członkowskich klasy, która ma już jego destruktora Uruchom; prawdopodobnie spowoduje awarię programu. Wywoływanie `delete t` na typie, który ma nie publicznego destruktor nie ma wpływu. Wywoływanie `delete this` dla typu lub base klasy, która ma znanego `private` lub `protected private` destruktora w swojej hierarchii typów również nie ma wpływu.  
  
 Przy deklarowaniu destruktorem publicznym kompilator generuje kod, dzięki czemu implementuje klasy referencyjnej `Platform::IDisposable` i implementuje destruktora `Dispose` metody. `Platform::IDisposable` jest C + +/ CX rzut `Windows::Foundation::IClosable`. Nigdy nie jawnie zaimplementować te interfejsy.  
  
## <a name="inheritance"></a>Dziedziczenie  
 Platform::Object jest uniwersalny klasa podstawowa dla wszystkich klas referencyjnych. Wszystkie klasy ref umożliwiają niejawnej konwersji na Platform::Object, można zmienić [Object::ToString](../cppcx/platform-object-class.md#tostring). Jednak modelu dziedziczenia środowiska wykonawczego systemu Windows nie pełnić rolę ogólny modelu dziedziczenia; w języku C + +/ CX, oznacza to, że klasa ref publiczne zdefiniowane przez użytkownika nie może służyć jako klasę podstawową.  
  
 Jeśli tworzysz kontrolkę użytkownika XAML i obiekt uczestniczy w systemie właściwości zależności, a następnie można użyć `Windows::UI::Xaml::DependencyObject` jako klasę podstawową.  
  
 Po zdefiniowaniu klasy niezapieczętowany `MyBase` dziedziczący po `DependencyObject`, klasy ref innych publicznych lub prywatnych w składniku lub aplikacji mogą dziedziczyć `MyBase`. Dziedziczenie klas publicznych ref można dokonać tylko do obsługi przesłonięcia metody wirtualne, tożsamość polimorficznych i hermetyzacji.  
  
 Klasy podstawowej ref prywatnych nie jest wymagane do pochodzi z niezapieczętowanego istniejącej klasy. Jeśli potrzebujesz hierarchię obiektów modelu struktury programu lub włączyć ponowne użycie kodu, użyj klasy ref prywatny lub wewnętrzny lub jeszcze lepiej standardowych klas C++. Można udostępniają funkcje hierarchii obiektu prywatnego za pomocą otoka publicznego ref zapieczętowane klasy.  
  
 Klasa ref, które ma on konstruktora public lub protected w języku C + +/ CX musi być zadeklarowany jako sealed. To ograniczenie oznacza, że nie istnieje sposób dla klas, które są zapisywane w innych językach, takich jak C# lub Visual Basic dziedziczyć typy deklarujące składnika środowiska wykonawczego systemu Windows, jest napisany w języku C + +/ CX.  
  
 Poniżej przedstawiono podstawowe zasady dziedziczenia w języku C + +/ CX:  
  
-   Klasy REF może dziedziczyć bezpośrednio co najwyżej jednej klasy podstawowej ref, ale można zaimplementować dowolną liczbę interfejsów.  
  
-   Jeśli klasa ma on publicznego konstruktora, musi być zadeklarowany jako sealed, aby uniknąć dalszych pochodnym.  
  
-   Można utworzyć publiczny niezapieczętowanych klas podstawowych mających wewnętrzny lub chronione konstruktory prywatne, pod warunkiem, że klasa podstawowa pochodzi bezpośrednio lub pośrednio z istniejący, niezapieczętowany klasy podstawowej takich jak `Windows::UI::Xaml::DependencyObject`. Dziedziczenie klas referencyjnych zdefiniowane przez użytkownika między plików winmd nie jest obsługiwany; jednak klasy referencyjnej można dziedziczyć interfejsu, który jest zdefiniowany w innym pliku winmd. Można utworzyć klasy pochodnej z klasy zdefiniowanej przez użytkownika podstawowej ref tylko w obrębie tego samego składnika środowiska wykonawczego systemu Windows lub aplikacji platformy uniwersalnej systemu Windows.  
  
-   Klasy ref obsługiwane są tylko publiczne dziedziczenie.  
  
     [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]  
  
 Poniższy przykład pokazuje, jak do udostępnienia klasy ref publicznego pochodzącego z innych klas referencyjnych w hierarchii dziedziczenia.  
  
 [!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Wartość klasy i struktury](../cppcx/value-classes-and-structs-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)