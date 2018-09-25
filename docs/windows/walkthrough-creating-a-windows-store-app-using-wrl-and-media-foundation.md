---
title: 'Przewodnik: Tworzenie aplikacji platformy uniwersalnej systemu Windows z użyciem biblioteki WRL i platformy Media Foundation | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9858ebe9affb47d61114bde072645f7002849ec7
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169466"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Przewodnik: Tworzenie aplikacji platformy uniwersalnej systemu Windows z użyciem biblioteki WRL i platformy Media Foundation

Dowiedz się, jak używać Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL) do tworzenia aplikacji uniwersalnych platformy Windows (UWP), która używa [Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk).

Ten przykład tworzy niestandardowe przekształcenia Media Foundation ma zastosowanie efektu skali szarości obrazy, które są przechwytywane z kamery internetowej. Aplikacja używa języka C++, aby zdefiniować niestandardowe przekształcenia i C# na potrzeby przekształcania obrazy przechwycone przez składnik.

> [!NOTE]
> Zamiast C# umożliwia także JavaScript, Visual Basic lub C++ z składnika niestandardowe przekształcenia.

W większości przypadków można użyć C + +/ CX, aby utworzyć środowiska wykonawczego Windows. Jednak czasami trzeba użyć biblioteki WRL. Na przykład gdy tworzysz rozszerzeniu usług media dla Microsoft Media Foundation, należy utworzyć składnik, który implementuje interfejsy modelu COM i środowiska wykonawczego Windows. Ponieważ C + +/ CX można tworzyć tylko obiekty Windows Runtime, aby utworzyć rozszerzenie nośnika należy użyć biblioteki WRL ponieważ umożliwia to implementacja interfejsy modelu COM i środowiska wykonawczego Windows.

> [!NOTE]
> Chociaż ten przykład kodu jest długa, przedstawia minimum, które są wymagane do utworzenia przydatne przekształcenie Media Foundation. Służy jako punkt wyjścia dla własnych niestandardowych przekształcenia. W tym przykładzie są zaczerpnięte z [przykład rozszerzeń z nośnika](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), rozszerzenia nośnik używa stosowanie efektów do wideo, dekodowanie wideo i tworzenie programów do obsługi systemu, które tworzą strumienie multimediów.

## <a name="prerequisites"></a>Wymagania wstępne

