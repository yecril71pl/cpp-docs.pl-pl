---
title: 'Wskazówki: tworzenie sieci przetwarzania obrazów'
ms.date: 04/25/2019
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
ms.openlocfilehash: 03d95be8fae3565a51811357ed9553c3a2649674
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140757"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Wskazówki: tworzenie sieci przetwarzania obrazów

W tym dokumencie przedstawiono sposób tworzenia sieci asynchronicznych bloków komunikatów, które wykonują przetwarzanie obrazu.

Sieć określa, które operacje wykonać na obrazie na podstawie jego właściwości. W tym przykładzie zastosowano model *przepływu danych* do przesyłania obrazów za pośrednictwem sieci. W modelu przepływu danych niezależne składniki programu komunikują się ze sobą przez wysyłanie komunikatów. Gdy składnik odbiera komunikat, może wykonać pewne działania, a następnie przekazać wynik tej akcji do innego składnika. Porównaj ten element z modelem *przepływu sterowania* , w którym aplikacja używa struktur kontroli, na przykład instrukcji warunkowych, pętli i tak dalej, aby kontrolować kolejność operacji w programie.

Sieć oparta na przepływu danych tworzy *potok* zadań. Każdy etap potoku jednocześnie wykonuje część ogólnego zadania. Analogicznie do tego jest linia montażowa dla produkcji samochodów. Gdy każdy pojazd przechodzi przez linię zestawu, jedna stacja składa się z ramki, drugi instaluje aparat i tak dalej. Dzięki umożliwieniu jednoczesnego montażu wielu pojazdów, linia zestawu zapewnia lepszą przepływność niż Montaż kompletnych pojazdów pojedynczo.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z następującymi dokumentami:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

Zalecamy także zapoznanie się z podstawą interfejsu GDI+ przed rozpoczęciem tego instruktażu.

## <a name="top"></a>Poszczególne

Ten Instruktaż zawiera następujące sekcje:

