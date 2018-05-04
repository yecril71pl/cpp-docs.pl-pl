---
title: Biblioteki MFC DLL — często zadawane pytania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f5740989562aea799f3a49adfa464e2c460acb3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="dll-frequently-asked-questions"></a>DLL — często zadawane pytania  
  
Poniżej przedstawiono często zadawane pytania dotyczące bibliotek DLL.  
    
-   [Biblioteki MFC DLL może tworzyć wiele wątków?](#mfc_multithreaded_1)  

-   [Można aplikacji wielowątkowych dostęp do biblioteki MFC DLL w różnych wątkach?](#mfc_multithreaded_2)  
  
-   [Czy istnieją klasy MFC lub funkcje, których nie można używać w bibliotece MFC DLL?](#mfc_prohibited_classes)  
  
-   [Jakich technik optymalizacji należy użyć, aby zwiększyć wydajność aplikacji klienckiej podczas ładowania?](#mfc_optimization)  
  
-   [W mojej regularne biblioteki DLL MFC występuje przeciek pamięci, ale wygląda dobrze mój kod. Jak można znaleźć przeciek pamięci?](#memory_leak)  

## <a name="mfc_multithreaded_1"></a> Biblioteki MFC DLL może tworzyć wiele wątków?  
  
Z wyjątkiem podczas inicjowania biblioteki MFC DLL może bezpiecznie tworzyć wiele wątków tak długo, jak używa wątku Win32 Magazyn lokalny (TLS) funkcje takie jak **TlsAlloc** przydzielić pamięć lokalna wątku. Jednak jeśli korzysta z biblioteki MFC DLL **__declspec(thread)** przydzielić pamięć lokalna wątku, aplikacja kliencka musi niejawnie połączona z biblioteki DLL. Jeśli aplikacja kliencka jawnie łącza do pliku DLL, wywołanie **LoadLibrary** nie zostanie pomyślnie załadować biblioteki DLL. Aby uzyskać więcej informacji o tworzeniu wielu wątków wewnątrz biblioteki DLL MFC zobacz artykuł bazy wiedzy, "PRB: wywołanie wywołanie funkcji LoadLibrary() do ładowania biblioteki DLL czy ma statycznych TLS" (Q118816). Aby uzyskać więcej informacji o zmiennych thread-local w bibliotekach DLL, zobacz [wątku](../cpp/thread.md).
  
 Biblioteki MFC DLL, która tworzy nowego wątku MFC podczas uruchamiania przestanie odpowiadać, gdy jest ładowany przez aplikację. Obejmuje to zawsze, gdy jest tworzony wątek, wywołując `AfxBeginThread` lub `CWinThread::CreateThread` wewnątrz:  
  
-   `InitInstance` z `CWinApp`-pochodnych obiektu w regularnych bibliotek DLL MFC.  
  
-   Podany `DllMain` lub **RawDllMain** funkcji w regularnych bibliotek DLL MFC.  
  
-   Podany `DllMain` lub **RawDllMain** funkcji w MFC DLL rozszerzenia.  
  
 Aby uzyskać więcej informacji na temat tworzenia wątków podczas inicjowania zobacz artykuł bazy wiedzy, "PRB: nie można utworzyć MFC wątku podczas DLL uruchamiania" (Q142243).  
  
## <a name="mfc_multithreaded_2"></a> Można aplikacji wielowątkowych dostęp do biblioteki MFC DLL w różnych wątkach?
Aplikacje wielowątkowe dostępne regularne biblioteki DLL MFC, która łączy dynamicznie z MFC i bibliotek DLL rozszerzeń MFC różnych wątkach. A począwszy od programu Visual C++ w wersji 4.2, aplikacja może uzyskiwać dostęp do regularne biblioteki DLL MFC, która łączy statycznie z MFC z wielu wątków utworzony w aplikacji.  
  
 Przed wersji 4.2 tylko jeden wątek zewnętrznych można dołączyć do regularne biblioteki DLL MFC, która połączone statycznie z MFC. Aby uzyskać więcej informacji na temat ograniczeń podczas uzyskiwania dostępu do regularne biblioteki DLL MFC, która łączy statycznie z MFC z wielu wątków (przed Visual C++ w wersji 4.2), zobacz artykuł bazy wiedzy, "wiele wątków i MFC _USRDLLs" (Q122676).  
  
 Należy pamiętać, że termin USRDLL nie jest już używany w dokumentacji Visual C++. Regularne biblioteki DLL MFC, która jest połączone statycznie z MFC ma takie same charakterystyki jak wcześniejsze USRDLL.  


## <a name="mfc_prohibited_classes"></a> Czy istnieją klasy MFC lub funkcje, których nie można używać w bibliotece MFC DLL?
Użyj biblioteki DLL rozszerzenia `CWinApp`-klasy aplikacji klienckiej. Nie muszą mieć własne `CWinApp`-klasy.  
  
Regularne biblioteki DLL MFC musi mieć `CWinApp`-pochodzi z klasy i pojedynczego obiektu dla tej klasy aplikacji, tak jak w przypadku aplikacji MFC. W odróżnieniu od `CWinApp` obiektu aplikacji `CWinApp` obiekt biblioteki DLL nie ma pompa głównej wiadomości.  
  
 Należy pamiętać, że ponieważ `CWinApp::Run` mechanizm nie ma zastosowania do biblioteki DLL, aplikacja jest właścicielem pompa głównej wiadomości. Jeśli ma główne okno ramowe własnej biblioteki DLL lub otwiera Niemodalne okna dialogowe, pompa głównej komunikat aplikacji należy wywołać procedury wyeksportowane przez bibliotekę DLL, która z kolei wywołuje `CWinApp::PreTranslateMessage` funkcji członkowskiej klasy obiektu aplikacji DLL.  

## <a name="mfc_optimization"></a> Jakich technik optymalizacji należy użyć, aby zwiększyć aplikacja kliencka&#39;wydajności s podczas ładowania?
Regularne biblioteki DLL MFC, która jest połączone statycznie z MFC, zmieniając go na zwykły przypadku biblioteki DLL MFC DLL, która jest połączona dynamicznie z MFC zmniejsza rozmiar pliku.  
  
 Jeśli plik DLL, który ma dużą liczbę eksportowane funkcje, aby wyeksportować funkcji przy użyciu pliku .def (zamiast **__declspec(dllexport)**) i korzystać z pliku .def [NONAME — atrybut](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) na każdym wyeksportowanej funkcji. Atrybut NONAME powoduje, że wartość porządkową, a nie nazwę funkcji mają być przechowywane w tabeli eksportu biblioteki DLL, co zmniejsza rozmiar pliku.  
  
 Biblioteki DLL połączone niejawnie do aplikacji są ładowane podczas ładowania aplikacji. Aby poprawić wydajność podczas ładowania, spróbuj dzielenia biblioteki DLL w różnych biblioteki dll. Umieść wszystkie funkcje, które aplikacja wywołująca musi natychmiast po załadowaniu do jednej biblioteki DLL i mieć aplikacja wywołująca niejawnie łącze do tej biblioteki DLL. Umieścić inne funkcje, które aplikacja wywołująca nie wymaga od razu w innej bibliotece DLL i mieć aplikacja jawnie łącze do tej biblioteki DLL. Aby uzyskać więcej informacji, zobacz [ustalić, jakiej metody łączenia użyć](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).  

## <a name="memory_leak"></a> Brak&#39;s przeciek pamięci w mojej regularne biblioteki DLL MFC, ale kod wygląda dobrze. Jak można znaleźć przeciek pamięci?  
  
Jedną z możliwych przyczyn przeciek pamięci jest, że MFC tworzy obiekty tymczasowe, które są używane wewnątrz funkcji obsługi komunikatów. W aplikacjach MFC, te obiekty tymczasowe są automatycznie czyszczone w `CWinApp::OnIdle()` funkcję wywoływaną Between przetwarzanie komunikatów. Jednak w MFC bibliotek dołączanych dynamicznie (dll) `OnIdle()` funkcja nie jest wywoływana automatycznie. W efekcie obiekty tymczasowe są nie automatycznie czyszczone. Aby wyczyścić obiekty tymczasowe, biblioteki DLL muszą jawnie wywołać `OnIdle(1)` okresowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)