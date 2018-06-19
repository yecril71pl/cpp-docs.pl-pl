---
title: C2978 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2978
dev_langs:
- C++
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cabf938343b375fdd27647711bb3e5b1d1f16d39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245002"
---
# <a name="compiler-error-c2978"></a>C2978 błąd kompilatora
Błąd składniowy: oczekiwano "keyword1" lub 'keyword2'; znaleziono typ 'keyword3'; Parametry bez typu nie są obsługiwane w typach ogólnych  
  
 Nieprawidłowo zadeklarowano klasy ogólnej. Zobacz [ogólne](../../windows/generics-cpp-component-extensions.md)Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2978.  
  
```  
// C2978.cpp  
// compile with: /clr /c  
generic <ref class T>   // C2978  
// try the following line instead  
// generic <typename T>   // OK  
ref class Utils {  
   static void sort(T elems, size_t size);  
};  
  
generic <int>  
// try the following line instead  
// generic <class T>  
ref class Utils2 {  
   static void sort(T elems, size_t size);  
};  
```