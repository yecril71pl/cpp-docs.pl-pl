---
title: Typowe problemy przy migracji Visual C++ ARM
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 2c29b4ffa5344b309622314970ce52c47a0ebd05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328794"
---
# <a name="common-visual-c-arm-migration-issues"></a>Typowe problemy przy migracji Visual C++ ARM

Podczas korzystania z kompilatora Microsoft C++ (MSVC), ten sam kod źródłowy języka C++ może dawać inne wyniki na architekturze ARM niż w architekturach x86 lub x64.

## <a name="sources-of-migration-issues"></a>Źródła problemów związanych z migracją

Wiele problemów, które mogą wystąpić podczas migracji kodu z architektury x86 lub x64 do architektury ARM są związane z konstrukcjami kodu źródłowego, które mogą wywoływać niezdefiniowane, zdefiniowane w implementacji lub nieokreślone zachowanie.

*Niezdefiniowane zachowanie* jest zachowanie, które standard C++ nie definiuje, a to jest spowodowane przez operację, która nie ma rozsądnego wyniku: na przykład konwertowanie wartości zmiennoprzecinkowej na niepodpisaną liczbę całkowitą lub przesunięcie wartości o liczbę pozycji, która jest ujemna lub przekracza liczbę bitów w jej typie promowanym.

*Zachowanie zdefiniowane w implementacji* jest zachowanie, które standard C++ wymaga dostawcy kompilatora do definiowania i dokumentowania. Program może bezpiecznie polegać na zachowanie zdefiniowane w implementacji, mimo że może to nie być przenośne. Przykłady zachowania zdefiniowane w implementacji obejmują rozmiary wbudowanych typów danych i ich wymagania dotyczące wyrównania. Przykładem operacji, na którą może mieć wpływ zachowanie zdefiniowane w implementacji, jest uzyskiwanie dostępu do listy argumentów zmiennych.

*Nieokreślone zachowanie* jest zachowanie, które standard C++ pozostawia celowo niedeterministyczne. Chociaż zachowanie jest uważane za niedeterministyczne, konkretne wywołania nieokreślonego zachowania są określane przez implementację kompilatora. Jednak nie ma wymogu dla dostawcy kompilatora, aby wstępnie określić wynik lub zagwarantować spójne zachowanie między porównywalnymi wywołaniami i nie ma wymogu dla dokumentacji. Przykładem nieokreślonego zachowania jest kolejność, w jakiej są oceniane wyrażenia podrzędne, które zawierają argumenty wywołania funkcji.

Inne problemy z migracją można przypisać różnicom sprzętowym między architekturami ARM i x86 lub x64, które w różny sposób współdziałają ze standardem C++. Na przykład model silnej pamięci architektury x86 i `volatile`x64 daje zmiennym kwalifikowanym niektóre dodatkowe właściwości, które zostały użyte w celu ułatwienia niektórych rodzajów komunikacji między wątkami w przeszłości. Ale model pamięci słabe architektury ARM nie obsługuje tego zastosowania, ani standard C++ wymaga.

> [!IMPORTANT]
> Mimo `volatile` że zyskuje niektóre właściwości, które mogą służyć do implementacji ograniczonych form komunikacji między wątkami na x86 i x64, te dodatkowe właściwości nie są wystarczające do zaimplementowania komunikacji między wątkami w ogóle. Standard C++ zaleca, aby taka komunikacja była implementowana przy użyciu odpowiednich ilucy synchronizacji zamiast.

Ponieważ różne platformy mogą wyrażać tego rodzaju zachowania inaczej, przenoszenie oprogramowania między platformami może być trudne i podatne na błędy, jeśli zależy to od zachowania określonej platformy. Chociaż wiele z tych rodzajów zachowań można zaobserwować i może wydawać się stabilne, poleganie na nich jest co najmniej nieprzenośne, a w przypadku niezdefiniowanego lub nieokreślonego zachowania jest również błędem. Nawet zachowanie, które jest cytowane w tym dokumencie nie należy polegać na i może ulec zmianie w przyszłych kompilatorów lub implementacji procesora CPU.

## <a name="example-migration-issues"></a>Przykładowe problemy z migracją

W dalszej części tego dokumentu opisano, jak różne zachowanie tych elementów języka C++ może dawać różne wyniki na różnych platformach.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Konwersja zmiennoprzecinowej na niepodpisaną liczbę całkowitą

