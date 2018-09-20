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
ms.openlocfilehash: 72dc6a613616d13e9ff92e8af0c39c63dfe63162
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413799"
---
# <a name="value-type-semantics"></a>Semantyka typów wartości

Semantyka typów wartości zostały zmienione z zarządzanych rozszerzeń dla C++ do Visual C++.

W tym miejscu jest typu canonical prostą wartością używaną w zarządzanych rozszerzeń dla C++ specyfikacje:

```
__value struct V { int i; };
__gc struct R { V vr; };
```

W zarządzanych rozszerzeń można mamy cztery warianty składni typu wartości (gdzie formularzy, 2 i 3 są takie same semantycznie):

```
V v = { 0 };       // Form (1)
V *pv = 0;         // Form (2) an implicit form of (3)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0; // Form (4) must be local
```

## <a name="invoking-inherited-virtual-methods"></a>Wywoływanie metody wirtualnej dziedziczone

`Form (1)` jest obiektem canonical wartość i przyjmuje się, jest również, z wyjątkiem sytuacji, gdy użytkownik próbuje wywołać odziedziczonej metody wirtualnej, takie jak `ToString()`. Na przykład:

```
v.ToString(); // error!
```

Aby można było wywołać tej metody, ponieważ nie została przesłonięta w `V`, kompilator musi mieć dostęp do skojarzonej tabeli wirtualnej klasy bazowej. Ponieważ typy wartości są w stanie magazynu bez skojarzony wskaźnik do jego tabeli wirtualnej (vptr), takie rozwiązanie wymaga `v` być ujęty w ramkach. W projekcie języka zarządzanych rozszerzeń niejawnej konwersji boxing nie jest obsługiwane, ale muszą być jawnie określone przez programistę, podobnie jak w

```
__box( v )->ToString(); // Managed Extensions: note the arrow
```

Podstawowy napędowa za ten projekt jest pedagogiczne: podstawowy mechanizm musi być widoczne na potwierdzeniu programisty, tak, aby użytkownik będzie zrozumiałe dla "koszt" nie udostępnia wystąpienie w ramach jej typ wartości. Zostały `V` zawiera wystąpienie `ToString`, pakowania, nie będzie to konieczne.

Złożoność leksykalne jawne pakowanie obiektu, ale nie podstawowych kosztów pakowania, zostanie usunięty w nowej składni:

```
v.ToString(); // new syntax
```

ale kosztem potencjalnie mylące projektanta klas, aby koszt nie podano konieczności jawnego wystąpienia `ToString` metodę w ramach `V`. Przyczyna preferowanie niejawnej konwersji boxing to zazwyczaj jest tylko jeden projektanta klas, brak nieograniczoną liczbę użytkowników, z których żadna nie miałoby swobody zmodyfikować `V` , aby wyeliminować polu jawne prawdopodobnie uciążliwe.

Kryteria, o którą należy określić, czy należy zapewnić wystąpienie nadrzędne `ToString` wewnątrz wartości klasy powinna być częstotliwość i lokalizację jego zastosowań. Jeśli jest to bardzo rzadko, oznacza to oczywiście niewielkie korzyści w ich definicji. Podobnie jeśli zostanie wywołana w obszarach bez wydajnych aplikacji, dodając go również nie znaczącym ulepszaniu warunków życia doda do ogólnej wydajności aplikacji. Alternatywnie jeden zachować śledzenie dojścia do wartości spakowanej i wywołań za pośrednictwem dojścia nie wymaga konwersji boxing.

## <a name="there-is-no-longer-a-value-class-default-constructor"></a>Nie ma już Konstruktor domyślny klasy wartości

Inny różnią się z typem wartości zarządzanych rozszerzeń i Nowa składnia jest usunięcie obsługi domyślnego konstruktora. Jest tak, ponieważ istnieją sytuacje, w czasie wykonywania, w którym środowisko CLR można utworzyć wystąpienia typu wartości bez wywoływania skojarzone domyślnego konstruktora. Oznacza to, że próba obsługi domyślnego konstruktora do typu wartości w ramach zarządzanych rozszerzeń można nie znajduje się w praktyce można zagwarantować. Biorąc pod uwagę tego braku gwarancji, został uznało lepszej całkowicie usunąć pomocy technicznej, a nie będzie niedeterministyczna w swojej aplikacji.

