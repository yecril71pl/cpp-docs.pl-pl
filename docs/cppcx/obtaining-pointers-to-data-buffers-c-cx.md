---
title: "Uzyskiwanie wskaźniki do buforów danych (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: db4f9370-dd95-4896-b5b8-4b202284f579
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 07e04a1adabab004ef64ed308d1222400192f235
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="obtaining-pointers-to-data-buffers-ccx"></a>Uzyskiwanie wskaźniki do buforów danych (C + +/ CX)
W środowisku wykonawczym systemu Windows [Windows::Storage::Streams::IBuffer](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ibuffer.aspx) interfejs umożliwia niezależny od języka, na podstawie strumienia dostępu buforów danych. W języku C++ raw wskaźnika do podstawowej tablicy typu byte można uzyskać za pomocą interfejsu IBufferByteAccess biblioteki środowiska uruchomieniowego systemu Windows, który jest zdefiniowany w robuffer.h. Za pomocą tej metody można zmodyfikować bajtów tablicy w miejscu bez wprowadzania żadnych niepotrzebnych kopie danych.  
  
 Na poniższym diagramie przedstawiono XAML elementu obrazu, którego źródłem jest [Windows::UI::Xaml::Media::Imaging WriteableBitmap](http://msdn.microsoft.com/%20library/windows/apps/windows.ui.xaml.media.imaging.writeablebitmap.aspx). Aplikację klienta, który jest zapisany w dowolnym języku można przekazać odwołanie do `WriteableBitmap` języka c++ kod, a następnie C++ użyciu odwołania można uzyskać w podstawowej buforu. W aplikacji platformy uniwersalnej systemu Windows, który jest napisany w języku C++ używając funkcji w poniższym przykładzie bezpośrednio w kodzie źródłowym bez pakowania składnika środowiska wykonawczego systemu Windows.  
  
 ![& C &43; 43; Kod bezpośrednie uzyskiwanie dostępu do danych pikseli](../cppcx/media/ibufferbyteaccessdiagram.png "IBufferByteAccessDiagram")  
  
## <a name="getpointertopixeldata"></a>GetPointerToPixelData  
 Akceptuje następującą metodę [Windows::Storage::Streams::IBuffer](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ibuffer.aspx) i zwraca nieprzetworzoną wskaźnik do podstawowej tablicy typu byte. Aby wywołać funkcję, należy przekazać w [WriteableBitmap::PixelBuffer](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.imaging.writeablebitmap.pixelbuffer.aspx) właściwości.  
  
```  
  
#include <wrl.h>  
#include <robuffer.h>  
using namespace Windows::Storage::Streams;  
using namespace Microsoft::WRL;  
typedef uint8 byte;  
// Retrieves the raw pixel data from the provided IBuffer object.  
// Warning: The lifetime of the returned buffer is controlled by  
// the lifetime of the buffer object that's passed to this method.  
// When the buffer has been released, the pointer becomes invalid  
// and must not be used.  
byte* Class1::GetPointerToPixelData(IBuffer^ pixelBuffer, unsigned int *length)  
{  
    if (length != nullptr)  
    {  
        *length = pixelBuffer ->Length;  
    }  
    // Query the IBufferByteAccess interface.  
    ComPtr<IBufferByteAccess> bufferByteAccess;  
    reinterpret_cast<IInspectable*>( pixelBuffer)->QueryInterface(IID_PPV_ARGS(&bufferByteAccess));  
  
    // Retrieve the buffer data.  
    byte* pixels = nullptr;  
    bufferByteAccess->Buffer(&pixels);  
    return pixels;  
}  
```  
  
## <a name="complete-example"></a>Kompletny przykład  
 W następujących krokach przedstawiono sposób tworzenia aplikacji platformy uniwersalnej systemu Windows C#, który przekazuje `WriteableBitmap` biblioteki DLL składnika C++ środowiska wykonawczego systemu Windows. Kod w języku C++ uzyskuje wskaźnik do buforu pikseli i wykonuje prostą modyfikację w miejscu na obrazie. Alternatywnie można utworzyć aplikacji klienckiej w Visual Basic, JavaScript lub C++ zamiast C#. Jeśli używasz języka C++, nie potrzebujesz składnika DLL; te metody można dodawać tylko bezpośrednio do klasy MainPage lub inna klasa zdefiniowana.  
  
#### <a name="create-the-client"></a>Tworzenie klienta  
  
1.  Szablon projektu pusta aplikacja umożliwia tworzenie aplikacji platformy uniwersalnej systemu Windows C#.  
  
2.  W MainPage.xaml  
  
    -   Użyj tego XAML, aby zamienić `Grid` elementu:  
  
        ```cpp  
        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">  
                <StackPanel HorizontalAlignment="Left" Margin="176,110,0,0" VerticalAlignment="Top" Width="932">  
                    <Image x:Name="Pic"/>  
                    <Button Content="Process Image" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Height="47" Click="Button_Click_1"/>  
                </StackPanel>  
            </Grid>  
        ```  
  
3.  In MainPage.xaml.cs  
  
    1.  Dodaj następujące deklaracje przestrzeni nazw:  
  
        ```  
        using Windows.Storage;  
        using Windows.Storage.FileProperties;  
        using Windows.UI.Xaml.Media.Imaging;  
        using Windows.Storage.Streams;  
        using Windows.Storage.Pickers;  
        ```  
  
    2.  Dodaj `WriteableBitmap` zmienną `MainPage` klasy i nadaj mu nazwę `m_bm`.  
  
        ```  
        private WriteableBitmap m_bm;  
        ```  
  
    3.  Użyj poniższego kodu, aby zamienić `OnNavigatedTo` szkieletu metody. Spowoduje to otwarcie selektora plików po uruchomieniu aplikacji. (Zwróć uwagę, że `async` — słowo kluczowe jest dodawany do sygnatury funkcji).  
  
        ```c#  
        async protected override void OnNavigatedTo(NavigationEventArgs e)  
                {  
                    FileOpenPicker openPicker = new FileOpenPicker();  
                    openPicker.ViewMode = PickerViewMode.Thumbnail;  
                    openPicker.SuggestedStartLocation = PickerLocationId.PicturesLibrary;  
                    openPicker.FileTypeFilter.Add(".jpg");  
                    openPicker.FileTypeFilter.Add(".jpeg");  
                    openPicker.FileTypeFilter.Add(".png");  
  
                    StorageFile file = await openPicker.PickSingleFileAsync();  
                    if (file != null)  
                    {  
                        // Get the size of the image for the WriteableBitmap constructor.  
                        ImageProperties props = await file.Properties.GetImagePropertiesAsync();  
                        m_bm = new WriteableBitmap((int)props.Height, (int)props.Width);  
                        m_bm.SetSource(await file.OpenReadAsync());  
                        Pic.Source = m_bm;  
                    }  
                    else  
                    {  
                      //  Handle error...  
                    }  
                }  
        ```  
  
    4.  Dodaj program obsługi zdarzeń kliknięcia przycisku. (Ponieważ `ImageManipCPP` odwołanie do przestrzeni nazw nie został utworzony, ale może mieć faliste podkreślenie w oknie edytora.)  
  
        ```  
        async private void Button_Click_1(object sender, RoutedEventArgs e)  
                {  
                    ImageManipCPP.Class1 obj = new ImageManipCPP.Class1();  
                    await obj.Negativize(m_bm);  
                    Pic.Source = m_bm;  
                }  
        ```  
  
#### <a name="create-the-c-component"></a>Tworzenie składnika C++  
  
1.  Dodaj nowy składnik C++ środowiska wykonawczego systemu Windows do istniejącego rozwiązania i nadaj mu nazwę `ImageManipCPP`. Dodaj odwołanie do niej w projekcie C# przez kliknięcie prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj**, **odwołania**.  
  
2.  W Class1.h  
  
    1.  Dodaj tę `typedef` w drugim wierszu, po prostu po `#pragma once`:  
  
        ```  
        typedef uint8 byte;  
  
        ```  
  
    2.  Dodaj `WebHostHidden` atrybutu powyżej początku `Class1` deklaracji.  
  
        ```  
        [Windows::Foundation::Metadata::WebHostHidden]  
        ```  
  
    3.  Dodaj publiczną metodę podpis `Class1`:  
  
        ```  
        Windows::Foundation::IAsyncAction^ Negativize(Windows::UI::Xaml::Media::Imaging::WriteableBitmap^ bm);  
        ```  
  
    4.  Dodaj podpis z `GetPointerToPixelData` metodę, która jest wyświetlana w starszych fragmentu kodu. Upewnij się, że ta metoda jest prywatny.  
  
3.  W Class1.cpp  
  
    1.  Dodaj te `#include` dyrektywy i deklaracje przestrzeni nazw:  
  
        ```  
  
        #include <ppltasks.h>  
        #include <wrl.h>  
        #include <robuffer.h>  
  
        using namespace Windows::Storage;  
        using namespace Windows::UI::Xaml::Media::Imaging;  
        using namespace Windows::Storage::Streams;  
        using namespace Microsoft::WRL;  
  
        ```  
  
    2.  Dodaj implementację `GetPointerToPixelData` z wcześniejszych fragmentu kodu.  
  
    3.  Dodaj implementację `Negativize`. Ta metoda tworzy efekt podobny filmu ujemna przez cofania wartość każdej wartości RGB w pikselach. Metoda wykonujemy asynchronicznego, ponieważ na większe obrazy może potrwać odczuwa ilość czasu, aby zakończyć.  
  
        ```  
        IAsyncAction^ Class1::Negativize(WriteableBitmap^ bm)  
        {  
            unsigned int length;  
            byte* sourcePixels = GetPointerToPixelData(bm->PixelBuffer, &length);  
            const unsigned int width = bm->PixelWidth;  
            const unsigned int height = bm->PixelHeight;  
  
            return create_async([this, width, height, sourcePixels]  
            {          
                byte* temp = sourcePixels;  
                for(unsigned int k = 0; k < height; k++)  
                {          
                    for (unsigned int i = 0; i < (width * 4); i += 4)  
                    {  
                        int pos = k * (width * 4) + (i);  
                        temp[pos] = ~temp[pos];  
                        temp[pos + 1] = ~temp[pos + 1] / 3;  
                        temp[pos + 2] = ~temp[pos + 2] / 2;  
                        temp[pos + 3] = ~temp[pos + 3];  
                    }  
                }  
            });  
  
        }  
        ```  
  
        > [!NOTE]
        >  Ta metoda może działać szybciej użycie AMP lub biblioteka równoległych wzorców do parallelize wykonać operację.  
  
4.  Upewnij się, czy ma co najmniej jeden obraz w folderze Obrazy, a następnie naciśnij klawisz F5, aby skompilować i uruchomić program.