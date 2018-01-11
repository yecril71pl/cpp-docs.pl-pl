---
title: Zmiany w semantyce destruktora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c85ac0b082e8ea1dfbff007a68061e6a286390cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-destructor-semantics"></a>Zmiany w semantyce destruktora
Semantyka dla klasy destruktory zmieniły się znacznie rozszerzeń Managed Extensions dla języka C++ dla Visual C++.  
  
 W zarządzanych rozszerzeń destruktora klasy uzyskanej w obrębie klasy odwołania, ale nie w klasie wartości. To nie została zmieniona w nowej składni. Jednak semantyce destruktora klasy zostały zmienione. Ten temat koncentruje się na przyczyny tego zmienić i omówiono jej wpływ na tłumaczenia istniejącego kodu CLR. Prawdopodobnie jest najważniejsze zmiany poziomu programisty między dwoma wersjami języka.  
  
## <a name="non-deterministic-finalization"></a>Finalizacja deterministyczna z systemem innym niż  
 Przed pamięci skojarzona z obiektem jest odzyskana przez moduł garbage collector, skojarzony `Finalize` , jeśli istnieje, jest wywoływana metoda. Można traktować tę metodę jako rodzaj nadtypem destruktor, ponieważ nie jest związana z programu okres istnienia obiektu. Nazywamy to finalizacji. Czas tylko gdy lub nawet czy `Finalize` wywoływana jest metoda nie jest zdefiniowana. Jest to, możemy znaczenie podczas mówi się, że wyrzucanie elementów bezużytecznych wykazuje finalizacji deterministyczna.  
  
 Finalizacja deterministyczna nie działa prawidłowo w przypadku zarządzania pamięci dynamicznej. Gdy dostępna pamięć staje się ograniczone, moduł zbierający elementy bezużyteczne jest uruchamiane. W obszarze pamięci zbierane środowiska, destruktory do wolnej pamięci nie są konieczne. Finalizacja deterministyczna inne niż nie działa dobrze, jednak podczas obiekt utrzymuje krytyczne zasobów takich jak połączenia z bazą danych lub blokady pewnego rodzaju. W takim przypadku należy jak najszybciej wydania tego zasobu. W środowisku macierzystym, które odbywa się przy użyciu pary konstruktora/destruktora. Zaraz po zakończeniu okresu istnienia obiektu podczas kończenia lokalnego bloku, w którym jest zadeklarowany lub gdy stos unravels z powodu zgłoszenia wyjątku, wykonuje destruktor i automatycznie zwolnieniu zasobu. Takie podejście dobrze działa i jego braku mocy rozszerzeń zarządzanych sorely została pominięta.  
  
 Rozwiązanie udostępniane przez środowisko CLR, to dla klasy do zaimplementowania `Dispose` metody `IDisposable` interfejsu. W tym miejscu problemu jest to, że `Dispose` wymaga jawnego wywołania przez użytkownika. To jest podatne na błędy. W języku C# zawiera niewielkie formę automatyzacji w formie specjalnego `using` instrukcji. Projekt rozszerzeń zarządzanych podać specjalnych nie są obsługiwane.  
  
## <a name="destructors-in-managed-extensions-for-c"></a>Destruktory w rozszerzenia zarządzane dla C++  
 W zarządzanych rozszerzeń destruktor klasy odwołania jest implementowane za pomocą następujących dwóch kroków:  
  
1.  Nazwa destruktora dostarczone przez użytkownika zostanie zmieniona wewnętrznie do `Finalize`. Jeśli klasa ma klasę podstawową (należy pamiętać, że w modelu obiektu CLR, obsługiwana jest tylko pojedyncze dziedziczenie), kompilator injects wywołanie jego finalizator po wykonaniu kodu podanego przez użytkownika. Rozważmy na przykład następująca hierarchia proste pobierane z zarządzanych rozszerzeń specyfikacji języka:  
  
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
  
 W tym przykładzie zarówno destruktory zostały zmienione `Finalize`. `B`w `Finalize` ma wywołanie `A`w `Finalize` metody dodane po wywołaniu `WriteLine`. Jest to, co moduł garbage collector domyślnie wywoła podczas finalizacji. Poniżej przedstawiono ten wewnętrzny przekształcania przykładową:  
  
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
  
1.  W drugim kroku kompilator zsyntetyzuje zmniejszonych destruktor wirtualny. Ten destruktor jest, co nasze programy użytkownika rozszerzeń zarządzanych wywołać bezpośrednio lub za pośrednictwem aplikacji wyrażenia usuwania. Nigdy nie zostanie wywołana przez moduł garbage collector.  
  
     Dwie instrukcje znajdują się w tym syntezatora destruktora. Jeden z nich jest wywołanie `GC::SuppressFinalize` aby upewnić się, że nie istnieją żadne więcej wywołania `Finalize`. Drugi to rzeczywiste wywołanie `Finalize`, reprezentuje destruktor dostarczone przez użytkownika dla tej klasy. Oto, co może to wyglądać tak:  
  
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
  
 Podczas tej implementacji umożliwia użytkownikowi jawnie wywołać klasy `Finalize` — metoda teraz zamiast jednocześnie mają nie kontrolę nad, go nie naprawdę blokuje przy użyciu `Dispose` metody rozwiązania. Jest to zmienić w programie Visual C++.  
  
