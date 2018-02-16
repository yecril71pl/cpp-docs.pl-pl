---
title: "Porady: uaktywnianie i korzystanie z składnika środowiska wykonawczego systemu Windows za pomocą biblioteki WRL | Dokumentacja firmy Microsoft"
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
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbdc9b583501bb0de08139acc78943c8c4d88a91
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Porady: uaktywnianie składnika środowiska wykonawczego systemu Windows za pomocą biblioteki WRL i korzystanie z niego
Ten dokument zawiera zainicjować środowiska uruchomieniowego systemu Windows przy użyciu systemu Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL) oraz sposobu uaktywnianie składnika środowiska wykonawczego systemu Windows i korzystanie.  
  
> [!NOTE]
>  W tym przykładzie aktywuje wbudowanych składników środowiska wykonawczego systemu Windows. Aby dowiedzieć się, jak utworzyć własne składnika, który można aktywować w podobny sposób, zobacz [wskazówki: Tworzenie podstawowego składnika środowiska wykonawczego systemu Windows](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md).  
  
 Użycie składnika, należy uzyskać wskaźnika interfejsu do typu, który jest implementowany przez składnik. I podstawową technologią środowiska uruchomieniowego systemu Windows jest składnik modelu COM (Object), dlatego należy wykonać reguły COM do obsługi wystąpienia typu. Na przykład trzeba zachować *odwołania liczba* określający, gdy typ są usuwane z pamięci.  
  
 Aby ułatwić korzystanie z środowiska uruchomieniowego systemu Windows, Biblioteka szablonów C++ środowiska wykonawczego systemu Windows zapewnia szablonu wskaźnika inteligentnego [comptr —\<T >](../windows/comptr-class.md), który automatycznie wykonuje liczenie odwołań. Gdy zmienna jest zadeklarowana, określ `ComPtr<` *Nazwa interfejsu* `>` *identyfikator*. Aby uzyskać dostęp do elementu członkowskiego interfejsu, zastosować operatora dostępu do elementu członkowskiego strzałkę (`->`) z identyfikatorem.  
  
> [!IMPORTANT]
>  Podczas wywoływania funkcji interfejsu należy zawsze przetestować `HRESULT` zwracają wartość.  
  
## <a name="activating-and-using-a-windows-runtime-component"></a>Aktywowanie i za pomocą składnika środowiska wykonawczego systemu Windows  
 Następujące kroki użyj `Windows::Foundation::IUriRuntimeClass` interfejsu pokazują, jak utworzyć fabryki aktywacji dla składnika środowiska wykonawczego systemu Windows, Utwórz wystąpienie tego składnika i pobrać wartości właściwości. Pokazują one również, jak zainicjować środowiska uruchomieniowego systemu Windows. Pełny przykład jest zgodna.  
  
> [!IMPORTANT]
>  Mimo że używasz zazwyczaj Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, w aplikacji Windows platformy Uniwersalnej, w tym przykładzie użyto aplikacji konsoli ilustracyjną. Funkcje, takie jak `wprintf_s` nie są dostępne w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji na temat typów i funkcje, których można użyć w aplikacji platformy uniwersalnej systemu Windows, zobacz [nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows w funkcji CRT](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) i [Win32 i COM dla aplikacji platformy UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Aby uaktywnianie składnika środowiska wykonawczego systemu Windows i korzystanie  
  
1.  Obejmują (`#include`) wymagane środowisko wykonawcze systemu Windows, Biblioteka szablonów C++ środowiska wykonawczego systemu Windows lub nagłówków standardowej biblioteki C++.  
  
     [!code-cpp[wrl-consume-component#2](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]  
  
     Zaleca się, że wykorzystanie `using namespace` dyrektywy w pliku .cpp, aby zwiększyć czytelność kodu.  
  
2.  Inicjowanie wątku, w którym aplikacja wykonuje. Każda aplikacja musi inicjować jego wątku i modelu wątkowości. W tym przykładzie użyto [Microsoft::WRL::Wrappers::RoInitializeWrapper](../windows/roinitializewrapper-class.md) zainicjować środowiska uruchomieniowego systemu Windows, określa [RO_INIT_MULTITHREADED](http://msdn.microsoft.com/library/windows/apps/br224661.aspx) jako modelu wątkowości. `RoInitializeWrapper` Klasy wywołania `Windows::Foundation::Initialize` w konstrukcji, i `Windows::Foundation::Uninitialize` kiedy zostanie zniszczony.  
  
     [!code-cpp[wrl-consume-component#3](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]  
  
     W drugim instrukcji [RoInitializeWrapper::HRESULT](../windows/roinitializewrapper-hresult-parens-operator.md) operator zwraca `HRESULT` z wywołania `Windows::Foundation::Initialize`.  
  
3.  Utwórz *fabryki aktywacji* dla `ABI::Windows::Foundation::IUriRuntimeClassFactory` interfejsu.  
  
     [!code-cpp[wrl-consume-component#4](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]  
  
     Środowisko wykonawcze systemu Windows używa nazwy w pełni kwalifikowane do identyfikacji typów. `RuntimeClass_Windows_Foundation_Uri` Jest ciągiem, są udostępniane przez środowisko wykonawcze systemu Windows, który zawiera nazwę klasy wymagane środowisko uruchomieniowe.  
  
4.  Inicjowanie [Microsoft::WRL::Wrappers::HString](../windows/hstring-class.md) zmienna, która reprezentuje identyfikator URI `"http://www.microsoft.com"`.  
  
     [!code-cpp[wrl-consume-component#6](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]  
  
     W środowisku wykonawczym systemu Windows nie przydzielić pamięci dla ciągu, który będzie używany przez środowisko wykonawcze systemu Windows. Zamiast tego środowiska uruchomieniowego systemu Windows tworzy kopię ciągu w buforze, czy obsługuje i używanym dla operacji, a następnie zwraca dojście do buforu on utworzony.  
  
5.  Użyj `IUriRuntimeClassFactory::CreateUri` metoda fabryki umożliwiająca utworzenie `ABI::Windows::Foundation::IUriRuntimeClass` obiektu.  
  
     [!code-cpp[wrl-consume-component#7](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]  
  
6.  Wywołanie `IUriRuntimeClass::get_Domain` metody do pobierania wartości `Domain` właściwości.  
  
     [!code-cpp[wrl-consume-component#8](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]  
  
7.  Wydrukuj nazwy domeny do konsoli i zwracać. Wszystkie `ComPtr` i obiekty RAII pozostaw zakresu i są wydawane automatycznie.  
  
     [!code-cpp[wrl-consume-component#9](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]  
  
     [WindowsGetStringRawBuffer](http://msdn.microsoft.com/library/windows/apps/br224636.aspx) funkcja pobiera podstawowego formularza Unicode w ciągu identyfikatora URI.  
  
 Oto pełny przykład:  
  
 [!code-cpp[wrl-consume-component#1](../windows/codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `wrl-consume-component.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe wrl korzystać component.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)