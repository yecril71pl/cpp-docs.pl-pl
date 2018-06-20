---
title: Programy i połączenie (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dba8698461636e292771fc1e5a4f5ac0a633e73
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238672"
---
# <a name="program-and-linkage-c"></a>Program i połączenie (C++)

W programie C++ *symbol*, na przykład nazwę zmiennej lub funkcji mogą być deklarowane dowolną liczbę razy w jego zakresie, ale jego można zdefiniować tylko raz. Jest to reguły jednej definicji (ODR). A *deklaracji* wprowadza (lub ponownego) nazwy do programu. A *definicji* wprowadza nazwę, a w przypadku zmiennej, która jawnie inicjuje go. A *funkcji definicji* składa się z podpisu i treści funkcji.

Są to deklaracje:

```cpp
int i;
int f(int x);
```

Definicje są to:

```cpp
int i{42};
int f(int x){ return x * i; }
```

Program składa się z co najmniej jeden *jednostki tłumaczenia*. Jednostka tłumaczenia składa się z plikiem implementacji (.cpp, .cxx itp.) oraz wszystkich nagłówków (.h, .hpp itp.), które zawiera bezpośrednio lub pośrednio. Każda jednostka tłumaczenia jest kompilowana niezależnie przez kompilator, po upływie którego konsolidator scala w ramach jednej jednostki tłumaczenia skompilowanych *program*. Naruszenia reguły ODR zwykle wyświetlane jako błędy konsolidatora podczas tej samej nazwie ma dwa różne definicje w różnych tłumaczenia jednostki.

Ogólnie rzecz biorąc, jest najlepszy sposób, aby uwidocznić zmiennej w wielu plikach umieść ją w pliku nagłówka, a następnie dodaj # dyrektywy include w każdym pliku .cpp, który wymaga deklaracji. Dodając *obejmują osłony* zawartości nagłówka upewnieniu się, że nazwy deklaruje są zdefiniować tylko raz.

Jednak w niektórych przypadkach może być konieczne zadeklarować zmiennej globalnej lub klasy w pliku .cpp. W takich przypadkach należy sprawdzić kompilatorze i konsolidatorze, czy nazwa obiektu ma być stosowany tylko do jednego pliku lub wszystkich plików.

## <a name="linkage-vs-scope"></a>Połączenie, a zakres

Pojęcie *połączenie* odwołuje się do widoczność globalne symbole (np. zmienne nazwy typu i nazwy funkcji) w programie jako całość przez jednostki tłumaczenia. Pojęcie *zakres* odwołuje się do symboli, które są zadeklarowane w bloku, takich jak przestrzeni nazw, klasy lub treści funkcji. Takie symbole są widoczne tylko w zakresie, w którym są zdefiniowane; pojęcie powiązanie nie ma zastosowania do nich. 

## <a name="external-vs-internal-linkage"></a>Zewnętrzny, a połączenie wewnętrzne

A *wolne funkcja* to funkcja, która jest zdefiniowana globalnie lub zakresie przestrzeni nazw. Zmienne globalne non-const i funkcje wolnego domyślnie mają *połączenie zewnętrzne*; są one widoczne z dowolnej jednostki tłumaczenia w programie. Ta nazwa może więc żadnego innego obiektu globalnego (zmiennej, definicji klasy itp.). Symbol z *zewnętrzne* lub *bez powiązania* jest widoczna tylko w jednostce tłumaczenia, w którym jest zadeklarowany. Jeśli nazwa ma połączenie zewnętrzne, tej samej nazwie może istnieć w innej jednostce tłumaczenia. Zmienne zadeklarowane w definicji klasy lub ciało funkcji ma bez połączenia. 

Możesz wymusić globalną nazwę służącą do Jawne zadeklarowanie go jako zewnętrzne **statycznych**. To ogranicza ich widoczność do tej samej jednostce tłumaczenia, w którym jest zadeklarowany. Należy pamiętać, że w tym kontekście **statycznych** oznacza, że coś innego niż po stosowane do zmiennych lokalnych.

Następujące obiekty są zewnętrzne domyślnie:
- obiekty const
- obiekty constexpr
- definicje typów
- obiekty statyczne w zakresie przestrzeni nazw

Aby zapewnić stałe połączenie zewnętrzne obiektu, Zadeklaruj ją jako **extern** i przypisz jej wartość:

```cpp
extern const int value = 42;
```

Zobacz [extern](extern-cpp.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

 [Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)