---
title: 'Porady: uzyskiwanie wskaźnika do tablicy typu Byte'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, to Byte array
- Byte arrays
ms.assetid: aea18073-3341-47f4-9f0e-04e03327037e
ms.openlocfilehash: ad17dd0049f83fd753af0f9d7a565f28c6681a59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638905"
---
# <a name="how-to-obtain-a-pointer-to-byte-array"></a>Porady: uzyskiwanie wskaźnika do tablicy typu Byte

Możesz uzyskać wskaźnik do bloku tablicy w <xref:System.Byte> tablicy przez pobranie adresu pierwszego elementu i przypisywanie jej do wskaźnika.

## <a name="example"></a>Przykład

```
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

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)