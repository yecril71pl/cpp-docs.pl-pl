---
title: Zmiany w semantyce destruktora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c25045291afed1e8072867ee668716b2f396ef30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420026"
---
# <a name="changes-in-destructor-semantics"></a>Zmiany w semantyce destruktora

Semantyka dla destruktory klasy zmieniły się znacznie z zarządzanych rozszerzeń dla języka C++ do Visual C++.

W zarządzanych rozszerzeń destruktor klasy został dozwolone w obrębie klasy odwołania, ale nie w klasie wartości. To nie została zmieniona w nowej składni. Jednak semantykę destruktor klasy uległy zmianie. Ten temat koncentruje się na przyczyny tego zmienić i w tym artykule omówiono, jak wpływa na tłumaczenie istniejącego kodu CLR. Prawdopodobnie jest najważniejsze zmiany poziomu programisty między dwoma wersjami języka.

## <a name="non-deterministic-finalization"></a>Finalizacja deterministyczna

Przed pamięci skojarzona z obiektem jest odzyskiwane przez moduł zbierający elementy bezużyteczne, skojarzoną `Finalize` , jeśli jest obecny, wywoływana jest metoda. Można traktować tej metody jako rodzaj właścicielami destruktora, ponieważ nie jest związany z programu okresu istnienia obiektu. Nazywamy to finalizacji jest zakończona. Chronometraż dla tylko kiedy lub nawet czy `Finalize` metoda jest wywoływana jest niezdefiniowana. Jest to, co mamy na myśli podczas mówi się, że wyrzucanie elementów bezużytecznych wykazuje finalizacja deterministyczna.

Finalizacja deterministyczna inne niż dobrze działa z pamięci dynamicznej zarządzania. Gdy deficytowe staje się dostępna pamięć, moduł odśmiecania pamięci jest uruchamiane. W obszarze pamięci zbierane środowiska, w usunięcie przez destruktory wolnej pamięci nie są konieczne. Finalizacja deterministyczna inne niż nie działa, jednak, gdy obiekt utrzymuje krytycznych zasobów, takich jak połączenia z bazą danych lub blokadę jakieś. W takim przypadku należy wydaniu tego zasobu tak szybko, jak to możliwe. W świecie natywne, które odbywa się przy użyciu pary konstruktora/destruktora. Zaraz po zakończeniu okresu istnienia obiektu podczas kończenia lokalnego bloku, w którym jest zadeklarowana lub gdy stos unravels ze względu na zgłoszony wyjątek, destruktor wykonuje i automatycznie zwolnieniu zasobu. Ta metoda działa bardzo dobrze, a jego nieobecności w ramach zarządzanych rozszerzeń sorely została pominięta.

Rozwiązania dostarczane przez środowisko CLR jest dla klasy do zaimplementowania `Dispose` metody `IDisposable` interfejsu. Problem polega na tym, `Dispose` wymaga jawnego wywołania przez użytkownika. To jest podatne na błędy. W języku C# zawiera niewielkie formę automatyzacji w formie specjalny `using` instrukcji. Projekt zarządzanych rozszerzeń udostępniane nie specjalne pomocy technicznej.

## <a name="destructors-in-managed-extensions-for-c"></a>Destruktory w Managed Extensions for C++

W zarządzanych rozszerzeń destruktor klasy odwołania jest implementowane za pomocą następujących dwóch kroków:

1. Destruktor dostarczone przez użytkownika została zmieniona wewnętrznie do `Finalize`. Jeśli klasa ma klasę bazową (Pamiętaj, że w modelu obiektu CLR, jest obsługiwane tylko pojedyncze dziedziczenie), kompilator wprowadza wywołanie w celu jego finalizator następujące wykonywanie kodu dostarczone przez użytkownika. Na przykład należy wziąć pod uwagę następujące hierarchii proste pobierane z zarządzanych rozszerzeń specyfikacji języka:

```
__gc class A {
public:
   ~A() { Console::WriteLine(S"in ~A"); }
};

__gc class B : public A {
public:
   ~B() { Console::WriteLine(S"in ~B");  }
};
```

