---
title: Semantyka typów wartości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 44662f2ad8e79712b4aab17e2784a72e01ec4116
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171856"
---
# <a name="value-type-semantics"></a>Semantyka typów wartości
Semantyka typów wartości zostały zmienione od rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 W tym miejscu jest typ wartości prostego kanonicznej używany podczas rozszerzenia zarządzane dla C++ specyfikacji:  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 W zarządzanych rozszerzeń firma Microsoft może mieć cztery warianty składni typu wartości (gdzie formularze 2 i 3 są takie same semantycznie):  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## <a name="invoking-inherited-virtual-methods"></a>Wywoływanie metody wirtualne dziedziczonych  
 `Form (1)` Obiekt wartości kanonicznej i dostatecznie dobrze przyjmuje się, z wyjątkiem przypadków, gdy ktoś spróbuje taką jak wywołanie dziedziczonej metody wirtualnej `ToString()`. Na przykład:  
  
```  
v.ToString(); // error!  
```  
  
 Aby można było wywołać tę metodę, ponieważ nie jest on przesłaniany w `V`, kompilator musi mieć dostęp do skojarzonej tabeli wirtualnej klasy podstawowej. Typy wartości są w stanie magazynu bez skojarzone wskaźnik do jego tabeli wirtualnej (vptr), wymagane jest, aby `v` można spakować. W projekcie języka rozszerzeń zarządzanych niejawnej konwersji boxing nie jest obsługiwane, ale musi być jawnie określona przez programistę, jak w programie  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 Podstawowy napędowej za ten projekt jest pedagogiczne: podstawowy mechanizm musi być widoczna dla programisty, dzięki czemu będzie ona zrozumiałe "koszt" nie udostępnia wystąpienie w jej typ wartości. Zostały `V` zawiera wystąpienie `ToString`, opakowywanie nie powinno być konieczne.  
  
 Złożoność leksykalne jawnie konwersja boxing obiekt, ale nie podstawowej koszt pakującej, jest usuwany w nowej składni:  
  
```  
v.ToString(); // new syntax  
```  
  
 ale kosztem prawdopodobnie są mylne Projektant klas, aby koszt nie podano konieczności jawnego wystąpienia `ToString` metodę `V`. Przyczyna preferowanie niejawnej konwersji boxing to zwykle jest tylko jeden projektant klas, brak nieograniczoną liczbę użytkowników, czy żaden z nich nie ma swobody zmodyfikować `V` wyeliminować prawdopodobnie uciążliwe pole jawnego.  
  
 Kryteria, o którą należy określić, czy należy zapewnić wystąpienie zastępowanie `ToString` wewnątrz wartości klasa powinna być częstotliwość i lokalizację jego zastosowań. Jeśli jest to bardzo rzadko, jest oczywiście małego korzyści w jego definicji. Podobnie jeśli jest ona wywoływana w obszarach z systemem innym niż wydajność aplikacji, dodać go również nie widoczny doda do ogólnej wydajności aplikacji. Alternatywnie jedną zachować śledzenie dojścia do wartości spakowanej i połączeń przy użyciu tego dojścia nie wymaga konwersji boxing.  
  
## <a name="there-is-no-longer-a-value-class-default-constructor"></a>Nie ma wartości domyślnej konstruktora  
 Inny różnica z typem wartości rozszerzeń zarządzanych i nowej składni jest usunięcie wsparcia dla konstruktora domyślnego. Jest to spowodowane jest zmieniana podczas wykonywania, w którym CLR można utworzyć wystąpienia typu wartości bez wywoływania skojarzone domyślnego konstruktora. Oznacza to, że próba obsługuje konstruktora domyślnego w ramach typu wartości w obszarze rozszerzeń zarządzanych może nie znajduje się w praktyce można zagwarantować. Biorąc pod uwagę że braku gwarancji, uważano lepiej całkowicie usunąć obsługi, a nie została ona być deterministyczna w aplikacji.  
  
 Nie jest to jako zła, początkowo może wydawać się. Jest to spowodowane każdego obiektu typu wartości jest automatycznie wyzerowanie (każdego typu został zainicjowany do wartości domyślnej). W związku z tym członkami lokalne wystąpienie nigdy nie są niezdefiniowane. W tym sensie utraty zdefiniowanie konstruktora domyślnego trivial naprawdę nie jest utratę cały — i w rzeczywistości jest bardziej wydajne, wykonywane przez środowisko CLR.  
  
 Problem jest, gdy użytkownik rozszerzeń zarządzanych definiuje nieuproszczony domyślnego konstruktora. To nie ma mapowania nowej składni. Kod w Konstruktorze będą musiały zostać poddane migracji do metody inicjowania nazwanego, który następnie musi być jawnie wywołana przez użytkownika.  
  
 Obiekt typu wartości w ramach nowej składni deklaracji w przeciwnym razie jest bez zmian. Dół strony to jest, że typów wartości nie są zadowalające zawijania natywnych typów, z następujących powodów:  
  
