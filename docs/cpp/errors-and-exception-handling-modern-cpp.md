---
title: Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów
description: Jak nowoczesne C++ obsługuje wyjątkowe style programistyczne względem kodów błędów.
ms.date: 08/24/2020
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: b402c93ea5af3cc7dab418b6dea58446ae300c67
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898375"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów

W nowoczesnych językach C++ w większości scenariuszy preferowany sposób raportowania i obsługi błędów logiki i błędów środowiska uruchomieniowego polega na użyciu wyjątków. Jest to szczególnie prawdziwe, gdy stos może zawierać kilka wywołań funkcji między funkcją, która wykryje błąd, a funkcją, która ma kontekst do obsługi błędu. Wyjątki zapewniają formalny, dobrze zdefiniowany sposób dla kodu, który wykrywa błędy w celu przekazania informacji do stosu wywołań.

## <a name="use-exceptions-for-exceptional-code"></a>Używanie wyjątków dla wyjątkowego kodu

Błędy programu są często podzielone na dwie kategorie: Błędy logiczne, które są spowodowane przez błędy programistyczne, na przykład błąd "indeks poza zakresem". I błędy środowiska uruchomieniowego, które wykraczają poza kontrolę programisty, na przykład błąd "Usługa sieciowa niedostępna". W programowaniu w stylu języka C i w modelu COM raportowanie błędów jest zarządzane przez zwrócenie wartości, która reprezentuje kod błędu lub kod stanu dla określonej funkcji, lub przez ustawienie zmiennej globalnej, którą obiekt wywołujący może opcjonalnie pobrać po każdym wywołaniu funkcji, aby sprawdzić, czy błędy zostały zgłoszone. Na przykład programowanie COM używa wartości zwracanej HRESULT do przekazywania błędów do obiektu wywołującego. Win32 API zawiera funkcję, która `GetLastError` umożliwia pobranie ostatniego błędu zgłoszonego przez stos wywołań. W obu tych przypadkach jest to obiekt wywołujący, aby rozpoznać kod i odpowiednio odpowiedzieć. Jeśli obiekt wywołujący nie obsługuje jawnie kodu błędu, program może ulec awarii bez ostrzeżenia. Może być również nadal wykonywany przy użyciu nieprawidłowych danych i generować nieprawidłowe wyniki.

Wyjątki są preferowane w nowoczesnej C++ z następujących powodów:

- Wyjątek wymusza Wywoływanie kodu, aby rozpoznać warunek błędu i obsłużyć go. Nieobsłużone wyjątki zatrzymują wykonywanie programu.

- Wyjątek przeskakuje do punktu w stosie wywołań, który może obsłużyć błąd. Funkcje pośrednie mogą pozwolić na propagację wyjątku. Nie muszą one koordynować z innymi warstwami.

- Mechanizm odwracania stosu wyjątku powoduje zniszczenie wszystkich obiektów w zakresie po zgłoszeniu wyjątku zgodnie z dobrze zdefiniowanymi regułami.

- Wyjątek umożliwia czyste rozdzielenie kodu, który wykrywa błąd i kod, który obsłuży błąd.

Poniższy uproszczony przykład pokazuje składnię niezbędną do zgłaszania i przechwytywania wyjątków w języku C++.

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

