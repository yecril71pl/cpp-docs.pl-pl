---
title: '/ Zc: referencebinding (wymuszanie zasad powiązania odwołań)'
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
ms.openlocfilehash: baf2106f015a4e8557cb8469d300709694e06d84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428330"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/ Zc: referencebinding (wymuszanie zasad powiązania odwołań)

Gdy **/Zc: referencebinding** opcja zostanie określona, kompilator nie zezwala na odwołanie niestałe l-wartości do powiązania do tymczasowej.

## <a name="syntax"></a>Składnia

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc: referencebinding** jest określony, kompilator poniżej sekcji 8.5.3 standardem C ++ 11 i nie zezwala na wyrażeniach, które powiązanie typu zdefiniowanych przez użytkownika tymczasowe odwołanie niestałe l-wartości. Domyślnie lub jeśli **/Zc:referenceBinding-** jest określony, kompilator umożliwi takie wyrażenia jako rozszerzeń firmy Microsoft, ale jest wyświetlane ostrzeżenie poziom 4. Zabezpieczenia kodu, przenoszenia i zgodności zaleca się użycie **/Zc: referencebinding**.

**/Zc: referencebinding** opcja jest domyślnie wyłączona. [/ Permissive-](permissive-standards-conformance.md) — opcja kompilatora niejawnie ustawia tę opcję, ale może być zastąpiona przy użyciu **/Zc:referenceBinding-**.

## <a name="example"></a>Przykład

Niniejszy przykład pokazuje rozszerzenie Microsoft, które umożliwia to tymczasowy typ zdefiniowany przez użytkownika może być powiązane z odwołaniem lvalue wartości innej niż stała.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

void main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: referencebinding** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
