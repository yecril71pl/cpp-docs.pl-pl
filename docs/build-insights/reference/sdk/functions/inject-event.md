---
title: Wtryskwent
description: Odwołanie do funkcji SDK InjectEvent w języku C++ Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c82aad5923eff60e5c72ceccaa39aa136f942665
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324036"
---
# <a name="injectevent"></a>Wtryskwent

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Funkcja `InjectEvent` jest wywoływana w relogger implementujących interfejs [IRelogger.](../other-types/irelogger-class.md) Służy do zapisywania zdarzeń śledzenia zdarzeń dla systemu Windows (ETW) w pliku śledzenia wyjściowego sesji ponownego rejestrowania.

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

*relogSesja*\
Wskaźnik do sesji ponownego rejestrowania. Sesja ponownego rejestrowania jest dostarczana do `IRelogger` reloggerów, które implementują interfejs. Aby uzyskać więcej informacji, zobacz [IRelogger](../other-types/irelogger-class.md).

*providerId*\
Identyfikator GUID dostawcy śledzenia zdarzeń dla systemu Windows (ETW), w ramach którego zdarzenie ETW zostanie ponownie zarejestrowane.

*Eventdescriptor*\
Deskryptor zdarzenia ETW dla zdarzenia ETW, które zostało ponownie zarejestrowane.

*Processid*\
Identyfikator procesu (PID) dla zdarzenia ETW, które jest ponownie rejestrowane.

*Threadid*\
Identyfikator wątku (TID) dla zdarzenia ETW, który jest ponownie zarejestrowany.

*procesorIndex*\
Indeks procesora dla zdarzenia ETW, które jest ponownie rejestrowane.

*Sygnatury czasowej*\
Sygnatura czasowa zdarzenia ETW, które jest ponownie rejestrowane.

*Danych*\
Wskaźnik do danych, które powinny być uwzględnione w relogged zdarzenie ETW.

*Bytecount*\
Rozmiar danych w bajtach, wskazywu przez *dane*.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat koncepcji ETW, takich jak *identyfikator GUID dostawcy* i *deskryptor zdarzeń,* zobacz [dokumentację ETW](/windows/win32/etw/about-event-tracing). Aby uzyskać szczegółowe informacje na temat uruchamiania sesji ponownego rejestrowania za pomocą sdk języka C++ Build Insights, zobacz [Relog](relog.md).

::: moniker-end
