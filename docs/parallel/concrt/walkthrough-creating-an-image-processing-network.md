---
title: 'Wskazówki: Tworzenie sieci przetwarzania obrazów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68b9aa25cef78780b0bb6f97d3cde1e27600481f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063422"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Wskazówki: tworzenie sieci przetwarzania obrazów

W tym dokumencie pokazano, jak utworzyć sieć bloki komunikatów asynchronicznych, wykonujących przetwarzanie obrazu.

Sieć Określa, jakie operacje do wykonania w przypadku obrazu na podstawie jego właściwości. W tym przykładzie użyto *przepływu danych* modelu do trasy obrazów za pośrednictwem sieci. W modelu przepływu danych niezależnie od składników programu komunikować się ze sobą, wysyłając komunikaty. Gdy składnik otrzymuje komunikat, jego wykonanie akcji, a następnie przekazać wynik tego działania, do innego składnika. Porównanie to za pomocą *przepływ sterowania* modelu, w której aplikacja używa struktury sterujące, na przykład, instrukcje warunkowe, pętli i tak dalej, aby kontrolować kolejność operacji w programie.

Tworzy sieci, która opiera się na przepływ danych *potoku* zadań. Każdy etap potoku wykonuje jednocześnie część całego zadania. Odpowiednio do tego jest do linii montażowej dla samochodów produkcji. Każdego pojazdu korzystał z linii montażowej, jedna stacja składa ramki, instaluje inny aparat i tak dalej. Po włączeniu wielu pojazdów do montażu jednocześnie linii montażowej zapewnia większą przepustowość niż łączenie pojazdów kompletnych jednego naraz.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu, przeczytaj następujące dokumenty:

- [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)

