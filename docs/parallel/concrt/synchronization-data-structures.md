---
title: Struktury danych synchronizacji
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 8c91de87bb5d579916743051d06c15f6df6921bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495930"
---
# <a name="synchronization-data-structures"></a>Struktury danych synchronizacji

Środowisko uruchomieniowe współbieżności udostępnia kilka struktur danych, które pozwalają synchronizowania dostępu do udostępnionych danych z wielu wątków. Te struktury danych są przydatne, gdy udostępniasz dane, które rzadko zmodyfikować. Obiekt synchronizacji, na przykład sekcję krytyczną, powoduje, że inne wątki, poczekać, aż udostępniony zasób jest dostępny. W związku z tym Jeśli używasz takiego obiektu do synchronizowania dostępu do danych, który jest używany często może utracić skalowalności w aplikacji. [Biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) zapewnia [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, która umożliwia udostępnianie zasobów między kilka wątków lub zadań bez konieczności synchronizacji. Aby uzyskać więcej informacji na temat `combinable` klasy, zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).

##  <a name="top"></a> Sekcje

W tym temacie opisano następujące typy komunikatów asynchronicznych w bloku, szczegółowo:

- [critical_section —](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock i scoped_lock_read —](#scoped_lock)

- [event](#event)

##  <a name="critical_section"></a> critical_section —

[Concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) klasa reprezentuje obiekt współpracy wzajemne wykluczenie, który daje do innych zadań, zamiast wywłaszczanie je. Sekcje krytyczne są przydatne, gdy wiele wątków wymaga wyłącznego dostępu odczytu i zapisu do udostępnionych danych.

`critical_section` Klasa jest nie obsługującą. [Concurrency::critical_section::lock](reference/critical-section-class.md#lock) metoda zgłasza wyjątek typu [concurrency::improper_lock](../../parallel/concrt/reference/improper-lock-class.md) Jeśli jest ona wywoływana przez wątek, który już posiada blokadę.

### <a name="methods-and-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono ważne metody, które są definiowane przez `critical_section` klasy.

|Metoda|Opis|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|Uzyskuje sekcję krytyczną. Wywołujący kontekstu blokuje, aż do jego uzyskuje blokadę.|
|[try_lock —](reference/critical-section-class.md#try_lock)|Próbuje uzyskać sekcję krytyczną, ale nie są blokowane.|
|[unlock](reference/critical-section-class.md#unlock)|Zwalnia sekcję krytyczną.|

[[Górnej](#top)]

##  <a name="reader_writer_lock"></a> reader_writer_lock

[Concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) klasa udostępnia operacje wątkowo odczytu/zapisu do udostępnionych danych. Użyj czytnika/moduł zapisujący blokady, gdy wiele wątków wymagają współbieżnych dostęp do odczytu do udostępnionych zasobów, ale rzadko zapisu do udostępnionego zasobu. Ta klasa udostępnia tylko jeden wątek zapisu obiektu w dowolnym momencie.

`reader_writer_lock` Klasy można wykonywać lepsze niż `critical_section` klasy, ponieważ `critical_section` obiektu uzyskuje wyłączny dostęp do udostępnionego zasobu, co uniemożliwia równoczesny dostęp do odczytu.

Podobnie jak `critical_section` klasy `reader_writer_lock` klasa reprezentuje obiekt współpracy wzajemne wykluczenie, który daje do innych zadań, zamiast wywłaszczanie je.

Gdy wątek, który trzeba napisać we współdzielonym zasobie uzyskuje blokadę czytnika/zapisu, inne wątki, które również musi uzyskać dostęp do zasobu są blokowane, aż moduł zapisujący zwalnia blokadę. `reader_writer_lock` Klasy jest przykładem *preferencji zapisu* blokadę, o której jest zablokowana, który odblokowuje autorzy oczekiwania przed jego odblokowuje czytelnicy oczekiwania.

Podobnie jak `critical_section` klasy `reader_writer_lock` klasa jest nie obsługującą. [Concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock) i [concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read) metody zgłosić wyjątek typu `improper_lock` Jeśli zostaną wywołane przez wątek, który już jest właścicielem Blokada.

> [!NOTE]
>  Ponieważ `reader_writer_lock` klasy nie obsługującą, nie można uaktualnić blokadę tylko do odczytu do czytnika/blokadę lub obniżyć czytnika/blokadę na blokadę tylko do odczytu. Wykonując jedną z tych operacji tworzy nieokreślone zachowanie.

### <a name="methods-and-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono ważne metody, które są definiowane przez `reader_writer_lock` klasy.

|Metoda|Opis|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|Ukończone operacje odczytu i zapisu blokady.|
|[try_lock —](reference/reader-writer-lock-class.md#try_lock)|Próbuje uzyskać dostępu do odczytu i zapisu do blokady, ale nie są blokowane.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Uzyskuje dostęp tylko do odczytu do blokady.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Próbuje uzyskać dostęp do blokadę tylko do odczytu, ale nie są blokowane.|
|[unlock](reference/reader-writer-lock-class.md#unlock)|Zwalnia blokadę.|

[[Górnej](#top)]

##  <a name="scoped_lock"></a> scoped_lock i scoped_lock_read —

`critical_section` i `reader_writer_lock` klasy zapewniają klas zagnieżdżonych pomocniczych, które upraszczają sposób pracy z obiektami wzajemne wykluczenie. Te klasy pomocy są znane jako *zakres blokady*.

`critical_section` Klasa zawiera [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) klasy. Konstruktor uzyskuje dostęp do udostępnionych `critical_section` obiekt; dostęp do wersji destruktora do tego obiektu. `reader_writer_lock` Klasa zawiera [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) klasy, która przypomina `critical_section::scoped_lock`, z tą różnicą, że zarządza zapisu do dostarczonego `reader_writer_lock` obiektu. `reader_writer_lock` Klasa zawiera także [concurrency::reader_writer_lock::scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) klasy. Ta klasa zarządza dostęp do odczytu do udostępnionych `reader_writer_lock` obiektu.

O określonym zakresie blokad zapewnia kilka korzyści, podczas pracy z `critical_section` i `reader_writer_lock` obiekty ręcznie. Zazwyczaj należy przydzielić o określonym zakresie blokady na stosie. O określonym zakresie blokady wydaje automatycznie dostęp do jego obiektu wzajemne wykluczenie, kiedy niszczony jest ona; w związku z tym należy nie ręcznie odblokować obiektu źródłowego. Jest to przydatne, gdy funkcja zawiera wiele `return` instrukcji. O określonym zakresie blokad ułatwiają także napisać kod bezpieczne pod względem wyjątków. Gdy `throw` instrukcja powoduje stosu na odpoczynek, destruktor dla żadnej aktywnej blokady o określonym zakresie jest wywoływany i w związku z tym obiektem wzajemne wykluczenie jest zawsze poprawnie zwolnione.

> [!NOTE]
>  Kiedy używasz `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`, i `reader_writer_lock::scoped_lock_read` klas, ręcznie nie zwalnia dostęp do bazowego obiektu wzajemne wykluczenie. To jest umieścić środowiska uruchomieniowego w nieprawidłowym stanie.

##  <a name="event"></a> Zdarzenia

[Concurrency::event](../../parallel/concrt/reference/event-class.md) klasa reprezentuje obiekt synchronizacji, w których stan może być sygnalizowane lub zasygnalizowane. W przeciwieństwie do synchronizacji obiektów, takich jak sekcji krytycznych, których celem jest ochrona dostępu do udostępnionych danych, zdarzenia synchronizować przepływem wykonania.

`event` Klasa jest przydatna, gdy jedno zadanie zakończy się nad innym zadaniem. Na przykład jedno zadanie podrzędne może sygnał inne zadanie, może go odczytywać dane z połączeniem sieciowym lub z pliku.

### <a name="methods-and-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono niektóre ważne metody, które są definiowane przez `event` klasy.

|Metoda|Opis|
|------------|-----------------|
|[Czekaj](reference/event-class.md#wait)|W tym czasie czeka na zdarzenie zostało zasygnalizowane.|
|[set](reference/event-class.md#set)|Ustawia zdarzenie do sygnalizowanego stanu.|
|[Resetuj](reference/event-class.md#reset)|Ustawia zdarzenie stanie zasygnalizowane.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|W tym czasie czeka na wiele zdarzeń zostało zasygnalizowane.|

### <a name="example"></a>Przykład

Aby uzyskać przykład ilustruje sposób używania `event` klasy, zobacz [porównywanie struktur danych synchronizacji z interfejsu API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Górnej](#top)]

## <a name="related-sections"></a>Sekcje pokrewne

[Porównywanie struktur danych synchronizacji z Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
Porównuje zachowanie struktur danych synchronizacji udostępnianych przez interfejs API Windows.

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)<br/>
W tym artykule opisano środowisko uruchomieniowe współbieżności, upraszczający Programowanie równoległe i zawiera linki do powiązanych tematów.