Wyjątki w języku C++ są podobne do tych w językach, takich jak C# i Java. W **`try`** bloku, jeśli zostanie *zgłoszony* wyjątek, zostanie *przechwycony* przez pierwszy skojarzony **`catch`** blok, którego typ pasuje do tego wyjątku. Innymi słowy, wykonanie przechodzi z **`throw`** instrukcji do **`catch`** instrukcji. Jeśli blok catch nie zostanie znaleziony, `std::terminate` zostanie wywołany, a program zakończy działanie. W języku C++ można zgłaszać dowolny typ; zaleca się jednak, aby zgłosić typ, który poprowadzi bezpośrednio lub pośrednio z `std::exception` . W poprzednim przykładzie typ wyjątku, [`invalid_argument`](../standard-library/invalid-argument-class.md) ,,, jest zdefiniowany w bibliotece standardowej w [`<stdexcept>`](../standard-library/stdexcept.md) pliku nagłówkowym. Język C++ nie udostępnia lub nie wymaga **`finally`** bloku, aby upewnić się, że wszystkie zasoby są wydane, jeśli wystąpi wyjątek. Funkcja pozyskiwania zasobów jest inicjowana (RAII) idiom, która używa inteligentnych wskaźników, zapewnia funkcje wymagane do oczyszczenia zasobów. Aby uzyskać więcej informacji, zobacz [jak: projektowanie pod kątem bezpieczeństwa wyjątków](how-to-design-for-exception-safety.md). Aby uzyskać informacje o mechanizmie odwracania stosu języka C++, zobacz [wyjątki i rozwinięcia stosu](exceptions-and-stack-unwinding-in-cpp.md).

## <a name="basic-guidelines"></a>Podstawowe wytyczne

Niezawodna obsługa błędów jest trudne w każdym języku programowania. Chociaż wyjątki udostępniają kilka funkcji, które obsługują dobrą obsługę błędów, nie mogą wykonać całej pracy za Ciebie. Aby zrealizować zalety mechanizmu wyjątków, należy zachować wyjątki podczas projektowania kodu.

