---
title: Obsługa wyjątków w MFC
ms.date: 11/04/2016
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
ms.openlocfilehash: afa49a4d54397cf79a3bd0af28e4a0f0a4c7639e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346049"
---
# <a name="exception-handling-in-mfc"></a>Obsługa wyjątków w MFC

W tym artykule opisano mechanizmy obsługi wyjątków dostępne w MFC. Dostępne są dwa mechanizmy:

- Wyjątki C++, dostępne w MFC w wersji 3.0 i nowszych wersjach

- Makra wyjątków MFC, dostępne w MFC w wersji 1.0 lub nowszy

Jeśli piszesz nową aplikację przy użyciu biblioteki MFC, należy użyć mechanizmu C++. Jeśli istniejąca aplikacja już używa tego mechanizmu często możesz użyć mechanizmu opartego na makra.

Można łatwo przekonwertować istniejącego kodu do wyjątków C++ zamiast makr wyjątków MFC. Zalety konwertowania kodu oraz wytyczne postępowania są opisane w artykule [wyjątków: Konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

Jeśli już opracowano aplikację przy użyciu makr wyjątków MFC, możesz kontynuować używanie tych makr w istniejącym kodzie podczas korzystania z wyjątków C++ w nowy kod. Artykuł [wyjątków: Zmiany w makrach wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) zapewnia wskazówki, aby to zrobić.

> [!NOTE]
>  Aby włączyć obsługę wyjątków C++ w kodzie, wybierz opcję Włącz wyjątki C++ na stronie generowanie kodu w folderze projektu języka C/C++ [stron właściwości](../build/reference/property-pages-visual-cpp.md) okno dialogowe lub użyj [/ehsc](../build/reference/eh-exception-handling-model.md) — opcja kompilatora.

W tym artykule omówiono następujące tematy:

- [Kiedy używać wyjątków](#_core_when_to_use_exceptions)

- [Obsługa wyjątków MFC](#_core_mfc_exception_support)

- [Dalsze informacje o wyjątkach](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a> Kiedy używać wyjątków

Trzy kategorie wyników może wystąpić, gdy funkcja jest wywoływana podczas wykonywania programu: normalnego wykonania, wykonanie błędne lub nietypowe wykonanie. Poniżej opisano każdej kategorii.

- Normalnego wykonywania

   Funkcja może wykonać normalnie i zwracają. Niektóre funkcje zwracają kod wyniku do obiektu wywołującego, co oznacza wynik funkcji. Kody wyników możliwe są ściśle zdefiniowane dla tej funkcji i reprezentują zakres możliwych wartości funkcji. Kod wyniku może wskazywać powodzenie lub niepowodzenie, lub nawet może wskazywać określonego typu awarii, który znajduje się w normalne gamę oczekiwania. Na przykład funkcja stan pliku może zwrócić kod, który wskazuje, że plik nie istnieje. Należy pamiętać, że termin "Kod błędu:" nie jest używana, ponieważ kod wyniku stanowi jeden z wielu oczekiwanych wyników.

- Błędne wykonywania

   Obiekt wywołujący sprawia, że niektóre pomyłka do przekazywania argumentów do funkcji lub wywołuje funkcję w kontekście nieodpowiednie. Taka sytuacja powoduje błąd i powinny zostać wykryte przy użyciu potwierdzenie podczas tworzenia programu. (Aby uzyskać więcej informacji na temat potwierdzeń, zobacz [potwierdzenia C/C++](/visualstudio/debugger/c-cpp-assertions).)

- Nietypowe wykonanie

   Nietypowe wykonanie dotyczy sytuacji, w którym warunki poza kontrolą programu, takie jak małej ilości pamięci lub błędy We/Wy są wywieranie wpływu na wynik funkcji. Nietypowych sytuacjach powinno zostać obsłużone przez przechwytywanie i zgłaszanie wyjątków.

Używanie wyjątków jest szczególnie przydatne do wykonania nietypowe.

##  <a name="_core_mfc_exception_support"></a> Obsługa wyjątków MFC

Czy używać wyjątków języka C++, bezpośrednio lub użyć makra wyjątków MFC, będą używane [klasa CException](../mfc/reference/cexception-class.md) lub `CException`-pochodnych obiekty, które mogą być generowane przez platformę, lub przez aplikację.

W poniższej tabeli przedstawiono wstępnie zdefiniowane wyjątki dostarczonych przez MFC.

|Klasa wyjątku|Znaczenie|
|---------------------|-------------|
|[Klasa CMemoryException](../mfc/reference/cmemoryexception-class.md)|Limit pamięci|
|[Klasa CFileException](../mfc/reference/cfileexception-class.md)|Wyjątek plików|
|[Klasa CArchiveException](../mfc/reference/carchiveexception-class.md)|Wyjątek archiwum/serializacji|
|[Klasa CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)|Odpowiedzi na żądania dla nieobsługiwanych usług|
|[Klasa CResourceException](../mfc/reference/cresourceexception-class.md)|Wyjątek alokacji zasobów Windows|
|[Klasa CDaoException](../mfc/reference/cdaoexception-class.md)|Wyjątki bazy danych (DAO klas)|
|[Klasa CDBException](../mfc/reference/cdbexception-class.md)|Wyjątki bazy danych (ODBC klas)|
|[Klasa COleException](../mfc/reference/coleexception-class.md)|wyjątki OLE|
|[Klasa COleDispatchException](../mfc/reference/coledispatchexception-class.md)|Wyjątki alokacji (automation)|
|[Klasa CUserException](../mfc/reference/cuserexception-class.md)|Wyjątek, który powiadomi użytkownika o okno komunikatu, a następnie zgłasza ogólny [cexception — klasa](../mfc/reference/cexception-class.md)|

> [!NOTE]
>  Biblioteka MFC obsługuje makr wyjątków MFC i wyjątków języka C++. MFC nie obsługuje bezpośrednio obsługi wyjątków systemu Windows NT strukturalnych (SEH), zgodnie z opisem w [obsługi wyjątków strukturalnych](/windows/desktop/debug/structured-exception-handling).

##  <a name="_core_further_reading_about_exceptions"></a> Dalsze informacje o wyjątkach

W poniższych artykułach opisano przy użyciu biblioteki MFC dla pierwszemu wyjątek:

- [Wyjątki: przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Wyjątki: badanie zawartości wyjątku](../mfc/exceptions-examining-exception-contents.md)

- [Wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Wyjątki: zgłaszanie wyjątków z własnych funkcji](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Wyjątki: wyjątki bazy danych](../mfc/exceptions-database-exceptions.md)

- [Wyjątki: wyjątki OLE](../mfc/exceptions-ole-exceptions.md)

Następujące artykuły porównać z makr wyjątków MFC przy użyciu słowa kluczowe wyjątków języka C++ i wyjaśniono, jak możesz dostosować swój kod:

- [Wyjątki: zmiany w makrach wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Wyjątki: konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Wyjątki: używanie makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)<br/>
[Jak mogę Tworzenie własnych klas wyjątków niestandardowych](http://go.microsoft.com/fwlink/p/?linkid=128045)