## <a name="destructors-in-new-syntax"></a>Destruktory w nowej składni  
 W nowej składni destruktora jest zmieniana wewnętrznie do `Dispose` — metoda i klasa odwołanie jest automatycznie rozszerzony do zaimplementowania `IDispose` interfejsu. Oznacza to w programie Visual C++, naszych pary klasy jest on przekształcany w następujący sposób:  
  
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
  
 Gdy albo destruktora jest wywoływane jawnie w nowej składni lub gdy `delete` jest stosowany do dojścia śledzenia odpowiadającego `Dispose` metoda jest wywoływana automatycznie. Jeśli istnieje klasa pochodna wywołania z `Dispose` przy zamknięciu syntezatora metody dodaje się metody klasy podstawowej.  
  
 Jednak to nie otrzymuje nam aż do finalizacja deterministyczna. Aby przejść, które, potrzebujemy dodatkowych obsługi obiektów lokalnego odwołania. (To ustawienie nie obsługuje analogiczne w zarządzanych rozszerzeń, a nie jest to problem tłumaczenia).  
  
## <a name="declaring-a-reference-object"></a>Deklarowanie obiektu referencyjnego.  
 Visual C++ obsługuje deklaracja obiektu klasy odwołania na stosie lokalnego lub jako element członkowski klasy tak, jakby był on dostępny bezpośrednio. W połączeniu z skojarzenie destruktor z `Dispose` metoda, wynik jest automatyczne wywoływanie semantyki finalizacji w typach referencyjnych.  
  
 Po pierwsze definicję klasy Nasze odwołania tak, aby utworzyć obiektu działa jako nabywania zasobów za pośrednictwem jej konstruktora klasy. Po drugie w ramach destruktora klasy wydania zasobów nabyte podczas tworzenia obiektu.  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // everything else...  
};  
```  
  
 Obiekt jest zadeklarowana lokalnie, używając nazwy typu, ale bez towarzyszącego hat. Wszystkie używa obiektu, takie jak wywołania metody, są wykonywane za pomocą kropka wyboru elementu członkowskiego (`.`) zamiast strzałkę (`->`). Na koniec bloku skojarzonego destruktora jest przekształcana na `Dispose`, jest wywoływana automatycznie, jak pokazano poniżej:  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here -  
   // that is, r.Dispose() is invoked  
}  
```  
  
 Jak `using` instrukcji w języku C#, to nie omiń podstawowej ograniczenia CLR wszystkie typy referencyjne muszą zostać przydzielone na stercie CLR. Semantyka podstawowej pozostają niezmienione. Użytkownik może ekwiwalentnie zostały zapisane następujące (i prawdopodobnie jest to wewnętrzny transformacja wykonywane przez kompilator):  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 W efekcie w nowej składni destruktory są ponownie łączyć się z konstruktorów jako automatyczne nabycia i wersji mechanizmu związana z okresu istnienia obiektu lokalnego.  
  
## <a name="declaring-an-explicit-finalize"></a>Deklarowanie Finalize jawne  
 W nowej składni, jak firma Microsoft w tym samouczku, destruktor jest syntezatora do `Dispose` metody. Oznacza to, że gdy destruktor nie jest jawnie wywołana, moduł zbierający elementy bezużyteczne podczas finalizacji, nie będzie jak poprzednio zawierał skojarzony `Finalize` metodę dla obiektu. Do obsługi zniszczenie i finalizacji, wprowadzono mają specjalne składni zapewniające finalizator. Na przykład:  
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 `!` Prefiks jest odpowiednikiem tyldy (`~`) powoduje to wprowadzenie destruktora klasy — oznacza to, że obie metody po okresie istnienia ma token prefiksu nazwy klasy. Jeśli syntetyzowane `Finalize` występuje metody w klasie pochodnej wywołaniem klasy podstawowej `Finalize` metody dodaje się jego końcem. Jeśli destruktor jawnie zostanie wywołany, finalizatora jest pomijane. Oto, jak może wyglądać transformacji:  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>Przenoszenie z rozszerzeń zarządzanych dla języka C++, Visual C++ 2010  
 Zachowania w czasie wykonywania zarządzanych rozszerzeń programu C++ jest zmieniany, gdy jest on skompilowany w programie Visual C++, zawsze, gdy klasa referencji zawiera nieuproszczony destruktora. Algorytm tłumaczenia wymagane jest podobny do następującego:  
  
1.  Jeśli ma destruktora ponownego zapisywania, że jest to finalizator klasy.  
  
2.  Jeśli `Dispose` — metoda, która przepisywania na destruktora klasy.  
  
3.  Jeśli destruktora jest obecny, ale jest nie `Dispose` metody zachować destruktor podczas pierwszego elementu.  
  
 Podczas przenoszenia kodu rozszerzeń Managed Extensions do nowej składni, możesz pominąć wykonywanie tej transformacji. Jeśli aplikacja zależna w jakiś sposób wykonywanie metod finalizacji skojarzony, zachowanie aplikacji różnią się dyskretnie niż ten, który powinien.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Destruktory i finalizatory w porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)