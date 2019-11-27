---
title: Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: 85a8bf0f64681387cbee63f273fda5ce93ab7ad5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245868"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów

W nowoczesnych C++, preferowanym sposobem raportowania i obsługi błędów logiki i błędów środowiska uruchomieniowego jest użycie wyjątków. Jest to szczególnie prawdziwe, gdy stos może zawierać kilka wywołań funkcji między funkcją, która wykryje błąd, a funkcją, która ma kontekst, aby wiedzieć, jak ją obsłużyć. Wyjątki zapewniają formalny, dobrze zdefiniowany sposób dla kodu, który wykrywa błędy w celu przekazania informacji do stosu wywołań.

Błędy programu są zwykle podzielone na dwie kategorie: Błędy logiki, które są spowodowane przez błędy programistyczne, na przykład błąd "indeks poza zakresem" i błędy czasu wykonywania, które są poza kontrolą programisty, na przykład "Usługa sieciowa niedostępna" Porn. W programowaniu w stylu języka C i w modelu COM raportowanie błędów jest zarządzane przez zwrócenie wartości, która reprezentuje kod błędu lub kod stanu dla konkretnej funkcji, lub przez ustawienie zmiennej globalnej, którą obiekt wywołujący może opcjonalnie pobrać po każdym wywołaniu funkcji, aby zobaczyć czy błędy zostały zgłoszone. Na przykład programowanie COM używa wartości zwracanej HRESULT do przekazywania błędów do obiektu wywołującego, a Win32 API ma funkcję GetLastError do pobrania ostatniego błędu zgłoszonego przez stos wywołań. W obu tych przypadkach jest to obiekt wywołujący, aby rozpoznać kod i odpowiednio odpowiedzieć. Jeśli obiekt wywołujący nie obsługuje jawnie kodu błędu, program może ulec awarii bez ostrzeżenia lub kontynuować wykonywanie z nieprawidłowymi danymi i generować nieprawidłowe wyniki.

Wyjątki są preferowane w C++ nowoczesnej z następujących powodów:

- Wyjątek wymusza Wywoływanie kodu, aby rozpoznać warunek błędu i obsłużyć go. Nieobsłużone wyjątki zatrzymują wykonywanie programu.

- Wyjątek przeskakuje do punktu w stosie wywołań, który może obsłużyć błąd. Funkcje pośrednie mogą pozwolić na propagację wyjątku. Nie muszą one koordynować z innymi warstwami.

- Mechanizm odrzucania stosu wyjątku powoduje zniszczenie wszystkich obiektów w zakresie zgodnie z dobrze zdefiniowanymi regułami po zgłoszeniu wyjątku.

- Wyjątek umożliwia czyste rozdzielenie kodu, który wykrywa błąd i kod, który obsłuży błąd.

Poniższy uproszczony przykład przedstawia składnię niezbędną do wyrzucania i C++przechwytywania wyjątków w programie.

```cpp

#include <stdexcept>
#include <limits>
#include <iostream>

using namespace std;

void MyFunc(int c)
{
    if (c > numeric_limits< char> ::max())
        throw invalid_argument("MyFunc argument too large.");
    //...
}

int main()
{
    try
    {
        MyFunc(256); //cause an exception to throw
    }

    catch (invalid_argument& e)
    {
        cerr << e.what() << endl;
        return -1;
    }
    //...
    return 0;
}
```

