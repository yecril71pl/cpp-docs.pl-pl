---
title: 'Wielowątkowość: Tworzenie wątków interfejsu użytkownika MFC'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: e618f11e3c574e5f53dff150beeb313d26fd4a6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566832"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>Wielowątkowość: Tworzenie wątków interfejsu użytkownika MFC

Wątek interfejsu użytkownika jest często używane do obsługi danych wejściowych użytkownika i reagowania na zdarzenia użytkownika, niezależnie od wątków wykonywanie innych części aplikacji. Wątku głównego aplikacji (podany w swojej `CWinApp`-klasy pochodnej) jest już utworzona i uruchomiona za Ciebie. W tym temacie opisano kroki niezbędne do tworzenia wątków interfejsu użytkownika.

Pierwszą rzeczą, którą należy wykonać podczas tworzenia wątku interfejsu użytkownika jest wyprowadzić klasę z [CWinThread](../mfc/reference/cwinthread-class.md). Należy zadeklarować i zaimplementowania tej klasy przy użyciu [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) i [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) makra. Ta klasa należy zastąpić niektóre funkcje i mogą zastąpić inne osoby. W poniższej tabeli przedstawiono te funkcje i co należy zrobić.

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Funkcje, aby zastąpić podczas tworzenia wątku interfejsu użytkownika

|Funkcja|Cel|
|--------------|-------------|
|[Exitinstance —](../mfc/reference/cwinthread-class.md#exitinstance)|Oczyszczanie należy wykonać, gdy wątek kończy działanie. Zazwyczaj jest to przesłonić.|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|Wykonywanie inicjowania wystąpienia wątku. Musi zostać zastąpiona.|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|Wykonaj przetwarzanie w czasie bezczynności właściwe dla wątków. Nie zawsze zastąpiony.|
|[Pretranslatemessage —](../mfc/reference/cwinthread-class.md#pretranslatemessage)|Filtrowanie komunikatów przed ich wysłaniem do `TranslateMessage` i `DispatchMessage`. Nie zawsze zastąpiony.|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|Przechwycić nieobsługiwane wyjątki rzucane przez wątek wiadomości i procedury obsługi poleceń. Nie zawsze zastąpiony.|
|[Uruchom](../mfc/reference/cwinthread-class.md#run)|Funkcje kontroli wątku. Zawiera "pompy komunikatów". Rzadko zastąpiona.|

Biblioteka MFC zawiera dwie wersje `AfxBeginThread` za pomocą parametru przeciążenia: jedną, która tworzy tylko wątki robocze i taki, który można utworzyć wątki interfejsu użytkownika lub wątków roboczych. Aby uruchomić wątek interfejsu użytkownika, należy wywołać drugie przeciążenie [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), podając następujące informacje:

- [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) klasy pochodzące z `CWinThread`.

- (Opcjonalnie) Żądany priorytet. Wartością domyślną jest normalnym priorytecie. Aby uzyskać więcej informacji na temat dostępnych poziomów priorytetu, zobacz [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w zestawie Windows SDK.

- (Opcjonalnie) Żądany rozmiar stosu dla wątku. Wartość domyślna to taki sam jak rozmiar stosu wątku tworzącego.

- (Opcjonalnie) CREATE_SUSPENDED, jeśli chcesz, aby wątek był utworzony w stanie wstrzymania. Wartość domyślna jest równa 0 lub wątek uruchamia się normalnie.

- (Opcjonalnie) Atrybuty pożądanych zabezpieczeń. Wartość domyślna to taki sam dostęp jak wątku nadrzędnego. Aby uzyskać więcej informacji dotyczących formatu informacji o zabezpieczeniach, zobacz [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) w zestawie Windows SDK.

`AfxBeginThread` wykonuje większość pracy za Ciebie. Tworzy nowy obiekt klasy, inicjuje go przy użyciu informacji podasz i wywołania [CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread) można rozpocząć wykonywanie wątku. Kontrole są wprowadzane w trakcie trwania procedury upewnij się, że wszystkie obiekty są zdelokowane poprawnie w przypadku dowolnej części tworzenia nie.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Wielowątkowość: przerywanie wątków](multithreading-terminating-threads.md)

- [Wielowątkowość: tworzenie wątków roboczych](multithreading-creating-worker-threads.md)

- [Procesy i wątki](/windows/desktop/ProcThread/processes-and-threads)

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)