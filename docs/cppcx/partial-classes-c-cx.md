---
title: Klasy częściowe (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 71df19e98192a7704d4528fe730ce79977383a9b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740420"
---
# <a name="partial-classes-ccx"></a>Klasy częściowe (C + +/ CX)

Częściowa klasa jest konstrukcja, która obsługuje scenariusze, w których w przypadku modyfikowania jednej części definicji klasy i automatyczne generowanie kodu oprogramowania — na przykład projektant XAML — jest także modyfikowanie kodu w tej samej klasy. Za pomocą klasy częściowej, można zapobiec projektanta zastępowanie kodu. W projekcie programu Visual Studio `partial` modyfikator, jest stosowane automatycznie wygenerowanego pliku.

## <a name="syntax"></a>Składnia

Aby zdefiniować klasę częściową, należy użyć `partial` — słowo kluczowe bezpośrednio przed klucz klasy o jakie byłyby definicję klasy normalne. Słowo kluczowe, takie jak `partial ref class` jest kontekstowym słowem kluczowym, który zawiera białych znaków. Definicje częściowe są obsługiwane w następujących konstrukcji.

- `class` lub `struct`

- `ref class` lub `ref struct`

- `value class` lub `value struct`

- `enum` lub `enum class`

- `ref interface`, `interface class`, `interface struct`, lub `__interface`

- `union`

W tym przykładzie przedstawiono częściowym `ref class`:

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>Spis treści

Definicji częściowej klasy może zawierać wszystko, co w przypadku może zawierać definicję klasy pełną `partial` pominięto — słowo kluczowe. Z jednym wyjątkiem w tym wszelkie prawidłowa konstrukcja, takich jak klas bazowych, elementy członkowskie danych, funkcje składowe, wyliczenia, deklaracje funkcji friend i atrybutów. I wbudowane definicje statyczne elementy członkowskie danych są dozwolone.

Jedynym wyjątkiem jest klasa ułatwień dostępu. Na przykład instrukcja `public partial class MyInvalidClass {/* ... */};` , występuje błąd. Wszystkie specyfikatory dostępu, które są używane w definicji klasy częściowej dla MyInvalidClass nie mają wpływu na dostępność domyślne w definicji kolejnych klasy częściowego lub pełnego dla MyInvalidClass.

Poniższy fragment kodu pokazuje ułatwień dostępu. W pierwszej klasy częściowej `Method1` jest publiczny, ponieważ jego dostępność jest publiczna. W drugim klasy częściowej `Method2` jest prywatny, ponieważ wartość domyślna klasa dostępu jest prywatny.

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>Deklaracja

Częściową definicję klasy, takie jak *MyClass* jest tylko deklaracja MyClass. Oznacza to, że tylko wprowadza nazwę *MyClass*. *MyClass* nie można używać w taki sposób, że wymaga definicji klasy, na przykład, wiedząc, rozmiar *MyClass* lub korzystanie z obiektem bazowym ani składową z *MyClass*. *MyClass* jest uważany za można zdefiniować tylko, gdy kompilator napotka definicji — do częściowego *MyClass*.

W poniższym przykładzie pokazano zachowanie deklaracji klasy częściowej. Po zgłoszeniu #1 *MyClass* może służyć jako, jeśli zostałaby napisana jako deklaracją do przodu `ref class MyClass;`. Deklaracja jest równoważna #1.Declaration deklaracji #3 #2 jest nieprawidłowa, ponieważ jest deklaracją do przodu dla klasy. Ale deklaracja #4 jest nieprawidłowy ponieważ

*MyClass* nie jest w pełni zdefiniowana.

Nie używa deklaracji #5 `partial` — słowo kluczowe i deklaracji pełni definiuje *MyClass*. W związku z tym deklaracja #6 jest nieprawidłowy.

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>Liczbę i kolejność

Może to być zero lub więcej częściowych definicji klasy dla każdej pełnej definicji klasy.

Każdy definicję klasy częściowej klasy leksykalnie musi poprzedzać jeden pełna definicja tej klasy, ale nie musi poprzedzać deklaracje przechodzenia do przodu klasy. W przypadku nie pełnej definicji klasy, następnie deklaracji klasy częściowej mogą być tylko deklaracje przechodzenia do przodu.

Wszystkie klucze klasy, takie jak `class` i `struct` muszą być zgodne. Na przykład, występuje błąd kodu `partial class X {}; struct X {};`.

Poniższy przykład pokazuje liczbę i kolejność. Ostatnie częściowa deklaracja kończy się niepowodzeniem, ponieważ klasa jest już zdefiniowana.

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>Pełna definicja

Punkcie pełna definicja klasy X zachowanie jest takie same tak, jakby definicji X była zadeklarowana wszystkie klasy podstawowe, członków i tak dalej, w kolejności, w którym zostały napotkano i zdefiniowane w klasach częściowa. Oznacza to, że zawartość klasy częściowe są traktowane tak, jakby były one napisane punkcie pełna definicja klasy i wyszukiwania nazw i inne reguły języka, które są stosowane punkcie pełna definicja klasy tak, jakby zawartość klasy częściowe zostały napisane w miejscu

Poniższe dwa przykłady kodu mają identyczne znaczenie i efekt. W pierwszym przykładzie użyto klasy częściowej, a nie w drugim przykładzie.

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>Szablony

Częściowe klasy nie może być szablonem.

## <a name="restrictions"></a>Ograniczenia

Klasy częściowe nie mogą rozciągać się poza jedno tłumaczenie jednostki.

`partial` Słowo kluczowe jest obsługiwane tylko w połączeniu z `ref class` — słowo kluczowe lub `value class` — słowo kluczowe.

### <a name="examples"></a>Przykłady

W poniższym przykładzie zdefiniowano `Address` klasy przez dwa pliki kodu. Modyfikuje projektanta `Address.details.h` i modyfikować `Address.h`. Tylko definicja klasy w pierwszym pliku używa `partial` — słowo kluczowe.

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
