---
title: 'Porady: wykonywanie operacji asynchronicznych za pomocą biblioteki WRL | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fff0a6e98dd6fdd28b1fbc2e9146d5b68975e0f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881528"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Porady: wykonywanie operacji asynchronicznych z użyciem biblioteki WRL
Ten dokument przedstawia sposób użycia systemu Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL) do uruchamiania operacji asynchronicznych i wykonywania pracy po ukończeniu operacji.  
  
 Ten dokument zawiera dwa przykłady. Pierwszym przykładzie uruchamia czasomierz asynchroniczne i czeka na czasomierz wygaśnie. W tym przykładzie zostanie akcja asynchroniczna podczas tworzenia obiektu czasomierza. Drugi przykład uruchamia wątku w tle proces roboczy. W tym przykładzie pokazano, jak pracować z metody środowiska uruchomieniowego systemu Windows, która zwraca `IAsyncInfo` interfejsu. [Wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md) funkcja jest ważnym elementem zarówno przykłady, ponieważ pozwala to określić program obsługi zdarzeń do przetwarzania wyniki operacji asynchronicznych.  
  
 Aby uzyskać więcej podstawowy przykład powoduje utworzenie wystąpienia składnika, który pobiera wartość właściwości, zobacz [porady: uaktywnianie składnika środowiska wykonawczego systemu Windows i korzystanie](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
> [!TIP]
>  Poniższe przykłady użycie wyrażeń lambda do definiowania wywołań zwrotnych. Umożliwia także obiekty funkcji (funktorów), wskaźniki funkcji lub [std::function](../standard-library/function-class.md) obiektów. Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C++, zobacz [wyrażenia Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="example-working-with-a-timer"></a>Przykład: Praca z czasomierzem  
 Poniższe kroki uruchomić czasomierza asynchroniczne i poczekaj, aż czasomierza wygaśnie. Pełny przykład jest zgodna.  
  
> [!WARNING]
>  Mimo że używasz zazwyczaj Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, w aplikacji Windows platformy Uniwersalnej, w tym przykładzie użyto aplikacji konsoli ilustracyjną. Funkcje, takie jak `wprintf_s` nie są dostępne w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji na temat typów i funkcje, których można użyć w aplikacji platformy uniwersalnej systemu Windows, zobacz [nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows w funkcji CRT](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) i [Win32 i COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
1.  Obejmują (`#include`) wymagane środowisko wykonawcze systemu Windows, Biblioteka szablonów C++ środowiska wykonawczego systemu Windows lub nagłówków standardowej biblioteki C++.  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     Windows.System.Threading.h deklaruje typów, które są wymagane do używania asynchroniczne czasomierza.  
  
     Zaleca się, że wykorzystanie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.  
  
2.  Inicjowanie środowiska uruchomieniowego systemu Windows.  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  Tworzenie fabryki aktywacji dla `ABI::Windows::System::Threading::IThreadPoolTimer` interfejsu.  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     Środowisko wykonawcze systemu Windows używa nazwy w pełni kwalifikowane do identyfikacji typów. `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` Jest ciągiem, są udostępniane przez środowisko wykonawcze systemu Windows, który zawiera nazwę klasy wymagane środowisko uruchomieniowe.  
  
4.  Utwórz [zdarzeń](../windows/event-class-windows-runtime-cpp-template-library.md) obiekt, który synchronizuje wywołanie zwrotne czasomierza do głównej aplikacji.  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  To zdarzenie jest do pokazania tylko jako część aplikacji konsoli. W tym przykładzie użyto zdarzenie, aby upewnić się, że zostało ukończone przed umożliwia zamknięcie aplikacji operacji asynchronicznej. W przypadku większości aplikacji zwykle nie poczekać na zakończenie operacji asynchronicznych.  
  
5.  Utwórz `IThreadPoolTimer` obiekt, który wygasa po dwóch sekund. Użyj `Callback` funkcji, aby utworzyć programu obsługi zdarzeń ( `ABI::Windows::System::Threading::ITimerElapsedHandler` obiektu).  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  Drukuj komunikat do konsoli i poczekaj na wywołanie zwrotne czasomierza, aby zakończyć. Wszystkie `ComPtr` i obiekty RAII pozostaw zakresu i są wydawane automatycznie.  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 Oto pełny przykład:  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-async.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **cl.exe wrl-consume-async.cpp runtimeobject.lib**  
  
## <a name="example-working-with-a-background-thread"></a>Przykład: Praca z wątku w tle  
 Poniższe kroki uruchomić wątku roboczego i zdefiniować akcję wykonywaną przez wątek. Pełny przykład jest zgodna.  
  
> [!TIP]
>  W tym przykładzie pokazano, jak pracować z `ABI::Windows::Foundation::IAsyncAction` interfejsu. Ten wzorzec można zastosować do dowolnego interfejsu, który implementuje `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`, i `IAsyncOperationWithProgress`.  
  
1.  Obejmują (`#include`) wymagane środowisko wykonawcze systemu Windows, Biblioteka szablonów C++ środowiska wykonawczego systemu Windows lub nagłówków standardowej biblioteki C++.  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h deklaruje typy, które są wymagane do używania wątku roboczego.  
  
     Firma Microsoft zaleca użycie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.  
  
2.  Inicjowanie środowiska uruchomieniowego systemu Windows.  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  Tworzenie fabryki aktywacji dla `ABI::Windows::System::Threading::IThreadPoolStatics` interfejsu.  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  Utwórz [zdarzeń](../windows/event-class-windows-runtime-cpp-template-library.md) obiekt, który synchronizuje zakończenia wątku głównego aplikacji.  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  To zdarzenie jest do pokazania tylko jako część aplikacji konsoli. W tym przykładzie użyto zdarzenie, aby upewnić się, że zostało ukończone przed umożliwia zamknięcie aplikacji operacji asynchronicznej. W przypadku większości aplikacji zwykle nie poczekać na zakończenie operacji asynchronicznych.  
  
5.  Wywołanie `IThreadPoolStatics::RunAsync` metodę w celu utworzenia wątku roboczego. Użyj `Callback` funkcji, aby zdefiniować akcję.  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     `IsPrime` Funkcji jest zdefiniowany w pełnym przykładem jest zgodna.  
  
6.  Drukuj komunikat do konsoli i poczekaj na zakończenie wątku. Wszystkie `ComPtr` i obiekty RAII pozostaw zakresu i są wydawane automatycznie.  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 Oto pełny przykład:  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-asyncOp.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)
