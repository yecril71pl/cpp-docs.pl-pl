---
title: Kompilator ostrzeżenie (poziom 1) C4692 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4692
dev_langs:
- C++
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 691be92230341d0cbf83b361310de4aab60f6859
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117741"
---
# <a name="compiler-warning-level-1-c4692"></a>Kompilator ostrzeżenie (poziom 1) C4692

'funkcja': podpis z nieprywatnego elementu członkowskiego zawiera typ macierzysty 'native_type' zestawu prywatnego

Typ, który jest widoczna spoza zestawu, zawiera funkcję członkowską, którego podpis zawiera typ macierzysty, który nie jest widoczna spoza zestawu. W związku z tym funkcja elementu członkowskiego nie powinna być wywoływana, jeśli jej typ zawierający jest utworzone spoza zestawu.

Aby uzyskać więcej informacji, zobacz [typ widoczności](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4692.

```
// C4692.cpp
// compile with: /W1 /c /clr
#pragma warning(default:4692)
class Private_Native_Class {};
public class Public_Native_Class {};
public ref class Public_Ref_Class {
public:
   void Test(Private_Native_Class *) {}   // C4692
   void Test2(Public_Native_Class *) {}   // OK
};
```