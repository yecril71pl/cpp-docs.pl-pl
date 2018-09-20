---
title: Grafika (C++ AMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97c673e564a91447854dc02a18ced0b4f0061a9f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408222"
---
# <a name="graphics-c-amp"></a>Grafika (C++ AMP)

C++ AMP zawiera kilka interfejsów API w [Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) przestrzeni nazw, która umożliwia dostęp do obsługi tekstur w procesorach GPU. Niektóre typowe scenariusze są następujące:

- Możesz użyć [tekstury](../../parallel/amp/reference/texture-class.md) klasy jako kontener danych dla obliczeń i wykorzystać *przestrzenne umiejscowienie* z pamięci podręcznej tekstury oraz układy w sprzęcie procesora GPU. Przestrzenne umiejscowienie jest właściwością elementów danych są fizycznie blisko siebie nawzajem.

- Środowisko wykonawcze zapewnia skuteczne współdziałanie z modułami cieniującymi poza obliczeniowymi. Pikseli, wierzchołków, mozaikowania i programów do cieniowania powłoki często tworzą lub wykorzystują tekstury, które można użyć w obliczeniach z C++ AMP.

- Interfejs graficzny API w bibliotece C++ AMP zapewnia alternatywne sposoby dostępu do buforów upakowaną słowo. Tekstury, które mają formaty reprezentujące *tekseli* (elementy tekstury), składają się z 8-bitowych lub 16-bitowych wartości skalarnych zezwolić na dostęp do takiego magazynu danych.

## <a name="the-norm-and-unorm-types"></a>Typy norm i unorm

`norm` i `unorm` typy są typami skalarnymi, które ograniczają zakres **float** wartości; jest to nazywane *obcinanie*. Te typy można jawnie zbudować z innych typów skalarnych. Podczas rzutowania wartość jest najpierw rzutowana na typ **float** a następnie obcinana do odpowiedniego regionu dozwolonego przez typ norm [-1,0, 1.0] lub unorm [0.0, 1.0]. Rzutowanie z +/-nieskończoności zwraca wartość +/-1. Rzutowanie z obiektu NaN jest niezdefiniowane. Typ norm może zostać niejawnie skonstruowany z typu unorm i bez utraty danych. Operator niejawnej konwersji na typ zmiennoprzecinkowy jest zdefiniowany dla tych typów. Operatory dwuargumentowe są zdefiniowane między tymi typami i innymi wbudowanymi typami skalarnymi, takich jak **float** i **int**: +, -, \*, /, ==,! =, >, \<, > =, < =. Złożone operatory przypisania są również obsługiwane: +=,-=, \*=, / =. Jednoargumentowy operator negacji (-) jest zdefiniowany dla typów norm.

## <a name="short-vector-library"></a>Biblioteka krótkich wektorów

Biblioteka krótkich wektorów zawiera niektóre funkcje [typ wektora](http://go.microsoft.com/fwlink/p/?linkid=248500) który jest zdefiniowany w języku HLSL i jest zazwyczaj używany do definiowania tekseli. Krótki wektor jest strukturą danych, która przechowuje jednej do czterech wartości tego samego typu. Obsługiwane typy to **double**, **float**, **int**, `norm`, `uint`, i `unorm`. Nazwy typów przedstawiono w poniższej tabeli. Dla każdego typu, jest również odpowiadające **typedef** , która nie ma znaku podkreślenia w nazwie. Typy, które mają podkreślenia znajdują się w [Namespace Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md). Typy, które nie mają podkreślenia znajdują się w [Namespace CONCURRENCY::Graphics:: Direct3D](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) , dzięki czemu są wyraźnie rozdzielone od podobnie nazwanych typów podstawowych takich jak **__int8** i **__int16**.

||Długość 2|Długość 3|Długość 4|
|-|--------------|--------------|--------------|
|double|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> FLOAT4|
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|

### <a name="operators"></a>Operatory

Jeśli zdefiniowano operator pomiędzy dwoma krótkimi wektorami, a następnie jest on także zdefiniowany pomiędzy krótkim wektorem a wektorem skalarnym. Ponadto te muszą być spełnione:

- Typ wartości skalarnej musi być taki sam jak typ elementu krótkiego wektora.

- Typ wartości skalarnej mogą być niejawnie konwertowane na typ elementu wektora za pomocą tylko jednej konwersji zdefiniowanej przez użytkownika.

Operacja jest wykonywana przenoszony między poszczególnych składników krótkiego wektora i wartości skalarnej. Oto prawidłowe operatory:

|Typ operatora|Prawidłowe typy|
|-------------------|-----------------|
|Operatory binarne|Prawidłowe dla wszystkich typów: +, -, \*, /,<br /><br /> Prawidłowe dla typów całkowitoliczbowych: %, ^, &#124;&, <\<, >><br /><br /> Dwa wektory muszą mieć taki sam rozmiar, a wynik jest wektorem tej samej wielkości.|
|Operatory relacyjne|Prawidłowe dla wszystkich typów: == i! =|
|Złożony operator przypisania|Prawidłowe dla wszystkich typów: +=,-=, \*=, / =<br /><br /> Prawidłowe dla typów całkowitoliczbowych: % =, ^ = &#124;= & =, <\<= >> =|
|Operatory inkrementacji i dekrementacji|Prawidłowe dla wszystkich typów: ++,--<br /><br /> Zarówno prefiks, jak i przyrostek są prawidłowe.|
|Bitowy operator NOT (~)|Prawidłowe dla typów całkowitoliczbowych.|
|Jednoargumentowy - — operator|Prawidłowe dla wszystkich typów, z wyjątkiem `unorm` i `uint`.|

### <a name="swizzling-expressions"></a>Wyrażenia przemieniane

Biblioteka krótkich wektorów obsługuje `vector_type.identifier` konstrukcji akcesor dostęp do składników krótkiego wektora. `identifier`, Który jest znany jako *wyrażenie przemieniane*, określa składniki wektora. Wyrażenie może być wartością l i r-wartości. Poszczególne znaki w identyfikatorze mogą być: x, y i z oraz w; lub r, g, b, a. "x" i "r" oznaczają składnik zerowy, "y" oraz "g" oznaczają pierwszy składnik i tak dalej. (Zwróć uwagę, że "x" i "r" nie można użyć w tym samym identyfikatorze.) "Rgba" i "xyzw" zwracają więc ten sam wynik. Jednoskładnikowe takie jak "x" i "y", są typami wartości skalarnych. Wieloskładnikowe metody dostępu są krótkimi wektorami. Na przykład można utworzyć `int_4` wektor, który nosi nazwę `fourInts` i zawiera wartości 2, 4, 6 i 8, następnie `fourInts.y` zwraca liczbę całkowitą 4 i `fourInts.rg` zwraca `int_2` obiekt, który zawiera wartości 2 i 4.

## <a name="texture-classes"></a>Klasy tekstur

Wiele procesorów GPU ma sprzęt i pamięci podręczne, które są zoptymalizowane do pobrania pikseli i tekseli oraz do renderowania obrazów i tekstur. [Tekstury\<T, N >](../../parallel/amp/reference/texture-class.md) klasy, która jest klasą kontenera obiektów teksela, udostępnia funkcję tekstury te procesorów GPU. Teksel może być:

- **Int**, `uint`, **float**, **double**, `norm`, lub `unorm` skalarne.

- Krótki wektor, który ma dwa lub cztery składniki. Jedynym wyjątkiem jest `double_4`, co jest niedozwolone.

`texture` Obiekt może mieć rangę 1, 2 lub 3. `texture` Obiektów mogą być przechwytywane jedynie poprzez odwołanie w wyrażeniu lambda wywołania `parallel_for_each`. Tekstury są przechowywane w procesorze GPU jako obiekty tekstury Direct3D. Aby uzyskać więcej informacji na temat tekstur i tekseli w Direct3D, zobacz [wprowadzenie do tekstur w Direct3D 11](http://go.microsoft.com/fwlink/p/?linkid=248502).

Użyty typ teksela może być jednym z wielu formatów tekstury, które są używane w programowaniu grafiki. Na przykład RGBA format może za pomocą 32-bitowy, 8 bitów dla języka R "," G "," B "i" element skalarny. Sprzęt teksturujący karty graficznej może uzyskać dostęp do poszczególnych elementów na podstawie formatu. Na przykład jeśli używasz formatu RGBA, sprzęt teksturujący może wyodrębnić każdy element 8-bitowy do formy 32-bitowej. W bibliotece C++ AMP można ustawić bity dla elementu skalarnego w tekselu, dzięki czemu mogą automatycznie uzyskiwać dostęp poszczególnych elementów skalarnych w kodzie, bez używania bitowych.

### <a name="instantiating-texture-objects"></a>Tworzenie wystąpień obiektów tekstury

Można zadeklarować obiekt tekstury bez inicjowania. Poniższy przykład kodu deklaruje kilka obiektów tekstur.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextures() {
    // Create a 16-texel texture of int.
    texture<int, 1> intTexture1(16);
    texture<int, 1> intTexture2(extent<1>(16));

    // Create a 16 x 32 texture of float_2.
    texture<float_2, 2> floatTexture1(16, 32);
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));

    // Create a 2 x 4 x 8 texture of uint_4.
    texture<uint_4, 3> uintTexture1(2, 4, 8);
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));
}
```

Można również użyć konstruktora do zadeklarowania i zainicjowania `texture` obiektu. Poniższy przykład kodu tworzy `texture` obiektu z wektora `float_4` obiektów. Bity na element skalarny jest ustawiona na wartość domyślna. Nie można użyć tego konstruktora z `norm`, `unorm`, lub krótkimi wektorami typów `norm` i `unorm`, ponieważ nie posiadają domyślnej liczby bitów na element skalarny.

```cpp
#include <amp.h>
#include <amp_graphics.h>
#include <vector>
using namespace concurrency;
using namespace concurrency::graphics;

