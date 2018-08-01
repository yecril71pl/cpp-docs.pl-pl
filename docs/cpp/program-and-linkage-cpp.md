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
ms.openlocfilehash: 9998e7ad9605d6d2e32bcaff6204fb09dcbca2a5
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405561"
---
# <a name="program-and-linkage-c"></a>Program i połączenie (C++)

W programie C++ *symbol*, na przykład nazwy zmiennej lub funkcji, można zadeklarować dowolną liczbę razy w jego zakresie, ale jej może zostać zdefiniowany tylko jeden raz. Jest to reguły jednej definicji (ODR). A *deklaracji* wprowadza (lub ponownie wprowadza) nazwy do programu. A *definicji* wprowadza nazwę, a w przypadku zmiennej, która jawnie inicjuje ją. A *funkcji definicji* składa się z podpisu i treści funkcji.

Są to deklaracje:

```cpp
int i;
int f(int x);
```

To są definicje:

```cpp
int i{42};
int f(int x){ return x * i; }
```

Program, który składa się z co najmniej jeden *jednostki translacji*. Jednostki translacji składa się z pliku implementacji (.cpp, .cxx itp.) i wszystkich nagłówków (.h, .hpp itp.), które on uwzględnia bezpośrednio lub pośrednio. Każdą jednostkę translacji jest kompilowany niezależnie przez kompilator, po upływie którego konsolidator scala jednostki translacji skompilowany w jednym *program*. Naruszenia reguły ODR zwykle wyświetlane jako błędy konsolidatora podczas takiej samej nazwie ma dwa różne definicje w jednostki translacji różne.

Ogólnie rzecz biorąc, najlepszym sposobem, aby uwidocznić zmienną na wiele plików jest umieszczenie go w pliku nagłówka, a następnie dodać # dyrektywy include w każdym pliku .cpp, który wymaga deklaracji. Dodając *obejmują osłony* wokół zawartości nagłówka możesz upewnić się, czy nazwy deklaruje tylko zdefiniowano jeden raz.

Jednak w niektórych przypadkach może być konieczne zadeklarować zmienną globalną lub klasy w pliku .cpp. W takich przypadkach należy umożliwia informowanie kompilatora i konsolidatora, czy nazwa obiektu ma być stosowany tylko do jednego pliku lub do wszystkich plików.

## <a name="linkage-vs-scope"></a>Powiązania, a zakres

Pojęcie *powiązania* odwołuje się do widoczność symbole globalne (na przykład, nazwy typów nazwy zmiennych i funkcji) w ramach programu jako całość w jednostki translacji. Pojęcie *zakres* odwołuje się do symboli, które są zadeklarowane w obrębie bloku, takich jak przestrzeń nazw, klasy lub treści funkcji. Symbole takie są widoczne tylko w zakresie, w której są zdefiniowane; pojęcie powiązania nie ma zastosowania do nich. 

## <a name="external-vs-internal-linkage"></a>Zewnętrzne i wewnętrzne łączenie

A *wolna funkcja* jest funkcją, która jest zdefiniowana w globalnie lub zakresie przestrzeni nazw. Zmienne globalne non-const i bezpłatne funkcje domyślnie mają *powiązania zewnętrzne*; są one widoczne w dowolnej jednostce translacji programu. Tę nazwę można więc nie innych obiektów globalnych (zmienna, definicja klasy itp.). Symbol z *zewnętrzne* lub *bez połączenia* jest widoczna tylko w obrębie jednostki translacji, w którym jest zdeklarowana. Jeśli nazwa zawiera zewnętrzne, takiej samej nazwie może istnieć w innej jednostce translacji. Zmienne zadeklarowane za pomocą definicji klasy lub w treści funkcji mają bez połączenia. 

Można wymusić globalnej nazwy mają wewnętrzne łączenie jawnie deklarując ją jako **statyczne**. Ogranicza to jego widoczność do tej samej jednostki translacji, w którym jest zdeklarowana. Należy pamiętać, że w tym kontekście **statyczne** oznacza coś innego niż podczas zastosowane do zmiennych lokalnych.

Domyślnie następujące obiekty mają zewnętrzne:
- obiektów stałych
- obiekty wyrażeń constexpr
- definicje typów
- obiekty statyczne w zakresie przestrzeni nazw

Aby dać const powiązania zewnętrzne obiektu, Zadeklaruj go jako **extern** i przypisz jej wartość:

```cpp
extern const int value = 42;
```

Zobacz [extern](extern-cpp.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także
 [Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)