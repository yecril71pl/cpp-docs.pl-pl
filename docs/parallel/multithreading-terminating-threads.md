---
title: 'Wielowątkowość: przerywanie wątków w MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 60c60d1aedf19ade6c84dafacd7de7a2e650e6ca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446272"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>Wielowątkowość: przerywanie wątków w MFC

Dwie normalne sytuacje powodują zakończenie wątku: funkcja kontrolująca kończy działanie lub wątek nie może działać do ukończenia. Jeśli procesor programu Word użył wątku do drukowania w tle, funkcja kontrolowania zostanie zakończona normalnie, Jeśli drukowanie zakończyło się pomyślnie. Jeśli użytkownik chce anulować drukowanie, należy przedwcześnie zakończyć wątek drukowania w tle. W tym temacie wyjaśniono, jak zaimplementować każdą sytuację i jak uzyskać kod zakończenia wątku po jego zakończeniu.

- [Normalne zakończenie wątku](#_core_normal_thread_termination)

- [Przedwczesne zakończenie wątku](#_core_premature_thread_termination)

- [Pobieranie kodu zakończenia wątku](#_core_retrieving_the_exit_code_of_a_thread)

## <a name="_core_normal_thread_termination"></a>Normalne zakończenie wątku

W przypadku wątku roboczego normalne zakończenie wątku jest proste: zamyka funkcję kontroli i zwraca wartość, która oznacza przyczynę zakończenia. Można użyć funkcji [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) lub instrukcji **Return** . Zazwyczaj 0 oznacza pomyślne zakończenie, ale jest to konieczne.

W przypadku wątku interfejsu użytkownika proces jest równie prosty: z poziomu wątku interfejsu użytkownika, wywołaj [PostQuitMessage](/windows/win32/api/winuser/nf-winuser-postquitmessage) w Windows SDK. Jedynym parametrem, który przyjmuje `PostQuitMessage` jest kod zakończenia wątku. Podobnie jak w przypadku wątków roboczych, 0 zazwyczaj oznacza pomyślne zakończenie.

## <a name="_core_premature_thread_termination"></a>Przedwczesne zakończenie wątku

Przedwczesne zakończenie wątku jest niemal proste: Wywołaj [AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) z wewnątrz wątku. Przekaż żądany kod zakończenia jako jedyny parametr. Spowoduje to zatrzymanie wykonywania wątku, oddzielenie stosu wątku, odłączenie wszystkich bibliotek DLL dołączonych do wątku i usunięcie obiektu wątku z pamięci.

Aby można było zakończyć, `AfxEndThread` musi być wywołana z poziomu wątku. Jeśli chcesz przerwać wątek z innego wątku, należy skonfigurować metodę komunikacji między dwoma wątkami.

## <a name="_core_retrieving_the_exit_code_of_a_thread"></a>Pobieranie kodu zakończenia wątku

Aby uzyskać kod zakończenia procesu roboczego lub wątku interfejsu użytkownika, wywołaj funkcję [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread) . Aby uzyskać informacje na temat tej funkcji, zobacz Windows SDK. Ta funkcja pobiera dojście do wątku (przechowywanego w elemencie członkowskim danych `m_hThread` obiektów `CWinThread`) i adres typu DWORD.

Jeśli wątek jest nadal aktywny, `GetExitCodeThread` umieszcza STILL_ACTIVE w podanym adresie DWORD; w przeciwnym razie kod zakończenia zostanie umieszczony w tym adresie.

Pobieranie kodu zakończenia obiektów [CWinThread](../mfc/reference/cwinthread-class.md) wykonuje dodatkowy krok. Domyślnie po zakończeniu `CWinThread` wątku obiekt wątku jest usuwany. Oznacza to, że nie można uzyskać dostępu do elementu członkowskiego danych `m_hThread`, ponieważ obiekt `CWinThread` już nie istnieje. Aby uniknąć tej sytuacji, wykonaj jedną z następujących czynności:

- Ustaw element członkowski danych `m_bAutoDelete` na wartość FALSE. Umożliwia to przejściu obiektu `CWinThread` po zakończeniu wątku. Następnie można uzyskać dostęp do elementu członkowskiego danych `m_hThread` po zakończeniu wątku. W przypadku korzystania z tej techniki, użytkownik jest odpowiedzialny za zniszczenie obiektu `CWinThread`, ponieważ struktura nie usunie go automatycznie. Jest to preferowana metoda.

- Przechowuj dojście wątku osobno. Po utworzeniu wątku skopiuj jego element członkowski danych `m_hThread` (przy użyciu `::DuplicateHandle`) do innej zmiennej i uzyskaj do niego dostęp za pośrednictwem tej zmiennej. W ten sposób obiekt jest automatycznie usuwany po zakończeniu działania i można nadal dowiedzieć się, dlaczego wątek został przerwany. Należy zachować ostrożność, aby wątek nie przerywał działania przed duplikowaniem dojścia. Najbezpieczniejszym sposobem jest przekazanie CREATE_SUSPENDED do [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), przechowanie uchwytu, a następnie wznowienie wątku przez wywołanie [ResumeThread](../mfc/reference/cwinthread-class.md#resumethread).

Każda z tych metod pozwala określić, dlaczego obiekt `CWinThread` został przerwany.

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread —](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)
