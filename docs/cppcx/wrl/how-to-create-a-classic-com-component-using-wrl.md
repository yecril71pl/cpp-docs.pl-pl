---
title: 'Porady: tworzenie klasycznego składnika COM za pomocą biblioteki WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: a1507a1a980dfd98a235b7456d73add955c02043
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213918"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Porady: tworzenie klasycznego składnika COM za pomocą biblioteki WRL

Za pomocą biblioteki szablonów środowisko wykonawcze systemu Windows C++ (WRL) można tworzyć podstawowe, klasyczne składniki com do użycia w aplikacjach klasycznych, a także używać ich na potrzeby aplikacji platforma uniwersalna systemu Windows (platformy UWP). Aby można było tworzyć składniki COM, Biblioteka szablonów C++ środowisko wykonawcze systemu Windows może wymagać mniej kodu niż ATL. Aby uzyskać informacje na temat podzbioru modelu COM obsługiwanego przez bibliotekę szablonów środowisko wykonawcze systemu Windows C++ , zobacz [szablon środowisko wykonawcze systemu Windows C++ Library (WRL)](windows-runtime-cpp-template-library-wrl.md).

W tym dokumencie przedstawiono sposób użycia biblioteki szablonów C++ środowisko wykonawcze systemu Windows do utworzenia podstawowego składnika modelu com. Mimo że można użyć mechanizmu wdrażania, który najlepiej odpowiada Twoim potrzebom, ten dokument zawiera również podstawowy sposób rejestrowania i używania składnika COM z poziomu aplikacji klasycznej.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Aby użyć biblioteki szablonów C++ środowisko wykonawcze systemu Windows do utworzenia podstawowego klasycznego składnika com

1. W programie Visual Studio Utwórz **pusty projekt rozwiązania** . Nazwij projekt, na przykład `WRLClassicCOM`.

2. Dodaj **projekt Win32** do rozwiązania. Nazwij projekt, na przykład `CalculatorComponent`. Na karcie **Ustawienia aplikacji** wybierz pozycję **dll**.

3. Dodaj plik **MIDL (. idl)** do projektu. Nazwij plik, na przykład `CalculatorComponent.idl`.

4. Dodaj ten kod do CalculatorComponent. idl:

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. W CalculatorComponent. cpp Zdefiniuj klasę `CalculatorComponent`. Klasa `CalculatorComponent` dziedziczy od [firmy Microsoft:: WRL:: RuntimeClass](runtimeclass-class.md). [Microsoft:: WRL:: RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md) określa, że Klasa pochodzi od [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , a nie [IInspectable](/windows/win32/api/inspectable/nn-inspectable-iinspectable). (`IInspectable` jest dostępny tylko dla środowisko wykonawcze systemu Windows składników aplikacji). `CoCreatableClass` tworzy fabrykę dla klasy, która może być używana z funkcjami, takimi jak funkcja [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. Użyj poniższego kodu, aby zamienić kod w `dllmain.cpp`. Ten plik definiuje funkcje eksportu biblioteki DLL. Te funkcje używają klasy [Microsoft:: WRL:: module](module-class.md) do zarządzania fabrykami klas dla modułu.

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. Dodaj plik **definicji modułu (. def)** do projektu. Nazwij plik, na przykład `CalculatorComponent.def`. Ten plik nadaje konsolidatorowi nazwy funkcji, które mają zostać wyeksportowane.

8. Dodaj ten kod do CalculatorComponent. def:

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. Dodaj środowisko runtimeobject. lib do linii konsolidatora. Aby dowiedzieć się, jak to zrobić, zobacz [. Pliki lib jako dane wejściowe konsolidatora](../../build/reference/dot-lib-files-as-linker-input.md).

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Aby użyć składnika COM z aplikacji klasycznej

1. Zarejestruj składnik COM przy użyciu rejestru systemu Windows. W tym celu Utwórz plik wpisów rejestracyjnych, nadaj mu nazwę `RegScript.reg`i Dodaj następujący tekst. Zastąp *\<Path dll >* ścieżką do biblioteki DLL, na przykład `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`.

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. Uruchom plik RegScript. reg lub Dodaj go do **zdarzenia po kompilacji**projektu. Aby uzyskać więcej informacji, zobacz [okno dialogowe zdarzenie przed kompilacją/wiersz polecenia zdarzenia po kompilacji](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box).

3. Dodaj projekt **aplikacji konsolowej Win32** do rozwiązania. Nazwij projekt, na przykład `Calculator`.

4. Użyj tego kodu, aby zastąpić zawartość `Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>Skuteczne programowanie

Ten dokument korzysta ze standardowych funkcji COM, aby wykazać, że można C++ użyć biblioteki szablonów środowisko wykonawcze systemu Windows do tworzenia składnika modelu COM i udostępnić go dla dowolnej technologii z obsługą modelu com. Aby zarządzać okresem istnienia modelu COM i innych obiektów, można również użyć środowisko wykonawcze systemu Windows C++ typów bibliotek szablonów, takich jak [Microsoft:: WRL:: ComPtr](comptr-class.md) w aplikacji klasycznej. Poniższy kod używa środowisko wykonawcze systemu Windows C++ biblioteki szablonów do zarządzania okresem istnienia wskaźnika `ICalculatorComponent`. Klasa `CoInitializeWrapper` jest otoką RAII, która gwarantuje, że biblioteka COM jest zwolniona, a także gwarantuje, że okres istnienia biblioteki modelu COM znajduje się na żywo `ComPtr` obiektu inteligentnego wskaźnika.

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)
