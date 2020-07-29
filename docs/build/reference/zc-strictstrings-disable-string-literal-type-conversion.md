---
title: /Zc:strictStrings (Wyłączanie konwersji typów literału ciągu)
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: df880ed64fa472ff55eb5ee0d17caacf56228ab6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211895"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>`/Zc:strictStrings`(Wyłącz konwersję typu literału ciągu)

Gdy jest określony, kompilator wymaga ścisłej zgodności **`const`** dla wskaźników inicjowanych za pomocą literałów ciągów.

## <a name="syntax"></a>Składnia

> **`/Zc:strictStrings`**[**`-`**]

## <a name="remarks"></a>Uwagi

Jeśli **`/Zc:strictStrings`** jest określony, kompilator wymusza standardowe kwalifikacje języka C++ **`const`** dla literałów ciągów, jako typ "array of `const char` " lub "array of" `const wchar_t` , w zależności od deklaracji. Literały ciągu są niezmienne, a próba zmodyfikowania zawartości jednego wyniku powoduje błąd naruszenia zasad dostępu w czasie wykonywania. Należy zadeklarować wskaźnik ciągu jako **`const`** do zainicjowania go za pomocą literału ciągu lub użyć jawnie **`const_cast`** do zainicjowania wskaźnika, który nie jest **`const`** wskaźnikiem. Domyślnie, lub jeśli **`/Zc:strictStrings-`** jest określony, kompilator nie wymusza standardowych kwalifikacji języka C++ **`const`** dla wskaźników ciągu inicjowanych za pomocą literałów ciągów.

**`/Zc:strictStrings`** Opcja jest domyślnie wyłączona. [`/permissive-`](permissive-standards-conformance.md)Opcja kompilatora niejawnie ustawia tę opcję, ale można ją zastąpić przy użyciu **`/Zc:strictStrings-`** .

Użyj **`/Zc:strictStrings`** opcji, aby zapobiec kompilacji nieprawidłowego kodu. Ten przykład pokazuje, jak prosta błąd deklaracji prowadzi do awarii w czasie wykonywania:

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

Gdy **`/Zc:strictStrings`** jest włączona, ten sam kod raportuje błąd w deklaracji `str` .

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

Jeśli używasz **`auto`** , aby zadeklarować wskaźnik ciągu, kompilator tworzy poprawną **`const`** deklarację typu wskaźnika. Próba zmodyfikowania zawartości **`const`** wskaźnika jest raportowana przez kompilator jako błąd.

> [!NOTE]
> Standardowa biblioteka języka C++ w Visual Studio 2013 nie obsługuje **`/Zc:strictStrings`** opcji kompilatora w kompilacjach debugowania. Jeśli widzisz kilka błędów [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) w danych wyjściowych kompilacji, może to być przyczyną problemu.

Aby uzyskać więcej informacji na temat problemów ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **`/Zc:strictStrings`** , a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[`/Zc`Zgodności](zc-conformance.md)<br/>
