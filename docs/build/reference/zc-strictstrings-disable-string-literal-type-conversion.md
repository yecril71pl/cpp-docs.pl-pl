---
title: '/ Zc: strictstrings (Wyłączanie konwersji typów literału ciągu) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:strictStrings
- strictStrings
dev_langs:
- C++
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7025a4bae2d4a7474cb366b041a3c62f3d7db819
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379942"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (Wyłączanie konwersji typów literału ciągu)

W przypadku kompilator wymaga strict `const`— zgodność kwalifikacji dla wskaźników zainicjowany przy użyciu literałów ciągów.

## <a name="syntax"></a>Składnia

> **/Zc:strictStrings**[**-**]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc: strictstrings** określono kompilator wymusza standardu C++ `const` kwalifikacji literałów ciągów jako typ "tablicę `const char`" lub "tablicę `const wchar_t`", w zależności od deklaracji. Literały ciągu są niezmienne i zmodyfikować zawartość jednej powoduje błąd naruszenia zasad dostępu w czasie wykonywania. Należy zadeklarować wskaźnika ciągu jako `const` Zainicjuj go za pomocą literału ciągu lub użyj jawnej `const_cast` zainicjować niż`const` wskaźnika. Domyślnie lub jeśli **/Zc:strictStrings-** określono kompilator nie Wymuszaj standard C++ `const` kwalifikacje dla wskaźników ciąg zainicjowany przy użyciu literałów ciągów.

**/Zc: strictstrings** opcja jest domyślnie wyłączona. [/ Ograniczająca-](permissive-standards-conformance.md) — opcja kompilatora niejawnie ustawia tę opcję, ale może być zastąpiona przy użyciu **/Zc:strictStrings-**.

Użyj **/Zc: strictstrings** opcję, aby uniemożliwić kompilacji niepoprawny kod. Ten przykład przedstawia, jak błąd proste deklaracji prowadzi do awarii w czasie wykonywania:

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

Jeśli używasz `auto` zadeklarować wskaźnika ciągu, kompilator tworzy poprawny `const` deklaracji typu wskaźnik dla Ciebie. Podjęto próbę zmodyfikowania zawartości `const` wskaźnik został zgłoszony przez kompilatora jako błąd.

> [!NOTE]
> Standardowa biblioteka C++ w [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] nie obsługuje **/Zc: strictstrings** kompilacje — opcja kompilatora podczas debugowania. Jeśli widzisz kilka [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) output błędy w kompilacji, może to być przyczyną.

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc: strictstrings** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
