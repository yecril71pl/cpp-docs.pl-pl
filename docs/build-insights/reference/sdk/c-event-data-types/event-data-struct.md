---
title: Struktura EVENT_DATA
description: C++ Build Insights SDK EVENT_DATA odwołania do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ce396febe278c5e7c34fe170939c9522913f92a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325598"
---
# <a name="event_data-structure"></a>Struktura EVENT_DATA

::: moniker range="<=vs-2015"

C++ Kompilacja insights SDK jest zgodny z visual studio 2017 i powyżej. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolka **selektora wersji** programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `EVENT_DATA` opisuje zdarzenie odebrane z analizy lub sesji ponownego rejestrowania. Sesje te są uruchamiane przez [wywołanie](../functions/analyze.md)funkcji Analyze , [AnalyzeA](../functions/analyze-a.md), [AnalyzeW](../functions/analyze-w.md), [Relog](../functions/relog.md), [RelogA](../functions/relog-a.md)lub [RelogW.](../functions/relog-w.md)

## <a name="syntax"></a>Składnia

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>Elementy członkowskie

|  |  |
|--|--|
| `EventId` | Liczba identyfikująca zdarzenie. Aby uzyskać listę identyfikatorów zdarzeń, zobacz [EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Liczba, która jednoznacznie identyfikuje bieżące zdarzenie wewnątrz śledzenia. Ta wartość nie zmienia się podczas analizowania lub ponownego rejestrowania tego samego śledzenia wiele razy. To pole służy do identyfikowania tego samego zdarzenia w wielu analizach lub przeksięgowania przebiegów przez ten sam ślad. |
| `TickFrequency` | Liczba znaczników na sekundę do użycia podczas oceny czasu trwania mierzonego w kleszczach. |
| `StartTimestamp` | Gdy zdarzenie jest *działanie,* to pole jest ustawione na wartość znacznika przechwycone w momencie rozpoczęcia działania. Jeśli to zdarzenie jest *zdarzeniem prostym,* to pole jest ustawione na wartość znacznika przechwyconą w momencie wystąpienia zdarzenia. |
| `StopTimestamp` | Gdy zdarzenie jest *działanie,* to pole jest ustawione na wartość znacznika przechwycone w momencie zatrzymania działania. Jeśli zdarzenie zatrzymania nie zostało jeszcze odebrane dla tego działania, to pole jest ustawione na zero. Jeśli to zdarzenie jest *zdarzeniem prostym,* to pole jest ustawione na zero. |
| `ExclusiveDurationTicks` | Jeśli to zdarzenie jest *działanie,* to pole jest ustawione na liczbę znaczników, które wystąpiły bezpośrednio w tym działaniu. Liczba znaczników, które wystąpiły w aktywności podrzędnej są wykluczone. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `CPUTicks` | Jeśli to zdarzenie jest *działanie,* to pole jest ustawione na liczbę znaczników procesora CPU, które wystąpiły podczas tego działania. Znacznik procesora różni się od zwykłego kleszcza. Znaczniki procesora CPU są liczone tylko wtedy, gdy procesor jest wykonywany kod w działaniu. Znaczniki procesora CPU nie są liczone, gdy wątek skojarzony z aktywnością jest uśpiony. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `ExclusiveCPUTicks` | To pole ma takie `CPUTicks`samo znaczenie jak , z tą różnicą, że nie obejmuje znaczników procesora CPU, które wystąpiły w działaniach dla dzieci. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `WallClockTimeResponsibilityTicks` | Jeśli to zdarzenie jest *działanie,* to pole jest ustawione na liczbę znaczników, która reprezentuje wkład tego działania w ogólny czas zegara ściennego. Odpowiedzialność za czas zegara ściennego różni się od zwykłego kleszcza. Odpowiedzialność zegara ściennego uwzględnia równoległość między działaniami. Na przykład dwa równoległe działania mogą mieć czas trwania 50 znaczników i ten sam czas rozpoczęcia i zatrzymania. W takim przypadku oba zostaną przypisane do odpowiedzialności zegara ściennego 25 kleszczy. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `ExclusiveWallClockTimeResponsibilityTicks` | To pole ma takie `WallClockTimeResponsibilityTicks`samo znaczenie jak , z tą różnicą, że nie zawiera znaczników odpowiedzialności za czas ścienny zajęć dla dzieci. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `Data` | Wskazuje na dodatkowe dane przechowywane w zdarzeniu. Typ wskazanych danych różni się w `EventId` zależności od pola. |
| `ProcessId` | Identyfikator procesu, w którym wystąpiło zdarzenie. |
| `ThreadId` | Identyfikator wątku, w którym wystąpiło zdarzenie. |
| `ProcessorIndex` | Numer procesora CPU z zerowym indeksem, na którym wystąpiło zdarzenie. |
| `EventName` | Ciąg ANSI zawierający nazwę jednostki identyfikowanej przez `EventId`. |
| `EventWideName` | Szeroki ciąg zawierający nazwę jednostki identyfikowanej przez `EventId`. |

## <a name="remarks"></a>Uwagi

Wiele pól `EVENT_DATA` zawiera liczbę znaczników. Usługa Buduj w usłudze C++ używa licznika wydajności window jako źródła znaczników. Aby przekształcić je w `TickFrequency` odpowiednią jednostkę czasu, taką jak sekundy, należy użyć liczby znaczników. Zobacz poniższy przykład, aby wykonać tę konwersję. `EVENT_DATA`nie zawiera pola dla zwykłej liczby znaczników działania. Aby uzyskać tę wartość, `StartTimestamp` `StopTimestamp`odejmij od . `EVENT_DATA`jest strukturą, która ma być używana przez użytkowników interfejsu API języka C. W przypadku użytkowników interfejsu API języka C++ klasy takie jak konwersje czasowe [eventowe](../cpp-event-data-types/event.md) automatycznie.

Wartość `EVENT_DATA` `Data` pola zależy od wartości jego `EventId` pola. Wartość jest `Data` opisana w poniższej tabeli. W poniższej tabeli mogą brakować niektórych identyfikatorów jednostek. W takim przypadku `Data` pole jest `nullptr` ustawione na lub zero.

| `EventId`Wartość | Typ wskazywowy przez`Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>Przykład konwersji zaznaczenia

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
