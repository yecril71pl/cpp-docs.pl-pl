---
title: "Błędy i obsługa wyjątków (Modern C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5b1ee1c7307f4e19db4ca0b7d03e218b0916538c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="errors-and-exception-handling-modern-c"></a>Błędy w obsłudze wyjątków (Modern C++)
W nowoczesnych wersji języka C++, w większości przypadków preferowany sposób raportu i obsługiwać zarówno błędów logicznych i błędów czasu wykonywania jest używać wyjątków. Dotyczy to zwłaszcza stosu może zawierać kilka wywołania funkcji między funkcję, która wykrywa błąd i funkcji, która ma kontekstu wiedzieć, jak je obsłużyć. Wyjątki umożliwiają formalne, dobrze zdefiniowany kod, który wykryje błędy do przekazywania informacji w górę stosu wywołań.  
  
 Błędy programu zazwyczaj są podzielone na dwie kategorie: błędy logiki, które są spowodowane programowania błędów, na przykład, błąd "indeks poza zakresem" i błędy środowiska wykonawczego, które są poza kontrolą programisty, na przykład "usługi sieciowej niedostępna" Wystąpił błąd. Raportowanie błędów jest zarządzany w stylu języka C programowania i w modelu COM, zwracając wartość, która reprezentuje kod błędu lub kod stanu dla określonej funkcji lub przez ustawienie zmiennej globalnej, który element wywołujący może opcjonalnie pobrać po co wywołanie funkcji, aby wyświetlić Określa, czy zostały zgłoszone błędy. Na przykład programowania COM używa zwracana wartość HRESULT do komunikowania się błędy do obiektu wywołującego, i interfejs API Win32 ma Funkcja GetLastError można pobrać ostatniego błędu, który został zgłoszony przez stos wywołań. W obu przypadkach to obiekt wywołujący, aby rozpoznać kodu i reagowania do niego. Jeśli element wywołujący nie obsługuje jawnie kodu błędu, program może ulec awarii bez ostrzeżenia lub nadal wykonywane za pomocą nieprawidłowych danych i prowadzić do niepoprawnych wyników.  
  
 Wyjątki są preferowane w nowoczesnych wersji języka C++ z następujących powodów:  
  
-   Wystąpił wyjątek wymusza kod wywołujący do rozpoznania warunek błędu i jego obsługa. Nieobsługiwane wyjątki zatrzymania wykonywania programu.  
  
-   Wystąpił wyjątek przechodzi do punktu w stosie wywołań, jaką może obsłużyć błąd. Funkcje pośredniego pozwolić propagowanie wyjątku. Nie mają do zapewnienia koordynacji z innych warstw.  
  
-   Mechanizm odwijanie stosu wyjątków niszczy wszystkich obiektów w zakresie zgodnie z regułami dobrze zdefiniowany po jest zgłaszany wyjątek.  
  
-   Wystąpił wyjątek umożliwia czyste rozdzielenie kod, który wykryje błąd i kod, który obsługuje błąd.  
  
 Poniższy przykład uproszczony przedstawia składni konieczne zgłaszanie i przechwytywanie wyjątków w języku C++.  
  
