---
title: "Wskazówki: Tworzenie sieci przetwarzania obrazów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b709179cb5bc0fefa3f342374c792656fa1e934
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Wskazówki: tworzenie sieci przetwarzania obrazów
Ten dokument przedstawia sposób tworzenia sieci bloki komunikatów asynchronicznych, które przetwarzania obrazu.  
  
 Sieci określa, jakie operacje do wykonania w przypadku obrazu na podstawie jego właściwości. W tym przykładzie użyto *przepływu danych* modelu do trasy obrazów za pośrednictwem sieci. W modelu przepływu danych niezależnie od składników programu komunikować się ze sobą przy wysyłaniu wiadomości. Gdy składnik odbiera wiadomości, jego wykonanie akcji, a następnie przekazać wynik tego działania do innego składnika. Porównaj te z *sterowania przepływem* modelu, w którym aplikacja używa struktury sterujące, na przykład, warunkowe instrukcje pętli i tak dalej, aby określić kolejność operacji w programie.  
  
 Tworzy sieci, która jest oparta na przepływ danych *potoku* zadań. Każdy etap potoku wykonuje jednocześnie części ogólnej zadania. Odpowiednio do tego zestawu dla jest wiersz samochodów produkcyjnym. Każdy vehicle przechodzi przez wiersz zestawu, jednej stacji składana ramki, instaluje inny aparat i tak dalej. Przez włączenie wielu pojazdów do jednocześnie, wiersz zestawu zapewnia większą przepustowość niż zebrania pojazdów kompletnych jednym naraz.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj następujące dokumenty przed skorzystaniem z tego przewodnika:  
  
