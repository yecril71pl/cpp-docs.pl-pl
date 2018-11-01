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
ms.openlocfilehash: d0fe7a7aa956ebc7662754b039389983d75ff590
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668718"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (Wyłączanie konwersji typów literału ciągu)

Jeśli zostanie określony, kompilator wymaga ścisłej `const`-zgodności dla wskaźników, zainicjowanej za pomocą literałów ciągów znaków.

## <a name="syntax"></a>Składnia

> **/Zc:strictStrings**[**-**]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc: strictstrings** jest określony, kompilator wymusza standardowe C++ `const` wymagania kwalifikacyjne literałów ciągów jako typ "tablica `const char`" lub "tablica `const wchar_t`", w zależności od deklaracji. Literały ciągów są niezmienne i próba zmodyfikowania zawartości jednego powoduje błąd naruszenia zasad dostępu w czasie wykonywania. Musisz zadeklarować wskaźnik ciągu jako `const` go zainicjować za pomocą literału ciągu lub użyć jawnego `const_cast` zainicjować innej niż`const` wskaźnika. Domyślnie lub jeśli **/Zc:strictStrings-** jest określony, kompilator nie Wymuszaj standard C++ `const` kwalifikacje dla wskaźników ciągu zainicjowanych za pomocą literałów ciągów znaków.

**/Zc: strictstrings** opcja jest domyślnie wyłączona. [/ Permissive-](permissive-standards-conformance.md) — opcja kompilatora niejawnie ustawia tę opcję, ale może być zastąpiona przy użyciu **/Zc:strictStrings-**.

Użyj **/Zc: strictstrings** opcję, aby uniemożliwić kompilacji niepoprawnego kodu. Ten przykład pokazuje, jak prosty błąd w deklaracji prowadzi do awarii w czasie wykonywania:

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

Gdy **/Zc: strictstrings** jest włączone, ten sam kod zgłasza błąd w deklaracji `str`.

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

Jeśli używasz `auto` Aby zadeklarować wskaźnik ciągu, kompilator tworzy poprawną `const` deklarację typu wskaźnika dla Ciebie. Podjęto próbę zmodyfikowania zawartości `const` wskaźnik jest zgłaszana przez kompilator jako błąd.

> [!NOTE]
> Standardowa biblioteka C++ w programie Visual Studio 2013 nie obsługuje **/Zc: strictstrings** kompilacji — opcja kompilatora podczas debugowania. Jeśli widzisz kilka [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) dane wyjściowe błędów w kompilacji, może to być przyczyną.

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: strictstrings** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
