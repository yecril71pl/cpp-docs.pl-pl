---
title: Struktury danych synchronizacji
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 85dec6b003330a3560ae1dcc5c41b5e6d49f765e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142794"
---
# <a name="synchronization-data-structures"></a>Struktury danych synchronizacji

Środowisko uruchomieniowe współbieżności zapewnia kilka struktur danych, które pozwalają synchronizować dostęp do danych udostępnionych z wielu wątków. Te struktury danych są przydatne, gdy dane udostępnione są modyfikowane rzadko. Obiekt synchronizacji, na przykład sekcję krytyczną, powoduje, że inne wątki oczekują na dostęp do zasobu udostępnionego. W związku z tym, jeśli używasz takiego obiektu do synchronizowania dostępu do danych, które są często używane, możesz utracić skalowalność aplikacji. [Biblioteka równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) udostępnia klasę [concurrency::Binding](../../parallel/concrt/reference/combinable-class.md) , która umożliwia udostępnianie zasobu między kilkoma wątkami lub zadaniami bez konieczności synchronizacji. Aby uzyskać więcej informacji na temat klasy `combinable`, zobacz [Parallel Containers and Objects](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="top"></a>Poszczególne

W tym temacie opisano szczegółowo następujące typy bloków komunikatów asynchronicznych:

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock i scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a>critical_section

Klasa [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) reprezentuje wspólny obiekt wykluczenia, który uzyskuje inne zadania, zamiast przekazywać je. Sekcje krytyczne są przydatne, gdy wiele wątków wymaga wyłącznego dostępu do odczytu i zapisu do udostępnionych danych.

Klasa `critical_section` nie jest współużytkowana. Metoda [concurrency:: critical_section:: Lock](reference/critical-section-class.md#lock) zgłasza wyjątek typu [concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md) , jeśli jest wywoływany przez wątek, który jest już właścicielem blokady.

### <a name="methods-and-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono ważne metody, które są zdefiniowane przez klasę `critical_section`.

|Metoda|Opis|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|Uzyskuje sekcję krytyczną. Wywołanie bloku kontekstu do momentu uzyskania blokady.|
|[try_lock](reference/critical-section-class.md#try_lock)|Próbuje uzyskać sekcję krytyczną, ale nie blokuje.|
|[odblokowania](reference/critical-section-class.md#unlock)|Zwalnia sekcję krytyczną.|

[[Top](#top)]

## <a name="reader_writer_lock"></a>reader_writer_lock

Klasa [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) zapewnia bezpieczne dla wątków operacje odczytu/zapisu do udostępnionych danych. Użyj blokady czytnika/składnika zapisywania, gdy wiele wątków wymaga jednoczesnego dostępu do odczytu do zasobu udostępnionego, ale rzadko zapisuj w tym udostępnionym zasobie. Ta klasa daje tylko jeden wątek zapisu do obiektu w dowolnym momencie.

Klasa `reader_writer_lock` może działać lepiej niż Klasa `critical_section`, ponieważ obiekt `critical_section` uzyskuje wyłączny dostęp do zasobu udostępnionego, co uniemożliwi dostęp współbieżny do odczytu.

Podobnie jak w przypadku klasy `critical_section`, Klasa `reader_writer_lock` reprezentuje wspólny obiekt wykluczenia, który daje inne zadania, zamiast przekazywać je.

Gdy wątek, który musi zapisywać w udostępnionym zasobie, uzyskuje blokadę czytnika/składnika zapisywania, inne wątki, które również muszą uzyskać dostęp do zasobu, są blokowane do momentu zwolnienia blokady przez moduł zapisujący. Klasa `reader_writer_lock` jest przykładem blokady *Write-Preference* , która jest blokadą, która odblokowuje blokowanych autorów przed odblokowaniem oczekujących czytników.

Podobnie jak Klasa `critical_section`, Klasa `reader_writer_lock` nie jest współużytkowana. [Concurrency:: reader_writer_lock:: Lock](reference/reader-writer-lock-class.md#lock) i [concurrency:: reader_writer_lock:: lock_read](reference/reader-writer-lock-class.md#lock_read) metody zgłaszają wyjątek typu `improper_lock`, jeśli są wywoływane przez wątek, który jest już właścicielem blokady.

> [!NOTE]
> Ponieważ Klasa `reader_writer_lock` nie jest współużytkowana, nie można uaktualnić blokady tylko do odczytu do blokady czytnika/składnika zapisywania ani obniżenia poziomu blokady czytnika/składnika zapisywania do blokady w trybie tylko do odczytu. Wykonanie jednej z tych operacji powoduje nieokreślone zachowanie.

### <a name="methods-and-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono ważne metody, które są zdefiniowane przez klasę `reader_writer_lock`.

|Metoda|Opis|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|Uzyskuje dostęp do odczytu i zapisu do blokady.|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Próbuje uzyskać dostęp do odczytu/zapisu do blokady, ale nie blokuje.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Uzyskuje dostęp tylko do odczytu do blokady.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Próbuje uzyskać dostęp tylko do odczytu do blokady, ale nie blokuje.|
|[odblokowania](reference/reader-writer-lock-class.md#unlock)|Zwalnia blokadę.|

[[Top](#top)]

## <a name="scoped_lock"></a>scoped_lock i scoped_lock_read

Klasy `critical_section` i `reader_writer_lock` zapewniają zagnieżdżone klasy pomocnicze, które upraszczają sposób pracy z obiektami wzajemnego wykluczania. Te klasy pomocnika są nazywane *blokadami objętymi zakresem*.

Klasa `critical_section` zawiera klasę [concurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) . Konstruktor uzyskuje dostęp do podanego obiektu `critical_section`; destruktor zwalnia dostęp do tego obiektu. Klasa `reader_writer_lock` zawiera klasę [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) , która przypomina `critical_section::scoped_lock`, z tą różnicą, że zarządza dostępem do zapisu do podanego obiektu `reader_writer_lock`. Klasa `reader_writer_lock` zawiera również klasę [concurrency:: reader_writer_lock:: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) . Ta klasa zarządza dostępem do odczytu do podanego obiektu `reader_writer_lock`.

Blokady z zakresami zapewniają kilka korzyści, gdy pracujesz ręcznie z obiektami `critical_section` i `reader_writer_lock`. Zwykle przypisujesz blokadę z zakresu na stosie. Blokada zakresu zwalnia dostęp do jego wzajemnego wykluczenia, gdy zostanie zniszczony; w związku z tym nie należy ręcznie odblokować bazowego obiektu. Jest to przydatne, gdy funkcja zawiera wiele instrukcji `return`. Blokady w zakresie mogą również pomóc w pisaniu kodu z bezpiecznymi wyjątkami. Gdy instrukcja `throw` powoduje cofnięcie stosu, destruktor dla każdej aktywnej blokady z zakresem jest wywoływany, w związku z czym wzajemny wykluczenie jest zawsze prawidłowo wydane.

> [!NOTE]
> W przypadku używania klas `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`i `reader_writer_lock::scoped_lock_read` nie należy ręcznie wydawania dostępu do podstawowego obiektu wykluczenia. Może to spowodować wystąpienie środowiska uruchomieniowego w nieprawidłowym stanie.

## <a name="event"></a>wydarzen

Klasa [concurrency:: Event](../../parallel/concrt/reference/event-class.md) reprezentuje obiekt synchronizacji, którego stan może być sygnalizowane lub nie jest sygnałem. W przeciwieństwie do obiektów synchronizacji, takich jak sekcje krytyczne, których celem jest ochrona dostępu do danych udostępnionych, synchronizacja zdarzeń przebiegu wykonywania.

Klasa `event` jest przydatna, gdy jedno zadanie zakończyło pracę nad innym zadaniem. Na przykład jedno zadanie może sygnalizować inne zadanie, że odczytaje dane z połączenia sieciowego lub z pliku.

### <a name="methods-and-features"></a>Metody i funkcje

W poniższej tabeli przedstawiono kilka ważnych metod, które są zdefiniowane przez klasę `event`.

|Metoda|Opis|
|------------|-----------------|
|[trwa](reference/event-class.md#wait)|Czeka, aż zdarzenie zostanie zasygnalizowane.|
|[set](reference/event-class.md#set)|Ustawia zdarzenie na sygnał.|
|[zresetować](reference/event-class.md#reset)|Ustawia dla zdarzenia niesygnalizowanego stanu.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Czeka na zasygnalizowanie wielu zdarzeń.|

### <a name="example"></a>Przykład

Aby zapoznać się z przykładem, który pokazuje, jak używać klasy `event`, zobacz [Porównywanie struktur danych synchronizacji z interfejsem API systemu Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Top](#top)]

## <a name="related-sections"></a>Sekcje pokrewne

[Porównywanie struktur danych synchronizacji z Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
Porównuje zachowanie struktur danych synchronizacji z tymi, które są udostępniane przez interfejs API systemu Windows.

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)<br/>
Opisuje środowisko uruchomieniowe współbieżności, które upraszczają programowanie równoległe i zawiera linki do powiązanych tematów.
