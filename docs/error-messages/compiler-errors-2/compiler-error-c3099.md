---
title: Błąd kompilatora C3099 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3099
dev_langs:
- C++
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea57a79fab92152824b7c9aaf0c5d50c14fee32e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211998"
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