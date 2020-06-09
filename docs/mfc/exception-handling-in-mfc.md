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
ms.openlocfilehash: ef827af413513d1a1753f84b1cb69a66f41f690c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618852"
---
# <a name="exception-handling-in-mfc"></a>Obsługa wyjątków w MFC

W tym artykule opisano mechanizmy obsługi wyjątków dostępne w MFC. Dostępne są dwa mechanizmy:

- Wyjątki języka C++, dostępne w bibliotece MFC w wersji 3,0 lub nowszej

- Makra wyjątku MFC, dostępne w MFC w wersji 1,0 lub nowszej

Jeśli piszesz nową aplikację przy użyciu MFC, należy użyć mechanizmu języka C++. Można użyć mechanizmu opartego na makrach, jeśli istniejąca aplikacja już korzysta z tego mechanizmu.

Możesz łatwo skonwertować istniejący kod, aby używać wyjątków C++ zamiast makr wyjątków MFC. Zalety konwertowania kodu i wytycznych do tego celu są opisane w artykule [wyjątki: konwertowanie z makr wyjątków MFC](exceptions-converting-from-mfc-exception-macros.md).

Jeśli aplikacja została już opracowana przy użyciu makr wyjątków MFC, można nadal używać tych makr w istniejącym kodzie, podczas gdy przy użyciu wyjątków C++ w nowym kodzie. Wyjątki artykułów [: zmiany w makrach wyjątków w wersji 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md) dają wskazówki dotyczące wykonania tej czynności.

> [!NOTE]
> Aby włączyć obsługę wyjątków C++ w kodzie, zaznacz opcję Włącz wyjątki C++ na stronie generowanie kodu w folderze C/C++ okna dialogowego [strony właściwości](../build/reference/property-pages-visual-cpp.md) projektu lub użyj opcji kompilatora [/EHsc](../build/reference/eh-exception-handling-model.md) .

W tym artykule omówiono następujące tematy:

