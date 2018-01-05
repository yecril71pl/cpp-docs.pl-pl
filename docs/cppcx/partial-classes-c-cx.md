---
title: "Klasy częściowe (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e122f84bff2b815a00e50950b90230a9d50907a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="partial-classes-ccx"></a>Klasy częściowe (C + +/ CX)
Klasy częściowej jest konstrukcję obsługuje scenariusze, w których modyfikujesz jednej części definicji klasy i automatyczne generowanie kodu oprogramowania — na przykład projektanta XAML — jest również modyfikowanie kodu w tej samej klasy. Za pomocą klasy częściowej, można zapobiec zastępowaniu kodu projektanta. W projekcie programu Visual Studio `partial` modyfikator jest automatycznie stosowane do wygenerowanego pliku.  
  
## <a name="syntax"></a>Składnia  
 Aby zdefiniować klasy częściowej, użyj `partial` — słowo kluczowe bezpośrednio przed klucz klasy z definicji klasy normalne co byłoby. Słowo kluczowe, takie jak `partial ref class` jest kontekstowe słowo kluczowe znaków odstępu. Definicje częściowe są obsługiwane w następujących konstrukcji.  
  
-   `class`lub`struct`  
  
-   `ref class`lub`ref struct`  
  
-   `value class`lub`value struct`  
  
-   `enum`lub`enum class`  
  
-   `ref interface`, `interface class`, `interface struct`, lub`__interface`  
  
-   `union`  
  
 W tym przykładzie pokazano częściowym `ref class`:  
  
 [!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]  
  
## <a name="contents"></a>Spis treści  
 Definicji częściowej klasy może zawierać wszystkich elementów, które mogą zawierać definicji klasy pełne, jeśli `partial` pominięto — słowo kluczowe. Z jednym wyjątkiem w tym wszelkie prawidłowa konstrukcja, takich jak klasy podstawowe, elementy członkowskie danych, funkcji Członkowskich, Typy wyliczeniowe, deklaracje funkcji friend i atrybutów. I tekście definicji statycznych elementów członkowskich danych są dozwolone.  
  
 Jedynym wyjątkiem jest klasa ułatwień dostępu. Na przykład instrukcja `public partial class MyInvalidClass {/* ... */};` jest błędem. Wszelkie specyfikatory dostępu, które są używane w definicji klasy częściowej dla MyInvalidClass nie mają wpływu na dostępność domyślne w definicji kolejnych pełnych lub klasy dla MyInvalidClass.  
  
 Poniższy fragment kodu przedstawia ułatwień dostępu. W klasie częściowej pierwszy `Method1` jest publiczny, ponieważ jego dostępność jest publiczny. W klasie częściowej drugi `Method2` jest prywatny, ponieważ dostępność klasy domyślny jest prywatny.  
  
 [!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]  
  
## <a name="declaration"></a>Deklaracja  
 Częściową definicją klasę, taką jak *MyClass* MyClass stanowi deklarację. Oznacza to, że tylko wprowadza nazwę *MyClass*. *MyClass* nie można używać w taki sposób, który wymaga definicji klasy, na przykład, wiedząc, rozmiar *MyClass* lub przy użyciu podstawowego lub członkiem *MyClass*. *MyClass* jest uznawane za zdefiniowane, tylko gdy kompilator napotka definicji z systemem innym niż częściowego *MyClass*.  
  
 W poniższym przykładzie pokazano zachowanie deklaracji klasy częściowej. Po deklaracji #1 *MyClass* można używać tak, jakby zostały zapisane jako deklaracja przekazująca dalej `ref class MyClass;`. Deklaracja #2 jest odpowiednikiem deklaracji #1.Declaration #3 jest nieprawidłowy, ponieważ jest deklaracja przekazująca dalej do klasy. Deklaracja #4 jest nieprawidłowa, ale ponieważ  
  
 *MyClass* nie jest w pełni zdefiniowana.  
  
 Deklaracja #5 nie używa `partial` — słowo kluczowe i deklarację pełni definiuje *MyClass*. W rezultacie deklaracji #6 jest prawidłowy.  
  
 [!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]  
  
## <a name="number-and-ordering"></a>Liczba i kolejność  
 Może to być zero lub więcej definicji częściowej klasy dla każdego pełnej definicji klasy.  
  
 Każdy definicję klasy częściowej klasy lexically musi poprzedzać jedną definicję pełny tej klasy, ale nie musi występować przed deklaracjami do przodu klasy. Jeśli nie ma pełnej definicji klasy, następnie deklaracjach częściowej klasy może być tylko do przodu deklaracji.  
  
 Wszystkie klucze klasy, takie jak `class` i `struct` muszą być zgodne. Na przykład jest błąd kodu `partial class X {}; struct X {};`.  
  
 W poniższym przykładzie pokazano, numer i kolejność. Ostatni częściowa deklaracja nie powiedzie się, ponieważ klasa jest już zdefiniowana.  
  
 [!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]  
  
## <a name="full-definition"></a>Pełnej definicji  
 W punkcie pełnej definicji klasy X, zachowanie jest takie samo tak, jakby definicji X ma zadeklarowany wszystkie klasy podstawowe, członków i tak dalej, w kolejności, w którym zostały napotkano i zdefiniowanych w klas częściowych. Oznacza to, że zawartość klasy częściowe są traktowane jak gdyby zostały napisane w punkcie pełnej definicji klasy i wyszukiwanie nazw oraz inne zasady języka są stosowane w punkcie pełnej definicji klasy tak, jakby zawartość klasy częściowe napisanych w miejscu  
  
 W poniższych przykładach kodu dwóch mają identyczne znaczenie i efekt. W pierwszym przykładzie użyto częściowej klasy, a nie drugi przykład.  
  
 [!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]  
  
 [!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]  
  
## <a name="templates"></a>Szablony  
 Klasy częściowe nie może być szablonem.  
  
## <a name="restrictions"></a>Ograniczenia  
 Klasy częściowe nie może występować poza jedno tłumaczenie jednostki.  
  
 `partial` — Słowo kluczowe jest obsługiwana tylko w połączeniu z `ref class` — słowo kluczowe lub `value class` — słowo kluczowe.  
  
### <a name="examples"></a>Przykłady  
 W poniższym przykładzie zdefiniowano `Address` klasy w dwóch plików kodu. Modyfikuje projektanta `Address.details.h` i modyfikować `Address.h`. Używa tylko definicję klasy w pliku pierwszego `partial` — słowo kluczowe.  
  
 [!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]  
  
 [!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)