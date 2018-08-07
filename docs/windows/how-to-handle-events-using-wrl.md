---
title: 'Porady: Obsługa zdarzeń z użyciem biblioteki WRL | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 287fe57868f1550e2f778bd9122d0d350011084e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570636"
---
# <a name="how-to-handle-events-using-wrl"></a>Porady: obsługa zdarzeń z użyciem biblioteki WRL
W tym dokumencie pokazano, jak subskrybować i obsługiwać zdarzenia obiektu Windows Runtime za pomocą zestawu Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL).  
  
 Na przykład bardziej podstawową, tworzy wystąpienie tego składnika, który pobiera wartość właściwości, zobacz [porady: uaktywnianie składnika środowiska wykonawczego Windows i korzystanie](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
## <a name="subscribing-to-and-handling-events"></a>Subskrybowanie i obsługa zdarzeń  
 Następujące kroki start `ABI::Windows::System::Threading::IDeviceWatcher` obiektu, a następnie monitorować postęp za pomocą procedury obsługi zdarzeń. `IDeviceWatcher` Interfejs umożliwia wyliczania urządzeń asynchronicznego lub w tle i otrzymywać powiadomienia, gdy urządzenia są dodane, usunięte lub zmienione. [Wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md) funkcji jest ważnym elementem w tym przykładzie, ponieważ umożliwia on określić obsługę zdarzenia, które przetwarzają wyniki operacji w tle. Pełny przykład poniżej.  
  
> [!WARNING]
>  Mimo że zazwyczaj używa się Biblioteka szablonów C++ środowiska wykonawczego Windows, w aplikacji uniwersalnych platformy Windows, w tym przykładzie użyto aplikacji konsoli do celów informacyjnych. Funkcje takie jak `wprintf_s` nie są dostępne z poziomu aplikacji Universal Windows Platform. Aby uzyskać więcej informacji na temat typów i funkcji, które można użyć w aplikacji uniwersalnych platformy Windows, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) i [Win32 i COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
1.  Obejmują (`#include`) wszystkie wymagane środowiska wykonawczego Windows, Biblioteka szablonów C++ środowiska wykonawczego Windows lub nagłówki standardowej biblioteki języka C++.  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     Windows.Devices.Enumeration.h deklaruje typy, które są wymagane do wyliczania urządzeń.  
  
     Firma Microsoft zaleca używanie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.  
  
2.  Zadeklaruj zmienne lokalne dla aplikacji. W tym przykładzie zawiera liczbę urządzeń wyliczany i tokenów rejestracji, umożliwiających realizację później anulowanie subskrypcji zdarzeń.  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  Inicjowanie środowiska wykonawczego Windows.  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  Tworzenie [zdarzeń](../windows/event-class-windows-runtime-cpp-template-library.md) obiekt, który synchronizuje zakończenie procesu wyliczania do głównej aplikacji.  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  To zdarzenie jest demonstracyjne tylko jako część aplikacji konsoli. W tym przykładzie użyto zdarzenie, aby upewnić się, że operacji asynchronicznej zakończy się przed zakończeniem aplikacji. W przypadku większości aplikacji należy zwykle nie Czekaj na zakończenie operacji asynchronicznej.  
  
5.  Utwórz fabrykę aktywacji dla `IDeviceWatcher` interfejsu.  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     Środowisko wykonawcze Windows używana w pełni kwalifikowanych nazw typów. `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` Parametru jest ciąg, który jest dostarczany przez środowisko wykonawcze Windows i zawiera nazwę klasy wymaganego środowiska uruchomieniowego.  
  
6.  Utwórz `IDeviceWatcher` obiektu.  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  Użyj `Callback` funkcję, aby subskrybować `Added`, `EnumerationCompleted`, i `Stopped` zdarzenia.  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     `Added` Program obsługi zdarzeń zwiększa liczbę urządzeń wyliczany. Znaleziono dziesięć urządzeń, zatrzymuje proces wyliczania.  
  
     `Stopped` Program obsługi zdarzeń usuwa procedury obsługi zdarzeń i ustawia zdarzenie zakończenia.  
  
     `EnumerationCompleted` Program obsługi zdarzeń zatrzymuje proces wyliczania. W przypadku, gdy istnieją mniej niż dziesięć urządzeń, obsługiwać to zdarzenie.  
  
    > [!TIP]
    >  W tym przykładzie używa wyrażenia lambda do definiowania wywołań zwrotnych. Umożliwia także obiekty funkcyjne (funktory), wskaźników do funkcji, lub [std::function](../standard-library/function-class.md) obiektów. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
8.  Uruchom proces wyliczania.  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. Poczekaj, aż proces wyliczania zakończyć, a następnie wydrukuj komunikat. Wszystkie `ComPtr` i obiektów RAII pozostaw zakresu są zwalniane, automatycznie.  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 Oto kompletny przykład:  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-events.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.  
  
 `cl.exe wrl-consume-events.cpp runtimeobject.lib`  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)