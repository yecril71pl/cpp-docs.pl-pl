---
title: przestarzałe (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: e4689d3cb1a1757e2ac3bf4ca9eef7670ad5c655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189484"
---
# <a name="deprecated-c"></a>przestarzałe (C++)

W tym temacie opisano przestarzałą deklarację declspec zainstalowaną przez firmę Microsoft. Aby uzyskać informacje o atrybucie `[[deprecated]]` języka c++ 14 i wskazówki dotyczące sytuacji, w których należy używać tego atrybutu w porównaniu z declspec lub pragma specyficzna dla firmy Microsoft, zobacz [ C++ atrybuty standardowe](attributes.md).

Zgodnie z wyjątkami wymienionymi poniżej **przestarzała** deklaracja ma takie same funkcje jak [przestarzała](../preprocessor/deprecated-c-cpp.md) dyrektywa pragma:

- **Przestarzała** deklaracja pozwala określić określone formy przeciążeń funkcji jako przestarzałe, natomiast formularz pragma dotyczy wszystkich przeciążonych formularzy nazwy funkcji.

- **Przestarzała** deklaracja pozwala określić komunikat, który będzie wyświetlany w czasie kompilacji. Tekst komunikatu może pochodzić z makra.

- Makra można oznaczyć tylko jako przestarzałe przy użyciu **przestarzałej** dyrektywy pragma.

Jeśli kompilator napotyka użycie przestarzałego identyfikatora lub standardowego atrybutu [`[[deprecated]]`](attributes.md) , zostanie wygenerowane ostrzeżenie [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak oznaczyć funkcje jako przestarzałe i jak określić komunikat, który będzie wyświetlany w czasie kompilacji, gdy zostanie użyta funkcja przestarzałe.

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak oznaczyć klasy jako przestarzałe i jak określić komunikat, który będzie wyświetlany w czasie kompilacji, gdy przestarzała Klasa jest używana.

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
