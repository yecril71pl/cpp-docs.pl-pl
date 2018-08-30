---
title: 'Wielowątkowość: Tworzenie wątków roboczych w MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1057d8992f6554d4d5fbbfd93b383e2ddd9dab53
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211640"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>Wielowątkowość: Tworzenie wątków roboczych w MFC
Wątek roboczy jest najczęściej używany do obsługi zadania w tle, które użytkownik nie powinien mieć zaczekać, aby kontynuować korzystanie z aplikacji. Zadania, takie jak ponowne obliczenie i drukowanie w tle są dobrym przykładem wątków roboczych. W tym temacie przedstawiono kroki niezbędne do utworzenia wątku roboczego. Tematy obejmują:  
  
- [Rozpoczęcie wątku](#_core_starting_the_thread)  
  
- [Implementacja funkcji kontroli](#_core_implementing_the_controlling_function)  
  
- [Przykład](#_core_controlling_function_example)  
  
Tworzenie wątku roboczego jest stosunkowo prostym zadaniem. Tylko dwie czynności, aby wątek działa: implementacja funkcji kontrolowania oraz Rozpoczęcie wątku. Nie jest konieczne, aby wyprowadzić klasę z [CWinThread](../mfc/reference/cwinthread-class.md). Możesz derywować klasę, jeżeli potrzebujesz specjalnej wersji `CWinThread`, ale nie jest wymagane dla większości prostych wątków roboczych. Możesz użyć `CWinThread` bez żadnych modyfikacji.  
  
##  <a name="_core_starting_the_thread"></a> Rozpoczęcie wątku  
 
Istnieją dwie przeciążone wersje `AfxBeginThread`: jedną, która tworzy tylko wątki robocze oraz jedna, która może tworzyć wątki interfejsu użytkownika oraz wątki robocze. Aby rozpocząć wykonywanie wątku roboczego, z użyciem pierwszego przeciążenia, wywołaj [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), podając następujące informacje:  
  
- Adres początkowy funkcji kontroli.  
  
- Parametr do przekazania do funkcji kontroli.  
  
- (Opcjonalnie) Żądany priorytet wątku. Wartością domyślną jest normalnym priorytecie. Aby uzyskać więcej informacji na temat dostępnych poziomów priorytetu, zobacz [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w zestawie Windows SDK.  
  
- (Opcjonalnie) Żądany rozmiar stosu dla wątku. Wartość domyślna to taki sam jak rozmiar stosu wątku tworzącego.  
  
- (Opcjonalnie) CREATE_SUSPENDED, jeśli chcesz, aby wątek był utworzony w stanie wstrzymania. Wartość domyślna jest równa 0 lub wątek uruchamia się normalnie.  
  
- (Opcjonalnie) Atrybuty pożądanych zabezpieczeń. Wartość domyślna to taki sam dostęp jak wątku nadrzędnego. Aby uzyskać więcej informacji dotyczących formatu informacji o zabezpieczeniach, zobacz [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) w zestawie Windows SDK.  
  
`AfxBeginThread` Tworzy i inicjuje `CWinThread` obiekt dla Ciebie, uruchomia go i zwraca jego adres, więc można odwołać się do niego później. Kontrole są wprowadzane w trakcie trwania procedury upewnij się, że wszystkie obiekty są zdelokowane poprawnie w przypadku dowolnej części tworzenia nie.  
  
##  <a name="_core_implementing_the_controlling_function"></a> Implementacja funkcji kontroli  
 
Funkcja kontrolowania definiuje wątek. Po wprowadzeniu tej funkcji, rozpoczyna się wątek, a kiedy wychodzi, wątek się kończy. Ta funkcja powinna mieć poniższy prototyp:  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
Parametr jest wartość typu single. Wartość otrzymywana przez funkcję w tym parametrze to wartość, która została przekazana do konstruktora, gdy został utworzony obiekt wątku. Funkcja kontroli może interpretować tę wartość w jakikolwiek sposób, który wybiera. Może być traktowana jako wartość skalarna lub wskaźnika do struktury zawierającej wiele parametrów lub można je zignorować. Jeśli parametr odnosi się do struktury, struktura może służyć nie tylko do przekazywania danych od elementu wywołującego do wątku, ale także do przekazywania danych powrotem od wątku do obiektu wywołującego. Jeśli używasz takiej struktury do przekazywania danych z powrotem do obiektu wywołującego, wątek musi powiadomić obiekt wywołujący, gdy wyniki są gotowe. Aby uzyskać informacje dotyczące komunikacji między wątkiem roboczym do obiektu wywołującego, zobacz [wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md).  
  
Kiedy funkcja kończy, powinna zwrócić UINT oznaczającą powód zakończenia. Zazwyczaj ten kod wyjścia to 0, informując o powodzeniu inne wartości oznaczają różne typy błędów. Jest to wyłącznie od implementacji zależy. Niektóre wątki mogą utrzymywać liczniki użycia obiektów i zwracać bieżącą liczbę zastosowań tego obiektu. Aby dowiedzieć się, jak aplikacje mogą odzyskiwać tę wartość, zobacz [wielowątkowość: Kończenie wątków](multithreading-terminating-threads.md).  
  
Istnieją pewne ograniczenia, co można zrobić w programie wielowątkowym napisane przy użyciu biblioteki MFC. Aby uzyskać opis tych ograniczeń i inne porady dotyczące korzystania z wątków, zobacz [wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md).  
  
##  <a name="_core_controlling_function_example"></a> Przykład funkcji sterowania  
 
Poniższy przykład pokazuje jak zdefiniować funkcję kontroli i używać jej z innej części programu.  
  
```  
UINT MyThreadProc( LPVOID pParam )  
{  
    CMyObject* pObject = (CMyObject*)pParam;  
  
    if (pObject == NULL ||  
        !pObject->IsKindOf(RUNTIME_CLASS(CMyObject)))  
    return 1;   // if pObject is not valid  
  
    // do something with 'pObject'  
  
    return 0;   // thread completed successfully  
}  
  
// inside a different function in the program  
.  
.  
.  
pNewObject = new CMyObject;  
AfxBeginThread(MyThreadProc, pNewObject);  
.  
.  
.  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?  
  
- [Wielowątkowość: tworzenie wątków interfejsu użytkownika](multithreading-creating-user-interface-threads.md)  
  
## <a name="see-also"></a>Zobacz też  
 
[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)