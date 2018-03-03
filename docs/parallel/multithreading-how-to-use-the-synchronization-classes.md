---
title: "Wielowątkowość: Jak używać klas synchronizacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d85ea58588ea889fc8294b23604d47aef725135
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-how-to-use-the-synchronization-classes"></a>Wielowątkowość: jak używać klas synchronizacji
Synchronizacja dostęp do zasobów między wątkami jest to powszechny problem, podczas pisania aplikacji wielowątkowych. Dwa lub więcej wątków jednocześnie dostęp do tych samych danych może prowadzić do niepożądanych i nieprzewidywalnych wyników. Na przykład jeden wątek może być aktualizowanie zawartości struktury, podczas gdy inny wątek odczytuje zawartość tej samej struktury. Jest nieznany otrzymają wątku czytania, jakie dane: stare dane nowo napisanych danych i prawdopodobnie ich kombinacjami. MFC zawiera pewną liczbę synchronizacji i klasy dostępu synchronizacji, aby pomóc w rozwiązaniu tego problemu. W tym temacie opisano klasy dostępne oraz sposób ich używać do tworzenia klas wątkowo w typowej aplikacji wielowątkowych.  
  
 Typowa aplikacja wielowątkowa ma klasę, która reprezentuje zasób współdzielenia wątków. Klasa prawidłowo zaprojektowana, pełni wielowątkowość nie wymaga wywołaniem dowolnej funkcji synchronizacji. To wszystko, co obsługiwany wewnętrznie do klasy, umożliwiając skoncentrować się na temat sposobu użycia najlepsze klasy, a nie na temat sposobu może pobrać uszkodzony. Skuteczne techniki tworzenia klasy pełni wielowątkowość polega na scaleniu klasa synchronizacji do klasy zasobów. Scalanie klas synchronizacji w udostępnionej klasie jest dość proste.  
  
 Na przykład mieć aplikację, która przechowuje połączonej listy kont. Ta aplikacja pozwala maksymalnie trzy konta należy zbadać w oddzielnych okien, ale tylko jeden z nich może być aktualizowana w dowolnym momencie konkretnego. Po zaktualizowaniu konta zaktualizowane dane są wysyłane przez sieć do archiwum danych.  
  
 Ta przykładowa aplikacja używa wszystkie trzy typy klas synchronizacji. Ponieważ zezwala ona na maksymalnie trzy konta należy zbadać w tym samym czasie, używa [CSemaphore](../mfc/reference/csemaphore-class.md) zajmującym się trzy obiekty widoku. Podczas próby wyświetlenia czwarty konta występuje, aplikacji, albo czeka, aż jeden z trzech pierwszych windows powoduje zamknięcie lub nie jest on. Po zaktualizowaniu konta, aplikacja używa [CCriticalSection](../mfc/reference/ccriticalsection-class.md) aby upewnić się, że tylko jedno konto jest aktualizowany w czasie. Po aktualizacji zakończy się powodzeniem, sygnały [CEvent](../mfc/reference/cevent-class.md), który zwalnia wątku oczekiwania na zdarzenie zostać zgłoszony. Ten wątek wysyła nowe dane do archiwum danych.  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a>Projektowanie klasy obsługujące wielowątkowość  
 Aby klasy pełni wielowątkowość, najpierw dodać klasy odpowiedniej synchronizacji do udostępnionego klas jako element członkowski danych. W poprzednim przykładzie zarządzania kontami **CSemaphore** element członkowski danych zostanie dodany do klasy widoku `CCriticalSection` element członkowski danych zostanie dodany do klasy połączone listy i `CEvent` danych zostanie dodany element członkowski danych Klasa magazynu.  
  
 Następnie dodaj wywołaniach synchronizacji do wszystkich funkcji Członkowskich, które modyfikować danych w klasie lub uzyskania dostępu do kontrolowanego zasobu. W każdej funkcji należy utworzyć albo [CSingleLock](../mfc/reference/csinglelock-class.md) lub [CMultiLock](../mfc/reference/cmultilock-class.md) obiektu i wywołania tego obiektu `Lock` funkcji. Gdy obiekt blokady wykracza poza zakres i zostanie zniszczony, obiektu destruktor wywoła `Unlock` , zwalniając zasobu. Oczywiście można wywołać `Unlock` bezpośrednio Jeśli chcesz.  
  
 Projektowanie klasy obsługującej wielowątkowość w ten sposób umożliwi można używać w aplikacji wielowątkowych jako łatwo jako klasa z systemem innym niż wątkowo, ale z wyższego poziomu bezpieczeństwa. Zawieranie obiekt synchronizacji i synchronizacji dostępu do obiektów w klasie zasobu zapewnia wszystkie korzyści programowania pełni wielowątkowość bez zwrotu utrzymywanie synchronizacji kodu.  
  
 Poniższy przykład kodu pokazuje tej metody za pomocą elementem członkowskim danych `m_CritSection` (typu `CCriticalSection`), a zadeklarowanych w klasie zasobu udostępnionego i `CSingleLock` obiektu. Synchronizacja zasobu udostępnionego (pochodną `CWinThread`) nastąpiła tworząc `CSingleLock` przy użyciu adresu `m_CritSection` obiektu. Aby zablokować zasobu podejmowana jest próba i po uzyskaniu praca jest wykonywana na obiekcie udostępnionym. Po zakończeniu pracy zasób został odblokowany w wyniku wywołania `Unlock`.  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
>  `CCriticalSection`, w przeciwieństwie do innych klas MFC synchronizacji nie ma opcji żądanie czasu blokady. Okres oczekiwania na wątek zwolnić to nieskończoność.  
  
 Wady tej metody to, że klasa będzie przebiegać wolniej niż tej samej klasy bez synchronizacji obiekty dodane. Ponadto jeśli istnieje ryzyko, że więcej niż jeden wątek może usunąć obiektu, scalonych podejście może nie zawsze działać. W takim przypadku warto zachować synchronizacji oddzielnych obiektów.  
  
 Aby uzyskać informacje dotyczące określania, która klasa synchronizacji używane w różnych sytuacjach, zobacz [Multithreading: kiedy używać klas synchronizacji](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Aby uzyskać więcej informacji o synchronizacji, zobacz [synchronizacji](http://msdn.microsoft.com/library/windows/desktop/ms686353) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Aby uzyskać więcej informacji na temat obsługi wielowątkowości w MFC, zobacz [Multithreading z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)