-   Nie jest obsługiwane dla destruktora w ramach typu wartości. Oznacza to, że jest sposobem zautomatyzowania działań wyzwalane przed upływem okresu istnienia obiektu.  
  
-   Klasy natywnej mogą być zawarte tylko w obrębie typu zarządzanego jako wskaźnik, który jest następnie przydzielić w stercie natywnej.  
  
 Chcielibyśmy opakowywanie klasy natywnej małych w typu wartości, a nie typu odwołania w celu uniknięcia alokacji sterty podwójne: natywnej sterty natywnej typu i stosu CLR do przechowywania zarządzanych otoki. Zawijanie klasy natywnej w ramach typu wartości umożliwia uniknięcie sterty zarządzanej, ale zapewnia sposobem zautomatyzowania odzyskiwanie pamięci natywnej sterty. Typy odwołań są tylko jest to możliwe typ zarządzany, w którym do zakodowania nieuproszczony klasach macierzystych.  
  
## <a name="interior-pointers"></a>Wewnętrznych wskaźników  
 `Form (2)` i `Form (3)` powyżej można rozwiązać prawie wszystko w tym world lub następnego (czyli niczego zarządzanym lub macierzystym). Tak na przykład następujące są dozwolone w zarządzanych rozszerzeń:  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
  
V v = { 0 };  // Form (1)  
V *pv = 0;  // Form (2)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0;  // Form (4)  
  
R* r;  
  
pv = &v;            // address a value type on the stack  
pv = __nogc new V;  // address a value type on native heap  
pv = pvgc;          // we are not sure what this addresses  
pv = pvbx;          // address a boxed value type on managed heap  
pv = &r->vr;        // an interior pointer to value type within a  
                    //    reference type on the managed heap  
