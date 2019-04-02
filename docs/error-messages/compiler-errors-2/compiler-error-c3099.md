---
title: Compiler Error C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 0f3eac1c232ef159d220a347d6b6dc3aed2fdd9a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771490"
---
# <a name="compiler-error-c3099"></a>Compiler Error C3099

"— słowo kluczowe": Użyj [System::AttributeUsageAttribute] dla atrybutów zarządzanych; na użytek [Windows::Foundation::Metadata::AttributeUsageAttribute] atrybuty WinRT

Użyj <xref:System.AttributeUsageAttribute> do deklarowania **/CLR** atrybutów. Użyj `Windows::Foundation::Metadata::AttributeUsageAttribute` można zadeklarować atrybutów środowiska wykonawczego Windows.

Aby uzyskać więcej informacji na temat atrybutów/CLR, zobacz [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md). W przypadku obsługiwanych atrybutów środowiska wykonawczego Windows, zobacz [Windows.Foundation.Metadata przestrzeni nazw](/uwp/api/windows.foundation.metadata)

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