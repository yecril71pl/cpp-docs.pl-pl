---
title: Wyjątki (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e7514fdfc07fcbb4a1fff42d80fd138ab7d6043
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100251"
---
# <a name="exceptions-ccx"></a>Wyjątki (C + +/ CX)

Obsługa błędów w języku C + +/ CX jest oparta na wyjątkach. Na poziomie większość podstawowych składników środowiska wykonawczego Windows raportować błędy jako wartości HRESULT. W języku C + +/ CX, te wartości są konwertowane na silnie typizowaną wyjątki, które zawierają wartość HRESULT i opis ciągu, które są dostępne programowo.  Wyjątki są implementowane jako `ref class` który pochodzi od klasy `Platform::Exception`.  `Platform` Nazw definiuje różne wyjątek klasy dla najbardziej typowych wartości HRESULT; wszystkie inne wartości są raportowane za pośrednictwem `Platform::COMException` klasy. Wszystkie klasy wyjątku mają [Exception::HResult](platform-exception-class.md#hresult) pola, które można użyć do pobrania, oryginalnym HRESULT. Można również sprawdzić informacje stosu wywołań dla kodu użytkownika w debugerze, które mogą ułatwić wskazanie oryginalnego źródła wyjątku, nawet jeśli pochodzi w kodzie, który został napisany w języku innym niż C++.

## <a name="exceptions"></a>Wyjątki

W programie C++, throw i catch wyjątku, który pochodzi z operacją środowiska wykonawczego Windows, wyjątek, który jest tworzony na podstawie `std::exception`, lub typ zdefiniowany przez użytkownika. Należy zgłosić wyjątek środowiska uruchomieniowego Windows tylko wtedy, gdy jej będzie między granic interfejsem binarnym (ABI) aplikacji, na przykład, gdy kod, który przechwytuje wyjątek jest napisany w języku JavaScript. Gdy wyjątek C++ inny niż Windows Runtime osiągnie granicę interfejsu ABI, wyjątek jest tłumaczony na `Platform::FailureException` wyjątek, który reprezentuje wartość HRESULT E_FAIL. Aby uzyskać więcej informacji na temat interfejsu ABI zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Można zadeklarować [Platform::Exception](platform-exception-class.md) przy użyciu jednej z dwóch konstruktorów parametrem HRESULT lub parametrem HRESULT i [Platform::String](platform-string-class.md)^ parametr, który może być przekazywany przez ABI do dowolnej aplikacji Windows Runtime, która je obsługuje. Lub możesz zadeklarować wyjątek przy użyciu jednej z dwóch [metoda Exception::CreateException](platform-exception-class.md#createexception) przeciążeń, które przyjmują parametr HRESULT lub parametrem HRESULT i `Platform::String^` parametru.

## <a name="standard-exceptions"></a>Standardowych wyjątków

C + +/ CX obsługuje zestaw standardowych wyjątków, które reprezentują typowe błędy HRESULT. Każdy standardowy wyjątek pochodzi od klasy [Platform::COMException](platform-comexception-class.md), który z kolei pochodzi od klasy `Platform::Exception`. Gdy zgłoszenie wyjątku przez granicę ABI należy zgłaszać jeden standardowych wyjątków.

Nie możesz wywodzić swój własny typ wyjątku z `Platform::Exception`. Wyjątku niestandardowych, należy używać do tworzenia HRESULT: zdefiniowane przez użytkownika `COMException` obiektu.

W poniższej tabeli wymieniono standardowych wyjątków.

|Nazwa|Bazowy HRESULT|Opis|
|----------|------------------------|-----------------|
|COMException|*hresult zdefiniowanych przez użytkownika*|Element zgłaszany, gdy wartość HRESULT nierozpoznany jest zwracany z wywołania metody COM.|
|AccessDeniedException|E\_ACCESSDENIED|Element zgłaszany, gdy odmowa dostępu do zasobów lub funkcji.|
|ChangedStateException|E\_ZMIENIONO\_STANU|Element zgłaszany, gdy metody iteratora kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, a tym samym unieważniając wyniki metody.|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Element zgłaszany, gdy klasa COM nie został zarejestrowany.|
|DisconnectedException|RPC\_E\_ROZŁĄCZONO|Element zgłaszany, gdy obiekt jest odłączony od swoich klientów.|
|FailureException|E\_ZAKOŃCZYĆ SIĘ NIEPOWODZENIEM|Element zgłaszany, gdy operacja nie powiedzie się.|
|InvalidArgumentException|E\_INVALIDARG —|Element zgłaszany, gdy jeden z argumentów, które są dostarczane do metody jest nieprawidłowy.|
|InvalidCastException|E\_NOINTERFACE|Element zgłaszany, gdy nie można rzutować typu na inny typ.|
|NotImplementedException|E\_NOTIMPL|Element zgłaszany, gdy metoda interfejsu nie została zaimplementowana w klasie.|
|Obiektu NullReferenceException|E\_WSKAŹNIKA|Zgłaszany, gdy jest próba cofnąć odwołanie odwołanie do obiektu o wartości null.|
|Objectdisposedexception —|RO\_E\_ZAMKNIĘTE|Element zgłaszany, gdy operacja jest wykonywana na zlikwidowanego obiektu.|
|OperationCanceledException|E\_PRZERWANIA|Element zgłaszany, gdy operacja została przerwana.|
|OutOfBoundsException|E\_GRANICE|Element zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|
|OutOfMemoryException|E\_ZDARZEŃ OUTOFMEMORY|Element zgłaszany, gdy ma za mało pamięci do ukończenia tej operacji.|
|WrongThreadException|RPC\_E\_NIEWŁAŚCIWEGO\_WĄTKU|Element zgłaszany, gdy wątek wywołuje za pomocą wskaźnika interfejsu, który jest dla obiektu serwera proxy, który nie należy do komórka wątku.|

## <a name="hresult-and-message-properties"></a>Właściwości HResult i komunikat

Wszystkie wyjątki mają [HResult](platform-comexception-class.md#hresult) właściwości i [komunikat](platform-comexception-class.md#message) właściwości. [Exception::HResult](platform-exception-class.md#hresult) właściwości pobiera wyjątek podstawowy liczbową wartość HRESULT. [Exception::Message](platform-exception-class.md#message) właściwości pobiera parametry dostarczane przez system, opisujący wyjątek. W systemie Windows 8 komunikat jest dostępna tylko w debugerze i jest tylko do odczytu. Oznacza to, że nie możesz go zmienić po użytkownik Zgłoś ponownie wyjątek. Windows 8.1 możesz programowy dostęp ciąg komunikatu i podaj nowy komunikat, jeśli możesz Zgłoś ponownie wyjątek. Lepsze informacje stosu wywołań jest również dostępna w debugerze, w tym stosy wywołań dla wywołań metod asynchronicznych.

### <a name="examples"></a>Przykłady

W tym przykładzie przedstawiono sposób wyjątku Windows Runtime synchroniczne operacje:

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

Następny przykład pokazuje, jak przechwycić wyjątek.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Aby przechwytywać wyjątki, które powstały podczas operacji asynchronicznej, przy użyciu klasy zadania, a następnie dodaj kontynuacji obsługi błędów. Kontynuacja obsługi błędów kieruje wyjątki wyrzucane na inny wątek z powrotem do wywołanego wątku, dzięki czemu może obsługiwać wszystkie potencjalne wyjątki w tylko jednym punkcie w kodzie. Aby uzyskać więcej informacji, zobacz [asynchronicznego programowania w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Zdarzenie UnhandledErrorDetected

W Windows 8.1 można subskrybować [Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror#Windows_ApplicationModel_Core_ICoreApplicationUnhandledError_UnhandledErrorDetected) zdarzeń statycznych, który zapewnia dostęp do nieobsługiwanych błędów, które chcesz obniżyć ten proces. Niezależnie od tego, skąd pochodzi ten błąd, osiągnie ten program obsługi jako [Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) obiektu, który jest przekazywany przy użyciu argumenty zdarzenia. Gdy wywołujesz `Propagate` dla obiektu, tworzy i zgłasza `Platform::*Exception` typu, który odnosi się do kodu błędu. W blokach catch, można zapisać stanu użytkownika, jeśli to konieczne, a następnie albo zezwolić na zakończenie przez wywołanie procesu `throw`, lub Opracuj coś dostępu programu do znanego stanu. Poniższy przykład przedstawia podstawowy wzorzec:

W app.xaml.h:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

W app.xaml.cpp:

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

C + +/ CX nie używa `finally` klauzuli.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka Visual C++](visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](namespaces-reference-c-cx.md)
