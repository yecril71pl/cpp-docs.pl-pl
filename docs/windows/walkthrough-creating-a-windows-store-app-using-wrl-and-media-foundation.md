---
title: "Wskazówki: Tworzenie aplikacji ze Sklepu Windows za pomocą biblioteki WRL i platformy Media Foundation | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eb26f38ece8c098e6f10ba2ec90738787cb20ff3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation"></a>Wskazówki: tworzenie aplikacji sklepu Windows Store z użyciem biblioteki WRL i platformy Media Foundation
Dowiedz się, jak używać systemu Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL) do tworzenia aplikacji platformy uniwersalnej systemu Windows, który używa [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197).  
  
 W tym przykładzie tworzy niestandardowe transformację Media Foundation ma zastosowanie efektu skali szarości obrazów, które są przechwytywane z kamery internetowej. Aplikacja używa C++ do definiowania przekształcenie niestandardowe i C#, aby użyć składnika do przekształcania przechwyconych obrazów.  
  
> [!NOTE]
>  Zamiast C# umożliwia także JavaScript, Visual Basic lub C++ korzystać składnik przekształcenie niestandardowe.  
  

 W większości przypadków można użyć C + +/ CX można utworzyć środowiska wykonawczego systemu Windows). Jednak czasami trzeba użyć WRL. Na przykład podczas tworzenia rozszerzenia nośnika dla Microsoft Media Foundation, musi utworzyć składnik, który implementuje interfejsy zarówno COM i środowiska wykonawczego systemu Windows. Ponieważ C + +/ CX można tworzyć tylko obiekty środowiska wykonawczego systemu Windows, aby utworzyć rozszerzenia nośnika należy użyć WRL, ponieważ dzięki implementacji interfejsów zarówno COM i środowiska wykonawczego systemu Windows.  

  
> [!NOTE]
>  Mimo że w tym przykładzie kodu jest długi, przedstawia minimum, które są wymagane, aby utworzyć użyteczne transformację Media Foundation. Można użyć jej jako punkt początkowy dla własnego niestandardowego przekształcenia. W tym przykładzie pochodzi z [przykład rozszerzeń z nośnika](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), używa rozszerzenia nośnika do zastosowania efektów wideo dekodowania wideo i Utwórz schemat programów obsługi, które wywołują strumieni nośnika.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   Obsługa przy użyciu z [środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/library/windows/apps/br211377.aspx).  
  
-   Środowisko z modelu COM.  
  
-   Kamera internetowa.  
  
## <a name="key-points"></a>Kwestie kluczowe  
  
-   Aby utworzyć niestandardowych składników platformy Media Foundation, użyj pliku definicji Microsoft interfejsu Definition Language (MIDL) do definiowania interfejsów, implementuje ten interfejs, a następnie dokonaj aktywowalnej z innymi składnikami.  
  
