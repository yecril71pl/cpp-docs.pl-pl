---
title: 'Porady: bezpośrednie tworzenie wystąpień składników biblioteki WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: f291e982d7f77c63821e5943a5867662ccd1b4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213905"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Porady: bezpośrednie tworzenie wystąpień składników biblioteki WRL

Dowiedz się, jak używać C++ biblioteki szablonów środowisko wykonawcze systemu Windows (WRL)[Microsoft:: WRL:: Make](make-function.md) i [Microsoft:: WRL::D etails:: MakeAndInitialize](makeandinitialize-function.md) Functions w celu utworzenia wystąpienia składnika z modułu, który go definiuje.

Bezpośrednie utworzenie wystąpienia składników może zmniejszyć obciążenia, jeśli nie ma potrzeby tworzenia fabryk klas lub innych mechanizmów. Można utworzyć wystąpienie składnika bezpośrednio w aplikacjach platforma uniwersalna systemu Windows i aplikacjach klasycznych.

Aby dowiedzieć się, jak C++ za pomocą biblioteki szablonów środowisko wykonawcze systemu Windows utworzyć klasyczny składnik com i utworzyć jego wystąpienie z zewnętrznej aplikacji klasycznej, zobacz [How to: Create an klasyczny model com](how-to-create-a-classic-com-component-using-wrl.md).

Ten dokument zawiera dwa przykłady. W pierwszym przykładzie użyto funkcji `Make` do utworzenia wystąpienia składnika. W drugim przykładzie użyto funkcji `MakeAndInitialize` do utworzenia wystąpienia składnika, które może się nie powieść podczas kompilacji. (Ponieważ COM zwykle używa wartości HRESULT zamiast wyjątków, aby wskazać błędy, typ COM zwykle nie jest zgłaszany z konstruktora. `MakeAndInitialize` umożliwia składnikowi sprawdzenie poprawności argumentów konstrukcyjnych za pomocą metody `RuntimeClassInitialize`.) Oba przykłady definiują podstawowy interfejs rejestratora i implementują ten interfejs przez zdefiniowanie klasy, która zapisuje komunikaty w konsoli.

> [!IMPORTANT]
> Nie można użyć operatora `new`, aby utworzyć wystąpienie C++ środowisko wykonawcze systemu Windows składników biblioteki szablonów. Dlatego zaleca się, aby zawsze używać `Make` lub `MakeAndInitialize` do bezpośredniego utworzenia składnika.

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Aby stworzyć i utworzyć instancję podstawowego składnika modułu logującego.

1. W programie Visual Studio Utwórz projekt **aplikacji konsolowej Win32** . Nazwij projekt, na przykład *WRLLogger*.

2. Dodaj plik **MIDL (. idl)** do projektu, nazwij plik `ILogger.idl`, a następnie Dodaj następujący kod:

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. Użyj poniższego kodu, aby zamienić zawartość `WRLLogger.cpp`.

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Aby obsłużyć awarię konstruktora podstawowego składnika modułu logującego

1. Użyj następującego kodu, aby zamienić definicję klasy `CConsoleWriter`. Ta wersja posiada prywatną zmienną typu string i nadpisuje metodę `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` nie powiedzie się, jeśli wywołanie `SHStrDup` nie powiedzie się.

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. Użyj następującego kodu, aby zamienić definicję `wmain`. Ta wersja używa `MakeAndInitialize`, aby utworzyć wystąpienie obiektu `CConsoleWriter` i sprawdza wynik HRESULT.

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft:: WRL:: Make](make-function.md)<br/>
[Microsoft:: WRL::D etails:: MakeAndInitialize](makeandinitialize-function.md)