void initializeTexture() {
    std::vector<int_4> texels;
    for (int i = 0; i < 768 * 1024; i++) {
        int_4 i4(i, i, i, i);
        texels.push_back(i4);
    }

    texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());
}
```

Można również zadeklarować i zainicjować `texture` obiektu za pomocą przeciążenia konstruktora, które przyjmuje wskaźnik do danych źródłowych, rozmiar danych źródłowych w bajtach i bity na element skalarny.

```cpp
void createTextureWithBPC() { // Create the source data.
    float source[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        source[i] = (float)i;
    }
    // Initialize the texture by using the size of source in bytes // and bits per scalar element.
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);
}
```

Tekstury w tych przykładach są tworzone w domyślnym widoku akceleratora domyślnego. Możesz użyć innych przeciążeń konstruktora, jeśli chcesz określić `accelerator_view` obiektu. Nie można utworzyć obiektu tekstury na akceleratorze CPU.

Istnieją limity dotyczące rozmiaru każdego wymiaru `texture` obiektu, jak pokazano w poniższej tabeli. Błąd czasu wykonania jest generowany, gdy zostaną przekroczone.

|Tekstura|Ograniczenie rozmiaru według wymiaru|
|-------------|---------------------|
|Tekstura\<T, 1 >|16384|
|Tekstura\<T, 2 >|16384|
|Tekstura\<T, 3 >|2048|

### <a name="reading-from-texture-objects"></a>Czytanie z obiektów tekstur

Może odczytywać `texture` obiektu za pomocą [texture::operator\[\]](reference/texture-class.md#operator_at), [texture:: operator() — Operator](reference/texture-class.md#operator_call), lub [Texture::Get — metoda](reference/texture-class.md#get). Dwa operatory zwracają wartość, nie odwołanie. W związku z tym, nie można zapisać do `texture` obiektu za pomocą `texture::operator\[\]`.

```cpp
void readTexture() {
    std::vector<int_2> src;
    for (int i = 0; i <16 *32; i++) {
        int_2 i2(i, i);

        src.push_back(i2);
    }

    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { // Use the subscript operator.
        arr[idx].x += tex9[idx].x; // Use the function () operator.
        arr[idx].x += tex9(idx).x; // Use the get method.
        arr[idx].y += tex9.get(idx).y; // Use the function () operator.
        arr[idx].y += tex9(idx[0], idx[1]).y;
    });

    arr.synchronize();
}
```

Poniższy przykład kodu pokazuje, jak przechowywać kanały tekstury w krótkim wektorze, a następnie uzyskać dostęp do poszczególnych elementów skalarnych jako właściwości krótkiego wektora.

```cpp
void UseBitsPerScalarElement() { // Create the image data. // Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).
    const int image_height = 16;
    const int image_width = 16;
    std::vector<unsigned int> image(image_height* image_width);

    extent<2> image_extent(image_height, image_width);

    // By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is // stored in one 32-bit component of a uint_4.
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

    // Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.
    parallel_for_each(image_extent,
        [&image_texture](index<2> idx) restrict(amp)
        { // 4 bytes are automatically extracted when reading.
            uint_4 color = image_texture[idx];
            unsigned int r = color.r;
            unsigned int g = color.g;
            unsigned int b = color.b;
            unsigned int a = color.a;
        });
}
```

W poniższej tabeli wymieniono prawidłowe liczby bitów na kanał dla każdego typu wektora sortowania.

|Typ danych tekstury|Prawidłowe bity na element skalarny|
|-----------------------|-----------------------------------|
|int, int_2, int_4<br /><br /> uint, uint_2, uint_4|8, 16, 32|
|int_3, uint_3|32|
|Float, float_2, float_4|16, 32|
|float_3|32|
|double_2 Double,|64|
|norm norm_2, norm_4<br /><br /> unorm, unorm_2, unorm, 4|8, 16|

### <a name="writing-to-texture-objects"></a>Zapisywanie do obiektów tekstury

Użyj [texture::set](reference/texture-class.md#set) metodę, aby zapisać `texture` obiektów. Obiekt tekstury może być tylko do odczytu lub odczytu i zapisu. Dla obiektu tekstury można Odczytywalny i zapisywalny muszą być spełnione następujące warunki:

- T ma tylko jeden składnik skalarny. (Krótkie wektory nie są dozwolone.)

- T nie jest **double**, `norm`, lub `unorm`.

- `texture::bits_per_scalar_element` Właściwości wynosi 32.

Jeśli wszystkie trzy nie jest spełniony, a następnie `texture` obiekt jest tylko do odczytu. Pierwsze dwa warunki są sprawdzane podczas kompilacji. Błąd kompilacji jest generowany, gdy masz kod, który próbuje zapisać do `readonly` obiektu tekstury. Warunek dla `texture::bits_per_scalar_element` wykrycia w czasie wykonywania i środowisko wykonawcze zgłasza [unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md) wyjątek, jeśli zostanie podjęta próba zapisu tylko do odczytu `texture` obiektu.

Poniższy przykład kodu zapisuje wartości do obiektu tekstury.

```cpp
void writeTexture() {
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {
        tex1.set(idx, 0);
    });
}
```

### <a name="copying-texture-objects"></a>Kopiowanie obiektów tekstur

Można kopiować między obiektami tekstur przy użyciu [kopiowania](reference/concurrency-namespace-functions-amp.md#copy) funkcji lub [copy_async —](reference/concurrency-namespace-functions-amp.md#copy_async) funkcji, jak pokazano w poniższym przykładzie kodu.

```cpp
void copyHostArrayToTexture() { // Copy from source array to texture object by using the copy function.
    float floatSource[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        floatSource[i] = (float)i;
    }
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

    // Copy from source array to texture object by using the copy function.
    char charSource[16* 16];
    for (int i = 0; i <16* 16; i++) {
        charSource[i] = (char)i;
    }
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
    // Copy from texture object to source array by using the copy function.
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));
}
```

Możesz również skopiować z jednego tekstury do innego za pomocą [texture::copy_to](reference/texture-class.md#copy_to) metody. Dwie tekstury mogą znajdować się w różnych widokach akceleratora. Przy kopiowaniu do `writeonly_texture_view` obiektu, dane są kopiowane do źródłowego `texture` obiektu. Liczba bitów na element skalarny oraz zakres musi być taka sama, w elemencie źródłowym i docelowym `texture` obiektów. Jeśli te wymagania nie są spełnione, środowisko uruchomieniowe zgłasza wyjątek.

## <a name="texture-view-classes"></a>Klasy widoku tekstury

C++ AMP wprowadza [texture_view, klasa](../../parallel/amp/reference/texture-view-class.md) w programie Visual Studio 2013. Widoki tekstury obsługują te same typy i rangi texeli, jak [texture, klasa](../../parallel/amp/reference/texture-class.md), ale w przeciwieństwie do tekstur, zapewniają dostęp do dodatkowych funkcji sprzętowych, takich jak próbkowanie tekstur i mipmapy. Widoki tekstury obsługują dostęp tylko do odczytu, tylko do zapisu i odczytu i zapisu danych źródłowych tekstury.

- Dostęp tylko do odczytu jest zapewniany przez `texture_view<const T, N>` specjalizacja szablonu, który obsługuje elementy, które mają 1, 2 lub 4 składniki, tekstury próbkowanie i dynamiczny dostęp do szeregu poziomów mipmappingu, które są określane podczas konkretyzacji widoku.

- Dostęp tylko do zapisu jest zapewniany przez klasę szablonu niewyspecjalizowaną `texture_view<T, N>`, obsługującą elementy, 2 lub 4 składniki, które mogą uzyskiwać dostęp do jednego poziomu mipmappingu, który jest określany podczas konkretyzacji widoku. Nie obsługuje pobierania próbek.

- Dostęp do odczytu i zapisu jest zapewniany przez klasę szablonu niewyspecjalizowaną `texture_view<T, N>`, która, podobnie jak tekstury obsługującą elementy, które mają tylko jeden składnik; widoku mogą uzyskiwać dostęp do jednego poziomu mipmappingu, który jest określany podczas konkretyzacji. Nie obsługuje pobierania próbek.

Widoki tekstury są analogiczne do widoków tablicy, ale nie zapewniają funkcje zarządzania i przenoszenia danych, [array_view, klasa](../../parallel/amp/reference/array-view-class.md) zapewnia [array, klasa](../../parallel/amp/reference/array-class.md). Element `texture_view` może zostać oceniony jedynie w widoku akceleratora, w którym znajduje się dane podstawowe tekstury.

### <a name="writeonlytextureview-deprecated"></a>writeonly_texture_view przestarzałe

Dla programu Visual Studio 2013 C++ AMP wprowadza lepszą obsługę funkcji tekstury sprzętowej, takich jak pobieranie próbek i mipmapy, które nie jest obsługiwany przez [writeonly_texture_view, klasa](../../parallel/amp/reference/writeonly-texture-view-class.md). Nowo wprowadzona `texture_view` klasy obsługuje nadzbiór funkcji w `writeonly_texture_view`; w związku z `writeonly_texture_view` jest przestarzała.

Firma Microsoft zaleca — co najmniej dla nowego kodu — używanej `texture_view` do dostępu do funkcjonalności, wcześniej zapewnianej przez `writeonly_texture_view`. Porównaj poniższe dwa przykłady kodu zapisu w obiekcie tekstury, który ma dwa składniki (int_2). Należy zauważyć, że w obu przypadkach widok, `wo_tv4`, musi być przechwycony przez wartość w wyrażeniu lambda. Oto przykład, który korzysta z nowych `texture_view` klasy:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

A Oto przestarzała `writeonly_texture_view` klasy:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

Jak widać, dwa przykłady kodu są niemal identyczne, podczas zapisywania wszystko, co robisz podstawowego poziomu mipmapowania. Jeśli użyto `writeonly_texture_view` w istniejącym kodzie, a nie planujesz zwiększyć, że kod, nie trzeba go zmienić. Jednak jeśli myślisz o kodem, zalecamy przepiszesz użyj `texture_view` ponieważ jego ulepszenia obsługują nowe funkcje tekstur sprzętowych. Czytaj dalej, aby uzyskać więcej informacji o tych nowych funkcjach.

Aby uzyskać więcej informacji na temat wycofania `writeonly_texture_view`, zobacz [Omówienie projektu widoku tekstury w bibliotece C++ AMP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx) na programowania równoległego w kodzie macierzystym blogu.

### <a name="instantiating-texture-view-objects"></a>Tworzenie wystąpień obiektów widoku tekstury

Deklarowanie `texture_view` jest podobne do deklarowania `array_view` skojarzony z **tablicy**. Poniższy przykład kodu deklaruje kilka `texture` obiektów i `texture_view` obiektów, które są skojarzone z nimi.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextureViews()
{
    // Create a 16-texel texture of int, with associated texture_views.
    texture<int, 1> intTexture(16);
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write

    // Create a 16 x 32 texture of float_2, with associated texture_views.
    texture<float_2, 2> floatTexture(16, 32);
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only

    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.
    texture<uint_4, 3> uintTexture(2, 4, 8);
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only
}
```