W architekturze ARM konwersja wartości zmiennoprzecinkowej do 32-bitowej liczby całkowitej nasyca się do najbliższej wartości, którą może reprezentować liczba całkowita, jeśli wartość zmiennoprzecinkowej znajduje się poza zakresem, który może reprezentować liczba całkowita. W architekturach x86 i x64 konwersja zawija się, jeśli liczba całkowita jest niepodpisana lub jest ustawiona na -2147483648, jeśli liczba całkowita jest podpisana. Żadna z tych architektur bezpośrednio obsługuje konwersję wartości zmiennoprzecinkowych do mniejszych typów liczby całkowitej; Zamiast tego konwersje są wykonywane do 32 bitów, a wyniki są obcinane do mniejszego rozmiaru.

Dla architektury ARM, kombinacja nasycenia i obcinania oznacza, że konwersja na typy niepodpisane poprawnie nasyca mniejsze niepodpisane typy, gdy nasyca 32-bitową liczbę całkowitą, ale daje obcięty wynik dla wartości, które są większe niż mniejszy typ może reprezentować, ale zbyt małe, aby nasycić pełną liczbę całkowitą 32-bitową. Konwersja nasyca się również poprawnie dla 32-bitowych podpisanych liczby całkowitej, ale obcięcie nasyconych, podpisanych wartości całkowitych powoduje -1 dla wartości dodatnio nasyconych i 0 dla wartości ujemnie nasyconych. Konwersja na mniejszą podpisaną liczbę całkowitą daje okrojony wynik, który jest nieprzewidywalny.

W przypadku architektur x86 i x64 połączenie zachowania zawijania dla niepodpisanych konwersji całkowitych i jawnej wyceny dla podpisanych konwersji liczby całkowitej w przepełnieniu, wraz z obcięciem, powoduje, że wyniki dla większości zmian są nieprzewidywalne, jeśli są zbyt duże.

Platformy te różnią się również w jaki sposób obsługiwać konwersji NaN (Not-a-Number) do typów liczb całkowitych. Na ARM NaN konwertuje na 0x00000000; na x86 i x64, konwertuje do 0x80000000.

Konwersji zmiennoprzecinowej można polegać tylko wtedy, gdy wiesz, że wartość mieści się w zakresie typu liczby całkowitej, który jest konwertowany do.

### <a name="shift-operator---behavior"></a>Zachowanie operatora\< \< zmiany ( >>)

W architekturze ARM wartość może być przesunięta w lewo lub w prawo do 255 bitów, zanim wzorzec zacznie się powtarzać. W architekturach x86 i x64 wzorzec jest powtarzany przy każdej wielokrotności 32, chyba że źródłem wzorca jest zmienna 64-bitowa; w takim przypadku wzorzec powtarza się co wielokrotność 64 na x64 i co wielokrotność 256 na x86, gdzie zastosowano implementację oprogramowania. Na przykład dla zmiennej 32-bitowej, która ma wartość 1 przesunięta w lewo o 32 pozycje, na ARM wynik wynosi 0, na x86 wynik wynosi 1, a na x64 wynik jest również 1. Jeśli jednak źródłem wartości jest zmienna 64-bitowa, wynik na wszystkich trzech platformach wynosi 4294967296, a wartość nie "zawija się", dopóki nie zostanie przesunięta o 64 pozycje na x64 lub 256 pozycjach na ARM i x86.

Ponieważ wynik operacji zmiany, która przekracza liczbę bitów w typie źródła jest niezdefiniowana, kompilator nie musi mieć spójne zachowanie we wszystkich sytuacjach. Na przykład jeśli oba argumenty zmiany są znane w czasie kompilacji, kompilator może zoptymalizować program przy użyciu wewnętrznej procedury do wstępnego porównania wynik zmiany, a następnie zastąpienie wyniku zamiast operacji zmiany. Jeśli kwota przesunięcia jest zbyt duża lub ujemna, wynik procedury wewnętrznej może być inny niż wynik tego samego wyrażenia zmiany, które zostało wykonane przez procesor CPU.

### <a name="variable-arguments-varargs-behavior"></a>Zachowanie argumentów zmiennych (varargs)

