---
title: 'Instrukcje: bezpośrednie tworzenie wystąpień składników biblioteki WRL | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0c0ea8537922c2458a48adf5a086dfec4b992f5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381110"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Porady: bezpośrednie tworzenie wystąpień składników biblioteki WRL

Dowiedz się, jak użyć Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL)[Microsoft::wrl:: Make](../windows/make-function.md) i [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) celu utworzenia instancji składnika z modułu, który Definiuje on.

Bezpośrednie utworzenie wystąpienia składników może zmniejszyć obciążenia, jeśli nie ma potrzeby tworzenia fabryk klas lub innych mechanizmów. Można utworzyć wystąpienie składnika bezpośrednio w obu aplikacji uniwersalnych platformy Windows i aplikacjach desktopowych.

Aby dowiedzieć się, jak Biblioteka szablonów C++ środowiska wykonawczego Windows umożliwiają tworzenie klasycznego składnika COM i tworzenia jego instancji z zewnętrznej aplikacji desktopowej, zobacz [porady: tworzenie klasycznego składnika COM](../windows/how-to-create-a-classic-com-component-using-wrl.md).

Ten dokument zawiera dwa przykłady. W pierwszym przykładzie użyto funkcji `Make` do utworzenia wystąpienia składnika. W drugim przykładzie użyto funkcji `MakeAndInitialize` do utworzenia wystąpienia składnika, które może się nie powieść podczas kompilacji. (Ponieważ COM zwykle korzysta wartości HRESULT, a nie wyjątków, do sygnalizowania błędów, typ COM zazwyczaj nie wyrzuca wyjątków z jej konstruktora. `MakeAndInitialize` umożliwia składnikowi sprawdzenie poprawności argumentów za pomocą metody `RuntimeClassInitialize`). Oba przykłady definiują podstawowy interfejs logowania i implementują ten interfejs za pomocą definicji klasy, która wypisuje komunikaty na konsoli.

> [!IMPORTANT]
> Nie można użyć **nowe** operatora do utworzenia wystąpienia składników Biblioteka szablonów C++ środowiska wykonawczego Windows. Dlatego zaleca się, aby zawsze używać `Make` lub `MakeAndInitialize` do bezpośredniego utworzenia składnika.

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Aby stworzyć i utworzyć instancję podstawowego składnika modułu logującego.

1. W programie Visual Studio, należy utworzyć **Aplikacja konsoli Win32** projektu. Nazwij projekt, na przykład *WRLLogger*.

2. Dodaj **plik Midl (.idl)** plik do projektu, nadaj plikowi nazwę `ILogger.idl`, a następnie dodaj ten kod:

   [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. Użyj poniższego kodu, aby zastąpić zawartość `WRLLogger.cpp`.

   [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Aby obsłużyć awarię konstruktora podstawowego składnika modułu logującego

1. Użyj następującego kodu, aby zamienić definicję klasy `CConsoleWriter`. Ta wersja posiada prywatną zmienną typu string i nadpisuje metodę `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` nie powiedzie się, jeśli nie powiedzie się wywołanie `SHStrDup`.

   [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. Użyj następującego kodu, aby zamienić definicję `wmain`. Ta wersja wykorzystuje `MakeAndInitialize` do utworzenia wystąpienia `CConsoleWriter` obiektu i sprawdza, czy wynik HRESULT.

   [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft::wrl:: Make](../windows/make-function.md)<br/>
[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)