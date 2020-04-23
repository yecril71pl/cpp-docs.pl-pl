---
title: 'Przewodnik: tworzenie aplikacji platformy uniwersalnej systemu Windows z użyciem biblioteki WRL i platformy Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 272092982c5e9cc57f52043e08c8bd384c43ea96
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031514"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Przewodnik: tworzenie aplikacji platformy uniwersalnej systemu Windows z użyciem biblioteki WRL i platformy Media Foundation

> [!NOTE]
> W przypadku nowych aplikacji i składników platformy uniwersalnej systemu Windows zaleca się używanie [języka C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), nowej standardowej projekcji języka C++17 dla interfejsów API środowiska wykonawczego systemu Windows. C++/WinRT jest dostępny w systemie Windows 10 SDK od wersji 1803. C++/WinRT jest zaimplementowana w całości w plikach nagłówkowych i ma na celu zapewnienie najwyższej klasy dostępu do nowoczesnego interfejsu API systemu Windows.

W tym samouczku dowiesz się, jak używać biblioteki szablonów C++ (WRL) środowiska wykonawczego systemu Windows do tworzenia aplikacji platformy uniwersalnej systemu Windows (UWP), która korzysta z [programu Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

W tym przykładzie tworzy niestandardowe Media Foundation transformacji, która stosuje efekt skali szarości do obrazów, które są przechwytywane z kamery internetowej. Aplikacja używa języka C++ do definiowania transformacji niestandardowej i języka C# do przekształcenia przechwyconych obrazów.

> [!NOTE]
> Zamiast języka C#można również użyć języka JavaScript, Visual Basic lub C++, aby korzystać ze składnika przekształcania niestandardowego.

W większości przypadków można użyć języka C++/CX do utworzenia środowiska wykonawczego systemu Windows. Jednak czasami trzeba użyć WRL. Na przykład podczas tworzenia rozszerzenia multimediów dla programu Microsoft Media Foundation należy utworzyć składnik, który implementuje interfejsy ŚRODOWISKA WYKONAWCZEGO COM i Windows. Ponieważ C++/CX można tworzyć tylko obiekty środowiska wykonawczego systemu Windows, aby utworzyć rozszerzenie nośnika należy użyć WRL, ponieważ umożliwia implementację interfejsów wykonawczych COM i Windows.

> [!NOTE]
> Chociaż ten przykład kodu jest długi, pokazuje minimum, które jest wymagane do utworzenia przydatne media fundacji transformacji. Można go używać jako punktu wyjścia dla własnego przekształcenia niestandardowego. W tym przykładzie jest dostosowany z [rozszerzenia mediów przykład](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), który używa rozszerzenia multimediów do stosowania efektów wideo, dekodowanie wideo i tworzenie programów obsługi schematu, które produkują strumienie multimediów.

## <a name="prerequisites"></a>Wymagania wstępne

- W programie Visual Studio 2017 i nowszych obsługa platformy uniwersalnej systemu wizowego jest składnikiem opcjonalnym. Aby go zainstalować, otwórz Instalatora programu Visual Studio z menu Start systemu Windows i znajdź swoją wersję programu Visual Studio. Wybierz **pozycję Modyfikuj,** a następnie upewnij się, że kafelek **deweloperów platformy systemu Windows** jest zaznaczony. W obszarze **Składniki opcjonalne** sprawdź **narzędzia C++ dla platformy uniwersalnej systemu Windows (w wersji 141)** dla programu Visual Studio 2017 lub **narzędzia C++ dla platformy uniwersalnej systemu Windows (w wersji 142)** dla programu Visual Studio 2019. Następnie sprawdź wersję sdk systemu Windows, którego chcesz użyć.

- Środowisko pracy z czasem [wykonywania systemu Windows](/uwp/api/).

- Doświadczenie z COM.

- Kamera internetowa.

## <a name="key-points"></a>Kwestie kluczowe

- Aby utworzyć niestandardowy składnik Media Foundation, użyj pliku definicji języka MIDL (Microsoft Interface Definition Language), aby zdefiniować interfejs, zaimplementować ten interfejs, a następnie aktywować go z innych składników.

- I `namespace` `runtimeclass` atrybuty i `NTDDI_WIN8`wartość atrybutu [wersji](/windows/win32/Midl/version) są ważnymi częściami definicji MIDL dla składnika Media Foundation, który używa WRL.

- [Microsoft::WRL::RuntimeClass](runtimeclass-class.md) jest klasą podstawową niestandardowego składnika Media Foundation. Wartość wyliczenia [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix,](runtimeclasstype-enumeration.md) która jest dostarczana jako argument szablonu, oznacza klasę do użycia zarówno jako klasa środowiska wykonawczego systemu Windows, jak i jako klasyczna klasa środowiska wykonawczego COM.

- Macro [InspectableClass](inspectableclass-macro.md) implementuje podstawowe funkcje COM, `QueryInterface` takie jak zliczanie odwołań i metoda, i ustawia nazwę klasy środowiska uruchomieniowego i poziom zaufania.

- Użyj[klasy](module-class.md) Microsoft::WRL:: Moduł do zaimplementowania funkcji punktu wejścia biblioteki DLL, takich jak [DllGetActivationFactory](/windows/win32/winrt/functions), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)i [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Połącz bibliotekę DLL składnika z plikem runtimeobject.lib. Należy również określić [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) w wierszu konsolidatora, aby wygenerować metadane systemu Windows.

- Użyj odwołań do projektu, aby składniki WRL były dostępne dla aplikacji platformy uniwersalnej systemu Windows.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Aby użyć WRL do utworzenia składnika przekształcania skali szarości Media Foundation

1. W programie Visual Studio utwórz projekt **pustego rozwiązania.** Nazwij projekt, na przykład *MediaCapture*.

1. Dodaj projekt **biblioteki DLL (Universal Windows)** do rozwiązania. Nazwij projekt, na przykład *GrayscaleTransform*.

1. Dodaj plik **midl file (idl)** do projektu. Nazwij plik, na przykład *GrayscaleTransform.idl*.

1. Dodaj ten kod do grayscaleTransform.idl:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Użyj następującego kodu, aby `pch.h`zastąpić zawartość:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Dodaj nowy plik nagłówka do `BufferLock.h`projektu, nazwij go , a następnie zastąp zawartość tym kodem:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`nie jest używany w tym przykładzie. Można go usunąć z projektu, jeśli chcesz.

1. Użyj następującego kodu, aby `GrayscaleTransform.cpp`zastąpić zawartość:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Dodaj nowy plik definicji modułu do `GrayscaleTransform.def`projektu, nazwij go , a następnie dodaj ten kod:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Użyj następującego kodu, aby `dllmain.cpp`zastąpić zawartość:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. W oknie dialogowym **Strony właściwości** projektu ustaw następujące właściwości **konsolidatora.**

   1. W obszarze **Wprowadzanie**, dla `GrayScaleTransform.def` **pliku definicji modułu,** określ .

   1. Również **Input**w obszarze `runtimeobject.lib` `mfuuid.lib`Input `mfplat.lib` , add , i do **właściwości Additional Dependencies.**

   1. W obszarze **Metadane systemu Windows**ustaw **pozycję Generuj metadane systemu Windows** na Tak **(/WINMD)**.

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Aby użyć składnika WRL niestandardowego programu Media Foundation z aplikacji języka C#

1. Dodaj nowy projekt **pustej aplikacji języka C# (Universal Windows)** do `MediaCapture` rozwiązania. Nazwij projekt, na przykład *MediaCapture*.

1. W **projekcie MediaCapture** dodaj odwołanie `GrayscaleTransform` do projektu. Aby dowiedzieć się, jak to zrobić, zobacz [Jak: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. W `Package.appxmanifest`obszarze , na karcie **Możliwości** wybierz **pozycję Mikrofon** i **kamera internetowa**. Obie funkcje są wymagane do robienia zdjęć z kamery internetowej.

1. W `MainPage.xaml`, dodaj ten kod do głównego elementu [siatki:](/uwp/api/windows.ui.xaml.controls.grid)

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Użyj następującego kodu, aby `MainPage.xaml.cs`zastąpić zawartość:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

Na poniższej `MediaCapture app`ilustracji przedstawiono plik .

![Aplikacja MediaCapture przechwytująca zdjęcie](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Następne kroki

W przykładzie pokazano, jak robić zdjęcia z domyślnej kamery internetowej po jednym naraz. Przykład [rozszerzenia multimediów](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) robi więcej. Pokazuje, jak wyliczyć urządzenia kamery internetowej i pracować z lokalnymi programami obsługi schematów i demonstruje dodatkowe efekty multimedialne, które działają zarówno na pojedyncze zdjęcia, jak i strumienie wideo.

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[Przykład rozszerzeń multimediów](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