Wyjątki w C++ programie przypominają te w językach, C# takich jak i Java. W bloku **try** , jeśli zostanie *zgłoszony* wyjątek, zostanie *przechwycony* przez pierwszy skojarzony blok **catch** , którego typ pasuje do tego wyjątku. Innymi słowy, wykonanie przechodzi z instrukcji **throw** do instrukcji **catch** . Jeśli nie zostanie znaleziony możliwy do użycia blok catch, `std::terminate` jest wywoływana, a program zostanie zakończony. W C++programie można zgłaszać dowolny typ; zaleca się jednak, aby zgłosić typ, który poprowadzi bezpośrednio lub pośrednio z `std::exception`. W poprzednim przykładzie typ wyjątku, [invalid_argument](../standard-library/invalid-argument-class.md), jest zdefiniowany w bibliotece standardowej w pliku nagłówkowym [\<stdexcept >](../standard-library/stdexcept.md) . C++nie dostarcza, i nie wymaga, blok **finally** , aby upewnić się, że wszystkie zasoby są wydane, jeśli wystąpi wyjątek. Funkcja pozyskiwania zasobów jest inicjowana (RAII) idiom, która używa inteligentnych wskaźników, zapewnia funkcje wymagane do oczyszczenia zasobów. Aby uzyskać więcej informacji, zobacz [jak: projektowanie pod kątem bezpieczeństwa wyjątków](how-to-design-for-exception-safety.md). Aby uzyskać informacje o C++ mechanizmie odwracania stosu, zobacz [wyjątki i rozwinięcia stosu](exceptions-and-stack-unwinding-in-cpp.md).

## <a name="basic-guidelines"></a>Podstawowe wytyczne

Niezawodna obsługa błędów jest trudne w każdym języku programowania. Chociaż wyjątki udostępniają kilka funkcji, które obsługują dobrą obsługę błędów, nie mogą wykonać całej pracy za Ciebie. Aby zrealizować zalety mechanizmu wyjątków, należy zachować wyjątki podczas projektowania kodu.

- Użyj potwierdzeń, aby wyszukać błędy, które nigdy nie powinny wystąpić. Użyj wyjątków, aby wyszukać błędy, które mogą wystąpić, na przykład błędy sprawdzania poprawności danych wejściowych w parametrach funkcji publicznych. Aby uzyskać więcej informacji, zapoznaj się z sekcją **wyjątki a potwierdzenia**.

- Wyjątki należy stosować, gdy kod, który obsługuje błąd, może być oddzielony od kodu, który wykrywa błąd przez jedno lub więcej wywoływanych funkcji. Należy rozważyć, czy należy używać kodów błędów zamiast w przypadku pętli krytycznych dla wydajności, gdy kod, który obsługuje błąd jest ściśle połączony z kodem, który go wykryje.

- Dla każdej funkcji, która może zgłosić lub propagować wyjątek, należy podać jedno z trzech gwarancji wyjątku: silna gwarancja, gwarancja podstawowa lub gwarancja nothrow (noexcept). Aby uzyskać więcej informacji, zobacz [jak: projektowanie pod kątem bezpieczeństwa wyjątków](how-to-design-for-exception-safety.md).

- Zgłoś wyjątki według wartości, należy je przechwycić przez odwołanie. Nie Przechwytuj tego, czego nie można obsłużyć.

- Nie używaj specyfikacji wyjątków, które są przestarzałe w języku C++ 11. Aby uzyskać więcej informacji, zapoznaj się z sekcją **specyfikacje wyjątków i noexcept**.

- Użyj standardowych typów wyjątków biblioteki, gdy mają zastosowanie. Utwórz niestandardowe typy wyjątków z hierarchii [klas wyjątków](../standard-library/exception-class.md) .

- Nie Zezwalaj na wyjątki do ucieczki z destruktorów lub funkcji dealokacji pamięci.

## <a name="exceptions-and-performance"></a>Wyjątki i wydajność

