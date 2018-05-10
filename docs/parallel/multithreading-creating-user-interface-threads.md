---
title: 'Wielowątkowość: Tworzenie wątków interfejsu użytkownika | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 480839316cc8d47b2af4be1cd81c0d02f09fad25
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-creating-user-interface-threads"></a>Wielowątkowość: tworzenie wątków interfejsu użytkownika
Wątek interfejsu użytkownika jest najczęściej używany do obsługi danych wejściowych użytkownika zdarzeń i reagowanie na użytkownika niezależnie od wątków wykonywania innych części aplikacji. Wątku głównego aplikacji (w Twojej `CWinApp`-klasy) jest już utworzony i uruchomiona. W tym temacie opisano kroki niezbędne do tworzenia wątków interfejsu użytkownika.  
  
 Najpierw należy wykonać podczas tworzenia wątku interfejsu użytkownika jest klasa wyprowadzona z [cwinthread —](../mfc/reference/cwinthread-class.md). Należy zadeklarować i wdrożyć przy użyciu [declare_dyncreate —](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) i [implement_dyncreate —](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) makra. Ta klasa musi zastąpić niektóre funkcje i mogą zastąpić inne osoby. W poniższej tabeli przedstawiono te funkcje i co należy zrobić.  
  
### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Funkcje do przesłonięcia podczas tworzenia wątku interfejsu użytkownika  
  
|Funkcja|Cel|  
|--------------|-------------|  

|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)| Wykonaj czyszczenie, gdy zakończenie wątku. Zazwyczaj przesłonięcia. |  
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)| Wykonaj inicjowania wystąpienia wątku. Musi zostać zastąpiona. |  
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)| Wykonaj właściwe dla wątków przetwarzania czas bezczynności. Nie zawsze przesłonięcia. |  
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)| Filtruj wiadomości, zanim zostaną rozesłane **TranslateMessage** i **DispatchMessage**. Nie zawsze przesłonięcia. |  
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)| Przechwycić nieobsługiwane wyjątki rzucane przez programy obsługi wiadomości i polecenia wątku. Nie zawsze przesłonięcia. |  
|[Uruchom](../mfc/reference/cwinthread-class.md#run)| Kontrolowanie funkcji wątku. Zawiera przekazywanie komunikatów. Rzadko przesłonięcia. |  

  
 MFC zawiera dwie wersje `AfxBeginThread` za pomocą parametru przeładowanie: klucz, który można tworzyć tylko wątków roboczych, a taki, który można utworzyć wątków interfejsu użytkownika lub wątków roboczych. Uruchamianie z wątku interfejsu użytkownika, wywołaj metodę przeciążenia drugi [afxbeginthread —](../mfc/reference/application-information-and-management.md#afxbeginthread), podając następujące informacje:  
  
-   [Runtime_class —](../mfc/reference/run-time-object-model-services.md#runtime_class) pochodzi od klasy `CWinThread`.  
  
-   (Opcjonalnie) Żądany priorytet. Wartość domyślna to normalnym priorytecie. Aby uzyskać więcej informacji na temat poziomów priorytet dostępne w temacie [wykonanie funkcji SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
-   (Opcjonalnie) Rozmiar żądanego stosu wątku. Wartością domyślną jest tym samym stosie rozmiar jako Tworzenie wątku.  
  
-   (Opcjonalnie) **CREATE_SUSPENDED** Jeśli chcesz wątku, który ma zostać utworzony w stanie wstrzymania. Wartość domyślna to 0 lub normalnie uruchomienie wątku.  
  
-   (Opcjonalnie) Atrybuty wymaganymi. Wartość domyślna to te same prawa dostępu jako wątku nadrzędnej. Aby uzyskać więcej informacji na temat formatu informacji o zabezpieczeniach, zobacz [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread` wykonuje większość pracy należy. Tworzy nowy obiekt klasy, inicjowane z informacji podanych i wywołania [CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread) można uruchomić na wykonywaniu wątku. Testy zostały wprowadzone w całej procedury upewnij się, że wszystkie obiekty są deallocated prawidłowo w przypadku dowolnej części Tworzenie nie.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Wielowątkowość: przerywanie wątków](../parallel/multithreading-terminating-threads.md)  
  
-   [Wielowątkowość: tworzenie wątków roboczych](../parallel/multithreading-creating-worker-threads.md)  
  
-   [Procesów i wątków](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)