W tym przykładzie oba destruktory zostały zmienione `Finalize`. `B`firmy `Finalize` ma wywołanie `A`firmy `Finalize` metoda dodane po wywołaniu `WriteLine`. Jest to, co moduł zbierający elementy bezużyteczne domyślnie wywoła podczas finalizacji. Poniżej przedstawiono, jak może wyglądać tej transformacji wewnętrznych:

```
// internal transformation of destructor under Managed Extensions
__gc class A {
public:
   void Finalize() { Console::WriteLine(S"in ~A"); }
};

__gc class B : public A {
public:
   void Finalize() {
      Console::WriteLine(S"in ~B");
      A::Finalize();
   }
};
```

1. W drugim kroku kompilator syntetyzuje destruktor wirtualny. Ten destruktor jest o tym, co naszych programów użytkowników zarządzanych rozszerzeń wywołać bezpośrednio lub za pośrednictwem aplikacji wyrażenie usunięcia. Nigdy nie zostanie wywołana przez moduł odśmiecania pamięci.

     Dwie instrukcje są umieszczane w ramach tego syntetyzowany destruktora. Jeden jest wywołaniem `GC::SuppressFinalize` aby upewnić się, że nie istnieją żadne więcej wywołań `Finalize`. Drugi to rzeczywiste wywołanie `Finalize`, która reprezentuje destruktor dostarczone przez użytkownika dla tej klasy. Oto, co to może wyglądać:

```
__gc class A {
public:
   virtual ~A() {
      System::GC::SuppressFinalize(this);
      A::Finalize();
   }
};

__gc class B : public A {
public:
   virtual ~B() {
      System::GC::SuppressFinalize(this);
      B::Finalize();
   }
};
```

Podczas tej implementacji umożliwia użytkownikowi jawnie wywołać klasy `Finalize` metoda teraz zamiast w danym momencie masz żadnej kontroli nad, go nie naprawdę blokuje przy użyciu `Dispose` metoda rozwiązania. Jest to zmienić w programie Visual C++.

## <a name="destructors-in-new-syntax"></a>Destruktory w nowej składni

W nowej składni destruktora została zmieniona wewnętrznie do `Dispose` metod i klas odwołanie jest automatycznie rozszerzony do zaimplementowania `IDispose` interfejsu. Oznacza to w obszarze Visual C++, nasze pary klasy jest przekształcana w następujący sposób:

```
// internal transformation of destructor under the new syntax
__gc class A : IDisposable {
public:
   void Dispose() {
      System::GC::SuppressFinalize(this);
      Console::WriteLine( "in ~A");
   }
};

__gc class B : public A {
public:
   void Dispose() {
      System::GC::SuppressFinalize(this);
      Console::WriteLine( "in ~B");
      A::Dispose();
   }
};
```

Gdy albo destruktor jest wywoływany jawnie w nowej składni lub `delete` jest stosowany do śledzenie dojścia bazowego `Dispose` metoda jest wywoływana automatycznie. Jeśli klasa pochodna, wywołanie jest `Dispose` metody klasy bazowej jest wstawiany przy zamknięciu syntetyzowany metody.

Ale to nie przeprowadzą NAS aż do finalizacja deterministyczna. Aby uzyskać dostęp, potrzebujemy dodatkową obsługę odwołań lokalnych obiektów. (Została to analogiczne nie są obsługiwane w ramach zarządzanych rozszerzeń, a nie jest to problem tłumaczenia).

## <a name="declaring-a-reference-object"></a>Deklarowanie dla obiektu referencyjnego.

Visual C++ obsługuje deklaracja obiektu klasy odwołania na stosie lokalnego lub jako członek klasy tak, jakby była dostępna bezpośrednio. W połączeniu z skojarzenie destruktor z `Dispose` metodą, wynik jest automatyczne wywołanie semantyki finalizacji w typach referencyjnych.

Najpierw definiujemy naszych klasy odwołania w taki sposób, że tworzenie obiektów działa jako nabywania zasobów za pośrednictwem jej konstruktora klasy. Po drugie w ramach destruktor klasy wydaniu zasobów uzyskane podczas tworzenia obiektu.

