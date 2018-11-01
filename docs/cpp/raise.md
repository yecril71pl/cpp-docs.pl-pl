---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: 865524fe91b7d137e3a943973dcca6d833bd16df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471441"
---
# <a name="raise"></a>__raise

Kładzie nacisk witryny wywołania zdarzenia.

## <a name="syntax"></a>Składnia

```
__raise method-declarator;
```

## <a name="remarks"></a>Uwagi

Z poziomu kodu zarządzanego zdarzenie można tylko będzie zgłaszany z w obrębie klasy, w którym jest zdefiniowana. Zobacz [zdarzeń](../windows/event-cpp-component-extensions.md) Aby uzyskać więcej informacji.

Słowo kluczowe **__raise** powoduje, że błąd emitowane, jeśli wywołasz niepowiązane zdarzeń.

> [!NOTE]
>  Szablonem klasy lub struktury nie mogą zawierać zdarzenia.

## <a name="example"></a>Przykład

```cpp
// EventHandlingRef_raise.cpp
struct E {
   __event void func1();
   void func1(int) {}

   void func2() {}

   void b() {
      __raise func1();
      __raise func1(1);  // C3745: 'int Event::bar(int)':
                         // only an event can be 'raised'
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func1();
   __raise e.func1(1);  // C3745
   __raise e.func2();   // C3745
}
```

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Obsługa zdarzeń](../cpp/event-handling.md)<br/>
[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)