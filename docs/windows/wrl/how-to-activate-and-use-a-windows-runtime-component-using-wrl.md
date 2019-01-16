---
title: 'Instrukcje: Uaktywnianie składnika środowiska wykonawczego Windows, za pomocą biblioteki WRL i korzystanie'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 4b8ce40e6c28f952596cab48848873be91b73c95
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334828"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Instrukcje: Uaktywnianie składnika środowiska wykonawczego Windows, za pomocą biblioteki WRL i korzystanie

Ten dokument zawiera, jak użyć Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL), aby zainicjować środowisko wykonawcze Windows oraz sposobu aktywacji i używania składnika wykonawczego Windows.

Aby użyć składnika, należy uzyskać wskaźnik interfejsu do typu, który jest implementowany przez składnik. A ponieważ podstawową używaną technologią środowiska uruchomieniowego Windows Component Object Model (COM), należy przestrzegać reguł modelu COM, aby zachować wystąpienia tego typu. Na przykład, musisz utrzymywać *odwoływać się do liczby* określający, gdy typ jest usuwane z pamięci.

Aby uprościć używanie środowiska wykonawczego Windows, Biblioteka szablonów C++ środowiska wykonawczego Windows oferuje szablon inteligentnego wskaźnika, [ComPtr\<T >](comptr-class.md), który automatycznie wykonuje zliczanie odwołań. Kiedy Deklarujesz zmienną, określ `ComPtr<` *nazwę interfejsu* `>` *identyfikator*. Aby uzyskać dostęp do składowej interfejsu, operator dostępu do elementu członkowskiego strzałkę zastosować (`->`) z identyfikatorem.

> [!IMPORTANT]
> Po wywołaniu funkcji interfejsu, należy zawsze przetestować zwracanej wartości HRESULT.

## <a name="activating-and-using-a-windows-runtime-component"></a>Uaktywniania i używania składnika środowiska wykonawczego Windows

Następujące kroki użycia `Windows::Foundation::IUriRuntimeClass` interfejs pokazują, jak utworzyć fabrykę aktywacji dla składnika wykonawczego Windows, Utwórz wystąpienie tego składnika i pobrać wartości właściwości. Pokazują one również, jak zainicjować środowisko wykonawcze Windows. Pełny przykład poniżej.

> [!IMPORTANT]
> Mimo że zazwyczaj używa się Biblioteka szablonów C++ środowiska wykonawczego Windows, w aplikacji platformy uniwersalnej Windows (UWP), w tym przykładzie użyto aplikacji konsoli do celów informacyjnych. Funkcje takie jak `wprintf_s` nie są dostępne w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji na temat typów i funkcji, które można użyć w aplikacji platformy uniwersalnej systemu Windows, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) i [Win32 i COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Aby aktywować i używać składnika wykonawczego Windows

1. Obejmują (`#include`) wszystkie wymagane środowiska wykonawczego Windows, Biblioteka szablonów C++ środowiska wykonawczego Windows lub nagłówki standardowej biblioteki języka C++.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   Firma Microsoft zaleca używanie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.

2. Zainicjuj wątku, w którym aplikacja wykonuje. Każda aplikacja musi zostać zainicjowany jego wątku i modelu wątkowości. W tym przykładzie użyto [Microsoft::WRL::Wrappers::RoInitializeWrapper](roinitializewrapper-class.md) klasy można zainicjować aparatu plików wykonywalnych Windows i określa [RO_INIT_MULTITHREADED](https://msdn.microsoft.com/library/windows/apps/br224661.aspx) jako modelu wątkowości. `RoInitializeWrapper` Klasy wywołania `Windows::Foundation::Initialize` w konstrukcji, i `Windows::Foundation::Uninitialize` kiedy zostanie zniszczony.

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   W drugiej instrukcji [RoInitializeWrapper::HRESULT](roinitializewrapper-class.md#hresult) operator zwraca `HRESULT` z wywołania `Windows::Foundation::Initialize`.

3. Tworzenie *fabryką aktywacji* dla `ABI::Windows::Foundation::IUriRuntimeClassFactory` interfejsu.

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Środowisko wykonawcze Windows używana w pełni kwalifikowanych nazw typów. `RuntimeClass_Windows_Foundation_Uri` Parametru jest ciąg, który jest dostarczany przez środowisko wykonawcze Windows i zawiera nazwę klasy wymaganego środowiska uruchomieniowego.

4. Inicjowanie [Microsoft::WRL::Wrappers::HString](hstring-class.md) zmienna, która reprezentuje identyfikator URI `"http://www.microsoft.com"`.

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   Ze środowiska wykonawczego Windows nie przydzielaj pamięci ciągu używanego przez środowisko wykonawcze Windows. Zamiast tego środowiska uruchomieniowego Windows tworzy kopię ciągu w buforze, czy go przechowuje i używa dla operacji, a następnie zwraca dojście do buforu on utworzony.

5. Użyj `IUriRuntimeClassFactory::CreateUri` metoda fabryki umożliwiająca utworzenie `ABI::Windows::Foundation::IUriRuntimeClass` obiektu.

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. Wywołaj `IUriRuntimeClass::get_Domain` metodę, aby pobrać wartość `Domain` właściwości.

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. Drukuj nazwy domeny do konsoli i zwracają. Wszystkie `ComPtr` i obiektów RAII pozostaw zakresu są zwalniane, automatycznie.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   [WindowsGetStringRawBuffer](https://msdn.microsoft.com/library/windows/apps/br224636.aspx) funkcja pobiera podstawowej postaci Unicode ciąg identyfikatora URI.

Oto kompletny przykład:

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-component.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)