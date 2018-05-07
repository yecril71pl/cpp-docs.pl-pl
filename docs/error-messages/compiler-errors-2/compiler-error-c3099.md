---
title: C3099 błąd kompilatora | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 27059beb1cb587b9060da8c5cc5702ea966422f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3099"></a>C3099 błąd kompilatora
"— słowo kluczowe": Użyj [System::AttributeUsageAttribute] dla atrybutów zarządzanych; na użytek [Windows::Foundation::Metadata::AttributeUsageAttribute] atrybuty WinRT  
  
 Użyj <xref:System.AttributeUsageAttribute> Aby zadeklarować **/CLR** atrybutów. Użyj `Windows::Foundation::Metadata::AttributeUsageAttribute` Aby zadeklarować atrybutów środowiska wykonawczego systemu Windows.  
  
 Aby uzyskać więcej informacji o atrybutach/CLR, zobacz [zdefiniowane przez użytkownika atrybuty](../../windows/user-defined-attributes-cpp-component-extensions.md). Dla atrybutów obsługiwane w środowisku wykonawczym systemu Windows, temacie [Windows.Foundation.Metadata przestrzeni nazw](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
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