---
title: 'Wielowątkowość: Przerywanie wątków w MFC'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
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
ms.openlocfilehash: c92d95bc2aa63d78c98d10e25de79344fe1ee0f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484022"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Wielowątkowość: Przerywanie wątków w MFC

Dwie normalne sytuacje powodują zakończenie wątku: funkcja kontrolowania istnieje lub wątek nie jest dozwolony do zakończenia. Jeśli Edytor tekstu używa wątku do drukowania w tle, funkcja kontrolowania zakończy się normalnie Jeśli drukowanie zostanie ukończone pomyślnie. Jeśli użytkownik chce anulować drukowanie, natomiast wątek drukowanie w tle musi być zakończony przedwcześnie. W tym temacie wyjaśniono, jak implementować każdą sytuację i jak uzyskać kod wyjścia wątku, po jego działania.

- [Zakończenie normalne wątku](#_core_normal_thread_termination)

- [Przedwczesne zakończenie wątku](#_core_premature_thread_termination)

- [Pobieranie kodu wyjścia wątku](#_core_retrieving_the_exit_code_of_a_thread)

##  <a name="_core_normal_thread_termination"></a> Zakończenie normalne wątku

W przypadku wątku roboczego zakończenie zwykłych wątków jest proste: zamknij funkcję kontrolującą i zwróć wartość, która oznacza powód zakończenia. Można użyć dowolnego [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) funkcji lub **zwracają** instrukcji. Typowo 0 oznacza pomyślne ukończenie, ale która zależy od użytkownika.

Dla wątku interfejsu użytkownika, proces jest równie prosty: z wewnątrz wątku interfejsu użytkownika Wywołaj [PostQuitMessage](https://msdn.microsoft.com/library/windows/desktop/ms644945) w zestawie Windows SDK. Jedynym parametrem, `PostQuitMessage` przyjmuje jest kod wyjścia wątku. Jak w przypadku wątków roboczych 0 zazwyczaj oznacza pomyślne zakończenie.

##  <a name="_core_premature_thread_termination"></a> Przedwczesne zakończenie wątku

Przedwczesne zakończenie wątku jest prawie tak samo proste: wywołanie [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) z wewnątrz wątku. Przekaż żądany kod zakończenia jako jedyny parametr. To zatrzymuje wykonanie wątku, powoduje cofnięcie przydziału stosu wątku, odłącza wszystkie biblioteki dll, dołączone do wątku i usuwa obiekt ciągu z pamięci.

`AfxEndThread` Musi być wywołana z wewnątrz wątku, który ma zostać zakończony. Jeśli chcesz zakończyć wątek z innego wątku, należy skonfigurować metodę komunikacji pomiędzy dwoma wątkami.

##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> Pobieranie kodu wyjścia wątku

Aby uzyskać kod zakończenia pracownika lub wątku interfejsu użytkownika, wywołaj [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) funkcji. Aby uzyskać informacji na temat tej funkcji zobacz zestaw Windows SDK. Ta funkcja pobiera uchwyt do wątku (przechowywany w `m_hThread` element członkowski danych `CWinThread` obiekty) i adres DWORD.

Jeśli wątek jest nadal aktywne `GetExitCodeThread` umieszcza STILL_ACTIVE w podany adres DWORD; w przeciwnym razie kod wyjścia jest umieszczany w tym adresie.

Trwa pobieranie kodu wyjścia [CWinThread](../mfc/reference/cwinthread-class.md) obiektów wymaga dodatkowego kroku. Domyślnie gdy `CWinThread` wątek kończy działanie, obiekt wątku jest usuwany. Oznacza to, nie masz dostępu do `m_hThread` element członkowski danych ponieważ `CWinThread` obiekt nie istnieje. Aby uniknąć tej sytuacji, wykonaj jedną z następujących czynności:

- Ustaw `m_bAutoDelete` element członkowski danych na wartość FALSE. Dzięki temu `CWinThread` obiektu przetrwać po wątek został zakończony. Mogą uzyskiwać dostęp do `m_hThread` element członkowski danych po zakończeniu wątku. Jeśli używasz tej techniki, jednak odpowiedzialność za zniszczenie `CWinThread` obiektu, ponieważ struktura nie automatycznie usunie ją dla Ciebie. Jest to preferowana metoda.

- Store uchwyt wątku oddzielnie. Po utworzeniu wątku, należy skopiować jego `m_hThread` element członkowski danych (za pomocą `::DuplicateHandle`) do innej zmiennej i uzyskać do niego dostęp za pośrednictwem tej zmiennej. W ten sposób obiekt jest automatycznie usuwany kiedy następuje koniec i możesz wciąż dowiedzieć się dlaczego wątek się zakończył. Należy zachować ostrożność, że wątek nie skończył się, zanim będzie można zduplikować dojście. Najbezpieczniejszy sposób, w tym celu służy do przekazywania CREATE_SUSPENDED do [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), Przechowaj uchwyt, a następnie Wznów wątek wywołując [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).

Każda z tych metod pozwala określić dlaczego `CWinThread` obiekt został zakończony.

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread)