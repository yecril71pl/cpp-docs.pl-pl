---
title: Porównywanie struktur danych synchronizacji z Windows API
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: 4fa0d3fbf3457bfafab731275584d206206161dd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275977"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Porównywanie struktur danych synchronizacji z Windows API

W tym temacie porównano zachowanie struktury danych synchronizacji, które są dostarczane przez środowisko uruchomieniowe współbieżności tych zapewnianych przez Windows API.

Postępuj zgodnie z struktury danych synchronizacji, które są dostarczane przez środowisko uruchomieniowe współbieżności *cooperative model wątkowości*. W wspólnego modelu wątkowości podstawowych synchronizacji jawnie przynieść ich przetwarzania zasobów dla innych wątków. To różni się od *preemptive model wątkowości*, w przypadku przeniesienia zasobów do przetwarzania dla innych wątków przez kontrolowanie harmonogramu lub system operacyjny.

## <a name="criticalsection"></a>critical_section

[Concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) klasa przypomina Windows `CRITICAL_SECTION` struktury, ponieważ może służyć tylko przez wątki jednego procesu. Aby uzyskać więcej informacji na temat sekcje krytyczne w interfejsie API Windows, zobacz [krytyczne obiekty sekcji](/windows/desktop/Sync/critical-section-objects).

## <a name="readerwriterlock"></a>Klasa reader_writer_lock

[Concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) klasa przypomina blokad kieszeń czytnika/składnika zapisywania (SRW) Windows. W poniższej tabeli opisano podobieństw i różnic.

|Funkcja|`reader_writer_lock`|Zablokuj SRW|
|-------------|--------------------------|--------------|
|Inne niż obsługującą|Tak|Tak|
|Podwyższyć poziom czytnika Writer (Obsługa uaktualnienia)|Nie|Nie|
|Można obniżyć poziom Edytor do czytnika (Obsługa obniżenia poziomu)|Nie|Nie|
|Blokady zapisu preferencji|Tak|Nie|
|FIFO dostęp do składników zapisywania|Tak|Nie|

Aby uzyskać więcej informacji na temat blokady SRW zobacz [blokad kieszeń czytnika/zapis (SRW)](https://msdn.microsoft.com/library/windows/desktop/aa904937) w zestawie SDK platformy.

## <a name="event"></a>zdarzenie

[Concurrency::event](../../parallel/concrt/reference/event-class.md) klasa przypomina nienazwane, zdarzenie resetowania ręcznego Windows. Jednak `event` obiektu zachowuje się wspólnie, natomiast zdarzeń Windows zachowuje się prewencyjnego. Aby uzyskać więcej informacji na temat zdarzeń Windows zobacz [obiekty zdarzeń](/windows/desktop/Sync/event-objects).

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Aby lepiej zrozumieć różnicę między `event` klasy i wydarzenia Windows, należy wziąć pod uwagę w poniższym przykładzie. Ten przykład włącza harmonogram można utworzyć maksymalnie dwa równoczesne zadania, a następnie wywołania dwóch podobnych funkcji używających `event` klasy i zdarzenie resetowania ręcznego Windows. Każda funkcja najpierw tworzy kilka zadań, które oczekiwania udostępnionego zdarzenie zostało zasygnalizowane. Każda funkcja następnie daje aby uruchomione zadania podrzędne, a następnie sygnalizuje zdarzenie. Każda funkcja, która jest następnie czeka na zasygnalizowany zdarzeń.

### <a name="code"></a>Kod

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>Komentarze

Ten przykład generuje następujące przykładowe dane wyjściowe:

```Output
Cooperative event:
    Context 0: waiting on an event.
    Context 1: waiting on an event.
    Context 2: waiting on an event.
    Context 3: waiting on an event.
    Context 4: waiting on an event.
    Setting the event.
    Context 5: received the event.
    Context 6: received the event.
    Context 7: received the event.
    Context 8: received the event.
    Context 9: received the event.
Windows event:
    Context 10: waiting on an event.
    Context 11: waiting on an event.
    Setting the event.
    Context 12: received the event.
    Context 14: waiting on an event.
    Context 15: received the event.
    Context 16: waiting on an event.
    Context 17: received the event.
    Context 18: waiting on an event.
    Context 19: received the event.
    Context 13: received the event.
```

Ponieważ `event` klasy zachowuje się wspólne, harmonogram można ponownie przydzielić zasoby przetwarzania do innego kontekstu, gdy zdarzenie oczekuje na zasygnalizowany stan. W związku z tym, więcej pracy jest realizowane przez wersję, która używa `event` klasy. W wersji, która używa zdarzeń Windows każde zadanie oczekiwania należy wprowadzić sygnalizowanego stanu przed rozpoczęciem następnego zadania.

Aby uzyskać więcej informacji o zadaniach, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Zobacz także

[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)
