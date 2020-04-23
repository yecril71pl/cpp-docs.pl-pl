---
title: Uzyskiwanie wskaźników do buforów danych (C++/CX)
ms.date: 11/19/2018
ms.assetid: db4f9370-dd95-4896-b5b8-4b202284f579
ms.openlocfilehash: 9e60adc4163e96349f6f4bafa919944e5d8d5b51
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032372"
---
# <a name="obtaining-pointers-to-data-buffers-ccx"></a>Uzyskiwanie wskaźników do buforów danych (C++/CX)

W czasie wykonywania systemu Windows interfejs [Windows::Storage::Streams::IBuffer](/uwp/api/windows.storage.streams.ibuffer) zapewnia neutralne dla języka, oparte na strumieniu środki dostępu do buforów danych. W języku C++ można uzyskać surowy wskaźnik do podstawowej tablicy bajtów przy użyciu interfejsu IBufferByteAccess biblioteki środowiska wykonawczego systemu Windows, który jest zdefiniowany w robuffer.h. Za pomocą tego podejścia można zmodyfikować tablicy bajtów w miejscu bez dokonywania żadnych niepotrzebnych kopii danych.

Na poniższym diagramie przedstawiono element obrazu XAML, którego źródłem jest [Windows::UI::Xaml::Media::Imaging WriteableBitmap](/uwp/api/windows.ui.xaml.media.imaging.writeablebitmap). Aplikacja kliencka, która jest napisana w dowolnym `WriteableBitmap` języku można przekazać odwołanie do kodu C++, a następnie C++ można użyć odwołania, aby uzyskać w buforze źródłowym. W aplikacji platformy uniwersalnej systemu Windows, która jest napisana w języku C++, można użyć funkcji w poniższym przykładzie bezpośrednio w kodzie źródłowym bez pakowania go w składniku środowiska wykonawczego systemu Windows.

![C&#43;&#43; kod, który uzyskuje bezpośredni dostęp do danych pikseli](../cppcx/media/ibufferbyteaccessdiagram.png "C&#43;&#43; kod, który uzyskuje bezpośredni dostęp do danych pikseli")

## <a name="getpointertopixeldata"></a>GetPointerToPixelData

Następująca metoda akceptuje [system Windows::Storage::Streams::IBuffer](/uwp/api/windows.storage.streams.ibuffer) i zwraca nieprzetworzony wskaźnik do podstawowej tablicy bajtów. Aby wywołać funkcję, przekaż w [WriteableBitmap::PixelBuffer](/uwp/api/windows.ui.xaml.media.imaging.writeablebitmap.pixelbuffer) właściwości.

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

Poniższe kroki pokazują, jak utworzyć aplikację uniwersalną `WriteableBitmap` platformy systemu Windows w języku C#, która przekazuje a do biblioteki DLL składnika środowiska wykonawczego systemu Windows W+. Kod C++ uzyskuje wskaźnik do buforu pikseli i wykonuje prostą modyfikację w miejscu obrazu. Alternatywnie można utworzyć aplikację kliencką w języku Visual Basic, JavaScript lub C++ zamiast języka C#. Jeśli używasz języka C++, nie potrzebujesz biblioteki DLL składnika; można po prostu dodać te metody bezpośrednio do MainPage klasy lub innej klasy, które można zdefiniować.

#### <a name="create-the-client"></a>Tworzenie klienta

1. Użyj szablonu pustej aplikacji, aby utworzyć aplikację uniwersalną platformy systemu Windows w języku C#.

1. W pliku MainPage.xaml

   - Użyj tego XAML, `Grid` aby zastąpić element:

        ```xml
        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <StackPanel HorizontalAlignment="Left" Margin="176,110,0,0" VerticalAlignment="Top" Width="932">
                <Image x:Name="Pic"/>
                <Button Content="Process Image" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Height="47" Click="Button_Click_1"/>
            </StackPanel>
        </Grid>
        ```

1. w MainPage.xaml.cs

   1. Dodaj te deklaracje obszaru nazw:

        ```csharp
        using Windows.Storage;
        using Windows.Storage.FileProperties;
        using Windows.UI.Xaml.Media.Imaging;
        using Windows.Storage.Streams;
        using Windows.Storage.Pickers;
        ```

   1. Dodaj `WriteableBitmap` zmienną elementu `MainPage` członkowskiego do `m_bm`klasy i nazwij ją .

        ```csharp
        private WriteableBitmap m_bm;
        ```

   1. Użyj następującego kodu, `OnNavigatedTo` aby zastąpić skrót metody. Spowoduje to otwarcie selektora plików po uruchomieniu aplikacji. (Zwróć uwagę, że `async` słowo kluczowe jest dodawane do podpisu funkcji).

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

   1. Dodaj program obsługi zdarzeń dla kliknięcia przycisku. (Ponieważ `ImageManipCPP` odwołanie do obszaru nazw nie zostało jeszcze utworzone, może mieć faliste podkreślenie w oknie edytora).

        ```csharp
        async private void Button_Click_1(object sender, RoutedEventArgs e)
        {
            ImageManipCPP.Class1 obj = new ImageManipCPP.Class1();
            await obj.Negativize(m_bm);
            Pic.Source = m_bm;
        }
        ```

#### <a name="create-the-c-component"></a>Tworzenie składnika C++

1. Dodaj nowy składnik środowiska wykonawczego systemu Windows języka C++ do istniejącego rozwiązania i nadaj jego `ImageManipCPP`nazwę . Dodaj odwołanie do niego w projekcie C#, klikając prawym przyciskiem myszy ten projekt w **Eksploratorze rozwiązań** i wybierając pozycję **Dodaj**, **Odwołanie**.

1. W klasie 1.h

   1. Dodaj `typedef` to w drugiej linii, zaraz po `#pragma once`:

        ```cpp
        typedef uint8 byte;
        ```

   1. Dodaj `WebHostHidden` atrybut tuż nad początkiem `Class1` deklaracji.

        ```cpp
        [Windows::Foundation::Metadata::WebHostHidden]
        ```

   1. Dodaj ten podpis `Class1`metody publicznej do:

        ```cpp
        Windows::Foundation::IAsyncAction^ Negativize(Windows::UI::Xaml::Media::Imaging::WriteableBitmap^ bm);
        ```

   1. Dodaj podpis z `GetPointerToPixelData` metody, która jest wyświetlana we wcześniejszym fragmentie kodu. Upewnij się, że ta metoda jest prywatna.

1. W klasie1.cpp

   1. Dodaj `#include` te dyrektywy i deklaracje obszaru nazw:

        ```cpp
        #include <ppltasks.h>
        #include <wrl.h>
        #include <robuffer.h>

        using namespace Windows::Storage;
        using namespace Windows::UI::Xaml::Media::Imaging;
        using namespace Windows::Storage::Streams;
        using namespace Microsoft::WRL;
        ```

   1. Dodaj implementację `GetPointerToPixelData` z wcześniejszego fragmentu kodu.

   1. Dodaj implementację `Negativize`programu . Ta metoda tworzy efekt, który przypomina film ujemny, cofając wartość każdej wartości RGB w pikselu. Robimy metodę asynchroniczne, ponieważ na większych obrazów może to zająć zauważalną ilość czasu, aby zakończyć.

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
      > Ta metoda może działać szybciej, jeśli używasz AMP lub biblioteki wzorców równoległych do równoległości operacji.

1. Upewnij się, że masz co najmniej jedno zdjęcie w folderze obrazów, a następnie naciśnij klawisz F5, aby skompilować i uruchomić program.