- [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

Zalecamy również, że rozumiesz podstawy GDI + przed rozpoczęciem tego instruktażu.

##  <a name="top"></a> Sekcje

Ten przewodnik zawiera następujące sekcje:

- [Definiowanie funkcji przetwarzania obrazów](#functionality)

- [Tworzenie sieci przetwarzania obrazów](#network)

- [Kompletny przykład](#complete)

##  <a name="functionality"></a> Definiowanie funkcji przetwarzania obrazów

W tej sekcji przedstawiono funkcje pomocy technicznej, które korzysta z sieci przetwarzania obrazów do pracy z obrazami, które są odczytywane z dysku.

Następujące funkcje `GetRGB` i `MakeColor`, wyodrębnianie i odpowiednio łączyć poszczególne składniki danego koloru.

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

Następującą funkcję `ProcessImage`, wywołania danej [std::function](../../standard-library/function-class.md) obiekt, aby przekształcić wartość koloru każdego piksela w GDI + [mapy bitowej](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap) obiektu. `ProcessImage` Używa funkcji [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm przetworzyć każdy wiersz mapy bitowej równolegle.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

Następujące funkcje `Grayscale`, `Sepiatone`, `ColorMask`, i `Darken`, wywołaj `ProcessImage` funkcję, aby przekształcić wartość koloru każdego piksela `Bitmap` obiektu. Każda z tych funkcji używa wyrażenia lambda do definiowania transformację koloru jednego piksela.

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

Poniższa funkcja `GetColorDominance`, wywołuje również `ProcessImage` funkcji. Jednak zamiast zmieniać wartość każdy kolor, ta funkcja używa [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) obiekty do obliczenia, czy składnika koloru czerwonego, zielonego lub niebieski większą obrazu.

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

Poniższa funkcja `GetEncoderClsid`, pobiera identyfikator klasy dla danego typu MIME kodera. Aplikacja korzysta z tej funkcji można pobrać kodera dla mapy bitowej.

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[Górnej](#top)]

##  <a name="network"></a> Tworzenie sieci przetwarzania obrazów

W tej sekcji opisano, jak utworzyć sieć bloki komunikatów asynchronicznych, wykonujących przetwarzania obrazu dla każdego obrazu JPEG (.jpg) w danym katalogu. Sieć wykonuje następujące operacje przetwarzania obrazów:

1. Dowolny obraz, który został utworzony przez Tom można przekonwertować w skali szarości.

1. Dla dowolnego obrazu, który ma dominujący kolor czerwony Usuń składniki zielonego i niebieskiego, a następnie ciemniejszy go.

1. Dla innego obrazu zastosowanie sepia tonowania.

Sieć dotyczy tylko pierwszej operacji przetwarzania obrazów, który pasuje do jednej z tych warunków. Na przykład jeśli obraz został utworzony przez Tom i czerwony jako koloru dominującego, obraz, który jest konwertowany tylko na skalę odcieni szarości.

Po sieci wykonuje każdej operacji przetwarzania obrazów, zapisuje obraz na dysku jako plik mapy bitowej (bmp).

Poniższe kroki pokazują jak utworzyć funkcję, która implementuje ten obraz przetwarzania sieci i ma zastosowanie tej sieci do każdego obrazu JPEG w danym katalogu.

#### <a name="to-create-the-image-processing-network"></a>Można utworzyć sieci przetwarzania obrazów

1. Tworzenie funkcji, `ProcessImages`, który przyjmuje nazwę katalogu na dysku.

   [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. W `ProcessImages` funkcji, Utwórz `countdown_event` zmiennej. `countdown_event` Klasy jest przedstawiony w dalszej części tego przewodnika.

   [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. Tworzenie [std::map](../../standard-library/map-class.md) obiekt, który kojarzy `Bitmap` obiekt z jego oryginalną nazwę pliku.

   [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. Dodaj następujący kod, aby zdefiniować członków sieci przetwarzania obrazów.

   [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. Dodaj następujący kod, aby połączyć sieć.

   [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. Dodaj następujący kod do wysyłania do głowy sieci pełną ścieżkę każdego pliku JPEG w katalogu.

   [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. Poczekaj, aż `countdown_event` zmiennej, aby osiągnąć zero.

   [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

W poniższej tabeli opisano elementy członkowskie w sieci.

|Element członkowski|Opis|
|------------|-----------------|
|`load_bitmap`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) obiekt, który ładuje `Bitmap` obiektu z dysku i doda wpis do `map` powiązania obiektu obrazu z oryginalną nazwą pliku.|
|`loaded_bitmaps`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiekt, który wysyła obrazy załadowane do filtrów przetwarzania obrazów.|
|`grayscale`|Element `transformer` obiektu, który konwertuje obraz, które były edytowane przez Tom na skalę odcieni szarości. Używa metadanych obrazu, aby określić jego autora.|
|`colormask`|A `transformer` obiekt, który usuwa składników koloru zielonego i niebieskiego z obrazów, które mają dominujący kolor czerwony.|
|`darken`|A `transformer` obiekt, który stopień obrazów, które mają dominujący kolor czerwony.|
|`sepiatone`|A `transformer` obiekt, który dotyczy sepia tonowania obrazy, które nie są tworzone przez Tom i nie są głównie czerwony.|
|`save_bitmap`|A `transformer` obiekt, który zapisuje przetworzonych `image` na dysku w postaci bitmapy. `save_bitmap` pobiera oryginalna nazwa pliku z `map` obiektu i zmiany jego rozszerzenie nazwy pliku .bmp.|
|`delete_bitmap`|A `transformer` obiekt, który zwalnia pamięć dla obrazów.|
|`decrement`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) obiekt, który działa jako terminala węzła w sieci. Jego zmniejsza `countdown_event` obiektu w celu zasygnalizowania do aplikacji głównej, że obraz został przetworzony.|

`loaded_bitmaps` Buforu komunikatu jest ważne, ponieważ jako `unbounded_buffer` obiektu oferuje `Bitmap` obiekty do wielu odbiorników. Kiedy blick docelowy akceptuje `Bitmap` obiektu `unbounded_buffer` obiektu, nie oferuje `Bitmap` obiektu do innych celów. W związku z tym, kolejność, w której obiekty do `unbounded_buffer` obiekt jest ważny. `grayscale`, `colormask`, I `sepiatone` komunikat bloki każdego Użyj filtru w celu akceptowania tylko niektórych `Bitmap` obiektów. `decrement` Buforu komunikatu jest ważne celem `loaded_bitmaps` buforu komunikatu, ponieważ akceptuje wszystkie `Bitmap` obiektów, które są odrzucane przez innych buforów komunikatów. `unbounded_buffer` Obiektu jest wymagany do propagowania wiadomości w kolejności. W związku z tym `unbounded_buffer` obiektu blokuje, dopóki nowy blok docelowy jest połączony i zaakceptuje wiadomość, jeśli brak bieżącego bloku docelowego akceptuje tej wiadomości.

Jeśli aplikacja wymaga wielu wiadomość blokuje proces wiadomości, a nie po prostu bloku jeden komunikat najpierw zaakceptuje wiadomość, możesz użyć inny typ bloku komunikatu, takich jak `overwrite_buffer`. `overwrite_buffer` Klasa przechowuje jeden komunikat w danym momencie, ale rozprzestrzenia się ten komunikat do każdego z jego elementów docelowych.

Poniższa ilustracja przedstawia sieci przetwarzania obrazów:

![Sieci przetwarzania obrazów](../../parallel/concrt/media/concrt_imageproc.png "concrt_imageproc")

`countdown_event` Obiekt w tym przykładzie umożliwia sieci przetwarzania obrazów, aby poinformować aplikacji głównej, gdy zostaną przetworzone wszystkie obrazy. `countdown_event` Klasy używa [concurrency::event](../../parallel/concrt/reference/event-class.md) obiekt do sygnalizowania, gdy wartość licznika osiągnie zero. Zwiększa wartość licznika głównej aplikacji, za każdym razem, gdy jej wysyła nazwę pliku do sieci. Terminalu węzeł zmniejsza sieci licznika po przetworzeniu każdego obrazu. Po aplikacji głównej przechodzi przez określony katalog, czeka `countdown_event` obiekt do sygnalizowania, że jego licznik osiągnęła wartość zero.

W poniższym przykładzie przedstawiono `countdown_event` klasy:

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[Górnej](#top)]

##  <a name="complete"></a> Kompletny przykład

Poniższy kod przedstawia kompletny przykład. `wmain` Funkcja zarządza GDI + biblioteki i wywołania `ProcessImages` pliki funkcji przetwarzającej JPEG `Sample Pictures` katalogu.

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

Poniższa ilustracja przedstawia przykładowe dane wyjściowe. Każdy obraz źródłowy przekracza jego odpowiedniego zmodyfikowany obraz.

![Przykładowe dane wyjściowe na przykład](../../parallel/concrt/media/concrt_imageout.png "concrt_imageout")

`Lighthouse` składowe, została utworzona przez Tom Alphin i dlatego jest konwertowany na skali szarości. `Chrysanthemum`, `Desert`, `Koala`, i `Tulips` ma czerwony jako dominującego koloru i w związku z tym składników kolor niebieski i zielony, usunięte i są przyciemniony. `Hydrangeas`, `Jellyfish`, i `Penguins` spełniających kryteria domyślne, dlatego sepia toned.

[[Górnej](#top)]

### <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `image-processing-network.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe /DUNICODE/ehsc/Link obrazów — przetwarzanie network.cpp gdiplus.lib**

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
