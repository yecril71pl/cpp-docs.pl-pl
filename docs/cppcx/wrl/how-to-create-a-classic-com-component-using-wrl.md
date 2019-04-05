---
title: 'Instrukcje: Tworzenie klasycznego składnika COM za pomocą biblioteki WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: bb38f36cdd481e61d049f82159fdc24c3726f646
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031845"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Instrukcje: Tworzenie klasycznego składnika COM za pomocą biblioteki WRL

Zestaw Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL) służy do tworzenia podstawowych składników modelu COM do użycia w aplikacjach komputerowych, tylko dla aplikacji uniwersalnych platformy Windows (UWP). Tworzenie składników COM Biblioteka szablonów C++ środowiska uruchomieniowego Windows mogą wymagać mniejszej ilości kodu niż ATL. Aby uzyskać informacje na temat podzbiór modelu COM, który obsługuje Biblioteka szablonów C++ środowiska wykonawczego Windows, zobacz [Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL)](windows-runtime-cpp-template-library-wrl.md).

W tym dokumencie pokazano, jak na potrzeby tworzenia podstawowego składnika modelu COM Biblioteka szablonów C++ środowiska wykonawczego Windows. Chociaż można używać mechanizmu wdrażania, która najlepiej spełnia Twoje potrzeby, ten dokument zawiera również podstawowy sposób zarejestrowania i używania składnika COM z aplikacji klasycznej.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Na potrzeby tworzenia podstawowych klasycznego składnika COM Biblioteka szablonów C++ środowiska wykonawczego Windows

1. W programie Visual Studio, należy utworzyć **puste rozwiązanie** projektu. Nazwij projekt, na przykład `WRLClassicCOM`.

2. Dodaj **projekt systemu Win32** do rozwiązania. Nazwij projekt, na przykład `CalculatorComponent`. Na **ustawienia aplikacji** zaznacz **DLL**.

3. Dodaj **plik Midl (.idl)** pliku do projektu. Nazwa pliku, na przykład `CalculatorComponent.idl`.

4. Dodaj następujący kod do CalculatorComponent.idl:

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. W CalculatorComponent.cpp, zdefiniuj `CalculatorComponent` klasy. `CalculatorComponent` Klasa dziedziczy [Microsoft::WRL::RuntimeClass](runtimeclass-class.md). [Microsoft::WRL::RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md) Określa, że klasa jest pochodną [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) i nie [IInspectable](/windows/desktop/api/inspectable/nn-inspectable-iinspectable). (`IInspectable` jest dostępna tylko dla składników aplikacji środowiska wykonawczego Windows.) `CoCreatableClass` tworzy fabrykę dla klasy, które mogą być używane z funkcji takich jak [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. Użyj poniższego kodu, Zastąp kod w `dllmain.cpp`. Ten plik definiuje funkcje eksportu biblioteki DLL. Te funkcje używają [Microsoft::WRL::Module](module-class.md) klasy, aby zarządzać fabryki klas dla modułu.

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. Dodaj **plik definicji modułu (.def)** pliku do projektu. Nazwa pliku, na przykład `CalculatorComponent.def`. Ten plik zawiera konsolidator nazwy funkcji, które mają zostać wyeksportowane.

8. Dodaj następujący kod do CalculatorComponent.def:

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. Dodaj runtimeobject.lib do wiersza konsolidatora. Aby dowiedzieć się więcej, zobacz temat [. Pliki lib — wejście konsolidatora](../../build/reference/dot-lib-files-as-linker-input.md).

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Do używania składnika COM z aplikacji klasycznej

1. Zarejestruj składnik COM w rejestrze systemu Windows. Aby to zrobić, należy utworzyć plik wpisów rejestracji, nadaj jej nazwę `RegScript.reg`i Dodaj następujący tekst. Zastąp  *\<ścieżka biblioteki dll >* ze ścieżką do biblioteki DLL — na przykład `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`.

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

2. Uruchom RegScript.reg, albo dodaj go do swojego projektu **zdarzenia Postkompilacyjnego**. Aby uzyskać więcej informacji, zobacz [prekompilacji zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box).

3. Dodaj **Aplikacja konsoli Win32** projektu do rozwiązania. Nazwij projekt, na przykład `Calculator`.

4. Zastąp zawartość przy użyciu tego kodu `Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>Niezawodne programowanie

Ten dokument używa standardowych funkcji COM, aby pokazują, że umożliwia Biblioteka szablonów C++ środowiska wykonawczego Windows autora składnika modelu COM i udostępnienie go do każdej z możliwością korzystania z COM technologii. Można również używać typów Biblioteka szablonów C++ środowiska wykonawczego Windows takich jak [Microsoft::WRL::ComPtr](comptr-class.md) w aplikacji komputerowej do zarządzania okresem istnienia COM i innych obiektów. W poniższym kodzie użyto Biblioteka szablonów C++ środowiska wykonawczego Windows w celu zarządzania okresem istnienia `ICalculatorComponent` wskaźnika. `CoInitializeWrapper` Klasa jest otoka RAII, który gwarantuje, że biblioteki COM jest zwalniana i gwarantuje również, że okres istnienia biblioteki COM outlives `ComPtr` inteligentnego wskaźnika obiektu.

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>Zobacz także

[Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)