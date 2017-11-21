---
title: "Porady: utworzenie wystąpienia składników biblioteki WRL bezpośrednio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6ecaebb2f846417f2fd3eeabdfe575d4d08a46fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Porady: bezpośrednie tworzenie wystąpień składników biblioteki WRL
Dowiedz się, jak używać systemu Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL)[Microsoft::WRL::Make](../windows/make-function.md) i [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) funkcji do utworzenia wystąpienia składnika z modułu który definiuje ją.  
  
 Bezpośrednie utworzenie wystąpienia składników może zmniejszyć obciążenia, jeśli nie ma potrzeby tworzenia fabryk klas lub innych mechanizmów. Można utworzyć wystąpienia składnika bezpośrednio w obu aplikacji platformy uniwersalnej systemu Windows i aplikacji klasycznych.  
  
 Aby dowiedzieć się, jak Biblioteka szablonów C++ środowiska wykonawczego systemu Windows umożliwiają tworzenie podstawowego składnika środowiska wykonawczego systemu Windows i utworzyć z zewnętrznych aplikacji platformy uniwersalnej systemu Windows, zobacz [wskazówki: Tworzenie podstawowego składnika środowiska wykonawczego systemu Windows](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md). Aby dowiedzieć się, jak Biblioteka szablonów C++ środowiska wykonawczego systemu Windows umożliwiają tworzenie klasycznego składnika COM i utworzyć z zewnętrznych aplikacji pulpitu, zobacz [porady: tworzenie klasycznego składnika COM](../windows/how-to-create-a-classic-com-component-using-wrl.md).  
  
 Ten dokument zawiera dwa przykłady. W pierwszym przykładzie użyto funkcji `Make` do utworzenia wystąpienia składnika. W drugim przykładzie użyto funkcji `MakeAndInitialize` do utworzenia wystąpienia składnika, które może się nie powieść podczas kompilacji. (Ponieważ COM zwykle korzysta z wartości `HRESULT`, a nie wyjątków do sygnalizowania błędów, typ COM zazwyczaj nie wyrzuca wyjątków z konstruktora. `MakeAndInitialize` umożliwia składnikowi sprawdzenie poprawności argumentów za pomocą metody `RuntimeClassInitialize`). Oba przykłady definiują podstawowy interfejs logowania i implementują ten interfejs za pomocą definicji klasy, która wypisuje komunikaty na konsoli.  
  
> [!IMPORTANT]
>  Nie można użyć `new` operatora do utworzenia wystąpienia składników Biblioteka szablonów C++ środowiska wykonawczego systemu Windows. Dlatego zaleca się, aby zawsze używać `Make` lub `MakeAndInitialize` do bezpośredniego utworzenia składnika.  
  
### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Aby stworzyć i utworzyć instancję podstawowego składnika modułu logującego.  
  
1.  W programie Visual Studio Utwórz **aplikacji konsoli Win32** projektu. Nazwa projektu, na przykład `WRLLogger`.  
  
2.  Dodaj **pliku Midl (.idl)** plików do projektu, określ nazwę pliku `ILogger.idl`, a następnie dodaj ten kod:  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  Zastąp zawartość WRLLogger.cpp następującym kodem.  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Aby obsłużyć awarię konstruktora podstawowego składnika modułu logującego  
  
1.  Użyj następującego kodu, aby zamienić definicję klasy `CConsoleWriter`. Ta wersja posiada prywatną zmienną typu string i nadpisuje metodę `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` nie powiedzie się, jeśli nie powiedzie się wywołanie `SHStrDup`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  Użyj następującego kodu, aby zamienić definicję `wmain`. Ta wersja wykorzystuje `MakeAndInitialize` do utworzenia wystąpienia obiektu `CConsoleWriter` i sprawdzenia wyniku `HRESULT`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów C++ środowiska wykonawczego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::WRL::Make](../windows/make-function.md)   
 [Microsoft::WRL::details::MakeAndInitialize](../windows/makeandinitialize-function.md)