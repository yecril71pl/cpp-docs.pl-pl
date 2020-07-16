---
title: Grafika (C++ AMP)
ms.date: 11/04/2016
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
ms.openlocfilehash: 393fadbba90b135e6394cf848668b4957a6d7ce2
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404837"
---
# <a name="graphics-c-amp"></a>Grafika (C++ AMP)

C++ AMP zawiera kilka interfejsów API w przestrzeni nazw [concurrency:: Graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) , których można użyć w celu uzyskania dostępu do obsługi tekstury na procesorach GPU. Niektóre typowe scenariusze są następujące:

- Klasy [tekstury](../../parallel/amp/reference/texture-class.md) można używać jako kontenera danych do obliczania i wykorzystania *przestrzennej lokalizacji* pamięci podręcznej tekstury i układów sprzętu GPU. Miejscowość przestrzenna jest właściwością elementów danych, które są fizycznie blisko siebie.

- Środowisko uruchomieniowe zapewnia wydajne współdziałanie z programem cieniowania nieobliczeniowego. Cieniowanie pikseli, wierzchołków, mozaikowania i łusek często wykorzystuje lub tworzy tekstury, których można użyć w obliczeniach C++ AMP.

- Interfejsy API grafiki w C++ AMP zapewniają alternatywne sposoby uzyskiwania dostępu do spakowanych buforów podrzędnych. Tekstury, które mają formaty reprezentujące *tekseli* (elementy tekstury), które składają się z 8-bitowych lub 16-bitowych wartości skalarnych, umożliwiają dostęp do takiego spakowanego magazynu danych.

## <a name="the-norm-and-unorm-types"></a>Typy norm i unorm

`norm`Typy i `unorm` są typami skalarnymi, które ograniczają zakres wartości **zmiennoprzecinkowych** ; jest to nazywane *clamping*ogranicznikiem. Te typy mogą być jawnie skonstruowane z innych typów skalarnych. W przypadku rzutowania wartość jest najpierw rzutowana na typ **float** , a następnie zamocowana do odpowiedniego regionu, który jest dozwolony przez normę [-1,0, 1,0] lub unorm [0,0, 1,0]. Rzutowanie z +/-nieskończone zwraca +/-1. Rzutowanie z NaN jest niezdefiniowane. Norma może być niejawnie skonstruowana z unorm, a dane nie są tracone. Operator niejawnej konwersji na wartość zmiennoprzecinkową jest zdefiniowany dla tych typów. Operatory binarne są definiowane między tymi typami i innymi wbudowanymi typami skalarnymi, takimi jak **zmiennoprzecinkowe** i **int**: +,-, \* ,/, = =,! =, >, \<, > =, <=. Operatory przypisania złożonego są również obsługiwane: + =,-=, \* =,/=. Jednoargumentowy operator negacji (-) jest zdefiniowany dla typów norm.

## <a name="short-vector-library"></a>Krótka Biblioteka wektorów

