---
title: 'Porady: deklarowanie unieruchamiania wskaźników i typów wartości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88c7b9d0b9ed8a39bae09e2ec1691de90549fc11
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607152"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Porady: deklarowanie unieruchamiania wskaźników i typów wartości

Typ wartości może być zapakowany niejawnie. Następnie można zadeklarować przypinania wskaźnik do obiektu typu wartościowego sam i użycia **pin_ptr** typem wartości spakowanej.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>Zobacz też

[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)