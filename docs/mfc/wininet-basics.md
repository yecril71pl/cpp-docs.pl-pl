---
title: Podstawy WinInet | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3c9502c720b0f443ace3cfe637fb4826281ecf4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="wininet-basics"></a>Podstawy WinInet
Aby dodać obsługę FTP, aby pobrać i przekazywania plików z poziomu aplikacji, można użyć WinInet. Można zastąpić [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) i użyj `dwContext` parametru zapewnia informacje o postępie do użytkowników, jak wyszukiwanie i pobieranie plików.  
  
 Ten artykuł zawiera następujące tematy:  
  
-   [Tworzenie bardzo proste przeglądarki](#_core_create_a_very_simple_browser)  
  
-   [Pobierz strony sieci Web](#_core_download_a_web_page)  
  
-   [Plik FTP](#_core_ftp_a_file)  
  
-   [Pobieranie katalogu Gopher](#_core_retrieve_a_gopher_directory)  
  
-   [Wyświetl informacje o postępie podczas transferu plików](#_core_display_progress_information_while_transferring_files)  
  
 Fragmenty kodu poniżej pokazano sposób tworzenia prostego przeglądarki, pobierania strony sieci Web, FTP pliku i wyszukać plik gopher. Nie są przeznaczone jako przykłady pełny i nie zawierają obsługi wyjątków.  
  
 Aby uzyskać dodatkowe informacje na temat WinInet, zobacz [rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md).  
  
##  <a name="_core_create_a_very_simple_browser"></a>Tworzenie bardzo proste przeglądarki  
 [!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]  
  
##  <a name="_core_download_a_web_page"></a>Pobierz strony sieci Web  
 [!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]  
  
##  <a name="_core_ftp_a_file"></a>Plik FTP  
 [!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a>Pobieranie katalogu Gopher  
 [!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]  
  
## <a name="use-onstatuscallback"></a>Użyj OnStatusCallback  
 Podczas używania klas WinInet, można użyć [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) członkiem aplikacji [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu można pobrać informacji o stanie. Przypadku klasy wyprowadzonej własne `CInternetSession` obiektów, Zastąp `OnStatusCallback`i Włącz stan wywołania zwrotne, wywoła MFC z `OnStatusCallback` funkcja postępu informacje o wszystkich działań w tej sesji Internet.  
  
 Ponieważ jedna sesja może obsługiwać wiele połączeń (które ich okresu istnienia, może wykonywać wiele różnych operacji distinct) `OnStatusCallback` musi mechanizm umożliwiający określenie każdej zmiany stanu z określonego połączenia lub transakcji. Ten mechanizm są udostępniane przez parametr ID kontekstu do wielu funkcji Członkowskich w klasach WinInet pomocy technicznej. Ten parametr jest zawsze typu `DWORD` i nosi nazwę zawsze `dwContext`.  
  
 Kontekst przypisane do określonego obiektu internetowych jest używany tylko do identyfikacji działania obiektu powoduje, że w `OnStatusCallback` członkiem `CInternetSession` obiektu. Wywołanie `OnStatusCallback` odbiera kilka parametrów; te parametry współpracują ze sobą poinformowanie aplikacji o jaki jest postęp które transakcji i połączenia.  
  
 Po utworzeniu `CInternetSession` obiektu, można określić `dwContext` parametru konstruktora. `CInternetSession`sam nie korzysta z Identyfikatorem kontekstu; Zamiast tego przechodzą identyfikator kontekstu do żadnego **InternetConnection**-pochodnych obiektów, które jawnie nie Pobierz identyfikator kontekstu we własnym. Z kolei, te `CInternetConnection` obiektów zostanie przekazany identyfikator kontekstu wzdłuż do `CInternetFile` obiekty tworzą, jeśli nie określisz jawnie identyfikatora inny kontekst Jeśli z drugiej strony, określ identyfikator kontekst własnych, obiekt i pracy będzie skojarzony z tym identyfikatorem kontekstu. Kontekst identyfikatorów umożliwia określenie, jakie informacje o stanie są przyznawane użytkownikowi w Twojej `OnStatusCallback` funkcji.  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a>Wyświetl informacje o postępie podczas transferu plików  
 Na przykład, jeśli piszesz aplikację, która tworzy połączenie z serwerem FTP można odczytać pliku, a także łączy się z serwerem HTTP, można pobrać strony sieci Web, będziesz mieć `CInternetSession` obiektu, dwa `CInternetConnection` obiektów (co będzie **CFtpSession** , a drugi będzie **CHttpSession**), a dwie `CInternetFile` obiektów (po jednej dla każdego połączenia). Jeśli używane wartości domyślne dla `dwContext` parametrów, użytkownik nie będzie mógł rozróżnienia `OnStatusCallback` wywołań wskazujące postępu dla połączeń FTP i wskazujący postęp dla połączenia HTTP wywołań. Jeśli określisz `dwContext` identyfikator, który można później sprawdzić w `OnStatusCallback`, będzie wiadomo, które operacja wygenerowała wywołania zwrotnego.  
  
## <a name="see-also"></a>Zobacz też  
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)   
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