Krótka Biblioteka wektorów udostępnia niektóre funkcje [typu wektora](https://go.microsoft.com/fwlink/p/?linkid=248500) zdefiniowanego w HLSL i są zwykle używane do definiowania tekseli. Krótki wektor jest strukturą danych, która przechowuje od jednej do czterech wartości tego samego typu. Obsługiwane typy to **Double**, **float**, **int**, `norm` , `uint` i `unorm` . Nazwy typów są pokazane w poniższej tabeli. Dla każdego typu istnieje również odpowiadający mu **element typedef** , który nie ma znaku podkreślenia w nazwie. Typy, które mają znaki podkreślenia, znajdują się w [przestrzeni nazw Concurrency:: Graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md). Typy, które nie mają podkreślenia, znajdują się w [przestrzeni nazw Concurrency:: Graphics::d irect3d](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) , dzięki czemu są wyraźnie oddzielone od typów podstawowych o podobnej nazwie, takich jak **__int8** i **__int16**.

||Długość 2|Długość 3|Długość 4|
|-|--------------|--------------|--------------|
|double|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> float4|
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|

### <a name="operators"></a>Operatory

Jeśli operator jest zdefiniowany między dwoma krótkimi wektorami, jest również definiowany między krótkim wektorem a skalarną. Należy również mieć jedną z następujących wartości:

- Typ skalarny musi być taki sam jak typ elementu krótkiego wektora.

- Typ skalarny może być niejawnie konwertowany na typ elementu Vector przy użyciu tylko jednej konwersji zdefiniowanej przez użytkownika.

Operacja jest wykonywana w składniku między każdym składnikiem krótkiej wektora a skalarną. Oto prawidłowe operatory:

|Typ operatora|Prawidłowe typy|
|-------------------|-----------------|
|Operatory binarne|Prawidłowe dla wszystkich typów: +,-, \* ,/,<br /><br /> Prawidłowe dla typów całkowitych:%, ^, &#124;, &, <\<, >><br /><br /> Dwa wektory muszą mieć ten sam rozmiar, a wynik jest wektorem o takim samym rozmiarze.|
|Operatory relacyjne|Prawidłowe dla wszystkich typów: = = i! =|
|Operator przypisania złożonego|Prawidłowe dla wszystkich typów: + =,-=, \* =,/=<br /><br /> Prawidłowe dla typów całkowitych:% =, ^ =, &#124;=, &=, <\<=, >>=|
|Operatory zwiększania i zmniejszania|Prawidłowe dla wszystkich typów: + +,--<br /><br /> Oba prefiksy i przyrosty są prawidłowe.|
|Bitowy operator NOT (~)|Prawidłowy dla typów całkowitych.|
|Operator jednoargumentowy|Prawidłowy dla wszystkich typów z wyjątkiem `unorm` i `uint` .|

### <a name="swizzling-expressions"></a>Wyrażenia przemieniane

Krótka Biblioteka wektorów obsługuje `vector_type.identifier` konstrukcję akcesora, aby uzyskać dostęp do składników krótkiego wektora. `identifier`Element, który jest znany jako *wyrażenie przemieniane*, określa składniki wektora. Wyrażenie może być l-wartością lub r-wartością. Poszczególne znaki w identyfikatorze mogą być: x, y, z i w; lub r, g, b i. "x" i "r" oznaczają składnik zero, "y" i "g" oznaczają pierwszy składnik itd. (Zauważ, że w tym samym identyfikatorze nie można używać "x" i "r"). W związku z tym "RGBA" i "xyzw" zwracają ten sam wynik. Metody dostępu jednoskładnikowego, takie jak "x" i "y", są typami wartości skalarnych. Metody dostępu wieloskładnikowego to krótkie typy wektorów. Na przykład jeśli utworzysz `int_4` wektor o nazwie `fourInts` i zawiera wartości 2, 4, 6 i 8, `fourInts.y` Funkcja zwraca liczbę całkowitą 4 i `fourInts.rg` zwraca `int_2` obiekt, który ma wartości 2 i 4.

## <a name="texture-classes"></a>Klasy tekstury

Wiele procesorów GPU ma sprzęt i pamięć podręczną zoptymalizowane pod kątem pobierania pikseli i tekseli oraz do renderowania obrazów i tekstur. Klasa [tekstury \<T,N> ](../../parallel/amp/reference/texture-class.md) , która jest klasą kontenera dla obiektów Texel, udostępnia funkcje tekstury tych procesorów GPU. Texel może:

- **Int**, `uint` , **float**, **Double**, `norm` lub `unorm` skalarny.

- Krótki wektor, który ma dwa lub cztery składniki. Jedynym wyjątkiem jest `double_4` , co jest niedozwolone.

`texture`Obiekt może mieć rangę 1, 2 lub 3. `texture`Obiekt może być przechwytywany tylko przez odwołanie w wyrażeniu lambda wywołania do `parallel_for_each` . Tekstura jest przechowywana w procesorze GPU jako obiekty tekstury Direct3D. Aby uzyskać więcej informacji na temat tekstur i tekseli w Direct3D, zobacz [wprowadzenie do tekstur w programie Direct3D 11](https://go.microsoft.com/fwlink/p/?linkid=248502).

Używany typ Texel może być jednym z wielu formatów tekstury, które są używane w programowaniu graficznym. Na przykład format RGBA może używać 32 bitów, z 8 bitów każdy dla elementów R, G, B i skalarnych. Sprzęt tekstury karty graficznej może uzyskać dostęp do poszczególnych elementów w oparciu o format. Na przykład jeśli używasz formatu RGBA, sprzęt tekstury może wyodrębnić każdy element 8-bitowy do postaci 32-bitowej. W C++ AMP można ustawić bity na element skalarny Texel, aby umożliwić automatyczne uzyskiwanie dostępu do poszczególnych elementów skalarnych w kodzie bez korzystania z przesunięcia bitowego.

### <a name="instantiating-texture-objects"></a>Tworzenie wystąpienia obiektów tekstury

Można zadeklarować obiekt tekstury bez inicjalizacji. Poniższy przykład kodu deklaruje kilka obiektów tekstury.

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

Można również użyć konstruktora, aby zadeklarować i zainicjować `texture` obiekt. Poniższy przykład kodu tworzy wystąpienie `texture` obiektu na podstawie wektora `float_4` obiektów. Liczba bitów na element skalarny jest ustawiona na wartość domyślną. Nie można użyć tego konstruktora z `norm` , `unorm` , ani krótkich wektorów `norm` i `unorm` , ponieważ nie mają one domyślnej liczby bitów na element skalarny.

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

Można również zadeklarować i zainicjować `texture` Obiekt przy użyciu przeciążenia konstruktora, które Pobiera wskaźnik do danych źródłowych, rozmiar danych źródłowych w bajtach oraz liczbę bitów na element skalarny.

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

Tekstury w tych przykładach są tworzone w domyślnym widoku akceleratora domyślnego. Można użyć innych przeciążeń konstruktora, jeśli chcesz określić `accelerator_view` obiekt. Nie można utworzyć obiektu tekstury na akceleratorze procesora.

Istnieją limity rozmiaru każdego wymiaru `texture` obiektu, jak pokazano w poniższej tabeli. W przypadku przekroczenia limitów jest generowany błąd czasu wykonywania.

|Tekstura|Ograniczenie rozmiaru na wymiar|
|-------------|---------------------|
|głębokości\<T,1>|16384|
|głębokości\<T,2>|16384|
|głębokości\<T,3>|2048|

### <a name="reading-from-texture-objects"></a>Odczytywanie z obiektów tekstury

Można odczytywać z `texture` obiektu za pomocą operatora [Texture:: operator \[ \] ](reference/texture-class.md#operator_at), [Texture:: operator ()](reference/texture-class.md#operator_call)lub [tekstury:: Get](reference/texture-class.md#get). Dwa operatory zwracają wartość, a nie odwołanie. W związku z tym nie można pisać do `texture` obiektu za pomocą `texture::operator\[\]` .

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

Poniższy przykład kodu demonstruje sposób przechowywania kanałów tekstury w krótkim wektorze, a następnie uzyskiwania dostępu do poszczególnych elementów skalarnych jako właściwości krótkiego wektora.

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

Poniższa tabela zawiera listę prawidłowych bitów na kanał dla każdego typu wektora sortowania.

|Typ danych tekstury|Prawidłowe bity na element skalarny|
|-----------------------|-----------------------------------|
|int, int_2, int_4<br /><br /> uint, uint_2, uint_4|8, 16, 32|
|int_3, uint_3|32|
|float, float_2, float_4|16, 32|
|float_3|32|
|Double, double_2|64|
|Norma, norm_2, norm_4<br /><br /> unorm, unorm_2, unorm, 4|8, 16|

### <a name="writing-to-texture-objects"></a>Zapisywanie do obiektów tekstury

Użyj metody [Texture:: Set](reference/texture-class.md#set) do zapisu w `texture` obiektach. Obiekt tekstury może być tylko do odczytu lub odczyt/zapis. Aby obiekt tekstury był możliwy do odczytu i zapisu, muszą być spełnione następujące warunki:

- T ma tylko jeden składnik skalarny. (Krótkie wektory są niedozwolone).

- T nie jest **Podwójna**, `norm` lub `unorm` .

- `texture::bits_per_scalar_element`Właściwość to 32.

Jeśli wszystkie trzy nie są spełnione, `texture` obiekt jest tylko do odczytu. Pierwsze dwa warunki są sprawdzane podczas kompilacji. Generowany jest błąd kompilacji, jeśli masz kod, który próbuje zapisać do `readonly` obiektu tekstury. Warunek dla `texture::bits_per_scalar_element` został wykryty w czasie wykonywania, a środowisko uruchomieniowe generuje wyjątek [unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md) w przypadku próby zapisu do obiektu tylko do odczytu `texture` .

Poniższy przykład kodu zapisuje wartości do obiektu tekstury.

```cpp
void writeTexture() {
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {
        tex1.set(idx, 0);
    });
}
```

### <a name="copying-texture-objects"></a>Kopiowanie obiektów tekstury

Można kopiować między obiektami tekstury za pomocą funkcji [copy](reference/concurrency-namespace-functions-amp.md#copy) lub funkcji [copy_async](reference/concurrency-namespace-functions-amp.md#copy_async) , jak pokazano w poniższym przykładzie kodu.

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

Możesz również kopiować z jednej tekstury do innej za pomocą metody [Texture:: copy_to](reference/texture-class.md#copy_to) . Dwie tekstury mogą znajdować się na różnych accelerator_views. Po skopiowaniu do `writeonly_texture_view` obiektu dane są kopiowane do `texture` obiektu źródłowego. Bity na element skalarny i zakres muszą być takie same dla obiektów źródłowych i docelowych `texture` . Jeśli te wymagania nie są spełnione, środowisko uruchomieniowe zgłasza wyjątek.

## <a name="texture-view-classes"></a>Klasy widoku tekstury

C++ AMP wprowadza [klasę texture_view](../../parallel/amp/reference/texture-view-class.md) w Visual Studio 2013. Widoki tekstury obsługują takie same typy Texel i rangi jak [Klasa tekstury](../../parallel/amp/reference/texture-class.md), ale w przeciwieństwie do tekstury, zapewniają dostęp do dodatkowych funkcji sprzętu, takich jak próbkowanie tekstury i mipmapy. Widoki tekstury obsługują dostęp tylko do odczytu, tylko do zapisu i odczytu i zapisu do podstawowych danych tekstury.

- Dostęp tylko do odczytu jest udostępniany przez `texture_view<const T, N>` specjalizację szablonu, która obsługuje elementy, które mają 1, 2 lub 4 składniki, próbkowanie tekstury i dynamiczny dostęp do zakresu poziomów mipmappingu, które są określane podczas tworzenia wystąpienia widoku.

- Dostęp tylko do zapisu jest zapewniany przez niewyspecjalizowaną klasę szablonu `texture_view<T, N>` , która obsługuje elementy, które mają 2 lub 4 składniki i mogą uzyskać dostęp do jednego poziomu mipmappingu, który jest określany podczas tworzenia wystąpienia widoku. Nie obsługuje próbkowania.

- Dostęp do odczytu i zapisu jest zapewniany przez niewyspecjalizowaną klasę szablonu `texture_view<T, N>` , która, podobnie jak tekstury, obsługuje elementy, które mają tylko jeden składnik; widok może uzyskać dostęp do jednego poziomu mipmappingu, który jest określany podczas tworzenia wystąpienia. Nie obsługuje próbkowania.

Widoki tekstury są analogiczne do widoków tablicowych, ale nie zapewniają funkcji automatycznej zarządzania danymi i przenoszenia, którą [klasa array_view](../../parallel/amp/reference/array-view-class.md) udostępnia w klasie [Array](../../parallel/amp/reference/array-class.md). Dostęp do programu `texture_view` można uzyskać tylko w widoku akceleratora, w którym znajdują się bazowe dane tekstury.

### <a name="writeonly_texture_view-deprecated"></a>writeonly_texture_view przestarzałe

W przypadku Visual Studio 2013 C++ AMP wprowadza lepszą obsługę funkcji tekstury sprzętu, takich jak próbkowanie i mipmapy, które nie mogą być obsługiwane przez [klasę writeonly_texture_view](../../parallel/amp/reference/writeonly-texture-view-class.md). Nowo wprowadzona `texture_view` Klasa obsługuje nadzbiór funkcji w `writeonly_texture_view` ; w związku z tym `writeonly_texture_view` jest przestarzały.

Zalecamy — co najmniej dla nowego kodu — który jest używany `texture_view` w celu uzyskania dostępu do funkcji, które były wcześniej dostępne w programie `writeonly_texture_view` . Porównaj poniższe dwa przykłady kodu, które zapisują do obiektu tekstury, który ma dwa składniki (int_2). Należy zauważyć, że w obu przypadkach widok, `wo_tv4` ,, musi być przechwytywany przez wartość w wyrażeniu lambda. Oto przykład, który używa nowej `texture_view` klasy:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

A oto Klasa przestarzała `writeonly_texture_view` :

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

Jak widać, dwa przykłady kodu są niemal identyczne, gdy wszystko jest wykonywane podczas zapisywania na podstawowym poziomie mipmappingu. Jeśli użyto `writeonly_texture_view` w istniejącym kodzie i nie planujesz udoskonalania tego kodu, nie musisz go zmieniać. Jeśli jednak myślisz o przeniesieniu tego kodu do przodu, zalecamy ponowne zapisanie go do użycia, `texture_view` ponieważ ulepszenia w nim obsługują nowe funkcje tekstury sprzętowej. Aby uzyskać więcej informacji na temat tych nowych możliwości, przeczytaj artykuł.

Aby uzyskać więcej informacji o zaniechaniu `writeonly_texture_view` , zobacz [Omówienie projektowania widoku tekstury w C++ amp](/archive/blogs/nativeconcurrency/overview-of-the-texture-view-design-in-c-amp) na blogu programowanie równoległe w kodzie natywnym.

### <a name="instantiating-texture-view-objects"></a>Tworzenie wystąpienia obiektów widoku tekstury

Deklarowanie `texture_view` jest podobne do deklarowania `array_view` , który jest skojarzony z **tablicą**. Poniższy przykład kodu deklaruje kilka `texture` obiektów i `texture_view` obiektów, które są z nimi skojarzone.

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

Zwróć uwagę, jak widok tekstury, którego typ elementu jest niestały i ma jeden składnik jest do odczytu i zapisu, ale widok tekstury, którego typ elementu jest niestały, ale ma więcej niż jeden składnik są tylko do zapisu. Widoki tekstury typów elementów const są zawsze tylko do odczytu, ale jeśli typ elementu jest niestały, liczba składników w elemencie określa, czy jest to odczyt-zapis (1 składnik) czy tylko do zapisu (wiele składników).

Typ elementu a `texture_view` — jego stała-stałość, a także liczba składników, które posiada — również odgrywa rolę w ustaleniu, czy widok obsługuje próbkowanie tekstury oraz jak można uzyskać dostęp do poziomów mipmappingu:

|Typ|Składniki|Odczyt|Zapisywanie|Próbkowanie|Dostęp mipmappingu|
|----------|----------------|----------|-----------|--------------|-------------------|
|texture_view\<const T, N>|1, 2, 4|Tak|Nie (1)|Tak|Tak, indeksowanie. Zakres jest określany podczas tworzenia wystąpienia.|
|Texture_view\<T, N>|1<br /><br /> 2, 4|Tak<br /><br /> Nie (2)|Tak<br /><br /> Tak|Nie (1)<br /><br /> Nie (1)|Tak, jeden poziom. Poziom jest określany podczas tworzenia wystąpienia.<br /><br /> Tak, jeden poziom. Poziom jest określany podczas tworzenia wystąpienia.|

Z tej tabeli można zobaczyć, że widoki tekstury tylko do odczytu w pełni obsługują nowe możliwości programu Exchange, aby nie mogli zapisywać w widoku. Widoki tekstury z możliwością zapisu są ograniczone, ponieważ mogą uzyskać dostęp tylko do jednego poziomu mipmappingu. Widoki tekstury do odczytu i zapisu są jeszcze bardziej wyspecjalizowane niż zapisywalne, ponieważ dodają wymaganie, aby typ elementu widoku tekstury miał tylko jeden składnik. Należy zauważyć, że próbkowanie nie jest obsługiwane w przypadku widoków tekstury z możliwością zapisu, ponieważ jest to operacja zorientowana na odczyt.

### <a name="reading-from-texture-view-objects"></a>Odczytywanie z obiektów widoku tekstury

Odczytywanie niepróbkowanych danych tekstury za pośrednictwem widoku tekstury jest takie samo jak odczytywanie go ze tekstury, z tą różnicą, że tekstury są przechwytywane przez odwołanie, a widoki tekstury są przechwytywane przez wartość. Poniższy dwa przykłady kodu przedstawiają; Po pierwsze, za pomocą `texture` tylko:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {
        tex_data.set(idx, int_2(1, 1));
    });
}
```

Jest to ten sam przykład, z tą różnicą, że teraz używa `texture_view` klasy:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        tex_view.set(idx, int_2(1, 1));
    });
}
```

Widoki tekstury, których elementy są oparte na typach zmiennoprzecinkowych — na przykład, float, float_2 lub float_4 — można również odczytywać przy użyciu próbkowania tekstury, aby korzystać z obsługi sprzętu w różnych trybach filtrowania i trybach adresowania. C++ AMP obsługuje dwa tryby filtrowania, które są najczęściej używane w scenariuszach obliczeniowych — filtrowanie punktów (najbliższy sąsiad) i filtrowanie liniowe (średnia ważona) — i cztery tryby adresowania — opakowane, dublowane, zamocowane i obramowanie. Aby uzyskać więcej informacji na temat trybów adresowania, zobacz [Address_mode Enumeration](reference/concurrency-graphics-namespace-enums.md#address_mode).

Oprócz trybów, które C++ AMP obsługują bezpośrednio, można uzyskać dostęp do innych trybów filtrowania i w trybach adresowania podstawowej platformy przy użyciu interfejsów API międzyoperacyjności w celu zastosowania próbnika tekstury, który został utworzony przy użyciu interfejsów API platformy bezpośrednio. Na przykład Direct3D obsługuje inne tryby filtrowania, takie jak filtrowanie anizotropowego, i można zastosować inny tryb adresowania do każdego wymiaru tekstury. Można utworzyć próbnik tekstury, którego współrzędne są opakowane w pionie, zdublowane w poziomie i próbkowane z filtrowaniem anizotropowego przy użyciu interfejsów API Direct3D, a następnie użyć próbnika w kodzie C++ AMP przy użyciu `make_sampler` interfejsu API międzyoperacyjności. Aby uzyskać więcej informacji, zobacz [próbkowanie tekstury w C++ amp](/archive/blogs/nativeconcurrency/texture-sampling-in-c-amp) na blogu programowanie równoległe w kodzie natywnym.

Widoki tekstury obsługują również odczytywanie mipmapy. Widoki tekstury tylko do odczytu (te, które mają typ elementu const) zapewniają największą elastyczność, ponieważ zakres MIP, który jest określany podczas tworzenia wystąpienia, może być dynamicznie próbkowany, i ponieważ elementy, które mają 1, 2 lub 4 składniki są obsługiwane. Widoki tekstury do odczytu i zapisu, które mają elementy, które mają jeden składnik obsługują również mipmapy, ale tylko dla poziomu określonego podczas tworzenia wystąpienia. Aby uzyskać więcej informacji, zobacz [Texture with mipmapy](/archive/blogs/nativeconcurrency/texture-with-mipmaps) na blogu programowanie równoległe w kodzie natywnym.

### <a name="writing-to-texture-view-objects"></a>Zapisywanie do obiektów widoku tekstury

Użyj [metody texture_view:: Get](reference/texture-view-class.md#get) , aby zapisać dane w źródłowej `texture` za pomocą `texture_view` obiektu. Widok tekstury może być tylko do odczytu, do odczytu i zapisu lub tylko do zapisu. Aby widok tekstury był zapisywalny, musi mieć typ elementu inny niż const; Aby można było odczytać i zapisać widok tekstury, jego typ elementu musi mieć tylko jeden składnik. W przeciwnym razie widok tekstury jest tylko do odczytu. Można uzyskać dostęp tylko do jednego poziomu mipmappingu tekstury w czasie za pomocą widoku tekstury, a poziom jest określany podczas tworzenia wystąpienia widoku.

Ten przykład pokazuje, jak napisać na drugim, najbardziej szczegółowym poziomie mipmappingu tekstury, która ma 4 poziomy mipmappingu. Najbardziej szczegółowym poziomem mipmappingu jest poziom 0.

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

Środowisko uruchomieniowe C++ AMP obsługuje współdziałanie między programem i interfejsem `texture<T,1>` [ID3D11Texture1D](https://go.microsoft.com/fwlink/p/?linkId=248503), między innymi interfejsem `texture<T,2>` [ID3D11Texture2D](https://go.microsoft.com/fwlink/p/?linkId=255317)i między programem `texture<T,3>` a [interfejsem ID3D11Texture3D](https://go.microsoft.com/fwlink/p/?linkId=255377). Metoda [get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture) przyjmuje `texture` obiekt i zwraca `IUnknown` interfejs. Metoda [make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture) przyjmuje `IUnknown` interfejs i `accelerator_view` obiekt i zwraca `texture` obiekt.

## <a name="see-also"></a>Zobacz też

[Klasa double_2](../../parallel/amp/reference/double-2-class.md)<br/>
[Klasa double_3](../../parallel/amp/reference/double-3-class.md)<br/>
[Klasa double_4](../../parallel/amp/reference/double-4-class.md)<br/>
[Klasa float_2](../../parallel/amp/reference/float-2-class.md)<br/>
[Klasa float_3](../../parallel/amp/reference/float-3-class.md)<br/>
[Klasa float_4](../../parallel/amp/reference/float-4-class.md)<br/>
[Klasa int_2](../../parallel/amp/reference/int-2-class.md)<br/>
[Klasa int_3](../../parallel/amp/reference/int-3-class.md)<br/>
[Klasa int_4](../../parallel/amp/reference/int-4-class.md)<br/>
[Klasa norm_2](../../parallel/amp/reference/norm-2-class.md)<br/>
[Klasa norm_3](../../parallel/amp/reference/norm-3-class.md)<br/>
[Klasa norm_4](../../parallel/amp/reference/norm-4-class.md)<br/>
[short_vector — Struktura](../../parallel/amp/reference/short-vector-structure.md)<br/>
[short_vector_traits — Struktura](../../parallel/amp/reference/short-vector-traits-structure.md)<br/>
[Klasa uint_2](../../parallel/amp/reference/uint-2-class.md)<br/>
[Klasa uint_3](../../parallel/amp/reference/uint-3-class.md)<br/>
[Klasa uint_4](../../parallel/amp/reference/uint-4-class.md)<br/>
[Klasa unorm_2](../../parallel/amp/reference/unorm-2-class.md)<br/>
[Klasa unorm_3](../../parallel/amp/reference/unorm-3-class.md)<br/>
[Klasa unorm_4](../../parallel/amp/reference/unorm-4-class.md)
