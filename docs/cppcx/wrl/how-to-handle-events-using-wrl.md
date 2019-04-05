---
title: 'Instrukcje: Obsługa zdarzeń z użyciem biblioteki WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 959a85d6cf6de666ae56d09035acefe9a3828ae8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033180"
---
# <a name="how-to-handle-events-using-wrl"></a>Instrukcje: Obsługa zdarzeń z użyciem biblioteki WRL

W tym dokumencie pokazano, jak subskrybować i obsługiwać zdarzenia obiektu Windows Runtime za pomocą zestawu Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL).

Na przykład bardziej podstawową, tworzy wystąpienie tego składnika, który pobiera wartość właściwości, zobacz [jak: Uaktywnianie składnika środowiska wykonawczego Windows i korzystanie](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

## <a name="subscribing-to-and-handling-events"></a>Subskrybowanie i obsługa zdarzeń

Następujące kroki start `ABI::Windows::System::Threading::IDeviceWatcher` obiektu, a następnie monitorować postęp za pomocą procedury obsługi zdarzeń. `IDeviceWatcher` Interfejs umożliwia wyliczania urządzeń asynchronicznego lub w tle i otrzymywać powiadomienia, gdy urządzenia są dodane, usunięte lub zmienione. [Wywołania zwrotnego](callback-function-wrl.md) funkcji jest ważnym elementem w tym przykładzie, ponieważ umożliwia on określić obsługę zdarzenia, które przetwarzają wyniki operacji w tle. Pełny przykład poniżej.

> [!WARNING]
> Mimo że zazwyczaj używa się Biblioteka szablonów C++ środowiska wykonawczego Windows, w aplikacji uniwersalnych platformy Windows, w tym przykładzie użyto aplikacji konsoli do celów informacyjnych. Funkcje takie jak `wprintf_s` nie są dostępne z poziomu aplikacji Universal Windows Platform. Aby uzyskać więcej informacji na temat typów i funkcji, które można użyć w aplikacji uniwersalnych platformy Windows, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) i [Win32 i COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Obejmują (`#include`) wszystkie wymagane środowiska wykonawczego Windows, Biblioteka szablonów C++ środowiska wykonawczego Windows lub nagłówki standardowej biblioteki języka C++.

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` deklaruje typy, które są wymagane do wyliczania urządzeń.

   Firma Microsoft zaleca używanie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.

2. Zadeklaruj zmienne lokalne dla aplikacji. W tym przykładzie zawiera liczbę urządzeń wyliczany i tokenów rejestracji, umożliwiających realizację później anulowanie subskrypcji zdarzeń.

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Inicjowanie środowiska wykonawczego Windows.

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. Tworzenie [zdarzeń](event-class-wrl.md) obiekt, który synchronizuje zakończenie procesu wyliczania do głównej aplikacji.

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > To zdarzenie jest demonstracyjne tylko jako część aplikacji konsoli. W tym przykładzie użyto zdarzenie, aby upewnić się, że operacji asynchronicznej zakończy się przed zakończeniem aplikacji. W przypadku większości aplikacji należy zwykle nie Czekaj na zakończenie operacji asynchronicznej.

5. Utwórz fabrykę aktywacji dla `IDeviceWatcher` interfejsu.

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Środowisko wykonawcze Windows używana w pełni kwalifikowanych nazw typów. `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` Parametru jest ciąg, który jest dostarczany przez środowisko wykonawcze Windows i zawiera nazwę klasy wymaganego środowiska uruchomieniowego.

6. Utwórz `IDeviceWatcher` obiektu.

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. Użyj `Callback` funkcję, aby subskrybować `Added`, `EnumerationCompleted`, i `Stopped` zdarzenia.

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   `Added` Program obsługi zdarzeń zwiększa liczbę urządzeń wyliczany. Znaleziono dziesięć urządzeń, zatrzymuje proces wyliczania.

   `Stopped` Program obsługi zdarzeń usuwa procedury obsługi zdarzeń i ustawia zdarzenie zakończenia.

   `EnumerationCompleted` Program obsługi zdarzeń zatrzymuje proces wyliczania. W przypadku, gdy istnieją mniej niż dziesięć urządzeń, obsługiwać to zdarzenie.

   > [!TIP]
   > W tym przykładzie używa wyrażenia lambda do definiowania wywołań zwrotnych. Umożliwia także obiekty funkcyjne (funktory), wskaźników do funkcji, lub [std::function](../../standard-library/function-class.md) obiektów. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../cpp/lambda-expressions-in-cpp.md).

8. Uruchom proces wyliczania.

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. Poczekaj, aż proces wyliczania zakończyć, a następnie wydrukuj komunikat. Wszystkie `ComPtr` i obiektów RAII pozostaw zakresu są zwalniane, automatycznie.

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

Oto kompletny przykład:

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-events.cpp` , a następnie uruchom następujące polecenie **Visual Studio Command Prompt** okna.

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>Zobacz także

[Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)