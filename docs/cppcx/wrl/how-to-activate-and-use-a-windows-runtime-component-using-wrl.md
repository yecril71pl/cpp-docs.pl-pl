---
title: 'Porady: uaktywnianie składnika środowiska wykonawczego systemu Windows za pomocą biblioteki WRL i korzystanie z niego'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 7f49c1362bea12576df6039b9e9f0b455cb4fae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213957"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Porady: uaktywnianie składnika środowiska wykonawczego systemu Windows za pomocą biblioteki WRL i korzystanie z niego

W tym dokumencie pokazano, jak za pomocą C++ biblioteki szablonów środowisko wykonawcze systemu Windows (WRL) zainicjować środowisko wykonawcze systemu Windows i jak aktywować składnik środowisko wykonawcze systemu Windows i korzystać z niego.

Aby użyć składnika, należy uzyskać wskaźnik interfejsu do typu, który jest implementowany przez składnik. Ponieważ podstawową technologią środowisko wykonawcze systemu Windows jest Component Object Model (COM), należy przestrzegać reguł COM, aby zachować wystąpienie typu. Na przykład należy zachować *liczbę odwołań* , która określa, kiedy typ jest usuwany z pamięci.

Aby uprościć korzystanie z środowisko wykonawcze systemu Windows, środowisko wykonawcze systemu Windows C++ Biblioteka szablonów udostępnia szablon inteligentnego wskaźnika, [ComPtr\<t >](comptr-class.md), który automatycznie wykonuje zliczanie odwołań. W przypadku deklarowania zmiennej Określ *identyfikator*`>` `ComPtr<`*Interface-Name* . Aby uzyskać dostęp do elementu członkowskiego interfejsu, Zastosuj do identyfikatora operator dostępu do elementów członkowskich (`->`) strzałek.

> [!IMPORTANT]
> Po wywołaniu funkcji interfejsu zawsze Przetestuj zwracaną wartość HRESULT.

## <a name="activating-and-using-a-windows-runtime-component"></a>Aktywowanie i używanie składnika środowisko wykonawcze systemu Windows

Poniższe kroki używają interfejsu `Windows::Foundation::IUriRuntimeClass`, aby pokazać, jak utworzyć fabrykę aktywacji dla składnika środowisko wykonawcze systemu Windows, utworzyć wystąpienie tego składnika i pobrać wartość właściwości. Pokazuje również, jak zainicjować środowisko wykonawcze systemu Windows. Kompletny przykład.

> [!IMPORTANT]
> Chociaż zwykle używasz biblioteki szablonów środowisko wykonawcze systemu Windows C++ w aplikacji platforma uniwersalna systemu Windows (platformy UWP), w tym przykładzie użyto aplikacji konsolowej na potrzeby ilustracji. Funkcje, takie jak `wprintf_s`, nie są dostępne w aplikacji platformy UWP. Aby uzyskać więcej informacji na temat typów i funkcji, których można użyć w aplikacji platformy UWP, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) oraz [Win32 i com for platformy UWP Apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Aby uaktywnić składnik środowisko wykonawcze systemu Windows i korzystać z niego

1. Dołącz (`#include`) wszystkie wymagane środowisko wykonawcze systemu Windows, środowisko wykonawcze systemu Windows C++ bibliotekę szablonów lub C++ nagłówki biblioteki standardowej.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   Zalecamy użycie dyrektywy `using namespace` w pliku CPP, aby kod był bardziej czytelny.

2. Zainicjuj wątek, w którym jest wykonywana aplikacja. Każda aplikacja musi zainicjować swój wątek i model wątkowości. Ten przykład używa klasy [Microsoft:: WRL:: otoki:: RoInitializeWrapper](roinitializewrapper-class.md) w celu zainicjowania środowisko wykonawcze systemu Windows i określa [RO_INIT_MULTITHREADED](/windows/win32/api/roapi/ne-roapi-ro_init_type) jako model wątkowości. Klasa `RoInitializeWrapper` wywołuje `Windows::Foundation::Initialize` podczas konstruowania i `Windows::Foundation::Uninitialize`, gdy zostanie zniszczona.

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   W drugiej instrukcji operator [RoInitializeWrapper:: HRESULT](roinitializewrapper-class.md#hresult) zwraca `HRESULT` z wywołania do `Windows::Foundation::Initialize`.

3. Utwórz *fabrykę aktywacji* dla interfejsu `ABI::Windows::Foundation::IUriRuntimeClassFactory`.

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Środowisko wykonawcze systemu Windows używa w pełni kwalifikowanych nazw do identyfikowania typów. `RuntimeClass_Windows_Foundation_Uri` parametr jest ciągiem dostarczonym przez środowisko wykonawcze systemu Windows i zawiera wymaganą nazwę klasy środowiska uruchomieniowego.

4. Zainicjuj zmienną [Microsoft:: WRL:: otoki:: HString](hstring-class.md) , która reprezentuje identyfikator URI `"https://www.microsoft.com"`.

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   W środowisko wykonawcze systemu Windows nie przydzielasz pamięci dla ciągu, który będzie używany przez środowisko wykonawcze systemu Windows. Zamiast tego środowisko wykonawcze systemu Windows tworzy kopię ciągu w buforze, który przechowuje i używa do operacji, a następnie zwraca dojście do tworzonego buforu.

5. Użyj metody fabryki `IUriRuntimeClassFactory::CreateUri`, aby utworzyć obiekt `ABI::Windows::Foundation::IUriRuntimeClass`.

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. Wywołaj metodę `IUriRuntimeClass::get_Domain`, aby pobrać wartość właściwości `Domain`.

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. Wydrukuj nazwę domeny w konsoli i wróć. Wszystkie obiekty `ComPtr` i RAII pozostawiają zakres i są automatycznie udostępniane.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   Funkcja [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer) pobiera podstawową postać Unicode ciągu identyfikatora URI.

Oto kompletny przykład:

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-component.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)
