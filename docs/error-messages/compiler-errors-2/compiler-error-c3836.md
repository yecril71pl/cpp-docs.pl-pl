---
title: Błąd kompilatora C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 33860273db07894a9a4d15ba6d578598a18819ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477548"
---
# <a name="compiler-error-c3836"></a>Błąd kompilatora C3836

Konstruktor statyczny nie może mieć listy inicjatorów składowej

Klasa zarządzana nie może mieć statyczny Konstruktor, który zawiera także listę inicjowania elementu członkowskiego. Klasa statyczna konstruktory są wywoływane przez środowisko uruchomieniowe języka wspólnego do klasy inicjowania i Inicjowanie elementów członkowskich danych statycznych.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3836:

```
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
