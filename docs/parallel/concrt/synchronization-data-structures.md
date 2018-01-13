---
title: Struktury danych synchronizacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1dd1c47cad01e0324f8027593eb4933f70cd6191
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="synchronization-data-structures"></a>Struktury danych synchronizacji
Współbieżność środowiska wykonawczego zawiera kilka struktury danych, które pozwalają synchronizujący dostęp do danych udostępnionych przez wiele wątków. Te struktury danych są przydatne, gdy udostępniasz dane, które rzadko modyfikacji. Obiekt synchronizacji, na przykład sekcja krytyczna, powoduje, że inne wątki poczekać, aż udostępniony zasób jest dostępny. W związku z tym Jeśli używasz takiego obiektu synchronizujący dostęp do danych, która jest często używane, zostaną utracone skalowalności w aplikacji. [Równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) zapewnia [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, która umożliwia udostępnianie zasobów między kilka wątków lub zadań bez konieczności synchronizacji. Aby uzyskać więcej informacji na temat `combinable` , zobacz [równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="top"></a>Sekcje  
 W tym temacie opisano następujące typy bloku komunikatów asynchronicznych szczegółowo:  
  
-   [critical_section](#critical_section)  
  
-   [reader_writer_lock](#reader_writer_lock)  
  
-   [scoped_lock i scoped_lock_read](#scoped_lock)  
  
-   [event](#event)  
  
##  <a name="critical_section"></a>critical_section  
 [Concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) klasa reprezentuje obiekt współpracy wzajemne wykluczenie, zwracające do wykonywania innych zadań zamiast preempting je. Sekcje krytyczne są przydatne, gdy wiele wątków wymaga wyłącznego dostępu odczytu i zapisu do współużytkowanych danych.  

 `critical_section` Nie obsługującą jest klasa. [Concurrency::critical_section::lock](reference/critical-section-class.md#lock) metoda zgłasza wyjątek typu [concurrency::improper_lock](../../parallel/concrt/reference/improper-lock-class.md) gdy została wywołana przez wątek, który już jest właścicielem blokady.  


  
### <a name="methods-and-features"></a>Metody i funkcje  
 W poniższej tabeli przedstawiono ważne metody, które są zdefiniowane przez `critical_section` klasy.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[lock](reference/critical-section-class.md#lock)|Uzyskuje sekcja krytyczna. Wywołanie kontekstu bloki do momentu jego uzyskuje blokady.|  
|[try_lock](reference/critical-section-class.md#try_lock)|Próbuje uzyskać sekcja krytyczna, ale nie są blokowane.|  
|[odblokowywanie](reference/critical-section-class.md#unlock)|Zwalnia sekcja krytyczna.|  
  
 [[Górnej](#top)]  
  
##  <a name="reader_writer_lock"></a>reader_writer_lock  
 [Concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) klasa udostępnia operacje wątkowo odczytu/zapisu do współużytkowanych danych. Blokady modułu odczytywania/zapisywania należy używać, gdy wiele wątków wymagają równoczesnych dostęp do odczytu do udostępnionych zasobów, ale rzadko zapisu do tego zasobu udostępnionego. Ta klasa udostępnia tylko jeden wątek zapisu obiektu w dowolnym momencie.  
  
 `reader_writer_lock` Klasy mogą wykonywać lepszym rozwiązaniem niż `critical_section` klasy, ponieważ `critical_section` wyłącznego dostępu do zasobu udostępnionego, co uniemożliwia dostęp do odczytu równoczesnych żądań obiektu.  
  
 Podobnie jak `critical_section` klasy `reader_writer_lock` klasa reprezentuje obiekt współpracy wzajemne wykluczenie, zwracające do wykonywania innych zadań zamiast preempting je.  
  
 Wątek, który musi być zapisana do udostępnionego zasobu uzyskuje blokadę odczytywania/zapisywania, innych wątków, które również muszą uzyskać dostęp do zasobu zostaną zablokowane do czasu twórcę zwalnia blokadę. `reader_writer_lock` Klasy jest przykładem *zapisu — preferencji* blokady, czyli blokada odblokowuje autorów oczekiwania przed jego odblokowuje czytników oczekiwania.  
  
 Podobnie jak `critical_section` klasy `reader_writer_lock` nie obsługującą jest klasa. [Concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock) i [concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read) metody Zgłoś wyjątek typu `improper_lock` Jeśli zostaną wywołane przez wątek, który już jest właścicielem blokady.  


  
> [!NOTE]
>  Ponieważ `reader_writer_lock` nie obsługującą jest klasa, nie może uaktualnić blokady tylko do odczytu z blokadą odczytywania/zapisywania ani obniżyć czytnika/blokadę z blokadą odczytu. Jedną z tych operacji wykonywania powoduje zachowanie nieokreślony.  
  
### <a name="methods-and-features"></a>Metody i funkcje  
 W poniższej tabeli przedstawiono ważne metody, które są zdefiniowane przez `reader_writer_lock` klasy.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[lock](reference/reader-writer-lock-class.md#lock)|Uzyskuje dostęp do odczytu i zapisu do blokady.|  
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Próbuje uzyskać dostęp do odczytu i zapisu do blokady, ale nie są blokowane.|  
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Uzyskuje dostęp tylko do odczytu do blokady.|  
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Próbuje uzyskać dostęp tylko do odczytu do blokady, ale nie są blokowane.|  
|[odblokowywanie](reference/reader-writer-lock-class.md#unlock)|Zwalnia blokadę.|  
  
 [[Górnej](#top)]  
  
##  <a name="scoped_lock"></a>scoped_lock i scoped_lock_read  
 `critical_section` i `reader_writer_lock` klasy Podaj klasy zagnieżdżonej pomocnika, które upraszczają sposób pracy z obiektami wzajemne wykluczenie. Te klasy pomocy są określane jako *zakres blokady*.  
  
 `critical_section` Klasa zawiera [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) klasy. Konstruktor uzyskuje dostęp do udostępnionych `critical_section` obiekt; destruktora wersjach dostęp do tego obiektu. `reader_writer_lock` Klasa zawiera [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) klasy, która jest podobny `critical_section::scoped_lock`, ale zarządza zapisu do dostarczonego `reader_writer_lock` obiektu. `reader_writer_lock` Klasa zawiera także [concurrency::reader_writer_lock::scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) klasy. Ta klasa zarządza dostęp do odczytu do udostępnionych `reader_writer_lock` obiektu.  

  
 Zakresie blokad zalety podczas pracy z `critical_section` i `reader_writer_lock` obiekty ręcznie. Zazwyczaj należy przydzielić zakresami blokady na stosie. Zakresie blokady zwalnia automatycznie dostęp do jego obiektu wzajemne wykluczenie, gdy został zniszczony; Dlatego użytkownik nie ręcznie odblokowane obiektu źródłowego. Jest to przydatne, gdy funkcja zawiera wiele `return` instrukcje. Zakresie blokad też pomóc Ci bezpieczne wyjątek w kodzie. Gdy `throw` instrukcja powoduje stosu cofnąć, destruktor dla żadnej aktywnej blokady zakresie jest wywoływany i w związku z tym obiektem wzajemne wykluczenie zawsze poprawnie zostanie zwolniony.  
  
> [!NOTE]
>  Jeśli używasz `critical_section::scoped_lock`, `reader_writer_lock::scoped_lock`, i `reader_writer_lock::scoped_lock_read` klas, ręcznie nie zwalnia dostępu do obiektu źródłowego wzajemne wykluczenie. To umieść środowiska uruchomieniowego w nieprawidłowym stanie.  
  
##  <a name="event"></a>zdarzenia  
 [Concurrency::event](../../parallel/concrt/reference/event-class.md) klasa reprezentuje obiekt synchronizacji, których stan mogą być sygnalizowane lub z systemem innym niż sygnalizowane. W przeciwieństwie do synchronizacji obiekty, takie jak sekcje krytyczne, których celem jest ochrona dostępu do danych udostępnionych, zdarzenia synchronizacji przepływ wykonania.  
  
 `event` Klasy jest przydatne, gdy jedno zadanie zakończy pracę na rzecz inne zadanie. Na przykład jedno zadanie może sygnalizować inne zadanie że może go odczytywać dane z połączeniem sieciowym lub z pliku.  
  
### <a name="methods-and-features"></a>Metody i funkcje  
 W poniższej tabeli przedstawiono kilka ważnych metod, które są definiowane przez `event` klasy.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[oczekiwania](reference/event-class.md#wait)|Czeka na zdarzenie sygnalizuje stają się.|  
|[set](reference/event-class.md#set)|Ustawia stan sygnałowego zdarzenia.|  
|[Resetowanie](reference/event-class.md#reset)|Ustawia stan sygnalizowane zdarzenia.|  
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Czeka na wiele zdarzeń stać się sygnalizowane.|  

  
### <a name="example"></a>Przykład  
 Na przykład, który przedstawia sposób użycia `event` , zobacz [porównywanie struktur danych synchronizacji interfejsu API systemu Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 [[Górnej](#top)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Porównywanie struktur danych synchronizacji z Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 Porównuje zachowanie struktury danych synchronizacji tych zapewnianych przez interfejs API systemu Windows.  
  
 [Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)  
 W tym artykule opisano współbieżność środowiska wykonawczego, co upraszcza Programowanie równoległe i zawiera linki do powiązanych tematów.