-   [Bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Instrukcje: korzystanie z filtra bloku komunikatów](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
-   [Przewodnik: tworzenie agenta przepływu danych](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
  
 Zalecamy również że rozumiesz podstawowe informacje o [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] przed skorzystaniem z tego przewodnika.  
  
##  <a name="top"></a>Sekcje  
 Ten przewodnik zawiera następujące sekcje:  
  
-   [Definiowanie funkcji przetwarzania obrazu](#functionality)  
  
-   [Tworzenie sieci przetwarzania obrazów](#network)  
  
-   [Pełny przykład](#complete)  
  
##  <a name="functionality"></a>Definiowanie funkcji przetwarzania obrazu  
 W tej sekcji przedstawiono funkcje obsługi sieci przetwarzania obrazów używanych do pracy z obrazami, które są odczytywane z dysku.  
  
 Następujące funkcje `GetRGB` i `MakeColor`, Wyodrębnij i odpowiednio łączenie pojedynczych składników danego koloru.  
  
 [!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]  
  

 Następująca funkcja `ProcessImage`, wywołania danego [std::function](../../standard-library/function-class.md) obiekt, aby przekształcić wartość koloru każdego piksela [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [mapy bitowej](https://msdn.microsoft.com/library/ms534420.aspx) obiektu. `ProcessImage` Używa [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm przetwarzania każdego wiersza mapy bitowej równolegle.  

  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]  
  
 Następujące funkcje `Grayscale`, `Sepiatone`, `ColorMask`, i `Darken`, wywołaj `ProcessImage` funkcji, aby przekształcić wartość koloru każdego piksela `Bitmap` obiektu. Każda z tych funkcji używa wyrażenia lambda do definiowania transformacja kolorów jednego piksela.  
  
 [!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]  
  
 Następująca funkcja `GetColorDominance`, wymaga także `ProcessImage` funkcji. Zamiast zmiana wartości każdego koloru, ta funkcja nie korzysta jednak [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) obiekty do obliczenia, czy składnik kolor czerwony, zielony lub niebieski dominuje obrazu.  
  
 [!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]  
  
 Następująca funkcja `GetEncoderClsid`, pobiera identyfikator klasy dla danego typu MIME kodera. Aplikacja używa tej funkcji można pobrać koder dla mapy bitowej.  
  
 [!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]  
  
 [[Górnej](#top)]  
  
##  <a name="network"></a>Tworzenie sieci przetwarzania obrazów  
 W tej sekcji opisano, jak utworzyć sieć bloki komunikatów asynchronicznych, które przetwarzania obrazu na każdym [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] obrazu (jpg) w podanym katalogu. Sieć wykonuje następujące operacje przetwarzania obrazów:  
  
1.  Dla żadnego obrazu, który został utworzony przez niestandardowy należy przekonwertować na skali szarości.  
  
2.  Dla dowolnego obrazu, który ma dominującą kolor czerwony Usuń składniki zielonemu i niebieskiemu, a następnie Ciemniej go.  
  
3.  Zastosować sepia tonowania innego obrazu.  
  
 Sieć dotyczy tylko pierwszej operacji przetwarzania obrazów, który pasuje do jednej z tych warunków. Na przykład jeśli obraz został utworzony przez niestandardowy i jego dominującą kolor czerwony, obraz jest tylko konwertowana na skali szarości.  
  
 Po każdej operacji przetwarzania obrazów są wykonywane w sieci, zapisuje obraz na dysku jako plik mapa bitowa (bmp).  
  
 Poniższe kroki pokazują, jak utworzyć funkcję, która implementuje tej sieci przetwarzania obrazów i dotyczą tej sieci do każdego [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] obrazu w podanym katalogu.  
  
#### <a name="to-create-the-image-processing-network"></a>Można utworzyć sieci przetwarzania obrazów  
  
1.  Utwórz funkcję, `ProcessImages`, który pobiera nazwę katalogu na dysku.  
  
     [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]  
  
2.  W `ProcessImages` funkcji, należy utworzyć `countdown_event` zmiennej. `countdown_event` Klasy przedstawiono w dalszej części tego przewodnika.  
  
     [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]  
  
3.  Utwórz [std::map](../../standard-library/map-class.md) obiekt, który kojarzy `Bitmap` obiekt z jego oryginalną nazwę pliku.  
  
     [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]  
  
4.  Dodaj następujący kod, aby zdefiniować elementów członkowskich sieci przetwarzania obrazów.  
  
     [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]  
  
5.  Dodaj następujący kod, aby połączyć się z siecią.  
  
     [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]  
  
6.  Dodaj następujący kod do wysyłania do head sieci pełną ścieżkę [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] pliku w katalogu.  
  
     [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]  
  
7.  Poczekaj, aż `countdown_event` zmiennej, aby osiągnąć zero.  
  
     [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]  
  
 W poniższej tabeli opisano elementy członkowskie w sieci.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`load_bitmap`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) obiektu, który ładuje `Bitmap` obiektu z dysku i dodaje wpis do `map` obiektu obrazu z oryginalną nazwą pliku.|  
|`loaded_bitmaps`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) obiekt, który wysyła obrazy załadowane do filtrów przetwarzania obrazu.|  
|`grayscale`|A `transformer` obiekt, który konwertuje obrazów, które były edytowane przez niestandardowy do skali szarości. Aby ustalić jego autora używa metadanych obrazu.|  
|`colormask`|A `transformer` obiekt, który usuwa zielony i niebieskiemu składnikowi koloru z obrazów, które mają dominującą kolor czerwony.|  
|`darken`|A `transformer` obiekt, który przyciemnia obrazów, które mają dominującą kolor czerwony.|  
|`sepiatone`|A `transformer` obiekt, który dotyczy sepia tonowania obrazów, które nie były edytowane przez niestandardowy i nie są głównie czerwony.|  
|`save_bitmap`|A `transformer` obiekt, który zapisuje przetworzonych `image` na dysku jako mapy bitowej. `save_bitmap`pobiera oryginalna nazwa pliku z `map` obiektu i zmiany .bmp rozszerzenie nazwy pliku.|  
|`delete_bitmap`|A `transformer` obiekt, który zwalnia pamięć dla obrazów.|  
|`decrement`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) obiekt, który działa jako węzeł terminali w sieci. Go zmniejsza `countdown_event` obiektu sygnalizują do aplikacji głównej, że obraz został przetworzony.|  
  
 `loaded_bitmaps` Bufor komunikatów jest ważne, ponieważ jako `unbounded_buffer` obiekt oferuje `Bitmap` obiektów, aby wiele odbiorników. Gdy blok docelowy akceptuje `Bitmap` obiektu `unbounded_buffer` obiektu nie oferuje który `Bitmap` obiektu do innych celów. W związku z tym kolejności, w której obiekty do `unbounded_buffer` obiekt jest ważne. `grayscale`, `colormask`, I `sepiatone` komunikat bloki każdego zastosować filtr do akceptowania tylko dla określonych `Bitmap` obiektów. `decrement` Bufor komunikatów jest ważne docelowym `loaded_bitmaps` buforu komunikatu, ponieważ akceptuje on wszystkie `Bitmap` obiektów, które zostały odrzucone prze buforów komunikatów. `unbounded_buffer` Propagację wiadomości w kolejności wymagany jest obiekt. W związku z tym `unbounded_buffer` obiektu blokuje dopóki nowy blok docelowy jest połączony i akceptuje komunikat, jeśli nie bieżący blok docelowy akceptuje tej wiadomości.  
  
 Jeśli aplikacja wymaga wielu wiadomości blokuje procesu wiadomości, zamiast tylko bloku jeden komunikat najpierw akceptuje wiadomości, inny typ bloku wiadomości, można użyć takich jak `overwrite_buffer`. `overwrite_buffer` Klasa przechowuje jeden komunikat w czasie, ale jego propaguje tej wiadomości do każdego z jego elementów docelowych.  
  
 Na poniższej ilustracji przedstawiono sieć przetwarzania obrazu:  
  
 ![Sieci przetwarzania obrazów](../../parallel/concrt/media/concrt_imageproc.png "concrt_imageproc")  
  
 `countdown_event` Obiektu w tym przykładzie umożliwia sieci przetwarzania obrazów poinformowanie aplikacji głównej po przetworzeniu wszystkich obrazów. `countdown_event` Klasy używa [concurrency::event](../../parallel/concrt/reference/event-class.md) obiektu, która sygnalizuje, gdy wartość licznika osiągnie wartość zero. Aplikacji głównej zwiększa licznik za każdym razem, gdy jego wysyła nazwę pliku do sieci. Węzeł terminali zmniejsza sieci licznika po przetworzeniu każdego obrazu. Po aplikacji głównej przechodzi przez określony katalog, oczekuje na `countdown_event` obiektu, która sygnalizuje, że jego licznika osiągnęła wartość zero.  
  
 W poniższym przykładzie przedstawiono `countdown_event` klasy:  
  
 [!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]  
  
 [[Górnej](#top)]  
  
##  <a name="complete"></a>Pełny przykład  
 Poniższy kod przedstawia pełny przykład. `wmain` Zarządza funkcja [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] biblioteki i wywołania `ProcessImages` funkcja procesu [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] plików `Sample Pictures` katalogu.  
  
 [!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]  
  
 Na poniższej ilustracji przedstawiono przykładowe dane wyjściowe. Każdego obrazu źródłowego jest powyżej jej odpowiednie zmodyfikowany obraz.  
  
 ![Przykładowe dane wyjściowe, na przykład](../../parallel/concrt/media/concrt_imageout.png "concrt_imageout")  
  
 `Lighthouse`został utworzony przez Alphin Tomasz i dlatego jest konwertowana na skali szarości. `Chrysanthemum`, `Desert`, `Koala`, i `Tulips` ma dominującą kolor czerwony i w związku z tym składniki kolor niebieski i zielony usunięte i są przyciemniane. `Hydrangeas`, `Jellyfish`, i `Penguins` spełniających kryteria domyślne, dlatego sepia toned.  
  
 [[Górnej](#top)]  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `image-processing-network.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe /DUNICODE/ehsc/Link obrazu przetwarzania network.cpp gdiplus.lib**  
  
## <a name="see-also"></a>Zobacz też  
 [Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