- Użyj potwierdzeń, aby wyszukać błędy, które nigdy nie powinny wystąpić. Użyj wyjątków, aby wyszukać błędy, które mogą wystąpić, na przykład błędy sprawdzania poprawności danych wejściowych w parametrach funkcji publicznych. Aby uzyskać więcej informacji, zobacz sekcję [wyjątki w porównaniu z potwierdzeniami](#exceptions_versus_assertions) .

- Wyjątki należy stosować, gdy kod, który obsługuje błąd jest oddzielony od kodu, który wykrywa błąd przez jedno lub więcej wywoływanych funkcji. Należy rozważyć, czy należy używać kodów błędów zamiast w przypadku pętli krytycznych dla wydajności, gdy kod, który obsługuje błąd jest ściśle połączony z kodem, który go wykryje.

- Dla każdej funkcji, która może zgłosić lub propagować wyjątek, należy podać jedno z trzech gwarancji wyjątku: silna gwarancja, gwarancja podstawowa lub gwarancja nothrow (noexcept). Aby uzyskać więcej informacji, zobacz [jak: projektowanie pod kątem bezpieczeństwa wyjątków](how-to-design-for-exception-safety.md).

- Zgłoś wyjątki według wartości, należy je przechwycić przez odwołanie. Nie Przechwytuj tego, czego nie można obsłużyć.

- Nie używaj specyfikacji wyjątków, które są przestarzałe w języku C++ 11. Aby uzyskać więcej informacji, zobacz sekcję [specyfikacje i `noexcept` wymagania dotyczące wyjątków](#exception_specifications_and_noexcept) .

- Użyj standardowych typów wyjątków biblioteki, gdy mają zastosowanie. Utwórz niestandardowe typy wyjątków z hierarchii [ `exception` klas](../standard-library/exception-class.md) .

- Nie Zezwalaj na wyjątki do ucieczki z destruktorów lub funkcji dealokacji pamięci.

## <a name="exceptions-and-performance"></a>Wyjątki i wydajność

Mechanizm wyjątków ma minimalny koszt wydajności, jeśli nie zostanie zgłoszony żaden wyjątek. Jeśli wystąpi wyjątek, koszt przechodzenia stosu i rozwinięcia jest w przybliżeniu porównywalny do kosztu wywołania funkcji. Dodatkowe struktury danych są wymagane do śledzenia stosu wywołań po **`try`** wprowadzeniu bloku, a dodatkowe instrukcje są wymagane do odwinięcia stosu, jeśli wystąpi wyjątek. Jednak w większości scenariuszy koszt wydajności i pamięci nie jest znaczący. Niekorzystny wpływ wyjątków na wydajność jest prawdopodobnie znaczący tylko w systemach z ograniczoną ilością pamięci. Lub w przypadku pętli krytycznych dla wydajności, w przypadku których błąd może wystąpić regularnie i istnieje ścisłe sprzężenie między kodem, który go obsługuje, i kod, który go zgłasza. W każdym przypadku nie można znać rzeczywistego kosztu wyjątków bez profilowania i pomiaru. Nawet w rzadkich przypadkach, gdy koszt jest znaczący, można go zważyć z większą dokładnością, łatwiejszym konserwacją i innymi korzyściami, które są udostępniane przez dobrze zaprojektowane zasady wyjątków.

## <a name="exceptions-versus-assertions"></a><a name="exceptions_versus_assertions"></a> Wyjątki a potwierdzenia

Wyjątki i potwierdzenia to dwa odrębne mechanizmy wykrywania błędów czasu wykonywania w programie. Używaj `assert` instrukcji do testowania pod kątem warunków podczas opracowywania, które nigdy nie powinny być prawdziwe, jeśli cały kod jest poprawny. Nie ma żadnego punktu na obsłudze takiego błędu przy użyciu wyjątku, ponieważ błąd wskazuje, że coś w kodzie musi być ustalone. Nie reprezentuje warunku, z którego program ma wykonać odzyskiwanie w czasie wykonywania. Powoduje `assert` zatrzymanie wykonywania instrukcji w celu sprawdzenia stanu programu w debugerze. Wyjątek kontynuuje wykonywanie od pierwszego odpowiedniej procedury obsługi catch. Użyj wyjątków, aby sprawdzić warunki błędów, które mogą wystąpić w czasie wykonywania nawet wtedy, gdy kod jest poprawny, na przykład "nie znaleziono pliku" lub "Brak pamięci". Wyjątki mogą obsługiwać te warunki, nawet jeśli odzyskiwanie tylko wysyła komunikat do dziennika i zatrzymuje program. Zawsze sprawdzaj argumenty funkcji publicznych przy użyciu wyjątków. Nawet jeśli funkcja jest bezpłatna bez błędów, może nie mieć pełnej kontroli nad argumentami, które użytkownik może przekazać do niego.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Wyjątki C++ a wyjątki SEH systemu Windows

Programy C i C++ mogą korzystać z mechanizmu obsługi wyjątków strukturalnych (SEH) w systemie operacyjnym Windows. Koncepcje w SEH przypominają te w wyjątkach C++, z tą różnicą, że SEH korzysta z **`__try`** **`__except`** konstrukcji,, i **`__finally`** zamiast **`try`** i **`catch`** . W kompilatorze języka Microsoft C++ (MSVC) wyjątki języka C++ są implementowane dla SEH. Jednak podczas pisania kodu C++ należy użyć składni wyjątków C++.

Aby uzyskać więcej informacji na temat SEH, zobacz [Obsługa wyjątków strukturalnych (C/C++)](structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a><a name="exception_specifications_and_noexcept"></a> Specyfikacje wyjątków i `noexcept`

Specyfikacje wyjątków zostały wprowadzone w języku C++ jako sposób, aby określić wyjątki, które może zgłosić funkcja. Jednakże specyfikacje wyjątków okazały się problematyczne i są przestarzałe w standardowym projekcie C++ 11. Zaleca się, aby nie używać **`throw`** specyfikacji wyjątków, z wyjątkiem `throw()` , co oznacza, że funkcja nie zezwala na ucieczki wyjątków. Jeśli musisz użyć specyfikacji wyjątków w postaci przestarzałej `throw( type-name )` , pomoc techniczna MSVC jest ograniczona. Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](exception-specifications-throw-cpp.md). **`noexcept`** Specyfikator jest wprowadzany w języku c++ 11 jako preferowana alternatywa dla `throw()` .

## <a name="see-also"></a>Zobacz też

[Instrukcje: interfejs między wyjątkowym i niewyjątkowym kodem](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)