Zwróć uwagę, jak widok tekstury, którego typ elementu jest niestały i ma jeden składnik jest odczytu i zapisu, ale widok tekstury, którego typ elementu jest niestały, ale ma więcej niż jeden dostępny jest tylko do zapisu. Widoki tekstury typów stałych elementów są zawsze tylko do odczytu, ale jeśli typ elementu jest niestały, następnie liczba składników w elemencie Określa, czy jest odczytu i zapisu (1 składnik) lub tylko do zapisu (wiele składników).

Typ elementu `texture_view`— jego stałość, a także liczba składników — również odgrywa rolę w określaniu, czy widok obsługuje pobieranie próbek tekstury i jak można uzyskać dostępu do poziomów mipmappingu:

|Typ|Składniki|Odczyt|Write|Próbkowania|Dostęp do mipmappingu|
|----------|----------------|----------|-----------|--------------|-------------------|
|texture_view\<const T, N >|1, 2, 4|Tak|Nie (1)|Tak|Tak, można indeksować. Zakres jest określany w konkretyzacji.|
|Texture_view\<T, N >|1<br /><br /> 2, 4|Tak<br /><br /> Nie (2)|Tak<br /><br /> Tak|Nie (1)<br /><br /> Nie (1)|Tak, jeden poziom. Poziom jest określany w konkretyzacji.<br /><br /> Tak, jeden poziom. Poziom jest określany w konkretyzacji.|

