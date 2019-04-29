---
title: Błąd kompilatora C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 6e956ccb021dc3bce4d107e4aa6e0bbe4356283b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364730"
---
# <a name="compiler-error-c2360"></a>Błąd kompilatora C2360

Inicjowanie 'Identyfikator' jest pomijana przy etykiecie "case"

Inicjowanie `identifier` może być pominięty w `switch` instrukcji. Nie można przeskoczyć poza deklaracją za pomocą inicjatora, chyba że deklaracja jest ujęty w bloku. (Chyba że zostanie ona zadeklarowana w bloku, zmienna znajduje się w zakresie aż do końca `switch` instrukcja.)

Poniższy przykład spowoduje wygenerowanie C2360:

```
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

Możliwe rozwiązanie:

```
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```