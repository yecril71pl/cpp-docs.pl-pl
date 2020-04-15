---
title: Obsługa wyjątków w MFC
ms.date: 11/19/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: d339ec98dabc6cb24fc7106c4c7238cd6a14a71b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365536"
---
# <a name="exception-handling-in-mfc"></a>Obsługa wyjątków w MFC

W tym artykule wyjaśniono mechanizmy obsługi wyjątków dostępne w MFC. Dostępne są dwa mechanizmy:

- Wyjątki języka C++, dostępne w wersji MFC 3.0 i nowszej

- Makra wyjątków MFC, dostępne w wersjach MFC 1.0 i nowszych

Jeśli piszesz nową aplikację przy użyciu MFC, należy użyć mechanizmu C++. Mechanizm oparty na makrach można użyć, jeśli istniejąca aplikacja już używa tego mechanizmu szeroko.

Można łatwo przekonwertować istniejący kod do używania wyjątków Języka C++ zamiast makr wyjątków MFC. Zalety konwersji kodu i wskazówki dotyczące tego są opisane w artykule [Wyjątki: Konwersja z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

Jeśli aplikacja została już opracowana przy użyciu makr wyjątków MFC, można kontynuować korzystanie z tych makr w istniejącym kodzie, przy użyciu wyjątków Języka C++ w nowym kodzie. Artykuł [Wyjątki: Zmiany makr wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) zawiera wskazówki, aby to zrobić.

> [!NOTE]
> Aby włączyć obsługę wyjątków języka C++ w kodzie, wybierz opcję Włącz wyjątki C++ na stronie Generowanie kodu w folderze C/C++ w oknie dialogowym [Strony właściwości](../build/reference/property-pages-visual-cpp.md) projektu lub użyj opcji kompilatora [/EHsc.](../build/reference/eh-exception-handling-model.md)

W tym artykule omówiono następujące tematy:

- [Kiedy stosować wyjątki](#_core_when_to_use_exceptions)

- [Obsługa wyjątków MFC](#_core_mfc_exception_support)

- [Dalsze czytanie o wyjątkach](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>Kiedy używać wyjątków

Trzy kategorie wyników może wystąpić, gdy funkcja jest wywoływana podczas wykonywania programu: normalne wykonanie, błędne wykonanie lub nieprawidłowe wykonanie. Każda kategoria jest opisana poniżej.

- Normalne wykonanie

   Funkcja może działać normalnie i zwracać. Niektóre funkcje zwracają kod wyniku do wywołującego, co wskazuje wynik funkcji. Możliwe kody wyników są ściśle zdefiniowane dla funkcji i reprezentują zakres możliwych wyników funkcji. Kod wyniku może wskazywać na powodzenie lub niepowodzenie lub nawet wskazać określony typ błędu, który mieści się w normalnym zakresie oczekiwań. Na przykład funkcja stanu pliku może zwrócić kod, który wskazuje, że plik nie istnieje. Należy zauważyć, że termin "kod błędu" nie jest używany, ponieważ kod wyniku reprezentuje jeden z wielu oczekiwanych wyników.

- Błędne wykonanie

   Wywołujący popełnia błąd w przekazywaniu argumentów do funkcji lub wywołuje funkcję w nieodpowiednim kontekście. Ta sytuacja powoduje błąd i powinny być wykrywane przez asercja podczas tworzenia programu. (Aby uzyskać więcej informacji na temat potwierdzeń, zobacz [C/C++ potwierdzenia](/visualstudio/debugger/c-cpp-assertions).)

- Nieprawidłowe wykonanie

   Nieprawidłowe wykonanie obejmuje sytuacje, w których warunki poza kontrolą programu, takie jak brak pamięci lub błędy we/wy, wpływają na wynik funkcji. Nietypowe sytuacje powinny być obsługiwane przez przechwytywanie i zgłaszanie wyjątków.

Używanie wyjątków jest szczególnie odpowiednie dla nieprawidłowego wykonywania.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>Obsługa wyjątków MFC

Niezależnie od tego, czy używasz wyjątków C++ bezpośrednio lub użyć makr wyjątków MFC, użyjesz [CException Class](../mfc/reference/cexception-class.md) lub `CException`-derived obiektów, które mogą być generowane przez strukturę lub przez aplikację.

W poniższej tabeli przedstawiono wstępnie zdefiniowane wyjątki dostarczone przez MFC.

|Klasa wyjątku|Znaczenie|
|---------------------|-------------|
|[Klasa CMemoryException](../mfc/reference/cmemoryexception-class.md)|Brak pamięci|
|[Klasa CFileException](../mfc/reference/cfileexception-class.md)|Wyjątek pliku|
|[Klasa CArchiveException](../mfc/reference/carchiveexception-class.md)|Wyjątek archiwum/serializacji|
|[Klasa CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)|Odpowiedź na żądanie nieobsługiwała usługa|
|[Klasa CResourceException](../mfc/reference/cresourceexception-class.md)|Wyjątek alokacji zasobów systemu Windows|
|[Klasa CDaoException](../mfc/reference/cdaoexception-class.md)|Wyjątki bazy danych (klasy DAO)|
|[Klasa CDBException](../mfc/reference/cdbexception-class.md)|Wyjątki bazy danych (klasy ODBC)|
|[Klasa COleException](../mfc/reference/coleexception-class.md)|wyjątki OLE|
|[Klasa COleDispatchException](../mfc/reference/coledispatchexception-class.md)|Wyjątki wysyłki (automatyzacji)|
|[Klasa CUserException](../mfc/reference/cuserexception-class.md)|Wyjątek, który ostrzega użytkownika z okna komunikatu, a następnie zgłasza ogólną [klasę CException](../mfc/reference/cexception-class.md)|

Od wersji 3.0, MFC wykorzystuje wyjątki C++, ale nadal obsługuje jego starsze makra obsługi wyjątków, które mają podobną formę do wyjątków C++. Chociaż wykorzystanie tych makr nie jest zalecane w przypadku nowych programów, nadal są one obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. W programach, które już używają makr, można bez ograniczeń wykorzystywać również wyjątki C++. Podczas przetwarzania wstępnego makra ocenić do obsługi wyjątków słów kluczowych zdefiniowanych w implementacji MSVC języka C++ w wersji Visual C++ w wersji 2.0. Podczas korzystania z języka C++, można pozostawić na miejscu istniejące makra wyjątków. Aby uzyskać informacje na temat mieszania makr i obsługi wyjątków C++ oraz konwertowania starego kodu na nowy mechanizm, zobacz artykuły [Wyjątki: Używanie makr MFC i wyjątków C++:](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) [Konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md). Starsze makra wyjątków MFC, jeżeli użytkownik nadal z nich korzysta, szacowane są jako słowa kluczowe wyjątków języka C++. Zobacz [Wyjątki: Zmiany makr wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md). MFC nie obsługuje bezpośrednio programów obsługi wyjątków strukturalnych systemu Windows NT (SEH), jak omówiono w [ustrukturyzowanej obsługi wyjątków](/windows/win32/debug/structured-exception-handling).

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>Dalsze czytanie o wyjątkach

Następujące artykuły wyjaśniają przy użyciu biblioteki MFC do przekazywania wyjątków:

- [Wyjątki: przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Wyjątki: badanie zawartości wyjątku](../mfc/exceptions-examining-exception-contents.md)

- [Wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Wyjątki: zgłaszanie wyjątków z własnych funkcji](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Wyjątki: wyjątki bazy danych](../mfc/exceptions-database-exceptions.md)

- [Wyjątki: wyjątki OLE](../mfc/exceptions-ole-exceptions.md)

Następujące artykuły porównują makra wyjątków MFC ze słowami kluczowymi wyjątków C++ i wyjaśniają, jak można dostosować kod:

- [Wyjątki: zmiany w makrach wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Wyjątki: konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Wyjątki: używanie makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Zobacz też

[Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Jak: Tworzenie własnych niestandardowych klas wyjątków](https://go.microsoft.com/fwlink/p/?linkid=128045)
