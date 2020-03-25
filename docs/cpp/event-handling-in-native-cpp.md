---
title: Obsługa zdarzeń w natywnym kodzie C++
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: cc9265cd3f9f400e2880405019e4d2c9a934f10a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180085"
---
# <a name="event-handling-in-native-c"></a>Obsługa zdarzeń w natywnym kodzie C++

W przypadku C++ obsługi zdarzeń natywnych należy skonfigurować źródło zdarzeń i odbiorcę zdarzeń przy użyciu odpowiednio atrybutów [event_source](../windows/attributes/event-source.md) i [event_receiver](../windows/attributes/event-receiver.md) , określając `type`=`native`. Te atrybuty umożliwiają klasom, do których są stosowane, do wyzwalania zdarzeń i obsługi zdarzeń w natywnym kontekście, innym niż COM.

## <a name="declaring-events"></a>Deklarowanie zdarzeń

W klasie źródła zdarzeń, użyj słowa kluczowego [__event](../cpp/event.md) w deklaracji metody, aby zadeklarować metodę jako zdarzenie. Pamiętaj, aby zadeklarować metodę, ale nie należy jej definiować; w tym celu wygeneruje błąd kompilatora, ponieważ kompilator definiuje metodę niejawnie, gdy jest ona wykonywana w zdarzeniu. Zdarzenia natywne mogą być metodami z zero lub więcej parametrami. Zwracany typ może być typu void lub dowolnego całkowitego.

## <a name="defining-event-handlers"></a>Definiowanie programów obsługi zdarzeń

W klasie odbiornika zdarzeń należy zdefiniować programy obsługi zdarzeń, które są metodami z podpisami (typy zwracane, konwencje wywoływania i argumenty), które odpowiadają obsługiwanemu zdarzeniu.

## <a name="hooking-event-handlers-to-events"></a>Podłączanie programów obsługi zdarzeń do zdarzeń

Ponadto w klasie odbiorcy zdarzeń można używać funkcji wewnętrznej [__hook](../cpp/hook.md) do kojarzenia zdarzeń z programami obsługi zdarzeń i [__unhook](../cpp/unhook.md) do usuwania skojarzeń zdarzeń z programów obsługi zdarzeń. Można podłączyć kilka zdarzeń do programu obsługi zdarzeń lub kilka programów obsługi zdarzeń do zdarzenia.

## <a name="firing-events"></a>Wyzwalanie zdarzeń

Aby wywołać zdarzenie, po prostu wywołaj metodę zadeklarowaną jako zdarzenie w klasie Źródło zdarzenia. Jeśli programy obsługi zostały podłączone do zdarzenia, zostaną wywołane programy obsługi.

### <a name="native-c-event-code"></a>Kod C++ zdarzenia natywnego

Poniższy przykład pokazuje, jak uruchomić zdarzenie w trybie macierzystym C++. Aby skompilować i uruchomić przykład, zobacz komentarze w kodzie.

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

## <a name="see-also"></a>Zobacz też

[Obsługa zdarzeń](../cpp/event-handling.md)