- Doświadczenie z [Windows Runtime](https://msdn.microsoft.com/library/windows/apps/br211377.aspx).

- Środowisko w modelu COM.

- Kamera internetowa.

## <a name="key-points"></a>Kwestie kluczowe

- Aby utworzyć niestandardowych składników platformy Media Foundation, należy użyć pliku definicji języka definicji interfejsu Microsoft (MIDL) do definiowania interfejsów, implementują ten interfejs, a następnie dokonaj aktywowalnej od innych składników.

- `namespace` i `runtimeclass` atrybutów, a `NTDDI_WIN8` [wersji](/windows/desktop/Midl/version) wartość atrybutu są ważne elementy definicji MIDL składnika platformy Media Foundation, który korzysta z biblioteki WRL.

- [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md) jest klasą bazową dla niestandardowego składnika platformy Media Foundation. [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia, która jest podawana jako argument szablonu, oznacza klasy do użycia zarówno jako klasę środowiska wykonawczego Windows, jak i w postaci klasycznego klasy środowiska uruchomieniowego COM.

- [InspectableClass](../windows/inspectableclass-macro.md) — makro implementuje podstawowe funkcje COM, takich jak zliczanie odwołań i `QueryInterface` metoda i zestawy środowiska uruchomieniowego Nazwa klasy i poziom zaufania.

- Użyj Microsoft::WRL::[klasy modułu](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/b4acf5de-2f4c-4c8b-b5ff-9140d023ecbe) do implementacji funkcji punktu wejścia biblioteki DLL, takie jak [DllGetActivationFactory](https://msdn.microsoft.com/library/br205771.aspx), [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow), i [ DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Połączyć runtimeobject.lib biblioteki DLL składnika. Również określić [/WINMD](../cppcx/compiler-and-linker-options-c-cx.md) w linii konsolidatora do generowania metadanych Windows.

- Użyj odwołania do projektu udostępnić składników biblioteki WRL dla aplikacji platformy uniwersalnej systemu Windows.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Używać składnik przekształcać WRL utworzyć skali szarości Media Foundation

1. W programie Visual Studio, należy utworzyć **puste rozwiązanie** projektu. Nazwij projekt, na przykład *MediaCapture*.

1. Dodaj **biblioteki DLL (Windows Universal)** projektu do rozwiązania. Nazwij projekt, na przykład *GrayscaleTransform*.

1. Dodaj **plik Midl (.idl)** pliku do projektu. Nazwa pliku, na przykład *GrayscaleTransform.idl*.

1. Dodaj następujący kod do GrayscaleTransform.idl:

   [!code-cpp[wrl-media-capture#1](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Użyj poniższego kodu, aby zastąpić zawartość `pch.h`:

   [!code-cpp[wrl-media-capture#2](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Dodaj nowy plik nagłówkowy do projektu, nadaj jej nazwę `BufferLock.h`, a następnie zastąp zawartość przy użyciu tego kodu:

   [!code-cpp[wrl-media-capture#3](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h` nie jest używana w tym przykładzie. Możesz usunąć go z projektu, jeśli chcesz.

1. Użyj poniższego kodu, aby zastąpić zawartość `GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Dodaj nowy plik definicji modułu do projektu, nadaj jej nazwę `GrayscaleTransform.def`, a następnie dodaj ten kod:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Użyj poniższego kodu, aby zastąpić zawartość `dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. W projekcie **stron właściwości** okna dialogowego pole, ustaw następujące **konsolidatora** właściwości.

   1. W obszarze **dane wejściowe**, aby uzyskać **plik definicji modułu**, określ `GrayScaleTransform.def`.

   1. Również w **dane wejściowe**, Dodaj `runtimeobject.lib`, `mfuuid.lib`, i `mfplat.lib` do **dodatkowe zależności** właściwości.

   1. W obszarze **metadanych Windows**ustaw **Generowanie metadanych Windows** do **tak (/ WINMD)**.

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Aby użyć biblioteki WRL niestandardowych składników platformy Media Foundation z aplikacją C#

1. Dodaj nową **C# pusta aplikacja (Windows Universal)** projekt `MediaCapture` rozwiązania. Nazwij projekt, na przykład *MediaCapture*.

1. W **MediaCapture** projektu, Dodaj odwołanie do `GrayscaleTransform` projektu. Aby dowiedzieć się więcej, zobacz temat [porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. W `Package.appxmanifest`na **możliwości** zaznacz **mikrofon** i **kamery internetowej**. Obie funkcje są wymagane do przechwycenia zdjęcia z kamery internetowej.

1. W `MainPage.xaml`, Dodaj następujący kod do katalogu głównego [siatki](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) elementu:

   [!code-xml[wrl-media-capture#7](../windows/codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Użyj poniższego kodu, aby zastąpić zawartość `MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../windows/codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

Poniższa ilustracja przedstawia `MediaCapture app`.

![Aplikacja MediaCapture Przechwytywanie zdjęcia](../windows/media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Następne kroki

W przykładzie pokazano, jak przechwycić fotografie pochodzące z kamery internetowej domyślne, jeden na raz. [Przykład rozszerzeń z nośnika](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) ma większe. Pokazuje, jak wyliczyć urządzeń kamery internetowej i pracować z lokalnego systemu obsługi i przedstawia skutki dodatkowego nośnika, które działają zarówno w przypadku poszczególnych fotografii, jak i strumieni wideo.

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk)<br/>
[Przykład rozszerzeń z nośnika](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)