```
public ref class R {
public:
   R() { /* acquire expensive resource */ }
   ~R() { /* release expensive resource */ }

   // everything else...
};
```

Obiekt został zadeklarowany lokalnie, używając nazwy typu, ale bez towarzyszącego hat. Wszystkie przypadki użycia obiektu, na przykład wywołanie metody, są wykonywane za pomocą kropka wyboru składowej (`.`) zamiast strzałka (`->`). Na koniec bloku Pomocy skojarzonego destruktora, przekształcane na `Dispose`, jest wywoływana automatycznie, jak pokazano poniżej:

```
void f() {
   R r;
   r.methodCall();

   // r is automatically destructed here -
   // that is, r.Dispose() is invoked
}
```

Podobnie jak w przypadku `using` instrukcji w języku C#, to nie mnóstwem bazowego ograniczenie CLR, wszystkie typy referencyjne muszą zostać przydzielone na stercie CLR. Podstawowy schemat działania pozostaje bez zmian. Użytkownik może ekwiwalentnie być napisane tak, że (i prawdopodobnie jest to wewnętrzny przekształcenie wykonywane przez kompilator):

```
// equivalent implementation
// except that it should be in a try/finally clause
void f() {
   R^ r = gcnew R;
   r->methodCall();

   delete r;
}
```

W efekcie w ramach nowej składni destruktory są ponownie skojarzone z konstruktorów jako automatyczne nabycia/wydania mechanizm związany z okresem istnienia obiektu lokalnego.

## <a name="declaring-an-explicit-finalize"></a>Deklarowanie jawne Finalize

W nowej składni, ponieważ w związku z czym dostrzegliśmy, destruktor jest przekształcony na `Dispose` metody. Oznacza to, że gdy destruktor nie zostanie jawnie wywołany, moduł odśmiecania pamięci podczas finalizacji, nie tak jak poprzednio znajdzie skojarzoną `Finalize` metodę dla obiektu. Do obsługi, niszczenie i finalizacji, wprowadziliśmy specjalnej składni zapewniające finalizatora. Na przykład:

```
public ref class R {
public:
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }
};
```

`!` Prefiks jest odpowiednikiem tyldy (`~`) powoduje to wprowadzenie destruktor klasy — oznacza to, że obie metody po okresie istnienia mają token poprzedzania ich nazwę klasy. Jeśli syntetyzowany `Finalize` metoda ma miejsce w klasie pochodnej, wywołanie klasy bazowej `Finalize` metoda dodaje się jego końcem. Jeśli destruktor zostanie jawnie wywołany, finalizator jest pomijane. Poniżej przedstawiono, jak może wyglądać transformacji:

```
// internal transformation under new syntax
public ref class R {
public:
   void Finalize() {
      Console::WriteLine( "I am the R::finalizer()!" );
   }
};
```

## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>Przenoszenie z zarządzanych rozszerzeń dla C++ do Visual C++ 2010

Zachowanie środowiska uruchomieniowego zarządzanych rozszerzeń dla programu C++ jest zmieniany, gdy jest ona kompilowana w obszarze Visual C++ zawsze wtedy, gdy klasa odwołania zawiera nieuproszczony destruktor. Algorytm tłumaczenia wymagane jest podobny do następującego:

1. Jeśli destruktor jest obecny, należy napisać ponownie, aby być finalizatory klasy.

1. Jeśli `Dispose` metody, napisz ponownie, do destruktor klasy.

1. Jeśli destruktor jest obecny, ale jest nie `Dispose` metody, zachować destruktor podczas wykonywania pierwszego elementu.

Podczas przenoszenia kodu z zarządzanych rozszerzeń do nowej składni, możesz pominąć wykonywanie tej transformacji. Jeśli aplikacja zależna w jakiś sposób wykonywania metody skojarzone finalizacji, zachowanie aplikacji różnią się dyskretnie niż ten, który powinien.

## <a name="see-also"></a>Zobacz też

[Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Destruktory i finalizatory w porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)