---
title: Struktura EVENT_DATA
description: Zestaw C++ SDK usługi Build insights EVENT_DATA odwołanie do struktury.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 572cbdaba346ddb77b665b5677b978c83a80aa3d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333777"
---
# <a name="event_data-structure"></a>Struktura EVENT_DATA

::: moniker range="<=vs-2015"

Zestaw C++ SDK usługi Build Insights jest zgodny z programem Visual Studio 2017 lub nowszym. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora wersji programu Visual Studio dla tego artykułu na Visual Studio 2017 lub Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `EVENT_DATA` opisuje zdarzenie odebrane z sesji analizy lub dziennika. Te sesje są uruchamiane przez wywołanie funkcji [Analizuj](../functions/analyze.md), [Analizuj](../functions/analyze-a.md)i [AnalyzeW](../functions/analyze-w.md), [relog](../functions/relog.md), [RelogA](../functions/relog-a.md)lub [RelogW](../functions/relog-w.md) .

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
| `ExclusiveCPUTicks` | To pole ma takie samo znaczenie jak `CPUTicks`, z tą różnicą, że nie obejmują taktów procesora, które wystąpiły w działaniach podrzędnych. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `WallClockTimeResponsibilityTicks` | Jeśli to zdarzenie jest *działaniem*, wartość tego pola jest równa liczbie cykli reprezentującej udział tego działania w ogólnym czasie zegara ściany. Cykl odpowiedzialności w czasie zegara ściany różni się od zwykłego taktu. Cykle odpowiedzialności za zegary ścienne są uwzględniane równolegle między działaniami. Na przykład dwie działania równoległe mogą mieć czas trwania 50 taktów i ten sam czas rozpoczęcia i zakończenia. W takim przypadku do obu tych elementów zostanie przypisany Czas zegarowy do 25 taktów. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `ExclusiveWallClockTimeResponsibilityTicks` | To pole ma takie samo znaczenie jak `WallClockTimeResponsibilityTicks`, z tą różnicą, że nie obejmuje to osi odpowiedzialności za czas zegara ściennego działań podrzędnych. To pole jest ustawione na zero dla *zdarzeń prostych*. |
| `Data` | Wskazuje dodatkowe dane przechowywane w zdarzeniu. Typ danych wskazywanych przez jest inny, w zależności od pola `EventId`. |
| `ProcessId` | Identyfikator procesu, w którym wystąpiło zdarzenie. |
| `ThreadId` | Identyfikator wątku, w którym wystąpiło zdarzenie. |
| `ProcessorIndex` | Numer procesora CPU, na którym wystąpiło zdarzenie. |
| `EventName` | Ciąg ANSI zawierający nazwę jednostki identyfikowanej przez `EventId`. |
| `EventWideName` | Szeroki ciąg zawierający nazwę jednostki identyfikowanej przez `EventId`. |

## <a name="remarks"></a>Uwagi

Wiele pól w `EVENT_DATA` zawiera liczby taktów. C++Usługi Build Insights wykorzystują licznik wydajności okna jako źródło taktów. Liczba cykli musi być używana z polem `TickFrequency`, aby przekonwertować ją do odpowiedniej jednostki czasu, na przykład sekund. Zapoznaj się z poniższym przykładem w celu wykonania tej konwersji. `EVENT_DATA` nie zawiera pola dla zwykłej liczby cykli działania. Aby uzyskać tę wartość, Odejmij `StartTimestamp` od `StopTimestamp`. `EVENT_DATA` to struktura, która jest przeznaczona do użycia przez użytkowników interfejsu API języka C. W C++ przypadku użytkowników interfejsu API klasy takie jak [zdarzenia](../cpp-event-data-types/event.md) do konwersji czasu są automatycznie.

Wartość pola `EVENT_DATA` `Data` zależy od wartości pola `EventId`. W poniższej tabeli opisano wartość `Data`. W poniższej tabeli mogą brakować identyfikatorów jednostek. W tym przypadku pole `Data` ma wartość `nullptr` lub zero.

| wartość `EventId` | Typ wskazywany przez `Data` |
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
