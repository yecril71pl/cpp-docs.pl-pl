---
title: (C/C++) obsługi wyjątków strukturalnych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1edcf2cb24273f475b1ba98e5e973f5704c0cec8
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461705"
---
# <a name="structured-exception-handling-cc"></a>Obsługa wyjątków strukturalnych (C/C++)
Chociaż Windows i Visual C++ obsługi wyjątków strukturalnych (SEH) obsługi, zaleca się używać ISO standard C++ obsługi wyjątków, ponieważ dzięki niej kod jest bardziej przenośny i elastyczny. Niemniej jednak w istniejącym kodzie lub dla szczególnych typów programów możesz nadal może być konieczne używanie SEH.  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
  
## <a name="grammar"></a>Gramatyka  
 *instrukcji z wyjątkiem try* :  
  
 `__try` *Compound-statement*  
  
 `__except` ( `expression` ) *compound-statement*  
  
## <a name="remarks"></a>Uwagi  
 Z SEH można zagwarantować, że zasoby, takie jak bloki pamięci i pliki są poprawnie Jeśli wykonanie następuje nieoczekiwane zakończenie. Może również obsługiwać konkretnych problemów — na przykład brak wystarczającej ilości pamięci — przy użyciu zwięzłe ze strukturą kodu, które nie zależą od **goto** instrukcji lub rozbudowane testowania kody powrotne.  
  
 Try-except i try-finally, określone w tym artykule są rozszerzenia Microsoft do języka C. Obsługiwane są też SEH, dzięki czemu aplikacje mogą przejąć kontrolę nad programem po zdarzenia, które w przeciwnym razie zakończy się wykonywanie. Mimo że SEH działa przy użyciu plików źródłowych języka C++, go nie opracowano specjalnie dla języka C++. Jeśli używasz strukturalnej obsługi wyjątków w programie C++, który kompilujesz przy użyciu [/EH](../build/reference/eh-exception-handling-model.md) opcji — wraz z niektórych Modyfikatory — destruktory obiektów lokalnych są wywoływane, ale inne zachowanie wykonywania może nie być, czego oczekiwać. (Ilustrację, zobacz przykład w dalszej części tego artykułu). W większości przypadków zamiast SEH firma Microsoft zaleca użycie ISO standard [obsługi wyjątków C++](../cpp/try-throw-and-catch-statements-cpp.md), który obsługuje również Visual C++. Korzystając z obsługi wyjątków C++, można upewnić się, że Twój kod będzie bardziej przenośny i może obsługiwać wyjątki dowolnego typu.  
  
 W przypadku modułów języka C, które SEH należy używać można łączyć je z modułami C++ tej obsługi wyjątków C++ użycia. Aby uzyskać informacje, zobacz [różnice w obsłudze wyjątków](../cpp/exception-handling-differences.md).  
  
 Istnieją dwa mechanizmy strukturalnej obsługi wyjątków:  
  
-   [Programy obsługi wyjątków](../cpp/writing-an-exception-handler.md), które można odpowiedzieć na lub odrzucać wyjątek.  
  
-   [Programy obsługi zakończenia](../cpp/writing-a-termination-handler.md), które są wywoływane, gdy wyjątek powoduje przerwanie w bloku kodu.  
  
 Te dwa rodzaje obsługi różniące się od siebie, ale są ściśle powiązane przez proces ten jest znany jako "odwijania stosu." Gdy wystąpi wyjątek, Windows wyszukuje ostatnio zainstalowane obsługi wyjątków, który jest obecnie aktywny. Program obsługi, można wykonać jedną z trzech zdarzeń:  
  
-   Nie można rozpoznać wyjątek i przekazać sterowanie do innych programów obsługi.  
  
-   Rozpoznaje wyjątek, ale je zamknąć.  
  
-   Rozpoznaje wyjątek, a następnie go obsłużyć.  
  
 Program obsługi wyjątku, który rozpoznaje wyjątek, może nie być w funkcji, która była uruchomiona w chwili wystąpienia wyjątku. W niektórych przypadkach może być w funkcji znacznie wyższa na stosie. Aktualnie uruchomionej funkcji i innych funkcji na ramce stosu są kończone. W trakcie tego procesu stos jest "rozwinięty"; oznacza to, zmiennych lokalnych funkcji zakończone — chyba że są one **statyczne**— są usuwane ze stosu.  
  
 Zgodnie z jego rozwija stos, system operacyjny wywołuje programy obsługi zakończenia, które zostały napisane dla każdej funkcji. Za pomocą programu obsługi zakończenia, możesz wyczyścić zasoby, które w przeciwnym razie mogłyby pozostają otwarte, jeśli ze względu na Nienormalne zakończenie. Jeśli zostały wprowadzone sekcję krytyczną, możesz wyjść programu obsługi zakończenia. Jeśli program będzie zamknięty, można wykonywać inne zadania celów, takich jak zamknięcie i usuwanie plików tymczasowych.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)  
  
-   [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)  
  
-   [Korzystanie z obsługi wyjątków strukturalnych za pomocą języka C++](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## <a name="example"></a>Przykład  
 Jak wspomniano wcześniej, destruktory dla obiektów lokalnych są wywoływane, jeśli SEH należy używać w programie C++ i skompiluj go za pomocą `/EH` opcji z niektórych Modyfikatory — na przykład `/EHsc` i `/EHa`. Jednakże zachowanie podczas wykonywania może nie być, oczekują Jeśli używane są również wyjątki C++. W poniższym przykładzie pokazano te różnice w zachowaniu.  
  
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
  
 Jeśli używasz **/ehsc** skompilować ten kod, ale kontroli lokalnego testu `CPPEX` jest niezdefiniowana, istnieje nie wykonywania `TestClass` destruktor i dane wyjściowe wyglądają podobnie do następującego:  
  
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
  
 Jeśli używasz **/eha** do kompilowania kodu, `TestClass` destruktor jest wykonywany niezależnie od tego, czy wyjątek został zgłoszony za pomocą `std::throw` lub za pomocą wyzwalacza wyjątek SEH (`CPPEX` zdefiniowany lub nie). Dane wyjściowe wyglądają następująco:  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md).  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [\<wyjątku >](../standard-library/exception.md)   
 [Błędy w obsłudze wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [(Windows) do obsługi wyjątków strukturalnych](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)