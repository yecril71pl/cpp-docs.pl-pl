---
title: Błędy i obsłudze wyjątków (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9d9d21514b0ea90021c9b0543cd742ed6a6206f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407237"
---
# <a name="errors-and-exception-handling-modern-c"></a>Błędy w obsłudze wyjątków (Modern C++)
W nowoczesnym C++, w większości scenariuszy preferowanym sposobem raportowania i obsługi błędów logicznych oraz błędów środowiska uruchomieniowego jest skorzystanie z wyjątków. Jest to szczególnie istotne w przypadku, gdy stos może zawierać kilka wywołać funkcji między funkcją, która wykryje błąd i funkcję, która posiada kontekst pozwalający na jego obsługę. Wyjątki umożliwiają formalny, dobrze zdefiniowany kodowi wykrywającemu błędy przekazywanie informacji w górę stosu wywołań.  
  
 Błędy programu można ogólnie podzielić na dwie kategorie: Błędy logiczne, które są spowodowane przez błędy programowania, na przykład błąd "indeks poza zakresem" i błędy czasu wykonywania, które są poza kontrolą programisty, na przykład "Usługa sieciowa niedostępna" Wystąpił błąd. W programowaniu w stylu języka C oraz w COM raportowanie błędów jest zarządzane, zwracając wartość, która reprezentuje kod błędu lub kod stanu dla określonej funkcji lub przez ustawienie zmiennej globalnej, obiekt wywołujący mógł opcjonalnie pobrać po każdym wywołaniu funkcji, aby wyświetlić czy zostały zgłoszone błędy. Na przykład programowanie COM używa zwracanej wartości HRESULT do komunikowania się błędy do obiektu wywołującego, a Win32 API zawiera funkcję GetLastError, by odtworzyć ostatni błąd zgłoszony przez stos wywołań. W obu tych przypadkach jest od wywołującego zależy rozpoznanie kodu i odpowiadać na nie go odpowiednio. Jeśli obiekt wywołujący nie obsługuje jawnie kodu błędu, program może ulec awarii bez ostrzeżenia lub kontynuować wykonywanie złych danych i wygenerować niepoprawne wyniki.  
  
 Wyjątki są preferowane w nowoczesnym języku C++ z następujących powodów:  
  
-   Wyjątek wymusza, żeby kod wywołujący rozpoznał warunek błędu i obsługiwał go. Nieobsługiwane wyjątki zatrzymują wykonywanie programu.  
  
-   Wyjątek skacze do punktu w stos wywołań, który może obsłużyć błąd. Funkcje pośrednie mogą umożliwić propagowanie wyjątku. Nie muszą współgrać z innymi warstwami.  
  
-   Mechanizm odwracania stosu wyjątku niszczy wszystkie obiekty w zakresie zgodnie z regułami wyraźnie określonymi po zgłaszany jest wyjątek.  
  
-   Wyjątek umożliwia czystą separacji między kodem, który wykrywa błąd i kod, który obsłuży błąd.  
  
 Poniższy uproszczony przykład pokazuje składnię niezbędną dla tworzenia i przechwytywania wyjątków w języku C++.  
  
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
      if(c > numeric_limits<char>::max())  
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
  
 Wyjątki w języku C++ przypominają wyjątki w językach takich jak C# i Java. W **spróbuj** zablokować, jeśli wyjątek jest *zgłoszony* będzie *przechwycono* przez pierwszy związany **catch** blok, którego typ jest zgodny z typem wyjątek. Innymi słowy, wykonywanie przeskakuje z **throw** instrukcję, aby **catch** instrukcji. Jeśli zostanie znalezione nie bloku catch można używać, `std::terminate` jest wywoływany i program jest zamykany. W języku C++ można wygenerować dowolny typ; Jednak firma Microsoft zaleca generowanie typu, który pochodzi bezpośrednio lub pośrednio z `std::exception`. W poprzednim przykładzie, typ wyjątku [invalid_argument](../standard-library/invalid-argument-class.md), jest zdefiniowany w bibliotece standardowej w [ \<stdexcept >](../standard-library/stdexcept.md) pliku nagłówka. C++ nie udostępnia i nie wymaga **na koniec** bloku, aby upewnić się, że wszystkie zasoby są zwalniane, jeśli wyjątek jest zgłaszany. Pobieranie źródeł to idiom inicjalizacji (RAII), który wykorzystuje inteligentne wskaźniki, zapewnia wymaganą funkcję czyszczenia źródeł. Aby uzyskać więcej informacji, zobacz [porady: Projektowanie pod kątem bezpieczeństwa wyjątków](../cpp/how-to-design-for-exception-safety.md). Aby uzyskać informacje o mechanizmie odwracania stosu C++, zobacz [wyjątków i rozwijania stosu](../cpp/exceptions-and-stack-unwinding-in-cpp.md).  
  
## <a name="basic-guidelines"></a>Podstawowe wytyczne  
 Obsługa błędów grubych jest trudna w dowolnym języku programowania. Chociaż wyjątki zapewniają kilka funkcji, które obsługują dobrą obsługę błędów, nie mogą one wykonać całą pracę za Ciebie. Aby korzystać z zalet mechanizmu wyjątków, pamiętaj o wyjątkach Projektując kod.  
  
-   Użyj deklaracji rozkazujących pod kątem błędów, które nie powinny wystąpić nigdy. Użyj wyjątków, aby wyszukać błędy, które mogą wystąpić na przykład błędy w walidacji danych wejściowych na parametrach funkcji publicznych. Aby uzyskać więcej informacji, zobacz sekcję pod tytułem **vs wyjątków. Potwierdzenia**.  
  
-   Użyj wyjątków, kiedy kod obsługujący błąd może być oddzielony od kodu, który wykrywa błąd przez jeden lub więcej interweniujących wywołań funkcji. Rozważ, czy używać kodów błędów zamiast w pętli wydajność krytycznych, gdy kod, który obsłuży błąd jest sprzężona ściśle do kodu, który wykrywa go. 
  
-   Dla każdej funkcji, która może zgłosić lub propagować wyjątek, należy podać jedną z trzech gwarancji wyjątku: silną gwarancję, podstawową gwarancję lub gwarancję nothrow (noexcept). Aby uzyskać więcej informacji, zobacz [porady: Projektowanie pod kątem bezpieczeństwa wyjątków](../cpp/how-to-design-for-exception-safety.md).  
  
-   Wyzwalaj wątki według wartości, wyłapuj je przez odwołanie. Nie Złap, czego nie możesz obsłużyć. 
  
-   Nie używaj specyfikacji wyjątków, które zostały zaniechane w C ++ 11. Aby uzyskać więcej informacji, zobacz sekcję pod tytułem **specyfikacje wyjątku i noexcept**.  
  
-   Użyj standardowych typów wyjątków biblioteki, kiedy obowiązują. Uzyskania wyjątku niestandardowych typów z [wyjątek klasy](../standard-library/exception-class.md) hierarchii.  
  
-   Nie zezwalaj na wyjątki uciekały z destruktorów lub funkcji pamięć dezalokacji.  
  
## <a name="exceptions-and-performance"></a>Wyjątki i wydajność  
 Mechanizm wyjątku charakteryzuje się bardzo niewielkimi kosztem działania, jeśli jest zgłaszany żaden wyjątek. Jeśli wyjątek jest zgłaszany, koszty przechodzenia przez stos i rozwijania są w przybliżeniu porównywalne do kosztu wywołania funkcji. Struktury dodatkowe danych są wymagane do śledzenia stosu wywołań po **spróbuj** wprowadzeniu bloku i dodatkowe instrukcje są wymagane do odkręcanie stosu, jeśli zostanie zgłoszony wyjątek. Jednak w większości scenariuszy koszt w zakresie wydajności i zużycia pamięci nie ma znaczenia. Niekorzystny wpływ wyjątków na wydajność może być istotne tylko w systemach o bardzo ograniczonej pamięci lub w newralgicznym dla wydajności w pętli gdzie błąd prawdopodobnie będzie występować regularnie, a kod obsługujący jest ściśle powiązany kod, który go zgłasza. W każdym przypadku jest niemożliwe znać rzeczywisty koszt wyjątków bez profilowania i dokonywania pomiarów. Nawet w tych rzadkich przypadkach, gdy koszt jest znaczący, użytkownik może przemyślane zwiększoną poprawność, łatwiejszą konserwację i inne korzyści, które są dostarczane przez dobrze zaprojektowanego wyjątki od zasad.  
  
## <a name="exceptions-vs-assertions"></a>Wyjątki a potwierdzenia  
 Wyjątki i potwierdzenia to dwa odrębne mechanizmy wykrywania błędów czasu wykonywania programu. Użyj zapewnień, aby skontrolować przetestować warunki podczas rozwoju które nigdy nie może mieć wartość true, jeśli Twój kod jest poprawny. Brak ma sensu obsługi takiego błędu przy użyciu wyjątku, ponieważ błąd oznacza, że w kodzie coś musi zostać naprawione, a nie oznacza warunek, którego program musi odzyskać w czasie wykonywania. Potwierdzenie zatrzymuje wykonywanie w instrukcji, dzięki czemu można sprawdzić stan programu w debugerze; wyjątek kontynuuje wykonywanie od pierwszego odpowiedniego elemetu obsługi catch. Użyj wyjątków, aby sprawdzić warunki błędów, które mogą wystąpić w czasie wykonywania, nawet jeżeli Twój kod jest poprawny, na przykład "nie znaleziono pliku" lub "za mało pamięci." Można odzyskać z tych warunków, nawet jeśli odzyskiwanie po prostu wyświetla komunikat w dzienniku i kończy się program. Zawsze sprawdzaj argumenty do funkcji publicznych za pomocą wyjątków. Nawet jeśli funkcja jest wolna od błędów, możesz nie mieć pełną kontrolę nad argumentami, które użytkownik może przenieść do niegho.  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Wyjątki C++ a wyjątki Windows SEH  
 Programy C i C++ mogą wykorzystywać mechanizm (SEH), w systemie operacyjnym Windows obsługi wyjątków strukturalnych. Koncepcje w SEH przypominają te w wyjątkach C++, z tą różnicą, że używa SEH **__try**, **__except**, i **__finally** tworzy zamiast **spróbuj** i **catch**. W programie Visual C++ wyjątki C++ są implementowane dla SEH. Jednak podczas pisania kodu w języku C++, należy użyć składni wyjątków języka C++.  
  
 Aby uzyskać więcej informacji o bibliotece SEH, zobacz [obsługi wyjątków strukturalnych, (C/C++)](../cpp/structured-exception-handling-c-cpp.md).  
  
## <a name="exception-specifications-and-noexcept"></a>Specyfikacje wyjątków i noexcept  
 Specyfikacje wyjątków zostały wprowadzone w języku C++ jako sposób określania wyjątków, które mogą zgłosić funkcji. Jednak specyfikacje wyjątków okazały się w praktyce problematyczne i zostały zaniechane w standardzie roboczym C++ 11. Firma Microsoft zaleca, nie używaj specyfikacji wyjątków z wyjątkiem `throw()`, co oznacza, że funkcja pozwala bez wyjątków anulować. Jeśli musisz użyć specyfikacji wyjątku typu `throw(` *typu*`)`, należy pamiętać, że Visual C++ odbiega od normy w określony sposób. Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md). `noexcept` Specyfikator został wprowadzony w C ++ 11 jako preferowana alternatywa dla `throw()`.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: interfejs między kodem obsługi wyjątków a innym kodem](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [Witamy z powrotem w C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)