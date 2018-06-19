---
title: 'Wielowątkowość: Przerywanie wątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
dev_langs:
- C++
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdf9376e9f8c9e9d74d88d0bef40dc71fd43d51f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689587"
---
# <a name="multithreading-terminating-threads"></a>Wielowątkowość: przerywanie wątków
Dwie sytuacje normalne spowodować zakończenie wątku: zamyka kontrolowanie funkcji lub wątek nie może zostać wykonane. Jeśli Edytor tekstów używana przez wątek na potrzeby drukowania w tle, kontrolowanie funkcji spowoduje przerwanie normalnie, jeśli drukowanie ukończone pomyślnie. Jeśli użytkownik chce anulować drukowanie, jednak wątku drukowania w tle musi zostać zakończone przedwcześnie. W tym temacie opisano zarówno do zaimplementowania w każdej sytuacji oraz sposobu pobrać kodu zakończenia wątku po zostaje zakończone.  
  
-   [Zakończenie wątku normalne](#_core_normal_thread_termination)  
  
-   [Przedwczesne zakończenie wątku](#_core_premature_thread_termination)  
  
-   [Trwa pobieranie kodu zakończenia wątku](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> Zakończenie wątku normalne  
 Dla wątku roboczego zakończenie wątku normalne jest prosty: Zamknij kontrolowanie funkcji i zwracać wartość oznacza przyczynie zakończenia. Możesz użyć dowolnej [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) funkcji lub `return` instrukcji. Zazwyczaj 0 oznacza ukończone pomyślnie, ale która zależy od użytkownika.  
  
 Dla wątku interfejsu użytkownika, proces jest tak proste: od w wątku interfejsu użytkownika Wywołaj [PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Tylko parametr który **PostQuitMessage** przyjmuje jest kod zakończenia wątku. Podobnie jak w przypadku wątków roboczych 0 zazwyczaj oznacza pomyślne zakończenie.  
  
##  <a name="_core_premature_thread_termination"></a> Przedwczesne zakończenie wątku  
 Przedwczesne zakończenie wątku jest prawie prosta: wywołanie [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) od w wątku. Przekaż kod zakończenia żądanej jako parametr tylko. To zatrzymuje wykonanie wątku, cofa alokację stosu wątku Odłącza wszystkie biblioteki dll dołączony do wątku i usuwa obiekt wątku z pamięci.  
  
 `AfxEndThread` Musi zostać wywołany z w wątku, który ma zostać zakończony. Jeśli chcesz przerwać wątek z innego wątku, należy skonfigurować metodę komunikacji między dwoma wątkami.  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> Trwa pobieranie kodu zakończenia wątku  
 Aby pobrać kodu zakończenia procesu roboczego lub wątku interfejsu użytkownika, należy wywołać [Funkcja GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190) funkcji. Aby uzyskać informacje o tej funkcji, zobacz [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Ta funkcja przyjmuje dojście do wątku (przechowywane w `m_hThread` elementu członkowskiego danych `CWinThread` obiekty) i adres `DWORD`.  
  
 Jeśli wątek jest nadal aktywne, **Funkcja GetExitCodeThread** umieszcza **STILL_ACTIVE** w podane `DWORD` adres; w przeciwnym razie kod zakończenia znajduje się w tym adresie.  
  
 Trwa pobieranie kodu zakończenia [cwinthread —](../mfc/reference/cwinthread-class.md) obiektów zajmuje dodatkowy krok. Domyślnie gdy `CWinThread` zakończenie wątku, obiekt wątku zostaje usunięty. Oznacza to, nie można uzyskać dostępu `m_hThread` element członkowski danych ponieważ `CWinThread` obiekt nie istnieje. Aby tego uniknąć, wykonaj jedną z następujących czynności:  
  
-   Ustaw `m_bAutoDelete` element członkowski danych do **FALSE**. Dzięki temu `CWinThread` obiektu przetrwać po wątek został zakończony. Następnie można uzyskać dostęp `m_hThread` element członkowski danych po wątek został zakończony. Jeśli używasz tej techniki, jednak jest odpowiedzialny za niszczenie `CWinThread` obiektu, ponieważ w ramach nie powoduje automatycznego usunięcia go dla Ciebie. Jest to preferowana metoda.  
  
-   Dojście wątku należy przechowywać oddzielnie. Po utworzeniu wątek, skopiuj jej `m_hThread` elementu członkowskiego danych (przy użyciu **:: DuplicateHandle**) do innej zmiennej i do niego dostęp za pośrednictwem tej zmiennej. Dzięki temu obiekt jest usuwane automatycznie, gdy występuje zakończenia i może nadal dowiedzieć się, dlaczego wątek zakończony. Pamiętaj, że wątek nie zakończyć przed można zduplikować dojścia. Jest to najbezpieczniejszy sposób, w tym do przekazania **CREATE_SUSPENDED** do [afxbeginthread —](../mfc/reference/application-information-and-management.md#afxbeginthread)i przechowywania dojście oraz wywołując wznowienie wątku [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).  
  
 Każda metoda pozwala określić dlaczego `CWinThread` obiektu zakończone.  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)   
 [_endthread —, _endthreadex —](../c-runtime-library/reference/endthread-endthreadex.md)   
 [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)