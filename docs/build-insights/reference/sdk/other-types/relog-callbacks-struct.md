---
title: Struktura RELOG_CALLBACKS
description: Zestaw C++ SDK usługi Build insights RELOG_CALLBACKS odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5dbed196e6cafaa301b6e07cd0f5546a0f4d563
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332342"
---
# <a name="relog_callbacks-structure"></a>Struktura RELOG_CALLBACKS

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `RELOG_CALLBACKS` jest używana podczas inicjowania obiektu [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Określa funkcje, które mają być wywoływane podczas rejestrowania śledzenia zdarzeń systemu Windows (ETW).

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
| `OnStartActivity` | Wywołuje się, by przetworzyć zdarzenie uruchomienia działania. |
| `OnStopActivity` | Wywołuje się, by przetworzyć zdarzenie zatrzymania działania. |
| `OnSimpleEvent` | Wywołuje się, by przetworzyć zdarzenie proste. |
| `OnTraceInfo` | Wywoływana raz na początku przebiegu rejestrowania, po wywołaniu `OnBeginReloggingPass`. |
| `OnBeginRelogging` | Wywołuje się, gdy rozpocznie się sesja ponowna rejestracja przed rozpoczęciem przebiegu rejestrowania. |
| `OnEndRelogging` | Wywołuje się, gdy kończy się sesja po zakończeniu rejestracji, po zakończeniu przebiegu rejestrowania. |
| `OnBeginReloggingPass` | Wywołuje się, gdy rozpoczyna się ponowny rejestrowanie przed przetwarzaniem dowolnego zdarzenia. |
| `OnEndReloggingPass` | Wywołuje się, gdy kończy się rejestrowanie przebiegu, po przetworzeniu wszystkich zdarzeń. |

## <a name="remarks"></a>Uwagi

Wszystkie elementy członkowskie struktury `RELOG_CALLBACKS` muszą wskazywać na prawidłową funkcję. Aby uzyskać więcej informacji na temat zaakceptowanych podpisów funkcji, zobacz [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)i [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
