---
title: /Zc:rvalueCast (Wymuszanie zasad konwersji typów)
ms.date: 03/06/2018
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
ms.openlocfilehash: e5a6abd3b85136b05ae58ebc8750aa9120cabc33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315784"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Wymuszanie zasad konwersji typów)

Gdy **/Zc: rvaluecast** opcja zostanie określona, kompilator poprawnie identyfikuje typ odwołania rvalue jako wynik operacji rzutowania zgodnie ze standardem C ++ 11. Jeśli nie określono opcji, zachowanie kompilatora jest taka sama, jak w programie Visual Studio 2012.

## <a name="syntax"></a>Składnia

> **/Zc:rvalueCast**[**-**]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc: rvaluecast** jest określony, kompilator postępuje ppkt 5.4 standardem C ++ 11 i traktuje tylko rzutowane wyrażenia, które powodują typy niebędące odwołaniami i rzutowane wyrażenia, które skutkują odwołaniami rvalue do typów niebędących funkcjami jako typy rvalue. Domyślnie lub jeśli **/Zc:rvalueCast-** jest określony, kompilator nie jest zgodny i traktuje wszystkie wyrażenia cast, które skutkują odwołaniami rvalue jako rvalue. Dla zgodności i wyeliminowania błędów w stosowaniu rzutowań zaleca się używanie **/Zc: rvaluecast**.

Domyślnie **/Zc: rvaluecast** jest wyłączona (**/Zc:rvalueCast-**). [/ Permissive-](permissive-standards-conformance.md) — opcja kompilatora niejawnie ustawia tę opcję, ale może być zastąpiona przy użyciu **/Zc:rvalueCast-**.

Użyj **/Zc: rvaluecast** w przypadku przekazywania wyrażenia rzutowania jako argumentu do funkcji, która przyjmuje typ odwołania rvalue. Domyślne zachowanie powoduje błąd kompilatora [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) Kiedy kompilator niepoprawnie określa typ wyrażenia rzutującego. Ten przykład pokazuje błąd kompilatora poprawne kodu, gdy **/Zc: rvaluecast** nie zostanie określony:

```cpp
// Test of /Zc:rvalueCast
// compile by using:
// cl /c /Zc:rvalueCast- make_thing.cpp
// cl /c /Zc:rvalueCast make_thing.cpp

#include <utility>

template <typename T>
struct Thing {
   // Construct a Thing by using two rvalue reference parameters
   Thing(T&& t1, T&& t2)
      : thing1(t1), thing2(t2) {}

   T& thing1;
   T& thing2;
};

// Create a Thing, using move semantics if possible
template <typename T>
Thing<T> make_thing(T&& t1, T&& t2)
{
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));
}

struct Test1 {
   long a;
   long b;

   Thing<long> test() {
      // Use identity casts to create rvalues as arguments
      return make_thing(static_cast<long>(a), static_cast<long>(b));
   }
};
```

Domyślne zachowanie kompilatora może nie zgłaszać błędu C2102, gdy jest to konieczne. W tym przykładzie, kompilator nie zgłasza błędu, jeśli adres rvalue utworzony przez rzutowanie tożsamości zostanie podjęta, gdy **/Zc: rvaluecast** nie zostanie określony:

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: rvaluecast** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