```cpp  
#include <stdexcept>  
#include <limits>  
#include <iostream>  
  
using namespace std;  
class MyClass  
{  
public:  
   void MyFunc(char c)  
   {  
      if(c < numeric_limits<char>::max())  
         throw invalid_argument("MyFunc argument too large.");  
      //...  
   }  
};  
  
int main()  
{  
   try  
   {  
      MyFunc(256); //cause an exception to throw  
   }  
  
   catch(invalid_argument& e)  
   {  
      cerr << e.what() << endl;  
      return -1;  
   }  
   //...  
   return 0;  
}  
  
```  
  
 Przypomina wyjątków w języku C++ w językach takich jak C# i Java. W `try` zablokować, jeśli wyjątek jest *zgłoszony* będzie *przechwycono* przez pierwszy skojarzone `catch` blok, którego typ jest zgodna z wersją wyjątku. Innymi słowy, wykonanie przechodzi z `throw` instrukcji `catch` instrukcji. Jeśli zostanie znaleziony nie bloku catch można używać, `std::terminate` jest wywoływany i wyjście z programu. W języku C++ może zostać zgłoszony dowolnego typu; jednak zaleca się generowanie typ, który pochodzi bezpośrednio lub pośrednio z `std::exception`. W poprzednim przykładzie typ wyjątku [invalid_argument —](../standard-library/invalid-argument-class.md), jest zdefiniowany w standardowej bibliotece w [ \<stdexcept — >](../standard-library/stdexcept.md) pliku nagłówka. C++ nie udostępnia i nie wymaga `finally` bloku, aby upewnić się, że wszystkie zasoby są zwalniane, jeśli wyjątek. Nabycie zasobów jest idiom inicjowania (RAII), która używa wskaźniki inteligentne, udostępnia funkcje wymagane dla oczyszczania zasobu. Aby uzyskać więcej informacji, zobacz [porady: Projektowanie pod kątem bezpieczeństwa wyjątków](../cpp/how-to-design-for-exception-safety.md). Informacje o mechanizm odwijanie stosu C++, zobacz [wyjątki i Odwijaniem stosu](../cpp/exceptions-and-stack-unwinding-in-cpp.md).  
  
## <a name="basic-guidelines"></a>Podstawowe wskazówki  
 Niezawodna obsługa tego błędu jest trudna w dowolnym języku programowania. Chociaż wyjątki zapewnia kilka funkcji, które obsługują dobrej obsługi błędów, one nie może wykonać całą pracę dla Ciebie. Aby wykorzystać zalety mechanizm wyjątków, pamiętać wyjątków podczas projektowania kodu.  
  
-   Użyj potwierdza, aby wyszukać błędy, które nigdy nie powinno wystąpić. Użyj wyjątki, aby sprawdzić błędy, które mogą wystąpić, na przykład błędy sprawdzania poprawności danych wejściowych na parametry funkcji publicznych. Aby uzyskać więcej informacji, zobacz sekcji **vs wyjątków. Potwierdzenia**.  
  
-   Użyj wyjątków, jeśli kod obsługujący ten błąd może być oddzielony od kod, który wykryje błąd co najmniej jeden pośredniczące wywołania funkcji. Należy rozważyć, czy używać kody błędów zamiast tego w pętli wydajności o znaczeniu krytycznym, gdy kod obsługujący ten błąd jest sprzężona ściśle do kodu, który wykryje. 
  
-   Dla każdej funkcji, która może zgłosić lub propagowanie wyjątku, podaj jeden z gwarancje trzy wyjątek: silnej gwarancji, podstawowe gwarancji lub gwarancji nothrow (noexcept). Aby uzyskać więcej informacji, zobacz [porady: Projektowanie pod kątem bezpieczeństwa wyjątków](../cpp/how-to-design-for-exception-safety.md).  
  
-   Zgłaszanie wyjątków według wartości, catch ich przez odwołanie. Nie catch nie może obsłużyć. 
  
-   Nie używaj specyfikacje wyjątków, które zostały uznane za przestarzałe w języku C ++ 11. Aby uzyskać więcej informacji, zobacz sekcji **specyfikacje wyjątków i noexcept**.  
  
-   Standardowa biblioteka typów wyjątków należy użyć, gdy mają one zastosowanie. Pochodzi typów wyjątków niestandardowych z [wyjątek klasy](../standard-library/exception-class.md) hierarchii.  
  
-   Nie zezwalaj na wyjątki, aby wyjść z destruktory lub pamięci — funkcje cofania alokacji.  
  