Nie jest to jak zła, może początkowo wydawać się. Jest to spowodowane każdego obiektu typu wartości jest zerowany automatycznie (każdego typu jest inicjowany do wartości domyślnej). W rezultacie elementów członkowskich lokalnego wystąpienia nigdy nie są niezdefiniowane. W tym sensie utratę możliwość definiowania trivial domyślnego konstruktora nie jest skomplikowane utratę na wszystkich — i w rzeczywistości jest bardziej wydajne, gdy przeprowadzane przez środowisko CLR.

Problem polega na po użytkownik zarządzanych rozszerzeń definiuje nietrywialnymi domyślnego konstruktora. To nie jest przyporządkowany do nowej składni. Kod w Konstruktorze będzie musiał zostać zmigrowana do metody o nazwie inicjowania, która następnie musi być jawnie wywołany przez użytkownika.

Deklaracja obiektu typu wartościowego, w ramach nowej składni, w przeciwnym razie jest bez zmian. Dół boku to jest, że typy wartości nie są wystarczający dla opakowanie natywnych typów z następujących powodów:

- Brak obsługi destruktora w ramach typu wartości. Oznacza to, że nie ma możliwości do automatyzacji działań wyzwolony przed upływem okresu istnienia obiektu.

- Klasy natywnej mogą być zawarte tylko w obrębie typu zarządzanego jako wskaźnik, który następnie jest przydzielany do natywnej sterty.

Chcielibyśmy opakowywanie klasy natywnej małe w typ wartości, a nie typem referencyjnym Aby uniknąć alokacji stosu podwójnego: sterty natywnej do przechowywania natywnego typu i stosu CLR do przechowywania zarządzanych otoka. OPAKOWYWANIE klasy natywnej do typu wartości pozwala uniknąć zarządzanym stosie, ale zapewnia sposób zautomatyzować odzyskiwanie pamięci sterty natywnej. Typy odwołań są tylko jest to możliwe typu zarządzanego, w którym do opakowania nietrywialnymi macierzystych klas.

## <a name="interior-pointers"></a>Wskaźniki posługiwanie się nimi

`Form (2)` i `Form (3)` powyżej rozwiązywania przy użyciu prawie wszystko w tym świecie lub następne (czyli niczego zarządzane lub natywne). Tak na przykład, następujące są dozwolone w zarządzanych rozszerzeń:

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

Dlatego `V*` rozwiązywania przy użyciu lokalizacji w ramach lokalnego bloku (i mogą być dangling) w zakresie globalnym, w ramach natywnych sterty (na przykład, jeśli obiekt spełnia został już usunięty), w ramach sterty CLR (i w związku z tym będą śledzone Jeśli powinien można przenieść podczas wyrzucania elementów bezużytecznych) i w ramach wewnętrznego obiektu odwołania na stosie CLR (wskaźnika wewnętrznego, ponieważ jest to nazywane również w przezroczysty sposób śledzenia).

W zarządzanych rozszerzeń nie istnieje sposób do oddzielenia natywnych aspektów `V*`; oznacza to, że jest ona traktowana w jego włącznie, który obsługuje możliwość jego odnoszący się do obiektu lub podobiektów na stosie zarządzanym.

W nowej składni wskaźnika typu wartości jest brane pod uwagę dwa typy: `V*`, która jest ograniczona do lokalizacji sterty / CLR i posługiwanie się nimi wskaźnik `interior_ptr<V>`, które umożliwia, ale nie wymaga adres znajdujący się w zarządzanym stosie.

```
// may not address within managed heap
V *pv = 0;

// may or may not address within managed heap
interior_ptr<V> pvgc = nullptr;
```

`Form (2)` i `Form (3)` zarządzanych rozszerzeń mapowania na `interior_ptr<V>`. `Form (4)` Umożliwia to śledzenie dojścia. Spełnia cały obiekt, który ma zostać opakowany w zarządzanym stosie. Jest tłumaczony w nowej składni w `V^`,