W architekturze ARM parametry z listy argumentów zmiennych, które są przekazywane na stosie, podlegają wyrównaniu. Na przykład parametr 64-bitowy jest wyrównany do granicy 64-bitowej. W x86 i x64 argumenty, które są przekazywane na stosie nie podlegają wyrównaniu i szczelnie spakowane. Ta różnica może spowodować, że `printf` funkcja variadic jak odczytywać adresy pamięci, które były przeznaczone jako dopełnienie na ARM, jeśli oczekiwany układ listy argumentów zmiennych nie jest dokładnie dopasowany, nawet jeśli może działać dla podzbioru niektórych wartości na architekturach x86 lub x64. Rozważmy następujący przykład:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

W takim przypadku błąd można naprawić, upewniając się, że używana jest specyfikacja poprawnego formatu, aby uwzględnić wyrównanie argumentu. Ten kod jest poprawny:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Kolejność oceny argumentów

Ponieważ procesory ARM, x86 i x64 są tak różne, mogą przedstawiać różne wymagania dotyczące implementacji kompilatora, a także różne możliwości optymalizacji. Z tego powodu, wraz z innymi czynnikami, takimi jak konwencja wywołania i ustawienia optymalizacji, kompilator może oceniać argumenty funkcji w innej kolejności na różnych architekturach lub po zmianie innych czynników. Może to spowodować zachowanie aplikacji, która opiera się na określonej kolejności oceny, aby zmienić nieoczekiwanie.

Ten rodzaj błędu może wystąpić, gdy argumenty funkcji mają skutki uboczne, które wpływają na inne argumenty funkcji w tym samym wywołaniu. Zazwyczaj tego rodzaju zależności jest łatwe do uniknięcia, ale czasami może być zasłonięte przez zależności, które są trudne do rozpoznania lub przez przeciążenie operatora. Rozważmy ten przykład kodu:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Wydaje się to dobrze `->` zdefiniowane, ale jeśli i `*` są przeciążonymi operatorami, ten kod jest tłumaczony na coś, co przypomina to:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

A jeśli istnieje zależność `operator->(memory_handle)` między `operator*(p)`i , kod może polegać na określonej kolejności oceny, nawet jeśli oryginalny kod wygląda nie ma możliwości zależności.

### <a name="volatile-keyword-default-behavior"></a>zachowanie domyślne słowa kluczowego nietrwałego

Kompilator MSVC obsługuje dwie różne `volatile` interpretacje kwalifikatora magazynu, które można określić przy użyciu przełączników kompilatora. [Przełącznik /volatile:ms](reference/volatile-volatile-keyword-interpretation.md) wybiera rozszerzoną semantykę lotną firmy Microsoft, która gwarantuje silne porządkowanie, tak jak w przypadku modeli x86 i x64 ze względu na silny model pamięci na tych architekturach. [Przełącznik /volatile:iso](reference/volatile-volatile-keyword-interpretation.md) wybiera ścisłą semantycę lotną ze standardem C++, która nie gwarantuje silnego zamawiania.

W architekturze ARM wartość domyślna to **/volatile:iso** ponieważ procesory ARM mają słabo uporządkowany model pamięci, a oprogramowanie ARM nie ma starszego polegania na rozszerzonej semantyki **/volatile:ms** i zwykle nie musi łączyć się z oprogramowaniem, które to robi. Jednak nadal czasami jest wygodne lub nawet wymagane do kompilacji programu ARM do korzystania z rozszerzonej semantyki. Na przykład może być zbyt kosztowne, aby przenieść program do korzystania z semantyki ISO C++ lub oprogramowanie sterownika może być konieczne do przestrzegania tradycyjnej semantyki, aby działały poprawnie. W takich przypadkach można użyć **przełącznika /volatile:ms;** jednak aby odtworzyć tradycyjne semantyki lotne na obiekty DOCELOWE ARM, kompilator musi `volatile` wstawić bariery pamięci wokół każdego odczytu lub zapisu zmiennej w celu wymuszenia silnego zamawiania, co może mieć negatywny wpływ na wydajność.

Na architekturach x86 i x64 wartość domyślna to **/volatile:ms,** ponieważ wiele oprogramowania, które zostało już utworzone dla tych architektur przy użyciu usługi MSVC, opiera się na nich. Podczas kompilowania programów x86 i x64 można określić przełącznik **/volatile:iso,** aby uniknąć niepotrzebnego polegania na tradycyjnej semantyki lotnej i promować przenośność.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie Visual C++ dla procesorów ARM](configuring-programs-for-arm-processors-visual-cpp.md)
