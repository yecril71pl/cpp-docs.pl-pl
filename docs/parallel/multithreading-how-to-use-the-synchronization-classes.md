---
title: 'Wielowątkowość: Jak używać klas synchronizacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cec2f873f1fc46ebac2e0f1714c8f46ebc10eac4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597892"
---
# <a name="multithreading-how-to-use-the-synchronization-classes"></a>Wielowątkowość: jak używać klas synchronizacji
Synchronizowanie dostęp do zasobów między wątkami jest to powszechny problem, podczas pisania aplikacji wielowątkowych. Masz co najmniej dwóch wątków jednocześnie dostępu do tych samych danych może prowadzić do niepożądanych i nieprzewidywalnych wyników. Na przykład jeden wątek może być aktualizowanie zawartości struktury, podczas gdy inny wątek odczytuje zawartość tę samą strukturę. Jest nieznany otrzymają wątku odczytywania danych: stare dane nowo zapisanych danych i prawdopodobnie kombinacji obu. Biblioteka MFC zawiera szereg synchronizacji i klasy dostępu synchronizacji, aby pomóc w rozwiązaniu tego problemu. W tym temacie opisano klasy, które są dostępne i jak ich używać do tworzenia klas metodą o bezpiecznych wątkach w typowej aplikacji wielowątkowych.  
  
Typowa aplikacja wielowątkowa ma klasę, która reprezentuje zasób do współdzielenia pośród wątków. Klasa prawidłowo zaprojektowana, w pełni metodą o bezpiecznych wątkach nie wymaga wywołaniem dowolnej funkcji synchronizacji. Wszystko, czego odbywa się wewnętrznie do klasy, dzięki czemu możesz skoncentrować się na najlepszego wykorzystania tej klasy, nie na temat sposobu może uzyskać uszkodzony. Skuteczną techniką tworzenia klasy pełni wątków jest scalić klasę synchronizacji do klasy zasobów. Scalanie klas synchronizacji w udostępnionej klasie jest dość proste.  
  
Na przykład potrwać aplikację, która utrzymuje połączonej listy kont. Ta aplikacja umożliwia maksymalnie trzy konta do badania w oddzielnych okien, ale w danym momencie można zaktualizować tylko jeden. Gdy konto zostanie zaktualizowany, zaktualizowane dane są wysyłane przez sieć do archiwum danych.  
  
Ta przykładowa aplikacja używa wszystkich trzech typów klas synchronizacji. Ponieważ zezwala ona na maksymalnie trzy konta do badania, w tym samym czasie, używa [CSemaphore](../mfc/reference/csemaphore-class.md) Aby ograniczyć dostęp do trzy obiekty widoku. Podczas próby wyświetlenia czwarty konta występuje, aplikacji, albo oczekuje, aż jeden z pierwszych trzech systemu windows zostanie zamknięty lub zakończy się niepowodzeniem. Gdy konto zostanie zaktualizowany, aplikacja używa [CCriticalSection](../mfc/reference/ccriticalsection-class.md) aby upewnić się, że tylko jedno konto jest aktualizowana w danym momencie. Po aktualizacji zakończy się powodzeniem, sygnalizuje [CEvent](../mfc/reference/cevent-class.md), które zwalnia oczekiwania na zdarzenie, które ma być zasygnalizowany wątku. Ten wątek wysyła nowe dane do archiwum danych.  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> Projektowanie klasy obsługujące wielowątkowość  
 
Aby klasę pełni metodą o bezpiecznych wątkach, najpierw dodać klasy synchronizacji odpowiednich do udostępnionego klas jako element członkowski danych. W poprzednim przykładzie zarządzania kontami `CSemaphore` element członkowski danych zostaną dodane do klasy widoku `CCriticalSection` element członkowski danych zostaną dodane do klasy połączonej listy i `CEvent` element członkowski danych zostaną dodane do klasy magazynu danych.  
  
Następnie dodaj wywołaniach synchronizacji do wszystkich składowych, które modyfikują dane w klasie lub uzyskania dostępu do kontrolowanego zasobu. W każdej funkcji, należy utworzyć jedną [CSingleLock](../mfc/reference/csinglelock-class.md) lub [CMultiLock](../mfc/reference/cmultilock-class.md) obiektu, a następnie wywołać ten obiekt `Lock` funkcji. Gdy obiekt blokady wykracza poza zakres i jest niszczony, destruktor obiektu wywołuje `Unlock` , przy zwalnianiu zasobów. Oczywiście można wywołać `Unlock` bezpośrednio chcącym.  
  
Projektowanie swojej klasy obsługujące wielowątkowość w ten sposób umożliwia może być ona używana w aplikacji wielowątkowych jako łatwo jako klasa bez wątkowo, ale na wyższym poziomie bezpieczeństwa. Zawieranie obiekt synchronizacji i synchronizacji dostępu do obiektów w klasie zasobu wszystkie ma zalety programowania pełni metodą o bezpiecznych wątkach bez zwrotu utrzymywanie synchronizacji kodu.  
  
Poniższy przykład kodu przedstawia tę metodę, przy użyciu element członkowski danych `m_CritSection` (typu `CCriticalSection`), jest zadeklarowana w klasie zasobów udostępnionych i `CSingleLock` obiektu. Synchronizacja udostępnionego zasobu (pochodną `CWinThread`) zostanie podjęta, tworząc `CSingleLock` obiektu przy użyciu adresu `m_CritSection` obiektu. Próby zablokowania zasobu i po uzyskaniu praca jest wykonywana na obiekcie udostępnionym. Po zakończeniu pracy zasobu jest odblokowana wywołaniem `Unlock`.  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
> `CCriticalSection`, w przeciwieństwie do innych klas synchronizacji MFC nie ma opcji żądania Przekroczono limit czasu blokady. Okres oczekiwania na wątek zwolnić jest nieskończona.  
  
Wady tego podejścia to, że klasa będzie przebiegać wolniej niż do tej samej klasy bez obiekty synchronizacji dodane. Ponadto w przypadku prawdopodobieństwo, że więcej niż jeden wątek może spowodować usunięcie obiektu scalonych podejście może nie zawsze działać. W takiej sytuacji zaleca się zachować oddzielne synchronizacji obiektów.  
  
Aby uzyskać informacje dotyczące ustalania, która klasa synchronizacji do użycia w różnych sytuacjach, zobacz [wielowątkowość: kiedy używać klas synchronizacji](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Aby uzyskać więcej informacji na temat synchronizacji, zobacz [synchronizacji](http://msdn.microsoft.com/library/windows/desktop/ms686353) w zestawie Windows SDK. Aby uzyskać więcej informacji na temat Obsługa wielowątkowości w MFC, zobacz [wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 
[Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)