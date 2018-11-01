---
title: Błąd kompilatora C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: 25798e793bec7d09ea1f307ec1e2d9a63b9dbe27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428109"
---
# <a name="compiler-error-c2978"></a>Błąd kompilatora C2978

Błąd składniowy: oczekiwano "keyword1" lub 'keyword2'; znaleziono typ 'keyword3'; Parametry bez typu nie są obsługiwane w typach ogólnych

Klasa generyczna zadeklarowano niepoprawnie. Zobacz [ogólne](../../windows/generics-cpp-component-extensions.md)Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2978.

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