- [Kiedy używać wyjątków](#_core_when_to_use_exceptions)

- [Obsługa wyjątków MFC](#_core_mfc_exception_support)

- [Dalsze informacje o wyjątkach](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>Kiedy używać wyjątków

Trzy kategorie wyników mogą wystąpić, gdy funkcja jest wywoływana podczas wykonywania programu: normalne wykonywanie, błędne wykonywanie lub nieprawidłowe wykonanie. Każda kategoria jest opisana poniżej.

- Normalne wykonywanie

   Funkcja może działać normalnie i zwracać. Niektóre funkcje zwracają kod wyniku do obiektu wywołującego, który wskazuje wynik funkcji. Możliwe kody wyników są ściśle zdefiniowane dla funkcji i reprezentują zakres możliwych wyników funkcji. Kod wyniku może wskazywać na powodzenie lub niepowodzenie lub nawet wskazywać konkretny typ błędu, który znajduje się w normalnym zakresie oczekiwań. Na przykład funkcja o stanie pliku może zwracać kod, który wskazuje, że plik nie istnieje. Należy zauważyć, że termin "kod błędu" nie jest używany, ponieważ kod wyniku reprezentuje jeden z wielu oczekiwanych wyników.

- Błędne wykonanie

   Obiekt wywołujący wykonuje jakiś błąd podczas przekazywania argumentów do funkcji lub wywołuje funkcję w niewłaściwym kontekście. Ta sytuacja powoduje błąd i powinna zostać wykryta przez potwierdzenie podczas tworzenia programu. (Aby uzyskać więcej informacji na temat potwierdzeń, zobacz " [potwierdzenia C/C++](/visualstudio/debugger/c-cpp-assertions)").

- Nieprawidłowe wykonanie

   Nietypowe wykonywanie obejmuje sytuacje, w których warunki poza kontrolką programu, takie jak mała ilość pamięci lub błędy we/wy, wpływają na wynik funkcji. Nietypowe sytuacje powinny być obsługiwane przez przechwytywanie i zgłaszanie wyjątków.

Użycie wyjątków jest szczególnie odpowiednie dla nietypowego wykonania.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>Obsługa wyjątków MFC

Niezależnie od tego, czy wyjątki języka C++ są używane bezpośrednio, czy za pomocą makr wyjątków MFC, użyjesz [klasy CException](reference/cexception-class.md) lub `CException` obiektów pochodnych, które mogą być zgłaszane przez platformę lub przez aplikację.

W poniższej tabeli przedstawiono wstępnie zdefiniowane wyjątki udostępniane przez MFC.

|Klasa wyjątku|Znaczenie|
|---------------------|-------------|
|[Klasa CMemoryException](reference/cmemoryexception-class.md)|Brak pamięci|
|[Klasa CFileException](reference/cfileexception-class.md)|Wyjątek pliku|
|[Klasa CArchiveException](reference/carchiveexception-class.md)|Wyjątek archiwizacji/serializacji|
|[Klasa CNotSupportedException](reference/cnotsupportedexception-class.md)|Odpowiedź na żądanie nieobsługiwanej usługi|
|[Klasa CResourceException](reference/cresourceexception-class.md)|Wyjątek alokacji zasobów systemu Windows|
|[Klasa CDaoException](reference/cdaoexception-class.md)|Wyjątki bazy danych (klasy DAO)|
|[Klasa CDBException](reference/cdbexception-class.md)|Wyjątki bazy danych (klasy ODBC)|
|[Klasa COleException](reference/coleexception-class.md)|wyjątki OLE|
|[Klasa COleDispatchException](reference/coledispatchexception-class.md)|Wyjątki wysyłania (Automatyzacja)|
|[Klasa CUserException](reference/cuserexception-class.md)|Wyjątek, który ostrzega użytkownika przy użyciu okna komunikatu, a następnie zgłasza rodzajową [klasę CException](reference/cexception-class.md)|

Od wersji 3.0, MFC wykorzystuje wyjątki C++, ale nadal obsługuje jego starsze makra obsługi wyjątków, które mają podobną formę do wyjątków C++. Chociaż wykorzystanie tych makr nie jest zalecane w przypadku nowych programów, nadal są one obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. W programach, które już używają makr, można bez ograniczeń wykorzystywać również wyjątki C++. Podczas przetwarzania wstępnego makra są oceniane do słów kluczowych obsługi wyjątków zdefiniowanych w implementacji MSVC języka C++ w Visual C++ wersji 2,0. Podczas korzystania z języka C++, można pozostawić na miejscu istniejące makra wyjątków. Aby uzyskać informacje o miksowaniu makr i obsłudze wyjątków C++ oraz o konwertowaniu starego kodu w celu korzystania z nowego mechanizmu, zobacz [wyjątki artykułów: używanie makr MFC i wyjątków C++](exceptions-using-mfc-macros-and-cpp-exceptions.md) i [wyjątków: konwertowanie z makr wyjątków MFC](exceptions-converting-from-mfc-exception-macros.md). Starsze makra wyjątków MFC, jeżeli użytkownik nadal z nich korzysta, szacowane są jako słowa kluczowe wyjątków języka C++. Zobacz [wyjątki: zmiany w makrach wyjątków w wersji 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md). MFC nie obsługuje bezpośrednio obsługi wyjątków strukturalnych systemu Windows NT (SEH), jak opisano w [strukturalnej obsłudze wyjątków](/windows/win32/debug/structured-exception-handling).

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>Dalsze informacje o wyjątkach

W poniższych artykułach opisano korzystanie z biblioteki MFC w celu uzyskania wyjątku:

- [Wyjątki: przechwytywanie i usuwanie wyjątków](exceptions-catching-and-deleting-exceptions.md)

- [Wyjątki: badanie zawartości wyjątku](exceptions-examining-exception-contents.md)

- [Wyjątki: zwalnianie obiektów w wyjątkach](exceptions-freeing-objects-in-exceptions.md)

- [Wyjątki: zgłaszanie wyjątków z własnych funkcji](exceptions-throwing-exceptions-from-your-own-functions.md)

- [Wyjątki: wyjątki bazy danych](exceptions-database-exceptions.md)

- [Wyjątki: wyjątki OLE](exceptions-ole-exceptions.md)

W poniższych artykułach porównano makra wyjątków MFC ze słowami kluczowymi wyjątków C++ i wyjaśniono, jak można dostosować kod:

- [Wyjątki: zmiany w makrach wyjątków w wersji 3.0](exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Wyjątki: konwertowanie z makr wyjątków MFC](exceptions-converting-from-mfc-exception-macros.md)

- [Wyjątki: używanie makr MFC i wyjątków języka C++](exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Zobacz też

[Nowoczesne najlepsze rozwiązania w języku C++ dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Jak: tworzenie własnych niestandardowych klas wyjątków](https://go.microsoft.com/fwlink/p/?linkid=128045)
