---
title: Obsługa zdarzeń w natywnym kodzie C++
ms.date: 11/04/2016
helpviewer_keywords:
- event handling [C++], Visual C++
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: 210eea760e80814041b4e97f50c4164ef98d75e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457554"
---
# <a name="event-handling-in-native-c"></a>Obsługa zdarzeń w natywnym kodzie C++

W obsłudze zdarzeń natywnego języka C++, można skonfigurować zdarzenia źródło i zdarzenie odbiornika zdarzenia za pomocą [event_source](../windows/event-source.md) i [event_receiver](../windows/event-receiver.md) , odpowiednio, atrybutów, określając `type` = `native`. Te atrybuty zezwalać na klasy, do których są stosowane klasom wywoływanie zdarzeń i obsługa zdarzeń w kontekście natywnego, innego niż COM.

## <a name="declaring-events"></a>Deklarowanie zdarzeń

W klasie źródła zdarzeń, użyj [__event](../cpp/event.md) — słowo kluczowe w deklaracji metody, aby zadeklarować metodę jako zdarzenie. Upewnij się zadeklarować metody, ale nie zostanie zdefiniowana. Aby to zrobić wygeneruje błąd kompilatora, ponieważ kompilator określa niejawnie metodę, gdy staje się do zdarzenia. Natywne zdarzenia mogą być metod z zero lub więcej parametrów. Zwracany typ może być typu void lub dowolnego całkowitego.

## <a name="defining-event-handlers"></a>Definiowanie programów obsługi zdarzeń

W klasie odbiornika zdarzeń należy zdefiniować programy obsługi zdarzeń, które są metodami z podpisami (typy zwracane, konwencje wywoływania i argumenty), które odpowiadają obsługiwanemu zdarzeniu.

## <a name="hooking-event-handlers-to-events"></a>Podłączanie programów obsługi zdarzeń do zdarzeń

Również w klasie odbiornika zdarzeń, możesz użyć Wewnętrzna funkcja [__hook](../cpp/hook.md) umożliwia kojarzenie zdarzeń z programami obsługi zdarzeń i [__unhook](../cpp/unhook.md) do zdarzenia z programu obsługi zdarzeń. Można podłączyć kilka zdarzeń do programu obsługi zdarzeń lub kilka programów obsługi zdarzeń do zdarzenia.

## <a name="firing-events"></a>Wyzwalanie zdarzeń

Aby wywołać zdarzenie, po prostu Wywołaj metodę zadeklarowany jako zdarzenie w przypadku klasy źródłowej. Jeśli programy obsługi zostały podłączone do zdarzenia, zostaną wywołane programy obsługi.

### <a name="native-c-event-code"></a>Kod natywny zdarzenia języka C++

Poniższy przykład pokazuje, jak wywołać zdarzenie w natywnym kodzie C++. Aby skompilować i uruchomić przykład, zobacz komentarze w kodzie.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```cpp
// evh_native.cpp
#include <stdio.h>

[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};

[event_receiver(native)]
class CReceiver {
public:
   void MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
   }

   void MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
   }

   void hookEvent(CSource* pSource) {
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void unhookEvent(CSource* pSource) {
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   CSource source;
   CReceiver receiver;

   receiver.hookEvent(&source);
   __raise source.MyEvent(123);
   receiver.unhookEvent(&source);
}
```

### <a name="output"></a>Dane wyjściowe

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>Zobacz także

[Obsługa zdarzeń](../cpp/event-handling.md)