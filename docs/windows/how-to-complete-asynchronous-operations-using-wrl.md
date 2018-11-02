---
title: 'Porady: wykonywanie operacji asynchronicznych z użyciem biblioteki WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: ec57d6dd94357a65b7aaa300d5622ec5feac9932
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534072"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Porady: wykonywanie operacji asynchronicznych z użyciem biblioteki WRL

W tym dokumencie pokazano, jak używać Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL) do uruchamiania operacji asynchronicznych i wykonywania pracy po ukończeniu operacji.

Ten dokument zawiera dwa przykłady. Pierwszy przykład uruchamia czasomierz asynchronicznego i czeka na czasomierz wygaśnie. W tym przykładzie należy określić akcję asynchroniczną podczas tworzenia obiektu czasomierza. Drugi przykład jest uruchamiany wątku roboczego tła. W tym przykładzie przedstawiono sposób pracy z metodą Windows Runtime, która zwraca `IAsyncInfo` interfejsu. [Wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md) funkcja jest ważną częścią oba przykłady, ponieważ pozwala określić program obsługi zdarzeń do przetwarzania wyników operacji asynchronicznych.

Na przykład bardziej podstawową, tworzy instancję składnika, który pobiera wartość właściwości, zobacz [porady: uaktywnianie składnika środowiska wykonawczego Windows i korzystanie](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

> [!TIP]
> Te przykłady używać wyrażeń lambda do definiowania wywołań zwrotnych. Umożliwia także obiekty funkcyjne (funktory), wskaźników do funkcji, lub [std::function](../standard-library/function-class.md) obiektów. Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C++, zobacz [wyrażeń Lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="example-working-with-a-timer"></a>Przykład: Praca z czasomierzem

Poniższe kroki uruchomić czasomierza asynchronicznego i oczekiwania na czasomierz wygaśnie. Pełny przykład poniżej.

> [!WARNING]
> Mimo że zazwyczaj używa się Biblioteka szablonów C++ środowiska wykonawczego Windows, w aplikacji platformy uniwersalnej Windows (UWP), w tym przykładzie użyto aplikacji konsoli do celów informacyjnych. Funkcje takie jak `wprintf_s` nie są dostępne w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji na temat typów i funkcji, które można użyć w aplikacji platformy uniwersalnej systemu Windows, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) i [Win32 i COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Obejmują (`#include`) wszystkie wymagane środowiska wykonawczego Windows, Biblioteka szablonów C++ środowiska wykonawczego Windows lub nagłówki standardowej biblioteki języka C++.

   [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` deklaruje typy, które są wymagane do użycia asynchronicznego czasomierza.

   Firma Microsoft zaleca używanie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.

2. Inicjowanie środowiska wykonawczego Windows.

   [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. Utwórz fabrykę aktywacji dla `ABI::Windows::System::Threading::IThreadPoolTimer` interfejsu.

   [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Środowisko wykonawcze Windows używana w pełni kwalifikowanych nazw typów. `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` Parametru jest ciąg, który jest dostarczany przez środowisko wykonawcze Windows i zawiera nazwę klasy wymaganego środowiska uruchomieniowego.

4. Tworzenie [zdarzeń](../windows/event-class-windows-runtime-cpp-template-library.md) obiekt, który synchronizuje czasomierza wywołania zwrotnego do głównej aplikacji.

   [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > To zdarzenie jest demonstracyjne tylko jako część aplikacji konsoli. W tym przykładzie użyto zdarzenie, aby upewnić się, że operacji asynchronicznej zakończy się przed zakończeniem aplikacji. W przypadku większości aplikacji należy zwykle nie Czekaj na zakończenie operacji asynchronicznej.

5. Utwórz `IThreadPoolTimer` obiekt, który wygasa po upływie dwóch sekund. Użyj `Callback` funkcji, aby utworzyć program obsługi zdarzeń ( `ABI::Windows::System::Threading::ITimerElapsedHandler` obiektu).

   [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. Drukuj komunikat do konsoli i poczekaj, aż wywołanie zwrotne czasomierza zakończyć. Wszystkie `ComPtr` i obiektów RAII pozostaw zakresu są zwalniane, automatycznie.

   [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

Oto kompletny przykład:

[!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-async.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>Przykład: Praca z wątku w tle

Poniższe kroki uruchomić wątku roboczego i zdefiniowania akcji, które jest wykonywane przez ten wątek. Pełny przykład poniżej.

> [!TIP]
> W tym przykładzie pokazano, jak pracować z `ABI::Windows::Foundation::IAsyncAction` interfejsu. Ten wzorzec można zastosować do dowolnego interfejsu, który implementuje `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`, i `IAsyncOperationWithProgress`.

1. Obejmują (`#include`) wszystkie wymagane środowiska wykonawczego Windows, Biblioteka szablonów C++ środowiska wykonawczego Windows lub nagłówki standardowej biblioteki języka C++.

   [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows.System.Threading.h deklaruje typy, które są wymagane do użycia wątku roboczego.

   Firma Microsoft zaleca użycie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.

2. Inicjowanie środowiska wykonawczego Windows.

   [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. Utwórz fabrykę aktywacji dla `ABI::Windows::System::Threading::IThreadPoolStatics` interfejsu.

   [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. Tworzenie [zdarzeń](../windows/event-class-windows-runtime-cpp-template-library.md) obiekt, który synchronizuje zakończenie wątku roboczego głównej aplikacji.

   [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > To zdarzenie jest demonstracyjne tylko jako część aplikacji konsoli. W tym przykładzie użyto zdarzenie, aby upewnić się, że operacji asynchronicznej zakończy się przed zakończeniem aplikacji. W przypadku większości aplikacji należy zwykle nie Czekaj na zakończenie operacji asynchronicznej.

5. Wywołaj `IThreadPoolStatics::RunAsync` metodę w celu utworzenia wątku roboczego. Użyj `Callback` funkcji do zdefiniowania akcji.

   [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   `IsPrime` Funkcja jest zdefiniowana w kompletnym przykładzie poniżej.

6. Drukuj komunikat do konsoli i poczekaj na ukończenie wątku. Wszystkie `ComPtr` i obiektów RAII pozostaw zakresu są zwalniane, automatycznie.

   [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

Oto kompletny przykład:

[!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-asyncOp.cpp` , a następnie uruchom następujące polecenie **Visual Studio Command Prompt** okna.

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)