Z tej tabeli widać, że widoki tekstury tylko do odczytu w pełni obsługują nowe możliwości w zamian za brak możliwości do zapisu do widoku. Zapisywalne widoki tekstury są ograniczone, w tym, że mają dostęp tylko jednego poziomu mipmappingu. Widoki tekstury do odczytu i zapisu są jeszcze bardziej wyspecjalizowane niż te zapisywalne, ponieważ dodają wymóg, że typ elementu widoku tekstury miał tylko jeden składnik. Należy zauważyć, że próbkowanie nie jest obsługiwane dla widoków tekstury do zapisu, ponieważ jest to operacja zorientowana na odczyt.

### <a name="reading-from-texture-view-objects"></a>Czytanie z obiektów widoku tekstury

Odczytywanie niepróbkowanych danych tekstury za pomocą widoku tekstury jest jak odczytywanie ich z samej tekstury, z tą różnicą, że tekstury są przechwytywane przez odniesienie, a widoki tekstury są przechwytywane przez wartość. Poniższe dwa przykłady kodu pokazują; Po pierwsze, za pomocą `texture` tylko:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {
        tex_data.set(idx, int_2(1, 1));
    });
}
```

A tutaj jest tym samym przykładzie, ale teraz używa `texture_view` klasy:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        tex_view.set(idx, int_2(1, 1));
    });
}
```