Mechanizm wyjątków ma bardzo minimalny koszt wydajności, jeśli nie zostanie zgłoszony żaden wyjątek. Jeśli wystąpi wyjątek, koszt przechodzenia stosu i rozwinięcia jest w przybliżeniu porównywalny do kosztu wywołania funkcji. Dodatkowe struktury danych są wymagane do śledzenia stosu wywołań po wprowadzeniu bloku **try** , a dodatkowe instrukcje są wymagane do odwinięcia stosu, jeśli wystąpi wyjątek. Jednak w większości scenariuszy koszt wydajności i pamięci nie jest znaczący. Niekorzystny wpływ wyjątków na wydajność może być istotny tylko w przypadku bardzo ograniczonych systemów pamięci lub w przypadku pętli o krytycznym znaczeniu dla wydajności, które mogą wystąpić regularnie, a kod, który obsłużył, jest ściśle połączony z kodem, który go zgłasza. W każdym przypadku nie można znać rzeczywistego kosztu wyjątków bez profilowania i pomiaru. Nawet w rzadkich przypadkach, gdy koszt jest znaczący, można go zważyć z większą dokładnością, łatwiejszym konserwacją i innymi korzyściami, które są udostępniane przez dobrze zaprojektowane zasady wyjątków.

## <a name="exceptions-vs-assertions"></a>Wyjątki a potwierdzenia

Wyjątki i potwierdzenia to dwa odrębne mechanizmy wykrywania błędów czasu wykonywania w programie. Użyj potwierdzeń do testowania pod kątem warunków podczas programowania, które nigdy nie powinny być prawdziwe, jeśli cały kod jest poprawny. Nie ma żadnego punktu na obsłudze takiego błędu przy użyciu wyjątku, ponieważ błąd wskazuje, że coś w kodzie musi być naprawione i nie reprezentuje warunku, z którego program ma zostać odzyskany w czasie wykonywania. Potwierdzenie kończy wykonywanie instrukcji, aby można było sprawdzić stan programu w debugerze; wyjątek kontynuuje wykonywanie od pierwszego odpowiedniej procedury obsługi catch. Użyj wyjątków, aby sprawdzić warunki błędów, które mogą wystąpić w czasie wykonywania nawet wtedy, gdy kod jest poprawny, na przykład "nie znaleziono pliku" lub "Brak pamięci". Może być konieczne odzyskanie z tych warunków, nawet jeśli odzyskiwanie wysyła komunikat do dziennika i skończy program. Zawsze sprawdzaj argumenty funkcji publicznych przy użyciu wyjątków. Nawet jeśli funkcja jest bezpłatna bez błędów, może nie mieć pełnej kontroli nad argumentami, które użytkownik może przekazać do niego.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>C++wyjątki a wyjątki SEH systemu Windows

Zarówno język C C++ , jak i programy mogą korzystać z mechanizmu obsługi wyjątków strukturalnych (SEH) w systemie operacyjnym Windows. Koncepcje w SEH przypominają te w C++ wyjątkach, z tą różnicą, że SEH korzysta z konstrukcji **__try**, **__except**i **__finally** zamiast **wypróbowania** i **przechwycenia**. W kompilatorze C++ Microsoft (MSVC) C++ wyjątki są implementowane dla SEH. Jednak podczas pisania C++ kodu, należy użyć składni C++ wyjątku.

Aby uzyskać więcej informacji na temat SEH, zobacz [Obsługa wyjątków strukturalnych (C++C/)](structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a>Specyfikacje wyjątków i noexcept

Specyfikacje wyjątków zostały wprowadzone w C++ sposób umożliwiający określenie wyjątków, które funkcja może zgłosić. Jednakże specyfikacje wyjątków okazały się problematyczne i są przestarzałe w standardowym projekcie C++ 11. Firma Microsoft zaleca, aby nie używać specyfikacji wyjątków, z wyjątkiem `throw()`, co oznacza, że funkcja nie zezwala na ucieczki wyjątków. Jeśli konieczne jest użycie specyfikacji wyjątków typu `throw(`*typ*`)`, należy pamiętać, że MSVC defragmentuje się ze standardu w określony sposób. Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](exception-specifications-throw-cpp.md). Specyfikator `noexcept` jest wprowadzany w C++ 11 jako preferowana alternatywa dla `throw()`.

## <a name="see-also"></a>Zobacz także

[Instrukcje: interfejs między kodem obsługi wyjątków a innym kodem](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
