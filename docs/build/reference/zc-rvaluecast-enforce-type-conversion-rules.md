---
title: "/ Zc: rvaluecast (wymuszanie zasad konwersji typów) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9e2223176082a2252dd410af4012ace31c14267
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Wymuszanie zasad konwersji typów)

Gdy **/Zc: rvaluecast** zostanie określona opcja, kompilator prawidłowo identyfikuje typu odwołania wartościowanego prawostronnie jako wyniku operacji rzutowania zgodnie ze standardem C ++ 11. Jeśli nie określono opcji, zachowanie kompilatora jest taki sam jak Visual Studio 2012.

## <a name="syntax"></a>Składnia

> **/Zc:rvalueCast**[**-**]

## <a name="remarks"></a>Uwagi

Jeśli **/Zc: rvaluecast** jest określony, kompilator następuje sekcji 5.4 standardem C ++ 11 i traktuje tylko rzutowanie wyrażeń, które powoduje w typach odwołań z systemem innym niż i wyrażeń, które powodują powstanie odwołania do r-wartości dla typów innych niż funkcja rzutowania jako typów wartości. Domyślnie lub jeśli **/Zc:rvalueCast-** jest określona, kompilator jest zgodna z systemem innym niż i traktuje wszystkie wyrażenia rzutowania, które powodują powstanie odwołania do r-wartości jako rvalues. Dla zgodności i wyeliminować błędy w przypadku użycia rzutowania, firma Microsoft zaleca użycie **/Zc: rvaluecast**.

Domyślnie **/Zc: rvaluecast** jest wyłączone (**/Zc:rvalueCast-**). [/ Ograniczająca-](permissive-standards-conformance.md) — opcja kompilatora niejawnie ustawia tę opcję, ale może być zastąpiona przy użyciu **/Zc:rvalueCast-**.

Użyj **/Zc: rvaluecast** przekazania wyrażeniem rzutowania jako argument do funkcji, która ma typ referencyjny wartościowany prawostronnie. Błąd kompilatora powoduje zachowanie domyślne [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) gdy kompilator niepoprawnie określa typ wyrażenie cast. W tym przykładzie pokazano wystąpi błąd kompilatora poprawne kodu, gdy **/Zc: rvaluecast** nie określono:

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

Domyślne zachowanie kompilatora nie może zgłaszać błąd C2102, gdy jest to konieczne. W tym przykładzie kompilator nie zgłaszać błąd, gdy wykonywana jest adres r-wartości utworzone przez rzutowanie tożsamości, gdy **/Zc: rvaluecast** nie określono:

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue 
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc: rvaluecast** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
