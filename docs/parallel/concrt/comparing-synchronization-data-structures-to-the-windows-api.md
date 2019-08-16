---
title: Porównywanie struktur danych synchronizacji z Windows API
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: 16d58431ae3f9859677302010f15a75b37ebedbf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510592"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Porównywanie struktur danych synchronizacji z Windows API

W tym temacie porównano zachowanie struktur danych synchronizacji, które są dostarczane przez środowisko uruchomieniowe współbieżności do tych dostarczonych przez interfejs API systemu Windows.

Struktury danych synchronizacji dostarczone przez środowisko uruchomieniowe współbieżności są zgodne z *modelem wątkowości*. W modelu wątkowości w organizacji elementy pierwotne synchronizacji jawnie zapewniają swoje zasoby przetwarzania do innych wątków. Różni się to od *modelu wielowątkowości*, gdzie zasoby przetwarzania są przesyłane do innych wątków przez kontrolowanie harmonogramu lub systemu operacyjnego.

## <a name="critical_section"></a>critical_section

Klasa [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) przypomina strukturę systemu Windows `CRITICAL_SECTION` , ponieważ może być używana tylko przez wątki jednego procesu. Aby uzyskać więcej informacji na temat krytycznych sekcji w interfejsie API systemu Windows, zobacz [najważniejsze obiekty sekcji](/windows/win32/Sync/critical-section-objects).

## <a name="reader_writer_lock"></a>Klasa reader_writer_lock

Klasa [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) przypomina blokady systemu Windows (SRW). W poniższej tabeli opisano podobieństwa i różnice.

|Funkcja|`reader_writer_lock`|Blokada SRW|
|-------------|--------------------------|--------------|
|Niewspółpracujący|Tak|Tak|
|Możliwość promowania czytnika do składnika zapisywania (Pomoc techniczna dotycząca uaktualniania)|Nie|Nie|
|Może obniżyć poziom składnika zapisywania do czytnika (obsługa obniżenia poziomu)|Nie|Nie|
|Blokada zapisu — preferencja|Tak|Nie|
|Dostęp do modułów zapisujących FIFO|Tak|Nie|

Więcej informacji na temat blokad SRW można znaleźć w temacie [Slim Reader/Writer (SRW)](/windows/win32/sync/slim-reader-writer--srw--locks) w zestawie SDK platformy.

## <a name="event"></a>zdarzenie

Klasa [concurrency:: Event](../../parallel/concrt/reference/event-class.md) przypomina nienazwane zdarzenie resetowania ręcznego systemu Windows. `event` Jednak obiekt zachowuje się wspólnie, podczas gdy zdarzenie systemu Windows działa zapobiegawczo. Aby uzyskać więcej informacji na temat zdarzeń systemu Windows, zobacz [obiektów zdarzeń](/windows/win32/Sync/event-objects).

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Aby lepiej zrozumieć różnicę między elementami `event` klasy i zdarzeń systemu Windows, weź pod uwagę Poniższy przykład. Ten przykład umożliwia harmonogramowi tworzenie co najwyżej dwóch jednoczesnych zadań, a następnie wywołuje dwie podobne funkcje, `event` które używają klasy i zdarzenia ręcznego resetowania systemu Windows. Każda funkcja najpierw tworzy kilka zadań, które oczekują na zasygnalizowanie zdarzenia udostępnionego. Każda funkcja zwraca do uruchomionych zadań, a następnie sygnalizuje zdarzenie. Każda funkcja czeka na zdarzenie sygnalizowane.

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

`event` Ponieważ Klasa zachowuje się wspólnie, harmonogram może ponownie przydzielić zasoby przetwarzania do innego kontekstu, gdy zdarzenie oczekuje na przekroczenie stanu sygnalizowania. W związku z tym więcej pracy jest realizowane przez wersję, która używa `event` klasy. W wersji korzystającej z zdarzeń systemu Windows każde zadanie oczekujące musi wprowadzić stan sygnalizujący, zanim następne zadanie zostanie uruchomione.

Aby uzyskać więcej informacji o zadaniach, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Zobacz także

[Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)
