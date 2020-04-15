---
title: częściowo  (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: 42e8cc9a20c96e65ed3ddf73d562fe014bd9fa28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350002"
---
# <a name="partial--ccli-and-ccx"></a>częściowo  (C++/CLI i C++/CX)

**Częściowe** słowo kluczowe umożliwia różne części tej samej klasy ref być autorstwa niezależnie i w różnych plikach.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Ta funkcja języka dotyczy tylko środowiska wykonawczego systemu Windows).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Dla klasy ref, która ma dwie definicje częściowe, **częściowe** słowo kluczowe jest stosowane do pierwszego wystąpienia definicji i jest to zazwyczaj wykonywane przez automatycznie wygenerowany kod, tak aby programista ludzki nie używa słowa kluczowego bardzo często. Dla wszystkich kolejnych definicje częściowe klasy, pominąć **modyfikator częściowy** z *klucza klasy* słowa kluczowego i identyfikator klasy. Gdy kompilator napotka wcześniej zdefiniowane ref klasy i identyfikator klasy, ale nie **częściowe** słowa kluczowego, wewnętrznie łączy wszystkie części ref definicji klasy w jednej definicji.

### <a name="syntax"></a>Składnia

```cpp
partial class-key identifier {
   /* The first part of the partial class definition.
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>Parametry

*klucz klasy*<br/>
Słowo kluczowe, które deklaruje klasę lub strukturę, która jest obsługiwana przez środowisko wykonawcze systemu Windows. Albo **ref,** **value class,** **ref struct**lub **value struct**.

*Identyfikator*<br/>
Nazwa zdefiniowanego typu.

### <a name="remarks"></a>Uwagi

Klasa częściowa obsługuje scenariusze, w których zmodyfikujesz jedną część definicji klasy w jednym pliku, a oprogramowanie do automatycznego generowania kodu — na przykład projektantA XAML — modyfikuje kod w tej samej klasie w innym pliku. Za pomocą klasy częściowej, można zapobiec automatycznego generatora kodu z nadpisywania kodu. W projekcie programu Visual Studio **modyfikator częściowy** jest stosowany automatycznie do wygenerowanego pliku.

Zawartość: Z dwoma wyjątkami definicja klasy częściowej może zawierać wszystko, co może zawierać pełna definicja klasy, jeśli pominięto **częściowe** słowo kluczowe. Nie można jednak określić dostępności klasy `public partial class X { ... };`(na przykład) ani **declspec**.

Specyfikatory dostępu używane w definicji klasy częściowej dla *identyfikatora* nie wpływają na domyślną dostępność w kolejnej definicji częściowej lub pełnej klasy dla *identyfikatora*. Definicje wbudowane statycznych elementów członkowskich danych są dozwolone.

Deklaracja: Częściowa definicja *identyfikatora* klasy wprowadza tylko *identyfikator*nazwy, ale *identyfikator* nie może być używany w sposób, który wymaga definicji klasy. Identyfikatora *identifier* nazwy nie można użyć do poznania rozmiaru *identyfikatora*ani do używania podstawy lub elementu członkowskiego *identyfikatora,* dopóki kompilator nie napotka pełnej definicji *identyfikatora.*

Liczba i kolejność: może istnieć zero lub więcej częściowych definicji klas dla *identyfikatora*. Każda częściowa definicja *identyfikatora* klasy musi leksycznie poprzedzać jedną pełną definicję *identyfikatora* (jeśli istnieje pełna definicja; w przeciwnym razie nie można użyć tej klasy, chyba że jest zadeklarowana dalej), ale nie musi poprzedzać przesyłania dalej deklaracji *identyfikatora*. Wszystkie klucze klasy muszą być zgodne.

Pełna definicja: W punkcie pełnej definicji *identyfikatora*klasy zachowanie jest takie samo, jak gdyby definicja *identyfikatora* zadeklarowała wszystkie klasy podstawowe, elementy członkowskie itp.

Szablony: Klasa częściowa nie może być szablonem.

Generyki: Klasa częściowa może być rodzajową, jeśli pełna definicja może być ogólna. Ale każda klasa częściowa i pełna musi mieć dokładnie te same parametry ogólne, w tym formalne nazwy parametrów.

Aby uzyskać więcej informacji na temat używania **częściowego** słowa kluczowego, zobacz [Klasy częściowe (C++/CX).](https://go.microsoft.com/fwlink/p/?LinkId=249023)

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

(Ta funkcja języka nie ma zastosowania do środowiska uruchomieniowego języka wspólnego).

## <a name="see-also"></a>Zobacz też

[Klasy częściowe (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)
