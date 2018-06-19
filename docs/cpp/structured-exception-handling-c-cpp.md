---
title: (C/C++) Obsługa wyjątków strukturalnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5b6aafa91ecfde27cc38cccc52f36af43ad21ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32424273"
---
# <a name="structured-exception-handling-cc"></a>Obsługa wyjątków strukturalnych (C/C++)
Chociaż system Windows i program Visual C++ obsługuje (SEH) do obsługi wyjątków strukturalnych, zalecane jest użycie normy ISO Obsługa wyjątków języka C++ ponieważ sprawia, że kod bardziej przenośne i elastyczne. Niemniej jednak w istniejącym kodzie lub konkretnej rodzaje programów, użytkownik nadal może być konieczne użycie SEH.  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
  
## <a name="grammar"></a>Gramatyka  
 *instrukcji z wyjątkiem try* :  
  
 `__try` *złożone — instrukcja*  
  
 `__except` ( `expression` ) *złożonej instrukcji*  
  
## <a name="remarks"></a>Uwagi  
 Z SEH można zapewnić, że zasoby, takie jak bloki pamięci i pliki są poprawnie Jeśli wykonanie następuje nieoczekiwane zakończenie. Można również obsługiwać określonych problemów — na przykład za mało pamięci — przy użyciu zwięzły strukturalny, które nie korzystają z `goto` instrukcji lub testowania złożonych kodów powrotnych.  
  
 Try-except i try-finally deklaracji określonych w tym artykule są rozszerzenia Microsoft do języka C. Obsługują one SEH, umożliwiając aplikacji przejąć kontrolę nad program po zdarzenia, które w przeciwnym razie spowoduje przerwanie wykonywania. Chociaż SEH działa zawierający pliki źródłowe C++, jego jest nie zaprojektowane specjalnie dla języka C++. Jeśli używasz programu C++ skompilować przy użyciu SEH [/EH](../build/reference/eh-exception-handling-model.md) opcji — wraz z niektórych Modyfikatory — zostaną wywołane destruktory dla obiektów lokalnego, ale inne sposób wykonywania nie może być oczekiwań. (Ilustrację, zobacz przykład w dalszej części tego artykułu). W większości przypadków, zamiast SEH firma Microsoft zaleca użycie normy ISO [C++, obsługa wyjątków](../cpp/try-throw-and-catch-statements-cpp.md), który obsługuje również Visual C++. Za pomocą C++, obsługa wyjątków, można Sprawdź, czy kod jest przenośną, i może obsłużyć wyjątki dowolnego typu.  
  
 Jeśli masz modułów C, które używają SEH można łączyć je z modułami C++ tego użycia C++, obsługa wyjątków. Aby uzyskać informacje, zobacz [różnice obsługi wyjątków](../cpp/exception-handling-differences.md).  
  
 Istnieją dwa mechanizmy SEH:  
  
-   [Programy obsługi wyjątków](../cpp/writing-an-exception-handler.md), które odpowiadają na, lub odrzucić wyjątek.  
  
-   [Programy obsługi zakończenia](../cpp/writing-a-termination-handler.md), które są nazywane, gdy wyjątek powoduje przerwanie w bloku kodu.  
  
 Te dwa rodzaje programów obsługi są różne, ale są ściśle powiązane za pośrednictwem procesu nazywanego "odwijanie stosu." Po wystąpieniu wyjątku, system Windows wyszukuje niedawno zainstalowany program obsługi wyjątku, który jest obecnie aktywny. Program obsługi można wykonać jedną z trzech zdarzeń:  
  
-   Nie można rozpoznać wyjątek i przekazanie sterowania do innych programów obsługi.  
  
-   Rozpoznaje wyjątek, ale je zamknąć.  
  
-   Rozpoznaje wyjątek, a jego obsługa.  
  
 Program obsługi wyjątku, który rozpoznaje wyjątku nie może być w funkcję, która była uruchomiona w chwili Wystąpił wyjątek. W niektórych przypadkach może być znacznie wyższa na stosie funkcji. Funkcja aktualnie uruchomione i inne funkcje w ramce stosu są zakończone. W trakcie tego procesu stos jest "oddzielić;" oznacza to, że zmienne lokalne funkcji zakończone — o ile nie są one `static`— zostały wyczyszczone ze stosu.  
  
 Zgodnie z jego cofa stosu, system operacyjny wywołuje programy obsługi zakończenia, które zostały napisane dla każdej funkcji. Za pomocą programu obsługi zakończenia, możesz wyczyścić zasoby, które w przeciwnym razie pozostanie otwarty z powodu przerwania pracy. Jeśli wprowadzono sekcja krytyczna, możesz zakończyć działanie programu obsługi zakończenia. Jeżeli program będzie można zamknąć, można wykonywać inne zadania celów, takich jak zamykania i usuwanie plików tymczasowych.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)  
  
-   [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)  
  
-   [Korzystanie z obsługi wyjątków strukturalnych za pomocą języka C++](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## <a name="example"></a>Przykład  
 Jak wspomniano wcześniej, destruktory dla lokalnych obiektów są nazywane, jeśli używasz SEH programu C++ i skompiluj go za pomocą **/EH** opcji z niektórych Modyfikatory — na przykład **/ehsc** i   **/eha**. Jednak w zachowanie podczas wykonywania oczekiwać Jeśli używane są również wyjątki C++ nie może być. W poniższym przykładzie pokazano te różnice funkcjonalne.  
  
```cpp  
#include <stdio.h>  
#include <Windows.h>  
#include <exception>  
  
class TestClass  
{  
public:  
    ~TestClass()  
    {  
        printf("Destroying TestClass!\r\n");  
    }  
};  
  
__declspec(noinline) void TestCPPEX()  
{  
#ifdef CPPEX  
    printf("Throwing C++ exception\r\n");  
    throw std::exception("");  
#else  
    printf("Triggering SEH exception\r\n");  
    volatile int *pInt = 0x00000000;  
    *pInt = 20;  
#endif  
}  
  
__declspec(noinline) void TestExceptions()  
{  
    TestClass d;  
    TestCPPEX();  
}  
  
int main()  
{  
    __try  
    {  
        TestExceptions();  
    }  
    __except(EXCEPTION_EXECUTE_HANDLER)  
    {  
        printf("Executing SEH __except block\r\n");  
    }  
  
    return 0;  
}  
  
```  
  
 Jeśli używasz **/ehsc** skompilować ten kod, ale formant lokalnego testu `CPPEX` jest niezdefiniowana, nie istnieje żadne wykonywanie `TestClass` destruktor i dane wyjściowe wygląda podobnie do następującej:  
  
```Output  
Triggering SEH exception  
Executing SEH __except block  
```  
  
 Jeśli używasz **/ehsc** skompilować kod i `CPPEX` jest definiowana za pomocą `/DCPPEX` (dzięki czemu jest zgłaszany wyjątek języka C++), `TestClass` wykonuje destruktor i dane wyjściowe wyglądają następująco:  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 Jeśli używasz **/eha** skompilować kod, `TestClass` destruktora wykonuje niezależnie od tego, czy wyjątek został zgłoszony przy użyciu `std::throw` lub za pomocą SEH do wyzwolenia wyjątek (`CPPEX` określone lub nie). Dane wyjściowe wyglądają następująco:  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md).  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [\<wyjątku >](../standard-library/exception.md)   
 [Błędy w obsłudze wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [(System Windows) do obsługi wyjątków strukturalnych](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)