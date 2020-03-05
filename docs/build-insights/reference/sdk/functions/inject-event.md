---
title: InjectEvent
description: Odwołanie C++ do funkcji InjectEvent zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7b53eb71cf7a2ae40d04dbc3f8b5829f2737aba4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332846"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `InjectEvent` jest wywoływana w ramach ponownego rejestrowania implementującego interfejs [IRelogger](../other-types/irelogger-class.md) . Służy do zapisywania zdarzenia śledzenia zdarzeń systemu Windows (ETW) w wyjściowym pliku śledzenia sesji ponownego rejestrowania.

## <a name="syntax"></a>Składnia

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>Parametry

*relogSession*\
Wskaźnik do sesji rejestrowania. Sesja ponownego rejestrowania jest udostępniana w celu ponownego wyrejestratora implementującego interfejs `IRelogger`. Aby uzyskać więcej informacji, zobacz [IRelogger](../other-types/irelogger-class.md).

*identyfikatorem*\
Identyfikator GUID dostawcy śledzenia zdarzeń systemu Windows (ETW), w którym zdarzenie ETW zostanie zarejestrowane.

*eventDescriptor*\
Deskryptor zdarzenia ETW dla zdarzenia ETW, które jest rejestrowane.

\ identyfikatora *procesu*
Identyfikator procesu (PID) dla zdarzenia ETW, które jest rejestrowane ponownie.

*threadId*\
Identyfikator wątku (TID) dla zdarzenia ETW, które jest rejestrowane.

*processorIndex*\
Indeks procesora dla zdarzenia ETW, które jest rejestrowane ponownie.

\ *znacznika czasu*
Sygnatura czasowa zdarzenia ETW, które jest rejestrowane.

\ *danych*
Wskaźnik do danych, które powinny zostać uwzględnione w rejestrowanym zdarzeniu ETW.

*byteCount*\
Rozmiar danych (w bajtach) wskazywanych przez *dane*.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat pojęć ETW, takich jak *Identyfikator GUID dostawcy* i *deskryptor zdarzenia*, zapoznaj się z [dokumentacją ETW](/windows/win32/etw/about-event-tracing). Aby uzyskać szczegółowe informacje na temat rozpoczynania sesji ponownego rejestrowania za C++ pomocą zestawu SDK usługi Build Insights, zobacz [relog](relog.md).

::: moniker-end