- [Definiowanie funkcji przetwarzania obrazów](#functionality)

- [Tworzenie sieci przetwarzania obrazów](#network)

- [Kompletny przykład](#complete)

## <a name="functionality"></a>Definiowanie funkcji przetwarzania obrazów

W tej sekcji przedstawiono funkcje obsługi, które są używane przez sieć przetwarzania obrazu do pracy z obrazami odczytywanymi z dysku.

Poniższe funkcje, `GetRGB` i `MakeColor`, wyodrębnią i łączą poszczególne składniki danego koloru.

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

Poniższa funkcja, `ProcessImage`, wywołuje dany obiekt [std:: Function](../../standard-library/function-class.md) , aby przekształcić wartość koloru każdego piksela w obiekcie [mapy bitowej](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) GDI+. Funkcja `ProcessImage` używa algorytmu [współbieżności:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) , aby przetwarzać każdy wiersz mapy bitowej równolegle.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

Poniższe funkcje, `Grayscale`, `Sepiatone`, `ColorMask`i `Darken`, wywołują funkcję `ProcessImage`, aby przekształcić wartość koloru każdego piksela w obiekt `Bitmap`. Każda z tych funkcji używa wyrażenia lambda do definiowania przekształcenia koloru jednego piksela.

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

Następująca funkcja, `GetColorDominance`, wywołuje również funkcję `ProcessImage`. Jednak zamiast zmieniać wartości każdego koloru, ta funkcja używa obiektów [concurrency::Binding](../../parallel/concrt/reference/combinable-class.md) do obliczenia, czy składnik koloru czerwony, zielony lub niebieski jest zdominowany.

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

Następująca funkcja, `GetEncoderClsid`, pobiera identyfikator klasy dla danego typu MIME kodera. Aplikacja używa tej funkcji do pobierania kodera dla mapy bitowej.

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[Top](#top)]

## <a name="network"></a>Tworzenie sieci przetwarzania obrazów

W tej sekcji opisano sposób tworzenia sieci asynchronicznych bloków komunikatów, które wykonują przetwarzanie obrazu na każdym obrazie JPEG (. jpg) w danym katalogu. Sieć wykonuje następujące operacje związane z przetwarzaniem obrazów:

1. Dla każdego obrazu, który jest tworzony przez Tomasz, Konwertuj na skalę szarości.

1. Dla każdego obrazu, który ma kolor czerwony, należy usunąć składniki zielone i niebieskie, a następnie przyciemnić je.

1. W przypadku innych obrazów Zastosuj Sepia Toning.

Sieć stosuje tylko pierwsze operacje przetwarzania obrazu, które pasują do jednego z tych warunków. Na przykład, jeśli obraz jest tworzony przez Tomasz i ma kolor czerwony w kolorze dominującym, obraz jest konwertowany tylko na skalę szarości.

Gdy sieć wykonuje każdą operację przetwarzania obrazu, zapisuje obraz na dysku jako plik mapy bitowej (. bmp).

Poniższe kroki pokazują, jak utworzyć funkcję implementującą tę sieć przetwarzania obrazów i zastosować tę sieć do każdego obrazu JPEG w danym katalogu.

#### <a name="to-create-the-image-processing-network"></a>Aby utworzyć sieć przetwarzania obrazów

1. Utwórz funkcję `ProcessImages`, która pobiera nazwę katalogu na dysku.

   [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. W funkcji `ProcessImages` Utwórz zmienną `countdown_event`. Klasa `countdown_event` jest pokazana w dalszej części tego przewodnika.

   [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. Utwórz obiekt [std:: map](../../standard-library/map-class.md) , który kojarzy obiekt `Bitmap` z jego pierwotną nazwą pliku.

   [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. Dodaj następujący kod w celu zdefiniowania elementów członkowskich sieci przetwarzania obrazów.

   [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. Dodaj następujący kod, aby połączyć sieć.

   [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. Dodaj następujący kod, aby wysłać do szefa sieci pełna ścieżka każdego pliku JPEG w katalogu.

   [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. Poczekaj, aż zmienna `countdown_event` osiągnie wartość zero.

   [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

W poniższej tabeli opisano elementy członkowskie sieci.

|Członek|Opis|
|------------|-----------------|
|`load_bitmap`|Obiekt [concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) ładujący obiekt `Bitmap` z dysku i dodaje wpis do obiektu `map` w celu skojarzenia obrazu z jego pierwotną nazwą pliku.|
|`loaded_bitmaps`|Obiekt [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) , który wysyła załadowane obrazy do filtrów przetwarzania obrazu.|
|`grayscale`|Obiekt `transformer`, który konwertuje obrazy, które są tworzone przez Tomasz w skali szarości. Używa metadanych obrazu w celu określenia jego autora.|
|`colormask`|Obiekt `transformer`, który usuwa zieloną i niebieską składową koloru z obrazów, które mają kolor czerwony.|
|`darken`|Obiekt `transformer`, który ciemnieje obrazy, które są czerwone jako kolor dominujący.|
|`sepiatone`|Obiekt `transformer`, który stosuje Sepia Toning do obrazów, które nie są tworzone przez Tomasz i nie są w przeważającej stopniu czerwone.|
|`save_bitmap`|Obiekt `transformer`, który zapisuje przetworzoną `image` na dysk jako mapę bitową. `save_bitmap` pobiera oryginalną nazwę pliku z obiektu `map` i zmienia rozszerzenie nazwy pliku na BMP.|
|`delete_bitmap`|Obiekt `transformer`, który zwalnia pamięć dla obrazów.|
|`decrement`|Obiekt [concurrency:: Call](../../parallel/concrt/reference/call-class.md) , który działa jako węzeł terminalu w sieci. Zmniejsza on obiekt `countdown_event`, aby sygnalizować główną aplikację, że obraz został przetworzony.|

Bufor komunikatów `loaded_bitmaps` jest ważny, ponieważ jako obiekt `unbounded_buffer` oferuje `Bitmap` obiektów do wielu odbiorników. Gdy blok docelowy akceptuje obiekt `Bitmap`, obiekt `unbounded_buffer` nie oferuje tego obiektu `Bitmap` innym elementom docelowym. W związku z tym kolejność obiektów połączonych z obiektem `unbounded_buffer` jest ważna. Komunikaty `grayscale`, `colormask`i `sepiatone` są blokowane przy użyciu filtru, aby akceptować tylko niektóre obiekty `Bitmap`. Bufor komunikatów `decrement` jest ważnym elementem docelowym buforu komunikatów `loaded_bitmaps`, ponieważ akceptuje wszystkie `Bitmap` obiekty odrzucone przez pozostałe bufory komunikatów. Obiekt `unbounded_buffer` jest wymagany do propagowania komunikatów w określonej kolejności. W związku z tym obiekt `unbounded_buffer` jest blokowany do momentu, gdy nowy blok docelowy zostanie połączony z nim i akceptuje komunikat, jeśli żaden blok docelowy nie akceptuje tego komunikatu.

Jeśli aplikacja wymaga, aby wiele bloków komunikatów przetworzył komunikat, a nie tylko jeden blok komunikatów, który najpierw akceptuje komunikat, można użyć innego typu bloku komunikatów, takiego jak `overwrite_buffer`. Klasa `overwrite_buffer` przechowuje jeden komunikat w danym momencie, ale propaguje ten komunikat do każdego z jego obiektów docelowych.

Na poniższej ilustracji przedstawiono sieć przetwarzania obrazów:

![Sieć przetwarzania obrazów](../../parallel/concrt/media/concrt_imageproc.png "Sieć przetwarzania obrazów")

Obiekt `countdown_event` w tym przykładzie umożliwia sieci przetwarzania obrazu informowanie głównej aplikacji o przetworzeniu wszystkich obrazów. Klasa `countdown_event` używa obiektu [concurrency:: Event](../../parallel/concrt/reference/event-class.md) do sygnalizowania, gdy wartość licznika osiągnie zero. Główna aplikacja zwiększa licznik za każdym razem, gdy wysyła nazwę pliku do sieci. Węzeł terminalu sieci zmniejsza licznik po przetworzeniu każdego obrazu. Gdy aplikacja główna przejdzie do określonego katalogu, czeka na obiekt `countdown_event`, aby sygnalizować, że jego licznik osiągnął wartość zerową.

W poniższym przykładzie przedstawiono klasę `countdown_event`:

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[Top](#top)]

## <a name="complete"></a>Kompletny przykład

Poniższy kod przedstawia kompletny przykład. Funkcja `wmain` zarządza biblioteką GDI+ i wywołuje funkcję `ProcessImages`, aby przetwarzać pliki JPEG w katalogu `Sample Pictures`.

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

Na poniższej ilustracji przedstawiono przykładowe dane wyjściowe. Każdy obraz źródłowy znajduje się powyżej odpowiadającego mu zmodyfikowanego obrazu.

![Przykładowe dane wyjściowe dla przykładu](../../parallel/concrt/media/concrt_imageout.png "Przykładowe dane wyjściowe dla przykładu")

`Lighthouse` jest tworzony przez Tomasz Alphin i w związku z tym jest konwertowany na skalę szarości. `Chrysanthemum`, `Desert`, `Koala`i `Tulips` mają kolor czerwony, a w związku z tym, że elementy niebieskie i zielonego koloru są usuwane i przyciemniane. `Hydrangeas`, `Jellyfish`i `Penguins` pasują do domyślnych kryteriów i dlatego są Sepia toned.

[[Top](#top)]

### <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `image-processing-network.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**CL. exe/DUNICODE/EHsc Image-Processing-Network. cpp/link Gdiplus. lib**

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