-   `namespace` i `runtimeclass` atrybutów, a `NTDDI_WIN8` [wersji](http://msdn.microsoft.com/en-us/66ac5cf3-2230-44fd-aaf6-8013e4a4ae81) wartość atrybutu są ważne części definicji MIDL składnika Media Foundation, który korzysta z biblioteki WRL.  
  
-   [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md) jest klasą bazową dla niestandardowych składników platformy Media Foundation. [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia, które jest dostępne jako argument szablonu, oznacza klasy do użycia klasy środowiska wykonawczego systemu Windows oraz w klasycznego modelu COM klasy środowiska wykonawczego.  
  
-   [Inspectableclass —](../windows/inspectableclass-macro.md) makro implementuje podstawowe funkcje COM, takie jak liczenie odwołań i `QueryInterface` — metoda i zestawów środowiska uruchomieniowego Nazwa klasy i poziomu zaufania.  
  
-   Użyj Microsoft::wrl —::[klasy modułu](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/b4acf5de-2f4c-4c8b-b5ff-9140d023ecbe/locales/en-US) do implementacji funkcji punktu wejścia biblioteki DLL, takich jak [DllGetActivationFactory](http://msdn.microsoft.com/library/br205771.aspx), [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368\(v=vs.85\).aspx), i [ Metody DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/ms680760\(v=vs.85\).aspx).  
  
-   Połącz runtimeobject.lib biblioteki DLL składnika. Określ również [/WINMD](../cppcx/compiler-and-linker-options-c-cx.md) w linii konsolidatora do generowania metadanych systemu Windows.  
  
-   Użyj odwołania do projektu Aby udostępnić składników biblioteki WRL do aplikacji platformy uniwersalnej systemu Windows.  
  
### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Do użycia biblioteki WRL, aby utworzyć skali szarości Media Foundation Przekształcenie składnika  
  
1.  W programie Visual Studio Utwórz **puste rozwiązanie** projektu. Nazwa projektu, na przykład `MediaCapture`.  
  
2.  Dodaj **DLL (aplikacje ze Sklepu Windows)** projektu do rozwiązania. Nazwa projektu, na przykład `GrayscaleTransform`.  
  
3.  Dodaj **pliku Midl (.idl)** plik do projektu. Nazwa pliku, na przykład `GrayscaleTransform.idl`.  
  
4.  Dodaj ten kod do GrayscaleTransform.idl.  
  
     [!code-cpp[wrl-media-capture#1](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]  
  
5.  Aby zastąpić zawartość pch.h, należy użyć poniższego kodu.  
  
     [!code-cpp[wrl-media-capture#2](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]  
  
6.  Dodaj nowy plik nagłówka do projektu, nadaj jej nazwę `BufferLock.h`, a następnie dodaj ten kod:  
  
     [!code-cpp[wrl-media-capture#3](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]  
  
7.  GrayscaleTransform.h nie jest używany w tym przykładzie. Możesz usunąć go z projektu, jeśli chcesz.  
  
8.  Aby zastąpić zawartość GrayscaleTransform.cpp, należy użyć poniższego kodu.  
  
     [!code-cpp[wrl-media-capture#4](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]  
  
9. Dodaj nowy plik definicji modułu do projektu, nadaj jej nazwę `GrayscaleTransform.def`, a następnie dodaj ten kod:  
  
   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```   
  
10. Aby zastąpić zawartość dllmain.cpp, należy użyć poniższego kodu.  
  
     [!code-cpp[wrl-media-capture#6](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]  
  
11. W projekcie **strony właściwości** okna dialogowego należy ustawić następującą **konsolidatora** właściwości.  
  
    1.  W obszarze **dane wejściowe**, dla **plik definicji modułu**, określ `GrayScaleTransform.def`.  
  
    2.  Również w obszarze **dane wejściowe**, Dodaj `runtimeobject.lib`, `mfuuid.lib`, i `mfplatf.lib` do **dodatkowe zależności** właściwości.  
  
    3.  W obszarze **metadanych systemu Windows**ustaw **Generowanie metadanych systemu Windows** do **tak (/ WINMD)**.  
  
### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Aby użyć WRL niestandardowych składników platformy Media Foundation z aplikacji C#  
  
1.  Dodaj nową **C# pusta aplikacja (XAML)** projektu do `MediaCapture` rozwiązania. Nazwa projektu, na przykład `MediaCapture`.  
  
2.  W **MediaCapture** projekt, Dodaj odwołanie do `GrayscaleTransform` projektu. Aby dowiedzieć się więcej, zobacz temat [porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).  
  
3.  W Package.appxmanifest na **możliwości** wybierz opcję **mikrofon** i **kamery internetowej**. Obie możliwości są wymagane do przechwytywania zdjęć z kamery internetowej.  
  
4.  W MainPage.xaml, Dodaj ten kod do katalogu głównego [siatki](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) elementu:  
  
     [!code-xml[wrl-media-capture#7](../windows/codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]  
  
5.  Użyć poniższego kodu, aby zastąpić zawartość MainPage.xaml.cs.  
  
     [!code-cs[wrl-media-capture#8](../windows/codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]  
  
 Na poniższej ilustracji przedstawiono MediaCapture aplikacji.  
  
 ![Przechwytywanie zdjęcie aplikacji MediaCapture](../windows/media/wrl_media_capture.png "WRL_Media_Capture")  
  
## <a name="next-steps"></a>Następne kroki  
 W przykładzie Przechwytywanie zdjęć z kamery domyślne jedną naraz. [Przykład rozszerzeń z nośnika](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) jest więcej. Pokazuje, jak wyliczyć urządzeń kamery internetowej i pracy z lokalnym systemem obsługi, a pokazuje efekty dodatkowego nośnika, które działają na poszczególnych zdjęć i strumieni wideo.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów C++ środowiska wykonawczego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197)   
 [Przykład rozszerzeń z nośnika](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)