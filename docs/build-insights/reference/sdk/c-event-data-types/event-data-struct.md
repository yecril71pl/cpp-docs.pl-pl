---
title: Struktura EVENT_DATA
description: Informacje o strukturze EVENT_DATA zestawu SDK usługi Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ccba320a8bb9279b874fae2484c71af913253148
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229925"
---
# <a name="event_data-structure"></a>Struktura EVENT_DATA

::: moniker range="<=vs-2015"

Zestaw SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_DATA`Struktura opisuje zdarzenie odebrane z analizy lub sesji rejestrowania. Te sesje są uruchamiane przez wywołanie funkcji [Analizuj](../functions/analyze.md), [Analizuj](../functions/analyze-a.md)i [AnalyzeW](../functions/analyze-w.md), [relog](../functions/relog.md), [RelogA](../functions/relog-a.md)lub [RelogW](../functions/relog-w.md) .

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
| `EventId` | Liczba, która identyfikuje zdarzenie. Aby uzyskać listę identyfikatorów zdarzeń, zobacz [EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Liczba, która jednoznacznie identyfikuje bieżące zdarzenie wewnątrz śladu. Ta wartość nie ulega zmianie podczas analizowania lub wielokrotnego rejestrowania tego samego śledzenia. To pole służy do identyfikowania tego samego zdarzenia w wielu analizach lub przerejestrowaniu przebiegów tego samego śledzenia. |
| `TickFrequency` | Liczba taktów na sekundę do użycia podczas oceniania czasu trwania mierzoną w taktach. |
| `StartTimestamp` | Gdy zdarzenie jest *działaniem*, to pole jest ustawione na wartość takt przechwyconą w momencie uruchomienia działania. Jeśli to zdarzenie jest *zdarzeniem prostym*, to pole jest ustawione na wartość taktu przechwyconą w momencie wystąpienia zdarzenia. |
| `StopTimestamp` | Gdy zdarzenie jest *działaniem*, to pole jest ustawione na wartość takt przechwyconą w momencie zatrzymania działania. Jeśli zdarzenie zatrzymania nie zostało jeszcze odebrane dla tego działania, to pole jest ustawione na wartość zero. Jeśli to zdarzenie jest *zdarzeniem prostym*, to pole jest ustawione na wartość zero. |
| `ExclusiveDurationTicks` | Jeśli to zdarzenie jest *działaniem*, to pole jest ustawione na liczbę taktów, które wystąpiły bezpośrednio w tym działaniu. Liczba znaczników, które wystąpiły w działaniu podrzędnym, jest wykluczona. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `CPUTicks` | Jeśli to zdarzenie jest *działaniem*, to pole jest ustawione na liczbę cykli procesora CPU, które wystąpiły w trakcie tego działania. Cykl procesora CPU różni się od zwykłego taktu. Takty procesora są zliczane tylko wtedy, gdy procesor wykonuje kod w działaniu. Takty procesora nie są zliczane, gdy wątek skojarzony z działaniem jest uśpiony. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `ExclusiveCPUTicks` | To pole ma takie samo znaczenie jak `CPUTicks` , z tą różnicą, że nie obejmuje taktów procesora, które wystąpiły w działaniach podrzędnych. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `WallClockTimeResponsibilityTicks` | Jeśli to zdarzenie jest *działaniem*, wartość tego pola jest równa liczbie cykli reprezentującej udział tego działania w ogólnym czasie zegara ściany. Cykl odpowiedzialności w czasie zegara ściany różni się od zwykłego taktu. Cykle odpowiedzialności za zegary ścienne są uwzględniane równolegle między działaniami. Na przykład dwie działania równoległe mogą mieć czas trwania 50 taktów i ten sam czas rozpoczęcia i zakończenia. W takim przypadku do obu tych elementów zostanie przypisany Czas zegarowy do 25 taktów. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `ExclusiveWallClockTimeResponsibilityTicks` | To pole ma takie samo znaczenie jak `WallClockTimeResponsibilityTicks` , z tą różnicą, że nie zawiera on znaczników odpowiedzialności za czas zegara ściennego działań podrzędnych. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `Data` | Wskazuje dodatkowe dane przechowywane w zdarzeniu. Typ danych wskazywanych przez jest inny, w zależności od `EventId` pola. |
| `ProcessId` | Identyfikator procesu, w którym wystąpiło zdarzenie. |
| `ThreadId` | Identyfikator wątku, w którym wystąpiło zdarzenie. |
| `ProcessorIndex` | Numer procesora CPU, na którym wystąpiło zdarzenie. |
| `EventName` | Ciąg ANSI zawierający nazwę jednostki identyfikowanej przez `EventId` . |
| `EventWideName` | Szeroki ciąg zawierający nazwę jednostki identyfikowanej przez `EventId` . |

## <a name="remarks"></a>Uwagi

Wiele pól w programie `EVENT_DATA` zawiera liczbę cykli. Informacje o kompilacji w języku C++ wykorzystują licznik wydajności okna jako źródło taktów. Liczba cykli musi być użyta z `TickFrequency` polem, aby przekonwertować ją do odpowiedniej jednostki czasu, na przykład sekund. Zapoznaj się z poniższym przykładem w celu wykonania tej konwersji. `EVENT_DATA`nie zawiera pola dla zwykłej liczby cykli działania. Aby uzyskać tę wartość, Odejmij `StartTimestamp` od `StopTimestamp` . `EVENT_DATA`jest strukturą, która jest przeznaczona do użycia przez użytkowników interfejsu API języka C. W przypadku użytkowników interfejsu API C++ klasy takie jak [zdarzenia](../cpp-event-data-types/event.md) do konwersji czasu są automatycznie.

Wartość `EVENT_DATA` `Data` pola zależy od wartości `EventId` pola. Wartość `Data` jest opisana w poniższej tabeli. W poniższej tabeli mogą brakować identyfikatorów jednostek. W tym przypadku `Data` pole jest ustawione na wartość **`nullptr`** lub zero.

| `EventId`wartościami | Typ wskazywany przez`Data` |
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

## <a name="tick-conversion-example"></a>Przykład konwersji znaczników

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
