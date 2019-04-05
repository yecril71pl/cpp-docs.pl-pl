---
title: częściowe (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: eb9b3907008147cb21f04aec5f42e4896fa35b3c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029951"
---
# <a name="partial--ccli-and-ccx"></a>częściowe (C + +/ CLI i C + +/ CX)

**Częściowe** — słowo kluczowe umożliwia różne części klasy ref autora, niezależnie od siebie i w różnych plikach.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Ta funkcja językowa dotyczy tylko środowiska wykonawczego Windows).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Dla klasy referencyjnej, która ma dwie definicje częściowe **częściowe** — słowo kluczowe jest stosowany do pierwszego wystąpienia definicji i jest to zazwyczaj wykonywane przez automatycznie wygenerowany kod, aby ludzi koder nie bardzo często używa słowa kluczowego. Wszystkie kolejne definicje częściowe klasy, można pominąć **częściowe** modyfikator z *klucz klasy* identyfikator słowa kluczowego i klasy. Gdy kompilator napotka klasy referencyjnej uprzednio zdefiniowany i identyfikator klasy, ale nie **częściowe** — słowo kluczowe, łączy wewnętrznie wszystkie części definicji klasy ref w jednej definicji.

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
Słowo kluczowe, która deklaruje klasy lub struktury, która jest obsługiwana przez środowisko wykonawcze Windows. Albo **klasy referencyjnej**, **klasę wartości**, **ref struct**, lub **struktury wartości**.

*identyfikator*<br/>
Nazwa zdefiniowanego typu.

### <a name="remarks"></a>Uwagi

Klasy częściowej obsługuje scenariusze, w którym można zmodyfikować jednej części definicji klasy, w jednym pliku i automatyczne generowanie kodu oprogramowania — na przykład projektant XAML — modyfikuje kodu w tej samej klasie w innym pliku. Za pomocą klasy częściowej, można zapobiec generatora kodu automatyczne zastępowanie kodu. W projekcie programu Visual Studio **częściowe** modyfikator, jest stosowane automatycznie wygenerowanego pliku.

Zawartość: Z dwoma wyjątkami definicji częściowej klasy może zawierać wszystko, co może zawierać definicję klasy pełna, jeśli **częściowe** — słowo kluczowe został pominięty. Jednak nie można określić klasy ułatwień dostępu (na przykład `public partial class X { ... };`), lub **declspec**.

Używane w definicji klasy częściowej specyfikatory dostępu *identyfikator* nie ma wpływu na dostępność domyślne w definicji kolejnych klas częściowego lub pełnego *identyfikator*. Wbudowane definicje statyczne elementy członkowskie danych są dozwolone.

Deklaracji: Częściową definicję klasy *identyfikator* tylko wprowadza nazwę *identyfikator*, ale *identyfikator* nie można używać w taki sposób, że wymaga definicji klasy. Nazwa *identyfikator* nie używane do ustalenia rozmiaru *identyfikator*, czy mają być używane z obiektem bazowym ani składową z *identyfikator* aż po kompilator napotka pełna definicja *identyfikator*.

Liczba i kolejności: Może to być zero lub więcej częściowych definicji klasy dla *identyfikator*. Każdej definicji klasy częściowej *identyfikator* leksykalnie musi poprzedzać jeden pełna definicja *identyfikator* (Jeśli pełna definicja; w przeciwnym razie klasa nie można użyć z wyjątkiem tak, jakby Deklaracja do przodu), ale nie muszą poprzedzać deklaracje przechodzenia do przodu o *identyfikator*. Wszystkie klucze klasy muszą być zgodne.

Pełna definicja: Punkcie pełna definicja klasy *identyfikator*, zachowanie jest takie same tak, jakby definicji *identyfikator* była zadeklarowana klas bazowych, elementy członkowskie, itp., w kolejności, w której znajdowały się Napotkano i zdefiniowane w klasach częściowa.

Szablony: Częściowe klasy nie może być szablonem.

Typy ogólne: Klasy częściowej mogą być ogólne, jeśli pełna definicja może być ogólna. Ale co klasy częściowe i pełne musi mieć dokładnie tych samych parametrom, w tym nazwy parametrów formalnych.

Aby uzyskać więcej informacji o sposobie używania **częściowe** — słowo kluczowe, zobacz [klasy częściowe (C + +/ CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

(Tej funkcji języka nie ma zastosowania do środowiska uruchomieniowego języka wspólnego).

## <a name="see-also"></a>Zobacz także

[Klasy częściowe (C + +/ CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)