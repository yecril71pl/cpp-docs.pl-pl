---
title: "Porady: Obsługa zdarzeń za pomocą biblioteki WRL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f79d35267750c42466a0b2448f9b10c37fe81f05
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-handle-events-using-wrl"></a>Porady: obsługa zdarzeń z użyciem biblioteki WRL
Ten dokument przedstawia sposób użycia systemu Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL) subskrybować i obsługi zdarzeń obiektu środowiska wykonawczego systemu Windows.  
  
 Na przykład bardziej podstawową, tworzy wystąpienie tego składnika, który pobiera wartość właściwości, zobacz [porady: uaktywnianie składnika środowiska wykonawczego systemu Windows i korzystanie](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
## <a name="subscribing-to-and-handling-events"></a>Subskrybowanie i obsługa zdarzeń  
 Następujące kroki start `ABI::Windows::System::Threading::IDeviceWatcher` obiektu i użyj procedury obsługi zdarzeń, aby monitorować postęp. `IDeviceWatcher` Interfejs umożliwia wyliczania urządzeń asynchronicznie lub w tle i otrzymywać powiadomienia, gdy urządzenia są dodane, usunięte lub zmodyfikowane. [Wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md) funkcja jest ważnym elementem tego przykładu, ponieważ umożliwia on do określania obsługi zdarzenia, które przetwarzają wyników operacji w tle. Pełny przykład jest zgodna.  
  
> [!WARNING]
>  Mimo że używasz zazwyczaj Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, w aplikacji platformy uniwersalnej systemu Windows, w tym przykładzie użyto aplikacji konsoli ilustracyjną. Funkcje, takie jak `wprintf_s` nie są dostępne w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji na temat typów i funkcje, których można użyć w aplikacji platformy uniwersalnej systemu Windows, zobacz [nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows w funkcji CRT](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) i [Win32 i COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
1.  Obejmują (`#include`) wymagane środowisko wykonawcze systemu Windows, Biblioteka szablonów C++ środowiska wykonawczego systemu Windows lub nagłówków standardowej biblioteki C++.  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     Windows.Devices.Enumeration.h deklaruje typy, które są wymagane do wyliczania urządzeń.  
  
     Zaleca się, że wykorzystanie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.  
  
2.  Deklarowanie zmiennych lokalnych dla aplikacji. W tym przykładzie przechowuje licznik wyliczany urządzeń i tokenów rejestracji, które umożliwiają później anulowanie subskrypcji zdarzeń.  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  Inicjowanie środowiska uruchomieniowego systemu Windows.  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  Utwórz [zdarzeń](../windows/event-class-windows-runtime-cpp-template-library.md) obiekt, który synchronizuje zakończenie procesu wyliczenie do głównego aplikacji.  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  To zdarzenie jest do pokazania tylko jako część aplikacji konsoli. W tym przykładzie użyto zdarzenie, aby upewnić się, że zostało ukończone przed umożliwia zamknięcie aplikacji operacji asynchronicznej. W przypadku większości aplikacji zwykle nie poczekać na zakończenie operacji asynchronicznych.  
  
5.  Tworzenie fabryki aktywacji dla `IDeviceWatcher` interfejsu.  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     Środowisko wykonawcze systemu Windows używa nazwy w pełni kwalifikowane do identyfikacji typów. `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` Jest ciągiem, są udostępniane przez środowisko wykonawcze systemu Windows, który zawiera nazwę klasy wymagane środowisko uruchomieniowe.  
  
6.  Utwórz `IDeviceWatcher` obiektu.  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  Użyj `Callback` funkcji do subskrybowania `Added`, `EnumerationCompleted`, i `Stopped` zdarzenia.  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     `Added` Program obsługi zdarzeń zwiększa liczbę urządzeń wyliczone. Proces wyliczania przestaje znaleziono dziesięć urządzeń.  
  
     `Stopped` Program obsługi zdarzeń usuwa obsługi zdarzeń i ustawia zdarzenie ukończenia.  
  
     `EnumerationCompleted` Proces wyliczania zatrzymuje program obsługi zdarzeń. Firma Microsoft obsługi tego zdarzenia zawierają mniej niż dziesięć urządzeń.  
  
    > [!TIP]
    >  W tym przykładzie używane wyrażenie lambda do definiowania wywołań zwrotnych. Umożliwia także obiekty funkcji (funktorów), wskaźniki funkcji lub [std::function](../standard-library/function-class.md) obiektów. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
8.  Uruchom proces wyliczania.  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. Poczekaj na wyliczenie zakończenie procesu i wydrukuj wiadomości. Wszystkie `ComPtr` i obiekty RAII pozostaw zakresu i są wydawane automatycznie.  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 Oto pełny przykład:  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-events.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **cl.exe wrl-consume-events.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)