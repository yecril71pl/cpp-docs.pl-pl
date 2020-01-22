---
title: /Zc:referenceBinding (Wymuszanie zasad powiązania odwołań)
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: b7e297d6fd913ddda4d44a42298a361e314af0b5
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518481"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (Wymuszanie zasad powiązania odwołań)

Gdy określona jest opcja **/Zc: referencebinding** , kompilator nie zezwala na odwołanie niestałe lvalue, które ma być powiązane z elementem tymczasowym.

## <a name="syntax"></a>Składnia

> **/Zc:referenceBinding**[ **-** ]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc: referencebinding** jest określony, kompilator postępuje zgodnie z sekcją 8.5.3 standardu c++ 11: nie zezwala na wyrażenia, które powiążą typ tymczasowy zdefiniowany przez użytkownika z niestałym odwołaniem lvalue. Domyślnie, lub jeśli **/Zc: referencebinding-** jest określony, kompilator zezwala na takie wyrażenia jako rozszerzenie Microsoft, ale wydawane jest ostrzeżenie poziomu 4. W celu zapewnienia bezpieczeństwa kodu, przenośności i zgodności zalecamy użycie **/Zc: referencebinding**.

Opcja **/Zc: referencebinding** jest domyślnie wyłączona. Opcja kompilatora [/permissive-](permissive-standards-conformance.md) niejawnie ustawia tę opcję, ale można ją zastąpić za pomocą **/Zc: referencebinding-** .

## <a name="example"></a>Przykład

Ten przykład pokazuje rozszerzenie firmy Microsoft, które umożliwia określenie tymczasowego typu zdefiniowanego przez użytkownika do powiązania z niestałym odwołaniem lvalue.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

int main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością C++w wizualizacji, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > strony właściwości **wiersza polecenia** **C++ C/**  > .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Zc: referencebinding** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Zgodność)](zc-conformance.md)<br/>
