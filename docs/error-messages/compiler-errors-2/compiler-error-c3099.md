---
title: Błąd kompilatora C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: e9a76fa2e0dc5602a88324cfd2fef85457ad7e99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512115"
---
# <a name="compiler-error-c3099"></a>Błąd kompilatora C3099

"— słowo kluczowe": Użyj [System::AttributeUsageAttribute] dla atrybutów zarządzanych; na użytek [Windows::Foundation::Metadata::AttributeUsageAttribute] atrybuty WinRT

Użyj <xref:System.AttributeUsageAttribute> do deklarowania **/CLR** atrybutów. Użyj `Windows::Foundation::Metadata::AttributeUsageAttribute` można zadeklarować atrybutów środowiska wykonawczego Windows.

Aby uzyskać więcej informacji na temat atrybutów/CLR, zobacz [atrybuty zdefiniowane przez użytkownika](../../windows/user-defined-attributes-cpp-component-extensions.md). W przypadku obsługiwanych atrybutów środowiska wykonawczego Windows, zobacz [Windows.Foundation.Metadata przestrzeni nazw](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)

## <a name="example"></a>Przykład

Poniższy przykład generuje C3099 i pokazuje, jak go naprawić.

```
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```