Tekstury widoków, w której elementy są oparte na typach zmiennopozycyjnych — na przykład, float, float_2 lub float_4 — można również odczytywać za pomocą pobierania próbek tekstury, aby wykorzystać zalety obsługi sprzętowej różnych trybów filtrowania i adresowania. C++ AMP obsługuje dwa tryby filtrowania, które są najbardziej rozpowszechnione w scenariuszach obliczeniowych — (najbliższego sąsiada) filtrowanie punktowe i filtrowanie liniowe (wg średniej ważonej) — i cztery tryby adresowania — zawinięty, dublowane, powiązany i obramowanie. Aby uzyskać więcej informacji na temat trybów adresowania, zobacz [address_mode — wyliczenie](reference/concurrency-graphics-namespace-enums.md#address_mode).

Oprócz trybów, które C++ AMP obsługuje bezpośrednio są dostępne inne tryby filtrowania i tryby adresowania bazowej platformy za pomocą międzyoperacyjnych interfejsów API do przyjęcia próbnika tekstur, który został utworzony bezpośrednio za pomocą interfejsów API platformy. Na przykład Direct3D obsługuje inne tryby filtrowania, takie jak filtrowanie anizotropowe i można zastosować inny tryb adresowania do każdego wymiaru tekstury. Można utworzyć próbnik tekstury, którego współrzędne są owinięte pionowo, odbite poziomo i próbkowane tak, z filtrowaniem anizotropowymo przy użyciu interfejsów API Direct3D, a następnie wykorzystać próbnik w kodzie języka C++ AMP za pomocą `make_sampler` interoperacyjnego API. Aby uzyskać więcej informacji, zobacz [pobierania próbek tekstury w bibliotece C++ AMP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx) na programowania równoległego w kodzie macierzystym blogu.

Widoki tekstury obsługują także odczyt mipmap. Widoki tekstury tylko do odczytu (te, które mają stały typ elementu) oferują największą elastyczność, ponieważ zakres poziomów mipmappingu, ustalony przy konkretyzacji, może być dynamicznie próbkowany, a elementy, które mają 1, 2 lub 4 składniki są obsługiwane. Widoki tekstury do odczytu i zapisu, które mają elementy, które mają jeden składnik, również obsługują mipmapy, ale tylko z poziomu, który jest określany w konkretyzacji. Aby uzyskać więcej informacji, zobacz [Tekstura z Mipmappingiem](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx) na programowania równoległego w kodzie macierzystym blogu.

### <a name="writing-to-texture-view-objects"></a>Zapisywanie do obiektów widoku tekstury

Użyj [texture_view::Get — metoda](reference/texture-view-class.md#get) do zapisu do podstawowej `texture` za pośrednictwem `texture_view` obiektu. Widok tekstury może być tylko do odczytu, odczytu i zapisu lub tylko do zapisu. Aby widok tekstury można było zapisywać musi mieć typ elementu jest niestały; Aby widok tekstury do odczytu i zapisu jego typ elementu musi mieć tylko jeden składnik. W przeciwnym razie widok tekstury jest tylko do odczytu. Możesz tylko dostęp do jednego poziomu mipmappingu tekstury w czasie za pomocą widoku tekstury, a poziom jest określany podczas konkretyzacji widoku.

W tym przykładzie pokazano, jak można zapisać do poziomu drugim mipmappingu tekstury, która ma 4 poziomy mipmap. Najbardziej szczegółowy poziom mipmappingu to 0.

```cpp
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

// Create a writable texture view to the second mipmap level :4x4
texture_view<int, 2> w_view(tex, 1);

parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)
{
    w_view.set(idx, 123);
});
```

## <a name="interoperability"></a>Współdziałanie

Środowisko wykonawcze C++ AMP wspiera współdziałanie między `texture<T,1>` i [interfejsem ID3D11Texture1D](http://go.microsoft.com/fwlink/p/?linkId=248503), między `texture<T,2>` i [interfejsem ID3D11Texture2D](http://go.microsoft.com/fwlink/p/?linkId=255317)oraz między `texture<T,3>`i [interfejsem ID3D11Texture3D](http://go.microsoft.com/fwlink/p/?linkId=255377). [Get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture) metoda przyjmuje `texture` obiektu i zwraca `IUnknown` interfejsu. [Make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture) metoda przyjmuje `IUnknown` interfejsu i `accelerator_view` obiektu i zwraca `texture` obiektu.

## <a name="see-also"></a>Zobacz też

[double_2, klasa](../../parallel/amp/reference/double-2-class.md)<br/>
[double_3, klasa](../../parallel/amp/reference/double-3-class.md)<br/>
[double_4, klasa](../../parallel/amp/reference/double-4-class.md)<br/>
[float_2, klasa](../../parallel/amp/reference/float-2-class.md)<br/>
[float_3, klasa](../../parallel/amp/reference/float-3-class.md)<br/>
[float_4, klasa](../../parallel/amp/reference/float-4-class.md)<br/>
[int_2, klasa](../../parallel/amp/reference/int-2-class.md)<br/>
[int_3, klasa](../../parallel/amp/reference/int-3-class.md)<br/>
[int_4, klasa](../../parallel/amp/reference/int-4-class.md)<br/>
[norm_2, klasa](../../parallel/amp/reference/norm-2-class.md)<br/>
[norm_3, klasa](../../parallel/amp/reference/norm-3-class.md)<br/>
[norm_4, klasa](../../parallel/amp/reference/norm-4-class.md)<br/>
[short_vector, struktura](../../parallel/amp/reference/short-vector-structure.md)<br/>
[short_vector_traits, struktura](../../parallel/amp/reference/short-vector-traits-structure.md)<br/>
[uint_2, klasa](../../parallel/amp/reference/uint-2-class.md)<br/>
[uint_3, klasa](../../parallel/amp/reference/uint-3-class.md)<br/>
[uint_4, klasa](../../parallel/amp/reference/uint-4-class.md)<br/>
[unorm_2, klasa](../../parallel/amp/reference/unorm-2-class.md)<br/>
[unorm_3, klasa](../../parallel/amp/reference/unorm-3-class.md)<br/>
[unorm_4, klasa](../../parallel/amp/reference/unorm-4-class.md)