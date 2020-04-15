---
title: Struktura RELOG_CALLBACKS
description: C++ Build Insights SDK RELOG_CALLBACKS odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 60e7db81a48731090a23b82332704a79a51e97df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328970"
---
# <a name="relog_callbacks-structure"></a>Struktura RELOG_CALLBACKS

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `RELOG_CALLBACKS` jest używana podczas inicjowania [obiektu RELOG_DESCRIPTOR.](relog-descriptor-struct.md) Określa, które funkcje do wywołania podczas ponownego rejestrowania śledzenia zdarzeń dla systemu Windows (ETW) śledzenia.

## <a name="syntax"></a>Składnia

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `OnStartActivity` | Wywoływana do przetwarzania zdarzenia rozpoczęcia działania. |
| `OnStopActivity` | Wywoływana do przetwarzania zdarzenia zatrzymania działania. |
| `OnSimpleEvent` | Wywoływana do przetwarzania prostego zdarzenia. |
| `OnTraceInfo` | Wywoływany raz na początku przepojenia pass, po `OnBeginReloggingPass` został wywołany. |
| `OnBeginRelogging` | Wywoływane podczas rozpoczynania sesji ponownego rejestrowania, przed rozpoczęciem przełęczy ponownego rejestrowania. |
| `OnEndRelogging` | Wywoływana po zakończeniu sesji ponownego rejestrowania, po zakończeniu przełęczy ponownego rejestrowania. |
| `OnBeginReloggingPass` | Wywoływane podczas rozpoczynania przepustu ponownego rejestrowania, przed przetworzeniem dowolnego zdarzenia. |
| `OnEndReloggingPass` | Wywoływane po zakończeniu przepustu ponownego rejestrowania, po przetworzeniu wszystkich zdarzeń. |

## <a name="remarks"></a>Uwagi

Wszystkie elementy `RELOG_CALLBACKS` członkowskie struktury muszą wskazywać prawidłową funkcję. Aby uzyskać więcej informacji na temat przyjętych podpisów funkcji, zobacz [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)i [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