```
V^ pvbx = nullptr; // __box V* pvbx = 0;
```

Następujące deklaracje w zarządzanych rozszerzeń wszystkie mapowane na wewnętrzne wskaźników w nowej składni. (Są one typów wartości w ramach `System` przestrzeni nazw.)

```
Int32 *pi;   // => interior_ptr<Int32> pi;
Boolean *pb; // => interior_ptr<Boolean> pb;
E *pe;       // => interior_ptr<E> pe; // Enumeration
```

Wbudowane typy nie są uznawane za typów zarządzanych, mimo że służą jako aliasów do typów w ramach `System` przestrzeni nazw. Zatem następujące mapowania przechowywać wartość true, między zarządzanych rozszerzeń i Nowa Składnia:

```
int * pi;     // => int* pi;
int __gc * pi2; // => interior_ptr<int> pi2;
```

Podczas tłumaczenia `V*` w programach istniejących najbardziej umiarkowaną strategii jest zawsze ustaw ją na `interior_ptr<V>`. Jest to, jak zostało potraktowane w ramach zarządzanych rozszerzeń. W nowej składni programistę posiada opcję ograniczenie typu wartości do adresów niezarządzanych sterty, określając `V*` zamiast wskaźnika wewnętrznego. Jeśli tłumaczenie programu, można zrobić przechodnie zamknięcia jego zastosowań i należy się upewnić, że nie przypisany adres w zarządzanym stosie, następnie równoczesnym pozostawieniu ich jako `V*` jest w dobrym stanie.

## <a name="pinning-pointers"></a>Unieruchamianie wskaźników

Moduł zbierający elementy bezużyteczne opcjonalnie może przenieść obiekty, które znajdują się na stosie CLR do innej lokalizacji w stosie, zazwyczaj w fazie kompaktowania. Ten ruch nie jest problemem, śledzenie dojścia, odwołań śledzenia i wskaźników wewnętrznych, które aktualizacji tych jednostek w sposób niewidoczny dla użytkownika. Ten przepływ jest to problem, jednak jeśli użytkownik został przekazany adres obiektu na stercie CLR poza środowisko uruchomieniowe. W tym przypadku volatile przenoszenia obiektu jest może spowodować błąd czasu wykonywania. Aby wykluczone obiekty, takie jak te przeniesienie, firma Microsoft musi lokalnie przypiąć je do ich lokalizacji dla zakresu ich wykorzystania poza.

W zarządzanych rozszerzeń *przypiętego wskaźnika* zadeklarowano kwalifikując deklaracji wskaźnika z `__pin` — słowo kluczowe. Oto przykład nieco zmodyfikować specyfikację zarządzanych rozszerzeń:

```
__gc struct H { int j; };

int main()
{
   H * h = new H;
   int __pin * k = & h -> j;

   // ...
};
```

W nowym projekcie języka przypiętego wskaźnika jest zadeklarowana za pomocą składni jest odpowiednikiem wskaźnika wewnętrznego.

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

Przypiętego wskaźnika w ramach nowej składni jest przypadkiem szczególnym wskaźnika wewnętrznego. Pozostają oryginalnego ograniczenia dotyczące przypiętego wskaźnika. Na przykład nie może być używany jako parametr lub zwracany typ metody mogą być deklarowane tylko na lokalny obiekt. Liczba dodatkowych ograniczeń, zostały dodane w nowej składni.

Wartość domyślna przypiętego wskaźnika jest `nullptr`, a nie `0`. A `pin_ptr<>` nie można zainicjować ani przypisany `0`. Wszystkie przypisania `0` w istniejącym kodzie należy ją zmienić na `nullptr`.

Przypiętego wskaźnika w ramach zarządzanych rozszerzeń był dozwolony umożliwiającą całego obiektu, jak w poniższym przykładzie pobierana z specyfikacji zarządzanych rozszerzeń:

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

W nowej składni przypinanie cały obiekt zwrócony przez `new` wyrażenie nie jest obsługiwane. Zamiast adresu posługiwanie się nimi składowej musi można przypiąć. Na przykład

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

[Typy wartości i ich zachowania (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)<br/>
[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)