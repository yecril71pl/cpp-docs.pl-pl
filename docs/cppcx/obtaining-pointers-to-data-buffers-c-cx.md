---
title: Uzyskiwanie wskaźników do buforów danych (C++/CX)
ms.date: 11/19/2018
ms.assetid: db4f9370-dd95-4896-b5b8-4b202284f579
ms.openlocfilehash: 46a81fa9e3d278645b654dca3c652653f6c21037
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426380"
---
# <a name="obtaining-pointers-to-data-buffers-ccx"></a>Uzyskiwanie wskaźników do buforów danych (C++/CX)

W środowisku uruchomieniowym Windows [Windows::Storage::Streams::IBuffer](/uwp/api/windows.storage.streams.ibuffer) interfejs zapewnia dostęp do buforów danych oznacza niezależny od języka, na podstawie strumienia. W języku C++ można uzyskać surowy wskaźnik do podstawowego tablicy typu byte, za pomocą interfejsu IBufferByteAccess biblioteki środowiska uruchomieniowego Windows, która jest zdefiniowana w robuffer.h. Za pomocą tej metody można zmodyfikować bajt tablicy w miejscu bez wprowadzania żadnych niepotrzebne kopie danych.

Na poniższym diagramie przedstawiono XAML elementu obrazu, którego źródłem jest [Windows::UI::Xaml::Media::Imaging WriteableBitmap](/uwp/api/Windows.UI.Xaml.Media.Imaging.WriteableBitmap). Aplikacja kliencka, która jest napisana w dowolnym języku można przekazać odwołanie do `WriteableBitmap` języka c++ kodu, a następnie C++ można użyć odwołania można pobrać w podstawowej buforu. W aplikacji Universal Windows Platform, która jest napisana w języku C++ można użyć funkcji w poniższym przykładzie bezpośrednio w kodzie źródłowym, bez pakowanie w składniku Windows w czasie wykonywania.

![C&#43; &#43; kod, który uzyskuje dostęp do danych pikseli bezpośrednio](../cppcx/media/ibufferbyteaccessdiagram.png "C&#43; &#43; kod, który uzyskuje dostęp do danych pikseli bezpośrednio")

## <a name="getpointertopixeldata"></a>GetPointerToPixelData

Akceptuje następującą metodę [Windows::Storage::Streams::IBuffer](/uwp/api/windows.storage.streams.ibuffer) i zwraca surowy wskaźnik do podstawowego tablicy typu byte. Aby wywołać funkcję, należy przekazać w [WriteableBitmap::PixelBuffer](/uwp/api/windows.ui.xaml.media.imaging.writeablebitmap.pixelbuffer) właściwości.

```cpp
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

Poniższe kroki pokazują jak utworzyć aplikację platformy uniwersalnej Windows C#, która przekazuje `WriteableBitmap` do składnika środowiska uruchomieniowego Windows C++ biblioteki DLL. Kod C++ uzyskuje wskaźnik do buforu pikseli i wykonuje prostą modyfikację w miejscu na obrazie. Alternatywnie można utworzyć aplikację kliencką w języku Visual Basic, JavaScript lub C++, zamiast C#. Jeśli używasz języka C++, nie potrzebujesz składnika biblioteki DLL; metody te można dodać tylko bezpośrednio do klasy MainPage lub innej klasy, który zdefiniujesz.

#### <a name="create-the-client"></a>Tworzenie klienta

1. Aby utworzyć aplikację platformy uniwersalnej Windows C#, należy użyć szablonu projektu pustą aplikację.

1. W pliku MainPage.xaml

   - Użyj tego XAML, aby zamienić `Grid` elementu:

        ```xml
        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <StackPanel HorizontalAlignment="Left" Margin="176,110,0,0" VerticalAlignment="Top" Width="932">
                <Image x:Name="Pic"/>
                <Button Content="Process Image" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Height="47" Click="Button_Click_1"/>
            </StackPanel>
        </Grid>
        ```

1. W MainPage.xaml.cs

   1. Dodaj następujące deklaracje przestrzeni nazw:

        ```csharp
        using Windows.Storage;
        using Windows.Storage.FileProperties;
        using Windows.UI.Xaml.Media.Imaging;
        using Windows.Storage.Streams;
        using Windows.Storage.Pickers;
        ```

   1. Dodaj `WriteableBitmap` zmienną członkowską na `MainPage` klasy i nadaj mu nazwę `m_bm`.

        ```csharp
        private WriteableBitmap m_bm;
        ```

   1. Użyj poniższego kodu, aby zastąpić `OnNavigatedTo` szkieletu metody. Spowoduje to otwarcie selektora plików, po uruchomieniu aplikacji. (Zwróć uwagę, że `async` — słowo kluczowe jest dodawany do sygnatury funkcji).

        ```csharp
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

   1. Dodaj program obsługi zdarzeń kliknięcia przycisku. (Ponieważ `ImageManipCPP` odwołanie do przestrzeni nazw, które nie zostało utworzone, ale może mieć linią falistą w oknie edytora.)

        ```csharp
        async private void Button_Click_1(object sender, RoutedEventArgs e)
        {
            ImageManipCPP.Class1 obj = new ImageManipCPP.Class1();
            await obj.Negativize(m_bm);
            Pic.Source = m_bm;
        }
        ```

#### <a name="create-the-c-component"></a>Tworzenie składnika języka C++

1. Dodaj nowy składnik środowiska uruchomieniowego Windows C++ do istniejącego rozwiązania i nadaj mu nazwę `ImageManipCPP`. Dodaj odwołanie do niej w projekcie języka C# klikając prawym przyciskiem myszy nad tym projektem w **Eksploratora rozwiązań** i wybierając pozycję **Dodaj**, **odwołania**.

1. In Class1.h

   1. Dodaj tę `typedef` w drugim wierszu, po prostu po `#pragma once`:

        ```cpp
        typedef uint8 byte;
        ```

   1. Dodaj `WebHostHidden` atrybut tuż nad początku `Class1` deklaracji.

        ```cpp
        [Windows::Foundation::Metadata::WebHostHidden]
        ```

   1. Dodaj metodę publiczną podpisu `Class1`:

        ```cpp
        Windows::Foundation::IAsyncAction^ Negativize(Windows::UI::Xaml::Media::Imaging::WriteableBitmap^ bm);
        ```

   1. Dodaj podpis z `GetPointerToPixelData` metodę, która jest wyświetlana w starszych fragmencie kodu. Upewnij się, że ta metoda jest prywatna.

1. W Class1.cpp

   1. Dodaj następujące `#include` dyrektywy i deklaracje przestrzeni nazw:

        ```cpp
        #include <ppltasks.h>
        #include <wrl.h>
        #include <robuffer.h>

        using namespace Windows::Storage;
        using namespace Windows::UI::Xaml::Media::Imaging;
        using namespace Windows::Storage::Streams;
        using namespace Microsoft::WRL;
        ```

   1. Dodaj implementację `GetPointerToPixelData` z wcześniejszych fragmentu kodu.

   1. Dodaj implementację `Negativize`. Ta metoda tworzy efekt podobny filmu ujemna odwracając wartość każdej wartości RGB w pikselach. Metoda ułatwiamy asynchronicznego, ponieważ w przypadku większych obrazów może potrwać zauważalne ilość czasu na ukończenie.

        ```cpp
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
      > Ta metoda może być szybsze wykonywanie równoległe przetwarzanie operacji za pomocą AMP lub biblioteka równoległych wzorców.

1. Upewnij się, ma co najmniej jeden obraz w folderze Obrazy, a następnie naciśnij klawisz F5, aby skompilować i uruchomić program.
