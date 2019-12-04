---
title: Błąd kompilatora C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 81f508c47c678d86f8f95303861b42f8a70daa57
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750055"
---
# <a name="compiler-error-c3099"></a>Błąd kompilatora C3099

"słowo kluczowe": Użyj [System:: AttributeUsageAttribute] dla atrybutów zarządzanych; Użyj [Windows:: Foundation:: Metadata:: AttributeUsageAttribute] dla atrybutów WinRT

Użyj <xref:System.AttributeUsageAttribute>, aby zadeklarować atrybuty **/CLR** . Użyj `Windows::Foundation::Metadata::AttributeUsageAttribute`, aby zadeklarować atrybuty środowisko wykonawcze systemu Windows.

Aby uzyskać więcej informacji na temat atrybutów/CLR, zobacz [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md). Aby uzyskać obsługiwane atrybuty w środowisko wykonawcze systemu Windows, zobacz [przestrzeń nazw Windows. Foundation. Metadata](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>Przykład

Poniższy przykład generuje C3099 i pokazuje, jak rozwiązać ten problem.

```cpp
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```
