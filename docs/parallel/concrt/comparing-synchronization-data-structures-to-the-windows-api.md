---
title: "Porównywanie struktur danych synchronizacji z Windows API | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4590724bfc34d0ed9136e74e85b09db6a805c50c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Porównywanie struktur danych synchronizacji z Windows API
W tym temacie porównuje zachowanie struktur danych synchronizacji, które są udostępniane przez współbieżność środowiska wykonawczego tych zapewnianych przez interfejs API systemu Windows.  
  
 Struktury danych synchronizacji, które są udostępniane przez współbieżności środowiska wykonawczego wykonaj *wspólnego modelu wątków*. W modelu wątkowości wspólne elementy podstawowe synchronizacji jawnie yield ich przetwarzania zasobów do innych wątków. To różni się od *cenią sobie wcześniejsze model wątkowości*, gdzie przetwarzania zasobów są przekazywane do innych wątków, kontrolowanie harmonogramu lub systemu operacyjnego.  
  
## <a name="criticalsection"></a>critical_section  
 [Concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) klasy podobny systemu Windows `CRITICAL_SECTION` struktury, ponieważ mogą zostać użyte tylko przez wątki tego procesu. Aby uzyskać więcej informacji na temat sekcje krytyczne w interfejsie API systemu Windows, zobacz [krytyczne obiekty sekcji](http://msdn.microsoft.com/library/windows/desktop/ms682530).  
  
## <a name="readerwriterlock"></a>Klasa reader_writer_lock  
 [Concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) klasy podobny blokad cienki odczytywania/zapisywania (SRW) systemu Windows. W poniższej tabeli opisano podobieństw i różnic.  
  
|Funkcja|`reader_writer_lock`|SRW blokady|  
|-------------|--------------------------|--------------|  
|Inne niż obsługującą|Tak|Tak|  
|Można podwyższyć poziom czytnik Writer (Obsługa uaktualnienia)|Nie|Nie|  
|Można obniżyć poziom Edytor do czytnika (Obsługa obniżenia poziomu)|Nie|Nie|  
|Blokady zapisu — preferencji|Tak|Nie|  
|FIFO dostępu do zapisywania|Tak|Nie|  
  
 Aby uzyskać więcej informacji na temat SRW blokad, zobacz [blokad cienki odczytywania/zapisywania (SRW)](http://msdn.microsoft.com/library/windows/desktop/aa904937) w zestawie SDK platformy.  
  
## <a name="event"></a>zdarzenie  
 [Concurrency::event](../../parallel/concrt/reference/event-class.md) klasy podobny nienazwane, zdarzenie resetowania ręcznego systemu Windows. Jednak `event` obiektu zachowuje się wspólnie, podczas gdy zdarzenie systemu Windows zachowuje się preemptively. Aby uzyskać więcej informacji na temat zdarzeń systemu Windows, zobacz [obiektów zdarzeń](http://msdn.microsoft.com/library/windows/desktop/ms682655).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Aby lepiej zrozumieć różnicę między `event` klasy i zdarzenia systemu Windows, należy wziąć pod uwagę w poniższym przykładzie. W tym przykładzie włącza harmonogram można utworzyć najwyżej dwóch jednoczesnych zadań, a następnie wywołania dwa podobne funkcje używające `event` klasy i zdarzenie systemu Windows resetowania ręcznego. Każda funkcja najpierw tworzy kilka zadań, które oczekiwać na udostępnionych zdarzenia stają się sygnalizowane. Każdej funkcji implikuje następnie do uruchomionych zadań i następnie sygnały zdarzenia. Każda funkcja następnie czeka na jego sygnałowego.  
  
### <a name="code"></a>Kod  
 [!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]  
  
### <a name="comments"></a>Komentarze  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe:  
  
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
  
 Ponieważ `event` klasy zachowuje wspólne, planista można ponownie przydzielić zasoby przetwarzania kontekst, gdy zdarzenie oczekuje na przejściu w stan sygnałowego. W związku z tym więcej pracy odbywa się przez wersję, która używa `event` klasy. W wersji, która używa zdarzeń systemu Windows każde zadanie oczekiwania należy wprowadzić sygnałowego stanu przed uruchomieniem następnego zadania.  
  
 Aby uzyskać więcej informacji o zadaniach, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury danych synchronizacji](../../parallel/concrt/synchronization-data-structures.md)
