---
title: Klasy częściowe (C++/CX)
description: Jak deklarować klasy częściowe i używać ich w języku C++/CX.
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 70225069c948a50b38ac3642113cf940c86cf8da
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609061"
---
# <a name="partial-classes-ccx"></a>Klasy częściowe (C++/CX)

Klasa częściowa to konstrukcja, która obsługuje scenariusze, w których jest modyfikowana jedna część definicji klasy oraz automatyczne oprogramowanie generujące kod — na przykład Projektant XAML — również modyfikuje kod w tej samej klasie. Korzystając z klasy częściowej, można zapobiec zastąpieniu kodu przez projektanta. W projekcie programu Visual Studio **`partial`** modyfikator jest automatycznie stosowany do wygenerowanego pliku.

## <a name="syntax"></a>Składnia

Aby zdefiniować klasę częściową, użyj **`partial`** słowa kluczowego bezpośrednio przed kluczem klasy, co mogłoby być normalną definicją klasy. Słowo kluczowe, takie jak **`partial ref class`** to kontekstowe słowo kluczowe, które zawiera znaki odstępu. Definicje częściowe są obsługiwane w następujących konstrukcjach.

- **`class`** oraz **`struct`**

- **`ref class`** oraz **`ref struct`**

- **`value class`** oraz **`value struct`**

- **`enum`** oraz **`enum class`**

- **`ref interface`**, **`interface class`** , **`interface struct`** lub **`__interface`**

- **`union`**

Ten przykład ilustruje częściowe **`ref class`** :

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>Zawartość

Definicja klasy częściowej może zawierać wszystko, co może zawierać cała definicja klasy, jeśli **`partial`** słowo kluczowe zostało pominięte. W przypadku jednego wyjątku obejmuje to wszelkie prawidłowe konstrukcje, takie jak klasy bazowe, składowe danych, funkcje składowe, wyliczenia, deklaracje zaprzyjaźnione i atrybuty. I definicje wbudowane składowych danych statycznych są dozwolone.

Jedynym wyjątkiem jest dostępność klas. Na przykład, instrukcja `public partial class MyInvalidClass {/* ... */};` jest błędem. Wszelkie specyfikatory dostępu, które są używane w definicji klasy częściowej dla MyInvalidClass, nie wpływają na domyślne ułatwienia dostępu w kolejnej częściowej lub pełnej definicji klasy dla MyInvalidClass.

Poniższy fragment kodu ilustruje ułatwienia dostępu. W pierwszej klasie częściowej `Method1` jest publiczna, ponieważ jej dostępność jest publiczna. Druga klasa częściowa `Method2` jest prywatna, ponieważ domyślna dostępność klas jest prywatna.

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>Oświadczeń

Częściowa definicja klasy, na przykład, `MyClass` jest tylko deklaracją MyClass. Oznacza to, że wprowadza tylko nazwę `MyClass` . `MyClass` nie można użyć w sposób, który wymaga definicji klasy, na przykład, wiedząc o rozmiarze `MyClass` lub korzystaniu z bazy lub składowej `MyClass` . `MyClass` jest uznawany za zdefiniowany tylko wtedy, gdy kompilator napotka nieczęściową definicję `MyClass` .

Poniższy przykład demonstruje zachowanie deklaracji klasy częściowej. Po #1 deklaracji, `MyClass` można użyć tak, jakby była zapisywana jako deklaracja do przodu, `ref class MyClass;` . Deklaracja #2 jest równoważna z deklaracją #1. Deklaracja #3 jest prawidłowa, ponieważ jest to Deklaracja do przodu klasy. Ale deklaracja #4 jest nieprawidłowa, ponieważ

`MyClass` nie jest w pełni zdefiniowany.

Deklaracja #5 nie używa **`partial`** słowa kluczowego, a deklaracja w pełni definiuje `MyClass` . W związku z tym #6 deklaracji jest prawidłowa.

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>Liczba i porządkowanie

Dla każdej pełnej definicji klasy może istnieć co najmniej zero definicji klasy częściowej.

Każda częściowa definicja klasy klasy musi być jednokierunkowa przed jedną pełną definicją tej klasy, ale nie musi poprzedzać deklaracji przekazywania klasy. Jeśli nie ma żadnej pełnej definicji klasy, deklaracje częściowej klasy mogą być wyłącznie deklaracjami do przodu.

Wszystkie klucze klasy, takie jak **`class`** i, **`struct`** muszą być zgodne. Na przykład jest to błąd do kodu `partial class X {}; struct X {};` .

Poniższy przykład ilustruje liczbę i porządkowanie. Ostatnia deklaracja częściowa nie powiodła się, ponieważ Klasa jest już zdefiniowana.

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>Pełna definicja

W punkcie pełnej definicji klasy X zachowanie jest takie samo, jak gdyby definicja X zadeklarowała wszystkie klasy podstawowe, elementy członkowskie itd., w kolejności, w której zostały napotkane i zdefiniowane w klasach częściowych. Oznacza to, że zawartość klas częściowych jest traktowana tak, jakby były zapisywane w punkcie pełnej definicji klasy, a wyszukiwanie nazw i inne reguły języka są stosowane w punkcie pełnej definicji klasy, tak jakby zawartość klas częściowych była zapisywana.

Poniższe dwa przykłady kodu mają identyczne znaczenie i skutek. Pierwszy przykład używa klasy częściowej, a drugi przykład nie.

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>Szablony

Klasa częściowa nie może być szablonem.

## <a name="restrictions"></a>Ograniczenia

Klasa częściowa nie może przekroczyć jednej jednostki tłumaczenia.

**`partial`** Słowo kluczowe jest obsługiwane tylko w połączeniu ze **`ref class`** słowem kluczowym lub **`value class`** słowem kluczowym.

### <a name="examples"></a>Przykłady

W poniższym przykładzie zdefiniowano `Address` klasę w dwóch plikach kodu. Projektant modyfikuje `Address.details.h` i zmodyfikuje `Address.h` . Tylko definicja klasy w pierwszym pliku używa **`partial`** słowa kluczowego.

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
