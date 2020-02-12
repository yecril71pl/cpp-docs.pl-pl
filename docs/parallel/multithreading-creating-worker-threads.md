---
title: 'Wielowątkowość: Tworzenie wątków roboczych w MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], worker threads
- background tasks [C++]
- threading [C++], worker threads
- worker threads [C++]
- threading [C++], creating threads
- threading [MFC], worker threads
- threading [C++], user input not required
ms.assetid: 670adbfe-041c-4450-a3ed-be14aab15234
ms.openlocfilehash: ab5b05b64ebcfbd6d15bd2229ee19d18fa7f919d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140515"
---
# <a name="multithreading-creating-worker-threads-in-mfc"></a>Wielowątkowość: Tworzenie wątków roboczych w MFC

Wątek roboczy jest często używany do obsługi zadań w tle, które użytkownik nie musi czekać, aby kontynuować korzystanie z aplikacji. Zadania, takie jak ponowne obliczanie i drukowanie w tle, są dobrymi przykładami wątków roboczych. W tym temacie opisano kroki niezbędne do utworzenia wątku roboczego. Tematy obejmują:

- [Uruchamianie wątku](#_core_starting_the_thread)

- [Implementowanie funkcji kontroli](#_core_implementing_the_controlling_function)

- [Przykład](#_core_controlling_function_example)

Tworzenie wątku roboczego jest stosunkowo prostym zadaniem. Do uruchomienia wątku są wymagane tylko dwa kroki: Implementowanie funkcji kontrolującej i uruchamianie wątku. Nie jest konieczne wyprowadzenie klasy z [CWinThread](../mfc/reference/cwinthread-class.md). Klasy można utworzyć, jeśli potrzebujesz specjalnej wersji `CWinThread`, ale nie jest to wymagane w przypadku większości prostych wątków roboczych. Możesz użyć `CWinThread` bez modyfikacji.

## <a name="_core_starting_the_thread"></a>Uruchamianie wątku

Istnieją dwie przeciążone wersje `AfxBeginThread`: te, które mogą tworzyć tylko wątki robocze, i takie, które mogą tworzyć wątki interfejsu użytkownika i wątki robocze. Aby rozpocząć wykonywanie wątku roboczego przy użyciu pierwszego przeciążenia, wywołaj [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), podając następujące informacje:

- Adres funkcji kontrolującej.

- Parametr, który ma zostać przesłany do funkcji kontrolującej.

- Obowiązkowe Żądany priorytet wątku. Wartość domyślna to normalny priorytet. Aby uzyskać więcej informacji na temat dostępnych poziomów priorytetów, zobacz [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) w Windows SDK.

- Obowiązkowe Żądany rozmiar stosu dla wątku. Wartość domyślna to ten sam stos rozmiaru co wątek tworzenia.

- Obowiązkowe CREATE_SUSPENDED, jeśli chcesz, aby wątek został utworzony w stanie wstrzymania. Wartość domyślna to 0 lub Uruchom wątek normalnie.

- Obowiązkowe Wymagane atrybuty zabezpieczeń. Wartość domyślna to ten sam dostęp co wątek nadrzędny. Aby uzyskać więcej informacji na temat formatu informacji o zabezpieczeniach, zobacz [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) w Windows SDK.

`AfxBeginThread` tworzy i inicjuje obiekt `CWinThread`, uruchamia go i zwraca swój adres, aby można było później odwołać się do niego. Kontrole są wykonywane w ramach procedury, aby upewnić się, że wszystkie obiekty są prawidłowo nieprzypisane, jeśli jakakolwiek część procesu tworzenia nie powiedzie się.

## <a name="_core_implementing_the_controlling_function"></a>Implementowanie funkcji kontroli

Funkcja kontrolująca definiuje wątek. Gdy ta funkcja zostanie wprowadzona, wątek rozpoczyna się, a kiedy kończy, wątek kończy. Ta funkcja powinna mieć następujący prototyp:

```cpp
UINT MyControllingFunction( LPVOID pParam );
```

Parametr jest pojedynczą wartością. Wartość odebrana przez funkcję w tym parametrze jest wartością, która została przeniesiona do konstruktora podczas tworzenia obiektu wątku. Funkcja kontrolowania może interpretować tę wartość w dowolny sposób. Może być traktowany jako wartość skalarna lub wskaźnik do struktury zawierającej wiele parametrów lub można go zignorować. Jeśli parametr odwołuje się do struktury, można użyć struktury nie tylko do przekazywania danych z obiektu wywołującego do wątku, ale również do przekazywania danych z wątku do obiektu wywołującego. Jeśli używasz takiej struktury do przekazywania danych z powrotem do obiektu wywołującego, wątek musi powiadomić obiekt wywołujący, gdy wyniki są gotowe. Aby uzyskać informacje o komunikacji między wątkiem roboczym a obiektem wywołującym, zobacz [wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md).

Po zakończeniu działania funkcja powinna zwrócić wartość UINT wskazującą przyczynę zakończenia. Zazwyczaj ten kod zakończenia ma wartość 0, aby wskazać sukces z innymi wartościami wskazującymi różne typy błędów. Jest to wyłącznie implementacja, która jest zależna od implementacji. Niektóre wątki mogą zachować liczbę obiektów użycia i zwrócić bieżącą liczbę zastosowań tego obiektu. Aby dowiedzieć się, jak aplikacje mogą pobrać tę wartość, zobacz [wielowątkowość: kończenie wątków](multithreading-terminating-threads.md).

Istnieją pewne ograniczenia dotyczące tego, co można zrobić w programie wielowątkowym zapisanym za pomocą biblioteki MFC. Opisy tych ograniczeń oraz inne porady dotyczące korzystania z wątków można znaleźć w temacie [wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md).

## <a name="_core_controlling_function_example"></a>Przykład kontroli funkcji

Poniższy przykład pokazuje, jak zdefiniować funkcję kontroli i użyć jej z innej części programu.

```cpp
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

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Wielowątkowość: tworzenie wątków interfejsu użytkownika](multithreading-creating-user-interface-threads.md)

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)
