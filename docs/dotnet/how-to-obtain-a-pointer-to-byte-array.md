---
title: 'Porady: uzyskiwanie wskaźnika do tablicy typu Byte'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, to Byte array
- Byte arrays
ms.assetid: aea18073-3341-47f4-9f0e-04e03327037e
ms.openlocfilehash: 5c0fc61f2876c652be6f25bf1627822537892dc9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988418"
---
# <a name="how-to-obtain-a-pointer-to-byte-array"></a>Porady: uzyskiwanie wskaźnika do tablicy typu Byte

Możesz uzyskać wskaźnik do bloku Array w tablicy <xref:System.Byte>, pobierając adres pierwszego elementu i przypisując go do wskaźnika.

## <a name="example"></a>Przykład

```cpp
// pointer_to_Byte_array.cpp
// compile with: /clr
using namespace System;
int main() {
   Byte bArr[] = {1, 2, 3};
   Byte* pbArr = &bArr[0];

   array<Byte> ^ bArr2 = gcnew array<Byte>{1,2,3};
   interior_ptr<Byte> pbArr2 = &bArr2[0];
}
```

## <a name="see-also"></a>Zobacz także

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