## <a name="exceptions-and-performance"></a>Wyjątki i wydajności  
 Mechanizm wyjątków ma minimalne wydajność, jeśli nie jest wyjątek. Jeśli wyjątek koszty przechodzenie stosu i odwijaniem jest porównywalna około koszt wywołania funkcji. Dodatkowe dane struktury są wymagane do śledzenia stosu wywołań po `try` bloku została wprowadzona, oraz dodatkowe instrukcje są wymagane do operacji unwind stosu, jeśli jest zgłaszany wyjątek. Jednak w większości przypadków koszt wydajność i zużycie pamięci nie ma znaczenia. Niekorzystny wpływ wyjątków na wydajność jest prawdopodobnie znaczący tylko w systemach bardzo ograniczone pamięci lub w wydajności krytyczne pętli którym błąd prawdopodobnie wykonywane są regularnie i kod, aby jego obsługa jest ściśle powiązane do kodu, który zgłasza. W każdym przypadku jest niemożliwe znać rzeczywistej wartości wyjątki bez profilowania i pomiaru. Nawet w rzadkich przypadkach, gdy koszt jest istotne, możesz można porównać ją przed poprawność zwiększona, ułatwia utrzymanie i inne korzyści zapewniane przez zasadę dobrze zaprojektowanego wyjątek.  
  
## <a name="exceptions-vs-assertions"></a>Wyjątki, a potwierdzenia  
 Wyjątki i potwierdzeń są dwa różne mechanizmy wykrywanie błędów czasu wykonywania w programie. Użyj deklaracji rozkazujących do testowania dla warunków podczas projektowania, które nigdy nie powinien mieć wartość PRAWDA, jeśli cały kod jest poprawny. Nie ma żadnych punktu obsługi takiego błędu przy użyciu wyjątek, ponieważ błąd oznacza, że coś w kodzie ma, należy naprawić w i nie zawiera warunek, który zawiera program pozwoli na odzyskanie w czasie wykonywania. Assert zatrzymuje wykonywanie w instrukcji, aby sprawdzić stan programu w debugerze; Wystąpił wyjątek kontynuuje wykonywanie z pierwszego programu obsługi catch odpowiednie. Użyj wyjątki, aby sprawdzić błędy, które mogą wystąpić w czasie wykonywania, nawet jeśli kod jest poprawny, na przykład "nie można odnaleźć pliku" lub "za mało pamięci." Można odzyskać z tych warunków, nawet jeśli odzyskiwanie po prostu wysyła komunikat do dziennika i kończy się program. Sprawdzać argumentów do funkcji publiczny za pomocą wyjątków. Nawet jeśli funkcja jest wolny od błędów, nie masz pełną kontrolę nad argumenty, które użytkownik może przekazać do niego.  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Wyjątki C++ i wyjątki SEH systemu Windows  
 Programy zarówno C i C++ mogą używać wyjątków strukturalnych obsługę mechanizmem (SEH) w systemie operacyjnym Windows. Pojęcia związane z SEH przypomina w wyjątków języka C++ z tą różnicą, że używa SEH `__try`, `__except`, i `__finally` tworzy zamiast `try` i `catch`. W programie Visual C++ wyjątki C++ są zaimplementowane w przypadku SEH. Jednak podczas pisania kodu C++, należy użyć składni wyjątków C++.  
  
 Aby uzyskać więcej informacji na temat SEH, zobacz [strukturalnych obsługi wyjątków (C/C++)](../cpp/structured-exception-handling-c-cpp.md).  
  
## <a name="exception-specifications-and-noexcept"></a>Specyfikacje wyjątków i noexcept  
 Specyfikacje wyjątków zostały wprowadzone w języku C++ w sposób określenia wyjątki, które może zgłosić funkcji. Jednak specyfikacje wyjątków okazały powodować problemy w praktyce i zostały uznane za przestarzałe w standardzie C ++ 11 wersji roboczej. Firma Microsoft zaleca, nie używaj specyfikacje wyjątków z wyjątkiem `throw()`, co oznacza, że funkcja umożliwia bez wyjątków wyjść. Jeśli musisz użyć specyfikacje wyjątków typu `throw(` *typu*`)`, należy pamiętać, że Visual C++ wychodzi z standard w określony sposób. Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md). `noexcept` Specyfikator wprowadzono w języku C ++ 11 preferowanych alternatywę dla `throw()`.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: interfejs między kodem obsługi wyjątków a innym kodem](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
