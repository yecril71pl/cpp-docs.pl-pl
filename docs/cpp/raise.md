---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: c5703c87945667f4ac65647019a72b304363bee2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244507"
---
# <a name="raise"></a>__raise

Kładzie nacisk witryny wywołania zdarzenia.

## <a name="syntax"></a>Składnia

```
__raise method-declarator;
```

## <a name="remarks"></a>Uwagi

Z poziomu kodu zarządzanego zdarzenie można tylko będzie zgłaszany z w obrębie klasy, w którym jest zdefiniowana. Zobacz [zdarzeń](../extensions/event-cpp-component-extensions.md) Aby uzyskać więcej informacji.

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
[Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md)