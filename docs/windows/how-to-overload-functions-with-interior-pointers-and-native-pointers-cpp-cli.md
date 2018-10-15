---
title: 'Instrukcje: funkcje przeładowania z wewnętrznymi i Natywnymi wskaźnikami (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02f8d15c69bfef361d8ce34d9d6a1748692ea345
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327833"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>Poradnik: Funkcje przeładowania z wewnętrznymi i natywnymi wskaźnikami (C++/CLI)

Funkcje mogą być przeciążone w zależności od tego, czy typ parametru wskaźnika wewnętrznego lub wskaźnik natywny.

> [!IMPORTANT]
> Tej funkcji języka jest obsługiwana przez `/clr` — opcja kompilatora, ale nie za `/ZW` — opcja kompilatora.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```cpp
// interior_ptr_overload.cpp
// compile with: /clr
using namespace System;

// C++ class
struct S {
   int i;
};

// managed class
ref struct G {
   int i;
};

// can update unmanaged storage
void f( int* pi ) {
   *pi = 10;
   Console::WriteLine("in f( int* pi )");
}

// can update managed storage
void f( interior_ptr<int> pi ) {
   *pi = 10;
   Console::WriteLine("in f( interior_ptr<int> pi )");
}

int main() {
   S *pS = new S;   // C++ heap
   G ^pG = gcnew G;   // common language runtime heap
   f( &pS->i );
   f( &pG->i );
};
```

```Output 
in f( int* pi )  
in f( interior_ptr<int> pi )  
```

## <a name="see-also"></a>Zobacz też

[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)