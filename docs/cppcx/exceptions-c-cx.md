---
title: Wyjątki (C++/CX)
ms.date: 07/02/2019
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
ms.openlocfilehash: 7b4475cfa92aa952dd5a2996508d9343255b7ed2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231016"
---
# <a name="exceptions-ccx"></a>Wyjątki (C++/CX)

Obsługa błędów w języku C++/CX jest oparta na wyjątkach. Na najbardziej podstawowym poziomie składniki środowisko wykonawcze systemu Windows zgłaszają błędy jako wartości HRESULT. W języku C++/CX te wartości są konwertowane na wyjątki o jednoznacznie określonym typie, które zawierają wartość HRESULT i opis ciągu, do którego można uzyskać dostęp programowo.  Wyjątki są implementowane jako **`ref class`** , które pochodzą od `Platform::Exception` .  `Platform`Przestrzeń nazw definiuje odrębne klasy wyjątków dla najbardziej typowych wartości HRESULT; wszystkie inne wartości są raportowane za pomocą `Platform::COMException` klasy. Wszystkie klasy wyjątków mają pole [Exception:: HRESULT](platform-exception-class.md#hresult) , za pomocą którego można pobrać pierwotny wynik HRESULT. Możesz również przeanalizować informacje stosu wywołań dla kodu użytkownika w debugerze, który może pomóc ustalić pierwotne źródło wyjątku, nawet jeśli pochodzi on z kodu, który został zapisany w języku innym niż C++.

## <a name="exceptions"></a>Wyjątki

W programie w języku C++ można zgłosić i wychwycić wyjątek, który pochodzi z środowisko wykonawcze systemu Windows operacji, wyjątek pochodzący z `std::exception` lub typu zdefiniowanego przez użytkownika. Musisz zgłosić wyjątek środowisko wykonawcze systemu Windows tylko wtedy, gdy będzie przekroczyć granicę interfejsu binarnego aplikacji (ABI), na przykład gdy kod, który przechwytuje wyjątek, jest zapisywana w języku JavaScript. Gdy wyjątek środowisko wykonawcze systemu Windows C++ osiągnie granicę ABI, wyjątek jest tłumaczony na `Platform::FailureException` wyjątek, który reprezentuje E_FAIL HRESULT. Aby uzyskać więcej informacji na temat ABI, zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Można zadeklarować [platformę:: Exception](platform-exception-class.md) przy użyciu jednego z dwóch konstruktorów, które przyjmują parametr HRESULT lub parametru HRESULT i klasy [platform:: String](platform-string-class.md)^, które mogą być przesyłane przez ABI do dowolnej aplikacji środowisko wykonawcze systemu Windows, która go obsługuje. Lub można zadeklarować wyjątek przy użyciu jednego z dwóch [wyjątków:: CreateException metody](platform-exception-class.md#createexception) overloads przyjmujących parametr HRESULT lub parametru HRESULT i `Platform::String^` parametru.

## <a name="standard-exceptions"></a>Wyjątki standardowe

C++/CX obsługuje zestaw wyjątków standardowych, które reprezentują typowe błędy HRESULT. Każdy wyjątek standardowy pochodzi z klasy [platform:: COMException](platform-comexception-class.md), która z kolei pochodzi od `Platform::Exception` . W przypadku zgłaszania wyjątku na granicy ABI należy zgłosić jeden z standardowych wyjątków.

Nie można utworzyć własnego typu wyjątku z `Platform::Exception` . Aby zgłosić wyjątek niestandardowy, użyj wartości HRESULT zdefiniowanej przez użytkownika do skonstruowania `COMException` obiektu.

W poniższej tabeli wymieniono standardowe wyjątki.

|Nazwa|Bazowy wynik HRESULT|Opis|
|----------|------------------------|-----------------|
|COMException|*wartość HRESULT zdefiniowana przez użytkownika*|Zgłaszany, gdy Nierozpoznana wartość HRESULT jest zwracana z wywołania metody COM.|
|AccessDeniedException|\_ACCESSDENIED E|Zgłaszany w przypadku odmowy dostępu do zasobu lub funkcji.|
|ChangedStateException|\_zmieniony \_ stan|Zgłaszany, gdy metody iteratora kolekcji lub widok kolekcji są wywoływane po zmianie kolekcji nadrzędnej, co powoduje unieważnienie wyników metody.|
|ClassNotRegisteredException|REGDB \_ E \_ CLASSNOTREG|Zgłaszany, gdy nie zarejestrowano klasy COM.|
|DisconnectedException|wywołanie RPC \_ E \_ odłączone|Zgłaszane po odłączeniu obiektu od jego klientów.|
|FailureException|E \_ Niepowodzenie|Zgłaszany, gdy operacja nie powiedzie się.|
|InvalidArgumentException|\_invalidArg — E|Zgłaszany, gdy jeden z argumentów dostarczonych do metody jest nieprawidłowy.|
|InvalidCastException|E \_ NOinterface|Zgłaszany, gdy typ nie może być rzutowany na inny typ.|
|NotImplementedException|\_NOTIMPL E|Zgłaszany, jeśli metoda interfejsu nie została zaimplementowana w klasie.|
|NullReferenceException|\_wskaźnik E|Zgłaszany w przypadku próby cofnięcia odwołania do odwołania do obiektu o wartości null.|
|ObjectDisposedException|\_ \_ ZAMKNIĘTo ro|Zgłaszany, gdy operacja jest wykonywana na usuniętym obiekcie.|
|OperationCanceledException|\_przerwanie E|Zgłaszany, gdy operacja zostanie przerwana.|
|OutOfBoundsException|\_granice E|Zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|
|OutOfMemoryException|\_OUTOFMEMORY E|Zgłaszany, gdy jest za mało pamięci, aby ukończyć operację.|
|WrongThreadException|\_niewłaściwy \_ \_ wątek RPC E|Zgłaszany, gdy wątek wywołuje za pośrednictwem wskaźnika interfejsu, który jest przeznaczony dla obiektu serwera proxy, który nie należy do Apartament wątku.|

## <a name="hresult-and-message-properties"></a>HResult i właściwości komunikatu

Wszystkie wyjątki mają właściwość [HRESULT](platform-comexception-class.md#hresult) i Właściwość [Message](platform-comexception-class.md#message) . Właściwość [Exception:: HRESULT](platform-exception-class.md#hresult) pobiera podstawową wartość wynikową dla wyjątku. Właściwość [Exception:: Message](platform-exception-class.md#message) Pobiera ciąg dostarczony przez system, który opisuje wyjątek. W systemie Windows 8 komunikat jest dostępny tylko w debugerze i jest tylko do odczytu. Oznacza to, że nie można go zmienić po ponownym wyrzucaniu wyjątku. W Windows 8.1 można programowo uzyskać dostęp do ciągu komunikatu i podać nowy komunikat, jeśli ponownie Zgłoś wyjątek. Lepsze informacje stosu wywołań są również dostępne w debugerze, w tym stosy wywołań dla wywołań metod asynchronicznych.

### <a name="examples"></a>Przykłady

Ten przykład pokazuje, jak zgłosić wyjątek środowisko wykonawcze systemu Windows dla operacji synchronicznych:

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

W następnym przykładzie pokazano, jak przechwytywać wyjątek.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Aby przechwytywać wyjątki, które są zgłaszane podczas operacji asynchronicznej, należy użyć klasy Task i dodać kontynuację obsługi błędu. Obsługa błędów kierowanie wyjątków, które są zgłaszane w innych wątkach z powrotem do wątku wywołującego, dzięki czemu można obsługiwać wszystkie potencjalne wyjątki w tylko jednym punkcie w kodzie. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Zdarzenie UnhandledErrorDetected

W Windows 8.1 można subskrybować zdarzenie statyczne [systemu Windows:: ApplicationModel:: Core:: CoreApplication:: UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror.unhandlederrordetected) , które zapewnia dostęp do nieobsługiwanych błędów, które mają zostać przełączone. Niezależnie od tego, skąd pochodzi błąd, dociera do tej procedury obsługi jako obiekt typu [Windows:: ApplicationModel:: Core:: UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) , który jest przesyłany za pomocą argumentów Event. Gdy wywołujesz `Propagate` obiekt, tworzy i zgłasza `Platform::*Exception` Typ, który odpowiada kod błędu. W blokach catch można zapisać stan użytkownika, jeśli jest to konieczne, a następnie zezwolić na zakończenie procesu przez wywołanie **`throw`** lub zrobić coś w celu przywrócenia znanego stanu programu. Poniższy przykład przedstawia podstawowy wzorzec:

W pliku App. XAML. h:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

W pliku App. XAML. cpp:

```cpp
// Subscribe to the event, for example in the app class constructor:
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);

// Event handler implementation:
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)
{
    auto err = e->UnhandledError;

    if (!err->Handled) //Propagate has not been called on it yet.
{
    try
    {
        err->Propagate();
    }
    // Catch any specific exception types if you know how to handle them
    catch (AccessDeniedException^ ex)
    {
        // TODO: Log error and either take action to recover
        // or else re-throw exception to continue fail-fast
    }
}
```

### <a name="remarks"></a>Uwagi

W języku C++/CX nie jest używana **`finally`** klauzula.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++/CX](visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](namespaces-reference-c-cx.md)
