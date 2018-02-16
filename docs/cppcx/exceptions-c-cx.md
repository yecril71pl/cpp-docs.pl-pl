---
title: "Wyjątki (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7e54d98ac4e1398753746dcac074de53ee2e7a0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="exceptions-ccx"></a>Wyjątki (C + +/ CX)

Obsługa błędów w języku C + +/ CX jest oparta na wyjątki. Na najbardziej podstawowym poziomie składników środowiska wykonawczego systemu Windows raportów o błędach jako wartości HRESULT. W języku C + +/ CX, te wartości są konwertowane na silnie typizowaną wyjątki, które zawierają wartość HRESULT i opis ciągu, której będziesz mieć dostęp programowo.  Wyjątki są zaimplementowane jako `ref class` która pochodzi z `Platform::Exception`.  `Platform` Przestrzeni nazw definiuje klasy wyjątków różne najbardziej typowe wartości HRESULT; wszystkie inne wartości są zgłaszane przez `Platform::COMException` klasy. Wszystkie klasy wyjątku mają [Exception::HResult](platform-exception-class.md#hresult) pola, które można pobrać oryginalnego HRESULT. Można także sprawdzić informacje stosu wywołań do kodu użytkownika w debugerze, które mogą ułatwić wskazanie oryginalne źródło wyjątku, nawet jeśli jego występowania w kodzie, który został napisany w języku innym niż C++.

## <a name="exceptions"></a>Wyjątki

W programie C++ throw i catch wyjątek pochodzi z działania środowiska wykonawczego systemu Windows, wyjątek pochodzi z `std::exception`, lub typ zdefiniowany przez użytkownika. Należy zgłosić wyjątek środowiska uruchomieniowego systemu Windows tylko wtedy, gdy go będzie cross granic binarny interfejsu (ABI) aplikacji, na przykład, gdy kod, który przechwytuje wyjątku jest napisany w języku JavaScript. Gdy wyjątków C++ środowiska wykonawczego z systemem innym niż Windows osiągnie granic ABI, wyjątek jest przekształcana na `Platform::FailureException` wyjątek, który reprezentuje E_FAIL HRESULT. Aby uzyskać więcej informacji na temat ABI zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Można zadeklarować [Platform::Exception](platform-exception-class.md) przy użyciu jednej z dwóch konstruktorów parametrem HRESULT lub parametrem HRESULT i [Platform::String](platform-string-class.md)^ parametrów, które mogą być przekazywane przez ABI do wszystkich aplikacji środowiska wykonawczego systemu Windows, która je obsługuje. Lub wyjątek można zadeklarować przy użyciu jednej z dwóch [metody Exception::CreateException](platform-exception-class.md#createexception) przeciążeń, które przyjmują parametr HRESULT lub parametrem HRESULT i `Platform::String^` parametru.

## <a name="standard-exceptions"></a>Standardowa wyjątków

C + +/ CX obsługuje zestaw standardowych wyjątki, które reprezentują typowe błędy HRESULT. Każdy standardowe wyjątek pochodzi z [Platform::COMException](platform-comexception-class.md), który z kolei jest pochodną `Platform::Exception`. Gdy granicy ABI należy zgłosić wyjątek, musi zgłosić jeden standardowy wyjątków.

Nie można utworzyć pochodnej własny typ wyjątku z `Platform::Exception`. Zgłoszenie wyjątku niestandardowe, należy używać do tworzenia wynik HRESULT zdefiniowane przez użytkownika `COMException` obiektu.

W poniższej tabeli wymieniono wyjątki standardowa.

|Nazwa|Bazowy HRESULT|Opis|
|----------|------------------------|-----------------|
|COMException|*hresult zdefiniowane przez użytkownika*|Element zgłaszany, gdy nierozpoznany HRESULT jest zwracana z wywołania metody COM.|
|AccessDeniedException|E\_ACCESSDENIED|Element zgłaszany, gdy odmowa dostępu do zasobów lub funkcji.|
|ChangedStateException|E\_ZMIENIONE\_STANU|Element zgłaszany, gdy metody iteracyjnej kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, a tym samym unieważnienie wyniki metody.|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Element zgłaszany, gdy klasa COM nie został zarejestrowany.|
|DisconnectedException|RPC\_E\_ROZŁĄCZONO|Element zgłaszany, gdy obiekt jest odłączony od klientów.|
|FailureException|E\_FAIL|Element zgłaszany, gdy operacja nie powiedzie się.|
|InvalidArgumentException|E\_INVALIDARG —|Element zgłaszany, gdy jeden z argumentów, które są dostarczane do metody jest nieprawidłowy.|
|Invalidcastexception —|E\_NOINTERFACE|Element zgłaszany, gdy nie można rzutować typu do innego typu.|
|Notimplementedexception —|E\_NOTIMPL|Element zgłaszany, gdy metoda interfejsu nie została zaimplementowana w klasie.|
|NullReferenceException|E\_WSKAŹNIKA|Element zgłaszany, gdy jest próba usuwania odwołania odwołanie do obiektu o wartości null.|
|Objectdisposedexception —|RO\_E\_ZAMKNIĘTE|Element zgłaszany, gdy operacja jest wykonywana na zlikwidowanym obiekcie.|
|OperationCanceledException|E\_PRZERWANIA|Element zgłaszany, gdy operacja została przerwana.|
|OutOfBoundsException|E\_GRANIC|Element zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|
|OutOfMemoryException|E\_ZDARZEŃ OUTOFMEMORY|Element zgłaszany, gdy jest za mało pamięci do ukończenia tej operacji.|
|WrongThreadException|RPC\_E\_NIEWŁAŚCIWY\_WĄTKU|Element zgłaszany, gdy wątek wywołuje za pomocą wskaźnika interfejsu dla obiekt serwera proxy, który nie należy do apartamentu wątku.|

## <a name="hresult-and-message-properties"></a>Właściwości HResult i komunikat

Wszystkie wyjątki mają [HResult](platform-comexception-class.md#hresult) właściwości i [komunikat](platform-comexception-class.md#message) właściwości. [Exception::HResult](platform-exception-class.md#hresult) właściwości pobiera wyjątek bazowy wartość liczbową HRESULT. [Exception::Message](platform-exception-class.md#message) właściwości pobiera parametry dostarczane przez system, opisujący wyjątek. W systemie Windows 8 wiadomość jest dostępna tylko w debugerze i jest tylko do odczytu. Oznacza to, że nie można zmienić go podczas było ponownie zgłosić wyjątek. Windows 8.1 możesz programowy dostęp ciąg z komunikatem i podaj nowy komunikat, jeśli było ponownie zgłosić wyjątek. Lepsze informacje stos wywołań jest również dostępna w debugera, w tym callstacks dla wywołań metod asynchronicznych.

### <a name="examples"></a>Przykłady

W tym przykładzie pokazano, jak zgłosić wyjątek środowiska uruchomieniowego systemu Windows dla operacji synchronicznych:

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

Kolejnym przykładzie przedstawiono sposób catch wyjątku.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Aby przechwytywać wyjątki, które są generowane podczas operacji asynchronicznej, przy użyciu klasy zadania, a następnie dodaj kontynuacji obsługi błędów. Obsługa błędów kontynuacji marshals wyjątki, które są zgłaszane na inne wątki powrót do wywoływania wątku, dzięki czemu można obsługiwać wszystkie wyjątki potencjalnych w tylko jednym punkcie w kodzie. Aby uzyskać więcej informacji, zobacz [asynchronicznego programowania w języku C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Zdarzenie UnhandledErrorDetected

W Windows 8.1 można subskrybować [Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror#Windows_ApplicationModel_Core_ICoreApplicationUnhandledError_UnhandledErrorDetected) zdarzeń statycznych, która zapewnia dostęp do nieobsługiwanych błędów, które mają doprowadzić do procesu. Niezależnie od tego, w którym zainicjowano błąd osiągnie ten program obsługi jako [Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) obiekt, który jest przekazywany za pomocą argumentów zdarzenia. Podczas wywoływania `Propagate` na obiekcie, tworzy i zgłasza `Platform::*Exception` typu, który odpowiada kod błędu. W blokach catch można zapisać stanu użytkownika, jeśli to konieczne, a następnie zezwolić na albo przerwanie przez wywołanie metody procesu `throw`, lub czymś dostępu programu do znanego stanu. W poniższym przykładzie przedstawiono podstawowe wzorca:

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

[Dokumentacja języka Visual C++](visual-c-language-reference-c-cx.md)  
[Odwołanie do przestrzeni nazw](namespaces-reference-c-cx.md)  
