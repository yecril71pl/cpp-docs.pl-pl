---
title: Obiekt okres istnienia i zarządzanie zasobami (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 634bef1bf9d2d3128497a1321631ca8665fed144
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423499"
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>Okres istnienia obiektów i zarządzanie zasobami (Modern C++)
W przeciwieństwie do zarządzanego języków C++ nie ma wyrzucanie elementów bezużytecznych (GC), który automatycznie zwalnia zasoby nie dłużej użycia pamięci podczas działania programu. W języku C++ zarządzanie zasobami jest bezpośrednio powiązana z okres istnienia obiektu. W tym dokumencie opisano czynników, które mają wpływ na okres istnienia obiektu w języku C++ oraz sposób zarządzania nim.  
  
 C++ nie ma GC, przede wszystkim, ponieważ nie obsługuje zasobów — do pamięci. Destruktory deterministyczna, podobnie jak w języku C++ może obsługiwać tylko zasoby pamięci i innych niż pamięci jednakowo. Wykaz Globalny ma również inne problemy, takie jak wyższe koszty w pamięci i użycie procesora CPU i lokalizacji. Ale powszechności podstawowych problem, który nie skorygowane przez inteligentne optymalizacji.  
  
## <a name="concepts"></a>Pojęcia  
 Hermetyzacja jest ważną kwestią w przystawce Zarządzanie okres istnienia obiektu — osoba używa obiektu nie musi wiedzieć, zasobów, które obiekt, do którego należy, lub jak je usuwać, lub nawet Określa, czy jest właścicielem żadnych zasobów w ogóle. Posiada zniszczyć obiektu. Podstawowe języka C++ ma na celu zapewnienie, że obiekty zostały zniszczone w właściwym czasie, oznacza to, jak bloki są zakończone, w kolejności odwrotnej konstrukcji. Gdy obiekt zostanie zniszczony, jego baz i elementów członkowskich zostaną zniszczone w określonej kolejności.  Język automatycznie niszczy obiektów, dopiero po wykonaniu specjalnych np. Alokacja sterty lub nowego położenia.  Na przykład [wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md) jak `unique_ptr` i `shared_ptr`, i, takich jak kontenery standardowa biblioteka C++ `vector`, Hermetyzowanie `new` / `delete` i `new[]` / `delete[]` w obiektach, które mają destruktory. Dlatego tak ważne użyć wskaźniki inteligentne i kontenery standardowa biblioteka C++.  
  
 Innym ważnym pojęciem w zarządzanie okresem istnienia: destruktorów. Destruktory hermetyzować zwolnienia zasobów.  (Często używane klawisz skrótu jest RRID, zniszczenie jest zwolnienia zasobów).  Zasób, to element, którego można uzyskać od "system" i muszą być ponownie później.  Pamięci jest najbardziej typowych zasobów, ale istnieją także pliki, sockets tekstury i innych zasobów z systemem innym niż pamięci. Zasób "właścicielem" oznacza, można go użyć, gdy zajdzie taka potrzeba, ale również mają zostać zwolnione po zakończeniu pracy z nim.  Gdy obiekt zostanie zniszczony, jego destruktora zwalnia zasoby, które są jego własnością.  
  
 Końcowe koncepcja jest DAG (skierowane wykresu acyklicznego.).  Struktury własności w programie formularzy DAG. Obiekt nie może należeć do samego siebie — nie jest to tylko możliwe, ale także z założenia jest bez znaczenia. Jednak dwa obiekty można udostępniać prawo własności obiektu trzecich.  Kilka rodzajów łącza są w grupie DAG, jak to możliwe: A jest członkiem grupy B (A właścicielem B), magazyny C `vector<D>` (C jest właścicielem każdy element D), magazyny E `shared_ptr<F>` (E udostępnia własność F, prawdopodobnie z innymi obiektami), itd.  Tak długo, jak nie ma żadnych cykle i każde łącze w DAG jest reprezentowana przez obiekt ma destruktora (zamiast raw wskaźnik, dojście lub inny mechanizm), a następnie przecieków zasobów jest niemożliwe, ponieważ język uniemożliwia je. Zasoby są wydawane natychmiast po nie są już potrzebne, bez modułu zbierającego elementy bezużyteczne uruchomiona. Okres istnienia, śledzenie jest wolny koszty dla zakresu stosu, zasad, członków i powiązanych przypadków i niedrogie dla `shared_ptr`.  
  
### <a name="heap-based-lifetime"></a>Na podstawie sterty okres istnienia  
 Okres istnienia obiektu sterty, można użyć [wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md). Użyj `shared_ptr` i `make_shared` jako wskaźnik domyślne i przydzielania. Użyj `weak_ptr` aby przerwać cykle, czy buforowanie i obserwować obiektów bez wpływu na i przy założeniu niczego o ich życia.  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 Użyj `unique_ptr` dla unikatowy własność, na przykład w *mechanizm pimpl w czasie* idiom. (Zobacz [mechanizm pimpl hermetyzacji w czasie kompilacji w czasie](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md).) Wprowadź `unique_ptr` podstawowym celem wszystkie jawne `new` wyrażenia.  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 Wskaźniki raw służącego do innych niż własności i obserwacji. Może dangle wskaźnik będącej właścicielem, ale nie nastąpił przeciek.  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 Gdy wymagana jest optymalizacji wydajności, może być konieczne użycie *dobrze hermetyzowany* będącej właścicielem, wskaźniki i jawnego wywołania do usunięcia. Przykładem jest podczas implementowania struktury danych niskiego poziomu.  
  
### <a name="stack-based-lifetime"></a>Na podstawie stosu okres istnienia  
 W nowoczesnych wersji języka C++ *opartego na stosie zakresu* wydajny sposób do pisania kodu, niezawodne, ponieważ oznacza połączenie automatyczne *istnienia stosu* i *okres istnienia elementu członkowskiego danych* o wysokiej wydajności — okres istnienia śledzenia jest zasadniczo bezpłatne koszty. Okres istnienia obiektów sterty wymaga większego ręcznego zarządzania i może być źródłem przecieków zasobów i wydajność, szczególnie w przypadku, gdy użytkownik pracuje z pierwotnych wskaźniki. Należy wziąć pod uwagę ten kod, który pokazuje zakresu na podstawie stosu:  
  
```cpp  
class widget {  
private:  
    gadget g;   // lifetime automatically tied to enclosing object  
public:  
    void draw();  
};  
  
void functionUsingWidget () {  
    widget w;   // lifetime automatically tied to enclosing scope  
                // constructs w, including the w.g gadget member  
    // ...
    w.draw();  
    // ...
} // automatic destruction and deallocation for w and w.g  
  // automatic exception safety,   
  // as if "finally { w.dispose(); w.g.dispose(); }"  
```  
  
 Oszczędnie korzystać statycznego okresu istnienia (globalne statyczna, funkcja statyczna lokalnych), ponieważ mogą wystąpić problemy. Co się stanie, gdy Konstruktor jest obiekt globalny zgłasza wyjątek? Zazwyczaj błędów aplikacji w taki sposób, który może być trudne do debugowania. Kolejność konstrukcji jest problematyczne statycznego okresu istnienia obiektów i nie jest bezpieczne współbieżności. Nie tylko słowo konstrukcji obiektów problem, może być skomplikowane, kolejność likwidacji, szczególnie w przypadku polimorfizm. Nawet jeśli z obiektu lub zmienna nie jest polimorficzny i nie ma złożonych konstrukcji/zniszczenia kolejności, występuje nadal problem wątkowo współbieżności. Aplikacji wielowątkowych bezpiecznie nie można modyfikować danych w obiektach statyczne bez magazynu lokalnego wątku, blokowania zasobów i inne specjalne środki ostrożności.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)