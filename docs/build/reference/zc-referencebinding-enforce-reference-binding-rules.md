---
title: /Zc:referenceBinding (wymuszanie zasad powiązanie odwołania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30038f6ff73eaa2d9536c3685927458a70209864
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378883"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (wymuszanie zasad powiązanie odwołanie)

Gdy **/Zc:referenceBinding** zostanie określona opcja, kompilator nie zezwala na odwołania do wartości innej niż stała powiązać do tymczasowej.

## <a name="syntax"></a>Składnia

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc:referenceBinding** jest określony, kompilator następuje sekcji 8.5.3 standardem C ++ 11 i nie zezwala na wyrażeń, które powiązanie tymczasowego zdefiniowane przez użytkownika typu odwołania do wartości innej niż stała. Domyślnie lub jeśli **/Zc:referenceBinding-** jest określony, kompilator umożliwia takich wyrażeń jako rozszerzenie firmy Microsoft, ale poziom 4 pojawi się ostrzeżenie. Kod zabezpieczeń, przenośność i zgodność, firma Microsoft zaleca się używanie **/Zc:referenceBinding**.

**/Zc:referenceBinding** opcja jest domyślnie wyłączona. [/ Ograniczająca-](permissive-standards-conformance.md) — opcja kompilatora niejawnie ustawia tę opcję, ale może być zastąpiona przy użyciu **/Zc:referenceBinding-**.

## <a name="example"></a>Przykład

W tym przykładzie pokazano rozszerzenia firmy Microsoft, które umożliwia tymczasowej typu zdefiniowane przez użytkownika może być powiązane z odwołania do wartości innej niż stała.

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

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc:referenceBinding** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
