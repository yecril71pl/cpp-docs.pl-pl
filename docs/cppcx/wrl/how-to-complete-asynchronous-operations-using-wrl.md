---
title: 'Porady: wykonywanie operacji asynchronicznych z użyciem biblioteki WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 8e7e52342cf73a56c6c33d4d1f998f446d632ddd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213944"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Porady: wykonywanie operacji asynchronicznych z użyciem biblioteki WRL

W tym dokumencie pokazano, jak używać biblioteki C++ szablonów środowisko wykonawcze systemu Windows (WRL) do uruchamiania operacji asynchronicznych i wykonywania pracy po zakończeniu operacji.

Ten dokument zawiera dwa przykłady. Pierwszy przykład uruchamia asynchroniczny czasomierz i czeka na wygaśnięcie czasomierza. W tym przykładzie należy określić akcję asynchroniczną podczas tworzenia obiektu Timer. Drugi przykład uruchamia wątek roboczy w tle. Ten przykład pokazuje, jak korzystać z metody środowisko wykonawcze systemu Windows, która zwraca interfejs `IAsyncInfo`. Funkcja [wywołania zwrotnego](callback-function-wrl.md) jest ważną częścią obu przykładów, ponieważ umożliwia im określenie programu obsługi zdarzeń do przetwarzania wyników operacji asynchronicznych.

Aby uzyskać bardziej podstawowy przykład, który tworzy wystąpienie składnika i pobiera wartość właściwości, zobacz [How to: Activate and use a środowisko wykonawcze systemu Windows Component](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

> [!TIP]
> Te przykłady używają wyrażeń lambda do definiowania wywołań zwrotnych. Można również używać obiektów Functions (funktory), wskaźników funkcji lub [std:: Function](../../standard-library/function-class.md) Objects. Aby uzyskać więcej informacji C++ na temat wyrażeń lambda, zobacz [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

## <a name="example-working-with-a-timer"></a>Przykład: Praca z czasomierzem

Poniższe kroki uruchamiają czasomierz asynchroniczny i oczekują na wygaśnięcie czasomierza. Kompletny przykład.

> [!WARNING]
> Chociaż zwykle używasz biblioteki szablonów środowisko wykonawcze systemu Windows C++ w aplikacji platforma uniwersalna systemu Windows (platformy UWP), w tym przykładzie użyto aplikacji konsolowej na potrzeby ilustracji. Funkcje, takie jak `wprintf_s`, nie są dostępne w aplikacji platformy UWP. Aby uzyskać więcej informacji na temat typów i funkcji, których można użyć w aplikacji platformy UWP, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) oraz [Win32 i com for platformy UWP Apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Dołącz (`#include`) wszystkie wymagane środowisko wykonawcze systemu Windows, środowisko wykonawcze systemu Windows C++ bibliotekę szablonów lub C++ nagłówki biblioteki standardowej.

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` deklaruje typy, które są wymagane do użycia asynchronicznego czasomierza.

   Zalecamy użycie dyrektywy `using namespace` w pliku CPP, aby kod był bardziej czytelny.

2. Zainicjuj środowisko wykonawcze systemu Windows.

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. Utwórz fabrykę aktywacji dla interfejsu `ABI::Windows::System::Threading::IThreadPoolTimer`.

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Środowisko wykonawcze systemu Windows używa w pełni kwalifikowanych nazw do identyfikowania typów. `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` parametr jest ciągiem dostarczonym przez środowisko wykonawcze systemu Windows i zawiera wymaganą nazwę klasy środowiska uruchomieniowego.

4. Utwórz obiekt [zdarzenia](event-class-wrl.md) , który synchronizuje wywołanie zwrotne czasomierza z główną aplikacją.

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > To zdarzenie jest przeznaczone tylko do demonstracji jako część aplikacji konsolowej. Ten przykład używa zdarzenia, aby upewnić się, że operacja asynchroniczna zakończy się przed zakończeniem działania aplikacji. W większości aplikacji zazwyczaj nie czekają na zakończenie operacji asynchronicznych.

5. Utwórz obiekt `IThreadPoolTimer`, który wygaśnie po upływie dwóch sekund. Użyj funkcji `Callback`, aby utworzyć procedurę obsługi zdarzeń (obiekt `ABI::Windows::System::Threading::ITimerElapsedHandler`).

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. Wydrukuj komunikat do konsoli i poczekaj na zakończenie wywołania zwrotnego czasomierza. Wszystkie obiekty `ComPtr` i RAII pozostawiają zakres i są automatycznie udostępniane.

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

Oto kompletny przykład:

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-async.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>Przykład: Praca z wątkiem w tle

Poniższe kroki umożliwiają uruchomienie wątku roboczego i zdefiniowanie akcji wykonywanej przez ten wątek. Kompletny przykład.

> [!TIP]
> W tym przykładzie przedstawiono sposób pracy z interfejsem `ABI::Windows::Foundation::IAsyncAction`. Ten wzorzec można zastosować do dowolnego interfejsu, który implementuje `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`i `IAsyncOperationWithProgress`.

1. Dołącz (`#include`) wszystkie wymagane środowisko wykonawcze systemu Windows, środowisko wykonawcze systemu Windows C++ bibliotekę szablonów lub C++ nagłówki biblioteki standardowej.

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   System Windows. System. Threading. h deklaruje typy, które są wymagane do użycia wątku roboczego.

   Zalecamy użycie dyrektywy `using namespace` w pliku CPP, aby kod był bardziej czytelny.

2. Zainicjuj środowisko wykonawcze systemu Windows.

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. Utwórz fabrykę aktywacji dla interfejsu `ABI::Windows::System::Threading::IThreadPoolStatics`.

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. Utwórz obiekt [zdarzenia](event-class-wrl.md) , który synchronizuje ukończenie wątku roboczego z główną aplikacją.

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > To zdarzenie jest przeznaczone tylko do demonstracji jako część aplikacji konsolowej. Ten przykład używa zdarzenia, aby upewnić się, że operacja asynchroniczna zakończy się przed zakończeniem działania aplikacji. W większości aplikacji zazwyczaj nie czekają na zakończenie operacji asynchronicznych.

5. Wywołaj metodę `IThreadPoolStatics::RunAsync`, aby utworzyć wątek roboczy. Użyj funkcji `Callback`, aby zdefiniować akcję.

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   Funkcja `IsPrime` jest definiowana w poniższym przykładzie.

6. Wydrukuj komunikat do konsoli i poczekaj na zakończenie wątku. Wszystkie obiekty `ComPtr` i RAII pozostawiają zakres i są automatycznie udostępniane.

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

Oto kompletny przykład:

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-asyncOp.cpp` a następnie uruchom następujące polecenie w oknie **wiersza polecenia programu Visual Studio** .

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)
