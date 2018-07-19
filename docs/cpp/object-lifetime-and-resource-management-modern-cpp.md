---
title: Obiekt okresu istnienia i zarządzanie zasobami (Modern C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fccba0fe09c6e2fcc636d478824c7dfcc699d653
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941554"
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>Okres istnienia obiektów i zarządzanie zasobami (Modern C++)
W odróżnieniu od języków zarządzanych C++ nie ma wyrzucania elementów bezużytecznych (GC), który automatycznie zwalnia wszystkie zasoby pamięci nie dłużej — używane podczas działania programu. W języku C++ zarządzania zasobami bezpośrednio dotyczą okres istnienia obiektu. Ten dokument zawiera opis czynników wpływających na okres istnienia obiektów w języku C++ i sposobu zarządzania nimi.  
  
 C++ nie ma GC, przede wszystkim, ponieważ jej nie obsługuje zasobów — do pamięci. Tylko deterministyczne destruktory, podobnie jak w języku C++ może równie obsługiwać zasoby pamięci i innych niż ilość pamięci. GC zawiera również inne problemy, takie jak wyższe koszty w użycie procesora CPU i pamięci oraz miejscowości. Ale powszechności podstawowego problemu, nie da się ograniczyć przy użyciu Sprytne optymalizacji.  
  
## <a name="concepts"></a>Pojęcia  
 Ważne w okresie istnienia obiektu zarządzania jest hermetyzacja — osoba używa obiektu nie musi wiedzieć, zasoby, które obiekt, do którego należy, lub sposobu ich usuwanie lub nawet tego, czy jest właścicielem wszystkich zasobów w każdym. Po prostu ma do zniszczenia obiektu. Język podstawowy C++ zaprojektowano w celu zapewnienia, że obiekty są niszczone w właściwym czasie, oznacza to, jak bloki są zakończone, w odwrotnej kolejności konstrukcji. Gdy obiekt jest niszczony, jego baz i elementów członkowskich są niszczone w określonej kolejności.  Język automatycznie niszczy obiekty, chyba że użytkownik nadanie specjalne alokacji stosu lub umieszczania nowych.  Na przykład [inteligentne wskaźniki](../cpp/smart-pointers-modern-cpp.md) takich jak `unique_ptr` i `shared_ptr`, i kontenery standardowej biblioteki C++, takich jak `vector`, hermetyzacji **nowe** /  **Usuń** i `new[]` / `delete[]` w obiektach, które mają destruktory. Dlatego tak ważne do używania inteligentnych wskaźników i kontenery standardowej biblioteki języka C++.  
  
 Kolejnym ważnym pojęciem w zarządzanie okresem istnienia: destruktorów. Destruktory hermetyzacji zasobu wersji.  (Często użyty mnemonik jest RRID, zniszczenia jest wersji zasobu).  Zasób jest coś, co można uzyskać od "system" i konieczne jest nadanie ponownie później.  Pamięć jest najbardziej typowych zasobów, ale istnieją również pliki, gniazda, tekstury i inne zasoby bez pamięci. Zasób "właścicielem" oznacza, można go użyć, gdy ich potrzebujesz, ale musisz też zwolnij go po zakończeniu pracy z nim.  Gdy obiekt jest niszczony, jego destruktor zwalnia zasoby, które jego właścicielem.  
  
 Końcowe koncepcja jest DAG (przekierowanie acykliczne wykresy).  Struktury własności w programie stanowi grupy DAG. Żaden obiekt nie może należeć do samego siebie — to nie tylko możliwe, ale również natury jest bez znaczenia. Jednak dwa obiekty można współwłaścicielem trzeci obiekt.  Kilka rodzajów łącza są możliwe w grupie DAG, takich jak to: element jest elementem członkowskim B (B jest właścicielem A), magazynów C `vector<D>` (C należą do każdego elementu D), magazynów E `shared_ptr<F>` (E udostępnia własności F, prawdopodobnie z innymi obiektami), itd.  Tak długo, jak istnieją żadne cykle i każde łącze na grafie DAG jest reprezentowany przez obiekt ma destruktor (zamiast surowy wskaźnik, dojście lub inny mechanizm), a następnie przeciekom zasobów jest niemożliwe, ponieważ język uniemożliwia ich. Zasoby są zwalniane, natychmiast po zakończeniu nie są już potrzebne, bez modułu zbierającego elementy bezużyteczne uruchomiona. Okres istnienia śledzenia jest bezpłatne obciążenie dla zakresu stosu, podstaw, członków i pokrewnych przypadków i tanią `shared_ptr`.  
  
### <a name="heap-based-lifetime"></a>Oparte na stosie okresu istnienia  
 Okres istnienia obiektów na stosie, można użyć [inteligentne wskaźniki](../cpp/smart-pointers-modern-cpp.md). Użyj `shared_ptr` i `make_shared` jako wskaźnik domyślne oraz alokatorem. Użyj `weak_ptr` Przerwij cykle, czy buforowanie i obserwować obiektów bez wpływu na lub zakładając, że nic o ich życia.  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 Użyj `unique_ptr` dla unikatowe własności, na przykład w *pimpl* idiom. (Zobacz [Pimpl hermetyzacji w czasie kompilacji](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md).) Wprowadź `unique_ptr` podstawowym celem wszystkie jawne **nowe** wyrażenia.  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 Za stosowanie surowych wskaźników dla braku własności i obserwacji. Wskaźnik nie będący właścicielem może dangle, ale go nie przecieki pamięci.  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 Gdy Optymalizacja wydajności jest wymagana, użytkownik może być konieczne użycie *dobrze zhermetyzowany* będącej właścicielem, wskaźniki i jawnych wywołań do usunięcia. Przykładem jest podczas implementowania strukturę danych niskiego poziomu.  
  
### <a name="stack-based-lifetime"></a>Oparty na stosie okresu istnienia  
 W nowoczesnym C++ *zakres oparty na stosie* jest wydajnym sposobem pisania kodu niezawodne, ponieważ łączy ona automatyczne *okres istnienia stosu* i *okres istnienia element członkowski danych* o wysokiej wydajności — okres istnienia śledzenia jest zasadniczo obciążenie. Okres istnienia obiektu sterty wymaga skrupulatne poprawianie listy ręczne zarządzanie i może być źródłem przeciekom zasobów i niskiej wydajności, szczególnie w przypadku, gdy pracujesz z surowych wskaźników. Rozważmy ten kod, który pokazuje zakres oparty na stosie:  
  
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
  
 Oszczędnie korzystać statyczny okres istnienia (globalne statyczne, funkcji lokalnej statycznej), ponieważ mogą wystąpić problemy. Co się stanie, gdy Konstruktor dla obiektów globalnych zgłasza wyjątek? Zazwyczaj błędy aplikacji w sposób, który może być trudne do debugowania. Kolejność konstrukcji jest problematyczne statyczny okres istnienia obiektów i nie jest bezpieczna pod kątem współbieżności. Nie tylko jest konstruowanie obiektu problemu, kolejność zniszczenia może być skomplikowane, zwłaszcza w przypadku polimorfizmu. Nawet jeśli zmiennej lub obiektu nie jest polimorficzny, nie ma złożone tworzenie/niszczenie obiektu porządkowanie się nadal istnieje problem współbieżności metodą o bezpiecznych wątkach. Aplikacja wielowątkowa bezpiecznie nie można zmodyfikować danych w obiektach statycznych bez konieczności lokalny magazyn wątków, blokad zasobów i innych specjalne środki ostrożności.  
  
## <a name="see-also"></a>Zobacz też  
 [Witamy z powrotem w C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)