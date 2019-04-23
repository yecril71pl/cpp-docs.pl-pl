---
title: Compiler Error C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: e11d830c3d662ea424caadeb50df669700f8c78f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778478"
---
# <a name="compiler-error-c3908"></a>Compiler Error C3908

poziom dostępu mniej restrykcyjny niż "konstrukcji"

Metoda dostępu właściwości (get lub set) nie może mieć dostęp mniej restrykcyjny niż dostępu określone na samej właściwości.  Podobnie dla metod dostępu zdarzeń.

Aby uzyskać więcej informacji, zobacz [właściwość](../../extensions/property-cpp-component-extensions.md) i [zdarzeń](../../extensions/event-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3908:

```
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```