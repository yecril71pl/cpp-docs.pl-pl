---
title: "Obsługa wyjątków w MFC | Dokumentacja firmy Microsoft"
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
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 544130f27fb01d0d29652087351c8a5bbc5bd5c7
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="exception-handling-in-mfc"></a>Obsługa wyjątków w MFC
W tym artykule opisano dostępne w MFC mechanizmy obsługi wyjątków. Dostępne są dwa mechanizmy:  
  
-   Wyjątki języka C++, dostępne w MFC w wersji 3.0 lub nowszy  
  
-   Makra wyjątków MFC, dostępne w MFC w wersji 1.0 lub nowszy  
  
 Jeśli piszesz nową aplikację za pomocą MFC, należy używać mechanizmu C++. Jeśli istniejąca aplikacja już używa mechanizmu często, można użyć mechanizmu opartego na makr.  
  
 Łatwo można przekonwertować istniejącego kodu do wyjątków języka C++ zamiast makr wyjątków MFC. Zalety konwertowanie kod i wytyczne dotyczące to opisane w artykule [wyjątki: konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
 Jeśli już korzystasz z aplikacji przy użyciu makra wyjątków MFC, możesz kontynuować przy użyciu tych makr w istniejącym kodzie podczas używania wyjątków języka C++ w nowy kod. Artykuł [wyjątki: zmiany w makrach wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) poda wskazówki dla w ten sposób.  
  
> [!NOTE]
>  Aby włączyć C++ obsługi wyjątków w kodzie, wybierz opcję Włącz wyjątki C++ na stronie generowanie kodu w folderze projektu C/C++ [strony właściwości](../ide/property-pages-visual-cpp.md) okno dialogowe, lub użyj /GX — opcja kompilatora. Wartość domyślna to /GX-, co spowoduje wyłączenie obsługi wyjątków.  
  
 W tym artykule omówiono następujące tematy:  
  
-   [Kiedy używać wyjątków](#_core_when_to_use_exceptions)  
  
-   [Obsługa wyjątków MFC](#_core_mfc_exception_support)  
  
-   [Dalsze informacje dotyczące wyjątków](#_core_further_reading_about_exceptions)  
  
##  <a name="_core_when_to_use_exceptions"></a>Kiedy używać wyjątków  
 Trzy kategorie wyników może wystąpić, gdy funkcja jest wywoływana podczas wykonywania programu: normalnego wykonywania, wykonanie błędne lub nietypowe wykonanie. Poniżej opisano każdej kategorii.  
  
-   Wykonanie normalnej  
  
     Funkcja może działać normalnie i zwracać. Niektóre funkcje zwracają kod wyniku do wywołującego, który wskazuje wynik funkcji. Kody wyników możliwe wyłącznie są zdefiniowane dla tej funkcji i reprezentują zakres możliwych wartości funkcji. Kod wyniku może wskazywać powodzenie lub Niepowodzenie lub nawet może wskazywać określonego typu awarii, który znajduje się w normalnym zakresie oczekiwań. Funkcja stan pliku można na przykład zwraca kod, który wskazuje, że plik nie istnieje. Należy pamiętać, że termin "Kod błędu:" nie jest używana, ponieważ wynikowy kod przedstawia jedną z wielu oczekiwanych wyników.  
  
-   Błędne wykonywania  
  
     Obiekt wywołujący sprawia, że niektóre błędu w przekazywanie argumentów do funkcji lub wywołuje funkcję w kontekście nieodpowiednie. Taka sytuacja powoduje błąd i powinny zostać wykryte przy użyciu potwierdzenia podczas tworzenia programu. (Aby uzyskać więcej informacji na potwierdzeń, zobacz [potwierdzenia C/C++](/visualstudio/debugger/c-cpp-assertions).)  
  
-   Nietypowe wykonanie  
  
     Nietypowe wykonanie dotyczy sytuacji, w którym warunki poza kontrolą programu, takie jak małej ilości pamięci lub błędów We/Wy są mające wpływ na wynik funkcji. Nietypowych sytuacjach powinno zostać obsłużone przez przechwytywanie i zgłaszanie wyjątków.  
  
 Używanie wyjątków jest szczególnie przydatne dla nietypowe wykonanie.  
  
##  <a name="_core_mfc_exception_support"></a>Obsługa wyjątków MFC  
 Czy używa wyjątków języka C++, bezpośrednio lub za pomocą makr wyjątków MFC, użyć [cexception — klasa](../mfc/reference/cexception-class.md) lub `CException`-pochodnych obiektów, które może zostać zgłoszony przez platformę, lub przez aplikację.  
  
 W poniższej tabeli przedstawiono wstępnie zdefiniowane wyjątki udostępniane przez MFC.  
  
|Klasa wyjątku|Znaczenie|  
|---------------------|-------------|  
|[Klasa CMemoryException](../mfc/reference/cmemoryexception-class.md)|Braku pamięci|  
|[Klasa CFileException](../mfc/reference/cfileexception-class.md)|Wyjątek plików|  
|[Klasa CArchiveException](../mfc/reference/carchiveexception-class.md)|Wyjątek archiwum/serializacji|  
|[Klasa CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)|Odpowiedzi na żądanie usługi nieobsługiwane|  
|[Klasa CResourceException](../mfc/reference/cresourceexception-class.md)|Wyjątek alokacji zasobów systemu Windows|  
|[Klasa CDaoException](../mfc/reference/cdaoexception-class.md)|Wyjątki bazy danych (DAO — klasy)|  
|[Klasa CDBException](../mfc/reference/cdbexception-class.md)|Wyjątki bazy danych (ODBC — klasy)|  
|[Klasa COleException](../mfc/reference/coleexception-class.md)|wyjątki OLE|  
|[Klasa COleDispatchException](../mfc/reference/coledispatchexception-class.md)|Wyjątki alokacji (automatyzacji)|  
|[Klasa CUserException](../mfc/reference/cuserexception-class.md)|Wyjątek, który powiadamia użytkownika z okno komunikatu, następnie zgłasza ogólnego [cexception — klasa](../mfc/reference/cexception-class.md)|  
  
> [!NOTE]
>  MFC obsługuje zarówno wyjątki C++ i makr wyjątków MFC. MFC nie obsługuje bezpośrednio programy obsługi wyjątków strukturalnych systemu Windows NT (SEH), zgodnie z opisem w [obsługi wyjątków strukturalnych](http://msdn.microsoft.com/library/windows/desktop/ms680657).  
  
##  <a name="_core_further_reading_about_exceptions"></a>Dalsze informacje dotyczące wyjątków  
 Następujące artykuły wyjaśniają, za pomocą biblioteki MFC dla przekazywanie wyjątek:  
  
-   [Wyjątki: przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md)  
  
-   [Wyjątki: badanie zawartości wyjątku](../mfc/exceptions-examining-exception-contents.md)  
  
-   [Wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md)  
  
-   [Wyjątki: zgłaszanie wyjątków z własnych funkcji](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)  
  
-   [Wyjątki: wyjątki bazy danych](../mfc/exceptions-database-exceptions.md)  
  
-   [Wyjątki: wyjątki OLE](../mfc/exceptions-ole-exceptions.md)  
  
 Następujące artykuły porównania makr wyjątków MFC z słowa kluczowe języka C++ wyjątku i wyjaśniono, jak można dostosować kodu:  
  
-   [Wyjątki: zmiany w makrach wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)  
  
-   [Wyjątki: konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)  
  
-   [Wyjątki: używanie makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [C++, obsługa wyjątków](../cpp/cpp-exception-handling.md)   
 [Jak: utworzyć własne klasy wyjątków niestandardowych](http://go.microsoft.com/fwlink/p/?linkid=128045)

