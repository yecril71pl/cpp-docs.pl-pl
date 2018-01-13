---
title: "Wielowątkowość: Tworzenie wątków roboczych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94a047de82bebb03f681e1bfdf6f68d56554fe8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-creating-worker-threads"></a>Wielowątkowość: tworzenie wątków roboczych
Wątek roboczy jest najczęściej używany do obsługi zadań w tle, które użytkownik nie powinny mieć zaczekać, aby kontynuować korzystanie z aplikacji. Zadania, takie jak ponowne obliczenie i drukowanie w tle są dobrym przykładem wątków roboczych. W tym temacie opisano kroki niezbędne do utworzenia wątku roboczego. Tematy obejmują:  
  
-   [Uruchamianie wątku](#_core_starting_the_thread)  
  
-   [Implementowanie funkcji sterowania](#_core_implementing_the_controlling_function)  
  
-   [Przykład](#_core_controlling_function_example)  
  
 Utworzenie wątku roboczego jest zadaniem stosunkowo proste. Tylko dwa kroki są wymagane do pobrania z wątku uruchomiona: implementacja kontrolowanie funkcji i uruchamianie wątku. Nie jest konieczne wyprowadzenia klasy z [cwinthread —](../mfc/reference/cwinthread-class.md). Można wyprowadzenia klasy, jeśli potrzebujesz specjalnej wersji `CWinThread`, ale nie jest wymagane dla większości proste wątków. Można użyć `CWinThread` bez żadnych modyfikacji.  
  
##  <a name="_core_starting_the_thread"></a>Uruchamianie wątku  
 Istnieją dwie wersje przeciążone `AfxBeginThread`:, który można tworzyć tylko wątków roboczych, a taki, który może tworzyć wątków interfejsu użytkownika oraz wątków roboczych. Aby rozpocząć wykonywania z wątku roboczego przy użyciu pierwszego przeciążenia, należy wywołać [afxbeginthread —](../mfc/reference/application-information-and-management.md#afxbeginthread), podając następujące informacje:  
  
-   Adres funkcji sterowania.  
  
-   Parametr do przekazania do kontrolowania funkcji.  
  
-   (Opcjonalnie) Żądany priorytet wątku. Wartość domyślna to normalnym priorytecie. Aby uzyskać więcej informacji na temat poziomów priorytet dostępne w temacie [wykonanie funkcji SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
-   (Opcjonalnie) Rozmiar żądanego stosu wątku. Wartością domyślną jest tym samym stosie rozmiar jako Tworzenie wątku.  
  
-   (Opcjonalnie) **CREATE_SUSPENDED** Jeśli chcesz wątku, który ma zostać utworzony w stanie wstrzymania. Wartość domyślna to 0 lub normalnie uruchomienie wątku.  
  
-   (Opcjonalnie) Atrybuty wymaganymi. Wartość domyślna to te same prawa dostępu jako wątku nadrzędnej. Aby uzyskać więcej informacji na temat formatu informacji o zabezpieczeniach, zobacz [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread`Tworzy i inicjuje `CWinThread` obiektu, uruchamia go i zwraca jego adres, więc można odwołać się do niego później. Testy zostały wprowadzone w całej procedury upewnij się, że wszystkie obiekty są deallocated prawidłowo w przypadku dowolnej części Tworzenie nie.  
  
##  <a name="_core_implementing_the_controlling_function"></a>Implementowanie funkcji sterowania  
 Kontrolowanie funkcji definiuje wątku. Po wprowadzeniu tej funkcji, uruchamiania wątku, a po wydaniu, Wątek zostaje zakończony. Ta funkcja powinny mieć następujące prototypu:  
  
```  
UINT MyControllingFunction( LPVOID pParam );  
```  
  
 Parametr jest pojedynczą wartość. Wartość, którą otrzymuje funkcji w tym parametrze jest to wartość, który został przekazany do konstruktora, podczas tworzenia obiektu wątku. Kontrolowanie funkcji mogą interpretować tę wartość w żaden sposób, który wybiera. Może być traktowana jako wartość skalarną lub wskaźnik do struktury zawierającej wiele parametrów lub można go zignorować. Jeśli parametr odwołuje się do struktury, struktura można nie tylko do przekazywania danych z obiektu wywołującego w wątku, ale do przekazywania danych z wątku do obiektu wywołującego. Jeśli używasz takiej struktury do przekazywania danych z powrotem do wywołującego wątek musi powiadomić wywołującego, gdy wyniki są gotowe. Informacje o komunikacji z wątku roboczego do elementu wywołującego, zobacz [Multithreading: Programowanie porady](../parallel/multithreading-programming-tips.md).  
  
 Gdy funkcja zakończenie, powinien on zwrócić **UINT** wskazujące przyczynę zakończenia. Zazwyczaj ten kod zakończenia to 0, informując o powodzeniu innych wartości wskazujący różnych typów błędów. Jest to czysto w zależy od implementacji. Niektóre wątki może obsługa liczniki zużycia obiektów i zwraca bieżącą liczbę używa tego obiektu. Aby dowiedzieć się, jak aplikacje mogą pobierać tę wartość, zobacz [Multithreading: przerywanie wątków](../parallel/multithreading-terminating-threads.md).  
  
 Istnieją pewne ograniczenia dotyczące co można zrobić w programie wielowątkowe napisany za pomocą biblioteki MFC. Aby uzyskać opis tych ograniczeń i inne porady dotyczące korzystania z wątków, zobacz [Multithreading: Programowanie porady](../parallel/multithreading-programming-tips.md).  
  
##  <a name="_core_controlling_function_example"></a>Kontrolowanie przykład — funkcja  
 Poniższy przykład pokazuje, jak zdefiniować funkcję kontrolowanie i użyć go w innej części programu.  
  
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
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Wielowątkowość: tworzenie wątków interfejsu użytkownika](../parallel/multithreading-creating-user-interface-threads.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)