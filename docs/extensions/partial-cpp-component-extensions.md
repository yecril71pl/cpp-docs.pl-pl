---
title: częściowe (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: ad8faa08a2c85e777cbc8721e5842e708b9e6cb1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181853"
---
# <a name="partial--ccli-and-ccx"></a>częściowe (C++/CLI i C++/CX)

**Częściowe** słowo kluczowe umożliwia tworzenie różnych części tej samej klasy referencyjnej niezależnie od siebie i w różnych plikach.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Ta funkcja języka dotyczy tylko środowisko wykonawcze systemu Windows).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Dla klasy referencyjnej, która ma dwie definicje częściowe, **częściowe** słowo kluczowe jest stosowane do pierwszego wystąpienia definicji i jest zazwyczaj wykonywane przez automatycznie wygenerowany kod, tak aby kod ludzki nie używa słowa kluczowego bardzo często. Dla wszystkich kolejnych częściowych definicji klasy Pomiń modyfikator **częściowy** od słowa *kluczowego klasy* i identyfikatora klasy. Gdy kompilator napotka wcześniej zdefiniowaną klasę ref i identyfikator klasy, ale nie ma słowa kluczowego **częściowego** , wewnętrznie łączy wszystkie części definicji klasy ref w jedną definicję.

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
Słowo kluczowe, które deklaruje klasę lub strukturę obsługiwaną przez środowisko wykonawcze systemu Windows. **Klasa ref**, **Klasa wartości**, **Struktura ref**lub **Struktura wartości**.

*identyfikatora*<br/>
Nazwa zdefiniowanego typu.

### <a name="remarks"></a>Uwagi

Klasa częściowa obsługuje scenariusze, w których można modyfikować jedną część definicji klasy w jednym pliku i automatyczne generowanie kodu — na przykład, Projektant XAML — modyfikuje kod w tej samej klasie w innym pliku. Korzystając z klasy częściowej, można uniemożliwić Automatyczne zastępowanie kodu przez generatora kodu. W projekcie programu Visual Studio **częściowy** modyfikator jest automatycznie stosowany do wygenerowanego pliku.

Zawartość: z dwoma wyjątkami definicja klasy częściowej może zawierać wszystko, co może zawierać cała definicja klasy, jeśli pominięto **częściowe** słowo kluczowe. Nie można jednak określić dostępności klasy (na przykład `public partial class X { ... };`) ani **declspec**.

Specyfikatory dostępu używane w definicji klasy częściowej dla *identyfikatora* nie wpływają na domyślną dostępność w kolejnej częściowej lub pełnej definicji klasy dla *identyfikatora*. Wbudowane definicje statycznych elementów członkowskich danych są dozwolone.

Deklaracja: częściowa definicja *identyfikatora* klasy wprowadza tylko *Identyfikator*nazwy, ale nie można użyć *identyfikatora* w sposób, który wymaga definicji klasy. *Identyfikatora* nazwy nie można użyć do znajomości rozmiaru *identyfikatora*lub do użycia podstawowego lub składowego *identyfikatora* do momentu, gdy kompilator napotka pełną definicję *identyfikatora*.

Liczba i porządkowanie: dla *identyfikatora*może istnieć zero lub więcej częściowych definicji klas. Każda częściowa definicja klasy *identyfikatora* musi być jednokierunkowa przed pełną definicją *identyfikatora* (jeśli istnieje pełna definicja; w przeciwnym razie nie można użyć klasy, chyba że jest to zadeklarowane dalej), ale nie musi poprzedzać deklaracji *identyfikatora*. Wszystkie klucze klasy muszą być zgodne.

Pełna definicja: w punkcie pełnej definicji *identyfikatora*klasy zachowanie jest takie samo jak w przypadku, gdy definicja *identyfikatora* zadeklaruje wszystkie klasy podstawowe, składowe itp. w kolejności, w której zostały napotkane i zdefiniowane w klasach częściowych.

Szablony: Klasa częściowa nie może być szablonem.

Typy ogólne: Klasa częściowa może być rodzajowa, jeśli pełna definicja może być ogólna. Natomiast każda klasa częściowa i pełna muszą mieć dokładnie te same parametry ogólne, w tym formalne nazwy parametrów.

Aby uzyskać więcej informacji na temat używania słowa kluczowego **częściowego** , zobacz [częściowe klasy (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

(Ta funkcja języka nie ma zastosowania do środowiska uruchomieniowego języka wspólnego).

## <a name="see-also"></a>Zobacz też

[Klasy częściowe (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)
