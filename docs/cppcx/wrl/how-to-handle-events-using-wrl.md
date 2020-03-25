---
title: 'Porady: obsługa zdarzeń z użyciem biblioteki WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 0e13212d7cb481bc72a903a31fb170fd1ff8b7ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213931"
---
# <a name="how-to-handle-events-using-wrl"></a>Porady: obsługa zdarzeń z użyciem biblioteki WRL

W tym dokumencie pokazano, jak za pomocą C++ biblioteki szablonów środowisko wykonawcze systemu Windows (WRL) subskrybować i obsłużyć zdarzenia środowisko wykonawcze systemu Windows obiektu.

Aby uzyskać bardziej podstawowy przykład, który tworzy wystąpienie tego składnika i pobiera wartość właściwości, zobacz [How to: Activate and use a środowisko wykonawcze systemu Windows Component](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

## <a name="subscribing-to-and-handling-events"></a>Subskrybowanie i obsługa zdarzeń

Poniższe kroki służą do uruchamiania obiektu `ABI::Windows::System::Threading::IDeviceWatcher` i używania programów obsługi zdarzeń do monitorowania postępu. Interfejs `IDeviceWatcher` umożliwia asynchroniczne wyliczanie urządzeń lub w tle oraz otrzymywanie powiadomień, gdy urządzenia są dodawane, usuwane lub zmieniane. Funkcja [wywołania zwrotnego](callback-function-wrl.md) jest ważną częścią tego przykładu, ponieważ umożliwia jej Określanie programów obsługi zdarzeń, które przetwarzają wyniki operacji w tle. Kompletny przykład.

> [!WARNING]
> Chociaż zwykle używasz biblioteki szablonów środowisko wykonawcze systemu Windows C++ w aplikacji platforma uniwersalna systemu Windows, w tym przykładzie użyto aplikacji konsolowej do ilustracji. Funkcje, takie jak `wprintf_s`, nie są dostępne w aplikacji platforma uniwersalna systemu Windows. Aby uzyskać więcej informacji na temat typów i funkcji, których można użyć w aplikacji platforma uniwersalna systemu Windows, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) i [Win32 i com for platformy UWP Apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Dołącz (`#include`) wszystkie wymagane środowisko wykonawcze systemu Windows, środowisko wykonawcze systemu Windows C++ bibliotekę szablonów lub C++ nagłówki biblioteki standardowej.

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` deklaruje typy, które są wymagane do wyliczenia urządzeń.

   Zalecamy użycie dyrektywy `using namespace` w pliku CPP, aby kod był bardziej czytelny.

2. Zadeklaruj zmienne lokalne dla aplikacji. Ten przykład zawiera liczbę wyliczonych urządzeń i tokenów rejestracji umożliwiających jej późniejsze anulowanie subskrypcji zdarzeń.

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Zainicjuj środowisko wykonawcze systemu Windows.

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. Utwórz obiekt [zdarzenia](event-class-wrl.md) , który synchronizuje zakończenie procesu wyliczania w aplikacji głównej.

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > To zdarzenie jest przeznaczone tylko do demonstracji jako część aplikacji konsolowej. Ten przykład używa zdarzenia, aby upewnić się, że operacja asynchroniczna zakończy się przed zakończeniem działania aplikacji. W większości aplikacji zazwyczaj nie czekają na zakończenie operacji asynchronicznych.

5. Utwórz fabrykę aktywacji dla interfejsu `IDeviceWatcher`.

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Środowisko wykonawcze systemu Windows używa w pełni kwalifikowanych nazw do identyfikowania typów. `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` parametr jest ciągiem dostarczonym przez środowisko wykonawcze systemu Windows i zawiera wymaganą nazwę klasy środowiska uruchomieniowego.

6. Utwórz obiekt `IDeviceWatcher`.

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. Użyj funkcji `Callback`, aby subskrybować zdarzenia `Added`, `EnumerationCompleted`i `Stopped`.

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   Obsługa zdarzeń `Added` zwiększa liczbę wyliczonych urządzeń. Kończy proces wyliczania po znalezieniu dziesięciu urządzeń.

   Program obsługi zdarzeń `Stopped` usuwa programy obsługi zdarzeń i ustawia zdarzenie ukończenia.

   Procedura obsługi zdarzeń `EnumerationCompleted` przerywa proces wyliczania. Obsługujemy to zdarzenie w przypadku, gdy jest mniej niż dziesięć urządzeń.

   > [!TIP]
   > W tym przykładzie używa wyrażenia lambda do definiowania wywołań zwrotnych. Można również używać obiektów Functions (funktory), wskaźników funkcji lub [std:: Function](../../standard-library/function-class.md) Objects. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

8. Rozpocznij proces wyliczania.

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. Poczekaj na zakończenie procesu wyliczania, a następnie wydrukuj komunikat. Wszystkie obiekty `ComPtr` i RAII pozostawiają zakres i są automatycznie udostępniane.

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

Oto kompletny przykład:

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-events.cpp` a następnie uruchom następujące polecenie w oknie **wiersza polecenia programu Visual Studio** .

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)