```  
  
 Tak `V*` można usunąć lokalizacji lokalnej bloku (i może być dangling), w zakresie globalnym, w ramach natywnego stercie (na przykład, jeśli obiekt spełnia już został usunięty), w stercie CLR (i w związku z tym będą śledzone Jeśli powinno być przemieszczane podczas wyrzucania elementów bezużytecznych) i w obrębie wewnątrz obiektu odwołania na stercie CLR (wskaźnik wewnętrzny, ponieważ jest to nazywane również w sposób niewidoczny dla śledzenia).  
  
 W zarządzanych rozszerzeń nie istnieje sposób wyodrębnienie natywnego aspektów `V*`; oznacza to, jest ona traktowana w jego włącznie, który obsługuje możliwość jego adresowania obiektu lub podobiektów na stercie zarządzanej.  
  
 W nowej składni wskaźnika typu wartości jest brane pod uwagę dwa typy: `V*`, która jest ograniczona do lokalizacji sterty-CLR i wskaźnik wewnętrzny `interior_ptr<V>`, który umożliwia, ale nie wymaga adresu w stercie zarządzanej.  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 `Form (2)` i `Form (3)` zarządzanych rozszerzeń Mapuj na `interior_ptr<V>`. `Form (4)` jest śledzenie dojścia. Dotyczy on cały obiekt, który został opakowany w stercie zarządzanej. Jest translacja w nowej składni w `V^`,  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 Następujące deklaracje rozszerzeń zarządzanych wszystkie mapowane na wewnętrznych wskaźników w nowej składni. (Są one typów wartości w ramach `System` przestrzeni nazw.)  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 Typy wbudowane nie są traktowane jako typy zarządzane, chociaż służą jako aliasów do typów w ramach `System` przestrzeni nazw. W związku z tym następujące mapowania przechowywania true między rozszerzeń zarządzanych i nowej składni:  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 Podczas tłumaczenia `V*` w programie istniejących ma zawsze zwrócić do najbardziej zachowawcze strategii `interior_ptr<V>`. Jest to, jak był traktowany w obszarze rozszerzeń zarządzanych. W nowej składni programistę ma ograniczenia typu wartości na adresy-zarządzanej sterty, określając opcję `V*` zamiast wskaźnik wewnętrzny. Jeśli tłumaczenia programu, można wykonać przechodnie zamknięcia jego zastosowań i pamiętaj, że żaden przypisany adres nie jest w stercie zarządzanej, następnie pozostawieniu ich jako `V*` funkcjonuje prawidłowo.  
  
## <a name="pinning-pointers"></a>Unieruchamianie wskaźników  
 Moduł zbierający elementy bezużyteczne opcjonalnie może przenieść obiekty, które znajdują się na stercie CLR do różnych lokalizacji w stercie, zazwyczaj podczas fazy kompaktowania. Ten ruch nie jest problemem śledzenie dojść, odwołań śledzenia i wskaźników wewnętrznych, które aktualizacji tych jednostek w sposób niewidoczny dla użytkownika. Ten ruch jest jednak problem, jeśli użytkownik przejdzie na stercie CLR poza środowisko uruchomieniowe adres obiektu. W takim przypadku volatile ruch obiektu jest może spowodować błąd czasu wykonywania. Do zwolnienia obiektów, takich jak te przeniesienie, firma Microsoft musi lokalnie przypiąć je do ich lokalizacji dla zakresu ich wykorzystania poza.  
  
 W zarządzanych rozszerzeń *przypiętego wskaźnika* jest deklarowany przez kwalifikowanie deklaracji wskaźnika z `__pin` — słowo kluczowe. Oto przykład nieco zmodyfikowany ze specyfikacji rozszerzeń zarządzanych:  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // ...  
};  
```  
  
 W nowym projekcie języka przypiętego wskaźnika jest zadeklarowana za pomocą składni jest odpowiednikiem wskaźnik wewnętrzny.  
  
```  
ref struct H  
{  
public:  
   int j;  
};  
  
int main()  
{  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
  
   // ...  
}  
```  
  
 Przypiętego wskaźnika w nowej składni jest specjalny przypadek wskaźnik wewnętrzny. Pozostają oryginalnego ograniczenia dotyczące przypiętego wskaźnika. Na przykład nie można użyć jako parametru lub zwracany typ metody; mogą być deklarowane tylko na lokalny obiekt. Liczba dodatkowych ograniczeń, jednak zostały dodane w nowej składni.  
  
 Wartość domyślna przypiętego wskaźnika jest `nullptr`, a nie `0`. A `pin_ptr<>` nie można zainicjować lub przypisać `0`. Wszystkie przypisania `0` w istniejącym kodzie będą musiały zostać zmienione do `nullptr`.  
  
 Przypiętego wskaźnika w obszarze rozszerzeń zarządzanych miał prawo adresów całego obiektu, jak w poniższym przykładzie pobierana z specyfikacji rozszerzeń zarządzanych:  
  
```  
__gc class G {  
public:  
   void incr(int* pi) { pi += 1; }  
};  
__gc struct H { int j; };  
void f( G * g ) {  
   H __pin * pH = new H;     
   g->incr(& pH -> j);     
};  
```  
  
 W nowej składni przypinanie całego obiektu zwrócone przez `new` wyrażenie nie jest obsługiwane. Zamiast adresu elementu członkowskiego wewnętrzne musi przypięty. Na przykład  
  
```  
ref class G {  
public:  
   void incr(int* pi) { *pi += 1; }  
};  
ref struct H { int j; };  
void f( G^ g ) {  
   H ^ph = gcnew H;  
   Console::WriteLine(ph->j);  
   pin_ptr<int> pj = &ph->j;  
   g->incr(  pj );  
   Console::WriteLine(ph->j);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wartości i ich zachowania (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md)   
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)