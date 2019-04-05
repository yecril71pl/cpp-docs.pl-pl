---
title: Błąd kompilatora C3831
ms.date: 11/04/2016
f1_keywords:
- C3831
helpviewer_keywords:
- C3831
ms.assetid: a125d8dc-b75a-4ea0-b6c7-fe7b119dba25
ms.openlocfilehash: d9aa703f12fd175d9f7fc00eb76e76097a32e860
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781669"
---
# <a name="compiler-error-c3831"></a>Błąd kompilatora C3831

"członek": "class" nie może mieć przypiętej składowej danych lub funkcji składowej zwracającej przypięty wskaźnik

[pin_ptr (C + +/ CLI)](../../extensions/pin-ptr-cpp-cli.md) zostało niepoprawnie użyte.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3831:

```
// C3831a.cpp
// compile with: /clr
ref class Y
{
public:
   int i;
};

ref class X
{
   pin_ptr<int> mbr_Y;   // C3831
   int^ mbr_Y2;   // OK
};

int main() {
   Y y;
   pin_ptr<int> p = &y.i;
}
```
